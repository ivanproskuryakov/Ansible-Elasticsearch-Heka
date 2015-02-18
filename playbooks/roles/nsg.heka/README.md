Role Name
========

This is a Ansible role that install Heka, the role contains basic service 
script (hekad) that loads all configurations from `/etc/hekad.d`.

Requirements
------------

This role will only setup the basic installation and a Heka Dashboard (can 
be disabled). You need to add the desired configuration files to enable 
inputs, outputs, ... Either update this role or add these to the playbook. 
There would be a lot of work, and very little to gain to maintain a complete 
up-to-date list of all available inputs/outputs ...

Role Variables
--------------

There are several default variables in `defaults/main.yml`, overload them on 
the appropriate place if you have the need.

Dependencies
------------

No

Example Playbook
-------------------------

Include like you normally do:

    - hosts: servers
      roles:
         - nsg.heka

License
-------

Copyright (c) 2014 Stefan Berggren <nsg@nsg.cc>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

Author Information
------------------

You are free to contact me at nsg@nsg.cc or open a issue at
https://github.com/nsg/ansible-heka
