IPAclient
========

This module configures clients to use FreeIPA with as little fuss as possible.
Based on Stephen Benjamin's [puppet-ipaclient](https://github.com/stbenjam/puppet-ipaclient)

Supported Platforms
-------------------

Tested on:
  * CentOS 6

It should hopefully work on any recent Red Hat or Debian
distro with IPA packages.  

Examples
--------

See the manifests for full descriptions of the various parameters
available.

Discovery register (w/ sane defaults: sudo, mkhomedir, ssh, etc):

    class { 'ipaclient':
      password => "rainbows"
    }

More complex:

    class { 'ipaclient':
       principal       => "admin",
       password        => "unicorns",
       server          => ["ipa01.pixiedust.com", "ipa02.pixiedust.com"]
       domain          => "pixiedust.com",
       hostname	       => "ipaclient01.pixiedust.com"
       realm           => "PIXIEDUST.COM",
       mkhomedir       => false,
       automount       => true,
       ssh             => false,
       fixed_primary   => true
       automount_location => "home",
    }

Simple sudoers setup:

    class { 'ipaclient::sudoers': }

Automounter only:

    class { 'ipaclient::automount':
        location    => 'home',
        server      => 'ipa01.pixiedust.com',
    }

MIT License
-----------
Original work **Copyright (c) 2014 Stephen Benjamin**
Modified work Copyright 2014 Victor Andrade

Permission is hereby granted, free of charge, to any person obtaining 
a copy of this software and associated documentation files (the "Software"), 
to deal in the Software without restriction, including without limitation 
the rights to use, copy, modify, merge, publish, distribute, sublicense, 
and/or sell copies of the Software, and to permit persons to whom the Software 
is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
 all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, 
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE 
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER 
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, 
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN 
THE SOFTWARE.

