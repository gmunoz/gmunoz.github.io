---
layout: post
title: Plans to write a custom module in Perl
category: Ansible
tags: ['Ansible', 'Perl']
published: true
---

I'm getting an idea to implement some custom modules for [Ansible](http://www.ansible.com/), but I'd prefer to use Perl instead of the built-in Python framework.

I've found a small project on github of someone implementing the same semantics of the built-in Python [AnsibleModule](http://docs.ansible.com/ansible/developing_modules.html) here: [https://github.com/PWBENNETT/perl-Ansible-Module]()

It looks promising, although, I didn't understand **why** it was doing everything that it was. I re-read [Lorin Hochstein's](https://twitter.com/lhochstein) excellent chapter on writing custom modules in [Ansible Up & Running](http://www.ansiblebook.com/) and it became clear that the example module in Hochstein's book would end up being a literal translation of the Python code to Perl. Just a bunch of helpers to get the inputs and outputs working as expected.

The only thing that stands out as a problem is that using the Python framework lets you include non-system modules and have them packaged by Ansible. The packaged script and dependencies is the thing that gets copied to the hosts to execute. Using Perl the only way I see working around this is having a two-stage process using [pp](https://metacpan.org/pod/pp) to package the script and dependent modules as a single script that only requires system Perl.

The plan is:

* git clone [https://github.com/PWBENNETT/perl-Ansible-Module.git]() into my Ansible playbook repo
* Tranlate the custom Ansible module in [Ansible Up & Running](http://www.ansiblebook.com/) into Perl using Ansible::Module
* Create a Makefile that uses [pp](https://metacpan.org/pod/pp) to create the final artifact.
* Test the new custom module out
* Send feedback to [https://github.com/PWBENNETT]()
