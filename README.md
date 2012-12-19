About
=====

These are some scripts that we have written to make GNU/Linux (and UNIX) system
administration easier. They're quite varied in their utility and quality.


Installation
============

To use these, it's best to just copy each file that you need directly from
Github. We recommend that you clone the repo on Github first, so you can make
any customized changes. Having your own repo also ensures that you get what
you're expecting, in case we make changes in our repo.

Most of the scripts will work best when installed in ``/usr/local/sbin``,
``/usr/local/bin``, or ``~/bin``. To copy them, use ``wget`` or something
similar. For example:

    cd ~/bin
    wget https://raw.github.com/boochtek/sysadmin/master/sbin/a2addsite
    chmod +x a2addsite


Usage
=====

  * ``sbin/a2addsite`` - Create directories and a basic config file for an Apache 2 web site.
  * ``sbin/a2addsitealias`` - Add domain name aliases to the config file for an Apache 2 web site.
  * ``sbin/a2setsiteowner`` - Set owner of a web site directory, config file, and log files for an Apache 2 web site.


TODO
====

  * Tools to modify BIND zone files.


License
=======

This software is Copyright &copy; 2011 by BoochTek, LLC.

This software is licensed under the MIT License:

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
