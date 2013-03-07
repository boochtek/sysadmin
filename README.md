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

Installation Helpers
--------------------
    package_install $package_name [$version]
    package_remove $package_name
    package_is_installed $package_name [$version]
    package_manager_name
    package_manager_update
    command_exists $command
    command_accepts_arguments $command [$args...]
    generate_password
    add_line_to_file $file $line [$after_existing_line_by_content_or_line_number]
    file_contains_line $file $line_content
    warn_if_not_root
    fail_if_not_root
    run_as $user $command [$args...]
    service $service_name $restart_or_stop_or_status

Tool to modify BIND zone files
------------------------------
  * Name it ''zone-update'' or ''named-updatezone''.
    * Using ''named-updatezone'' would make it analagous to ''named-checkzone''.
      * Pro: Pretty similar in functionality to ''named-checkzone''.
      * Con: Implies that it's an official part of BIND.
  * Make sure to explain how it differs from ''nsupdate''.
  * Initial implementation will probably be in Ruby, because that's easiest for me.
    * Use [methadone](http://davetron5000.github.com/methadone/)
  * Examples:
    * named-updatezone add fqdn [class] TYPE [ttl] value
      * Provide a flag to allow multiple entries of a given fqdn and type.
    * named-updatezone del fqdn [class] [TYPE] [ttl] [value]
      * AKA delete, rem, remove
      * TYPE and value are optional, if the record to delete can be unambiguously determined without them.
    * named-updatezone update fqdn [class] TYPE [ttl] value
      * AKA change
  * Options (can also be specificed in environment variables):
    * Where the zone files are located.
      * Makes it really easy to run an automated test suite.
    * Whether to use FQDNs in the zone files, or relative to the zone.
    * What order to put the records in.
      * By type: SOA, NS, TXT, SPF, all DNSSEC records, A/AAAA, MX, CNAME, SRV, others.
      * Alphabetical
      * Append
    * Whether to reformat existing records (only white space and FQDN added/removed).
  * What it does:
    * Determines what zone file to update, from the fqdn.
      * Can handle subzone files, as well as subzones in the top-level zone file.
    * Checks to make sure that the zone file is valid before starting (named-checkzone).
    * Checks to make sure that the requested change is valid.
      * Won't let you make a CNAME record if a record with that name already exists.
      * Won't let you make a record if a CNAME record with that name already exists.
      * Recognizes exception to the CNAME rule for DNSSEC-related records.
      * Checks for CNAMEs pointing at CNAMEs.
    * Makes a backup of the zone file.
    * Increments the zone file serial number.
      * Is smart enough to determine whether it's a date-based S/N, and does the right thing.
    * Updates the zone file.
    * Checks to make sure that the zone file is still valid (named-checkzone).
    * DOES NOT RELOAD BIND.


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
