# snortsnarf

README file for SnortSnarf v1.0
------------------------------------

Welcome to the release of SnortSnarf v1.0 now hosted on github: https://github.com/ebdavison/snortsnarf).  This project was recently moved from SourceForge and the original pages ar still there: http://www.sourceforge.net/projects/snortsnarf/.  


This program creates a
set of HTML pages to allow you to quickly and conveniently navigate around
alerts output by the Snort intrusion detection system (http://www.snort.org/).


This release marks the revival of the development of this project after its
creators, SiliconDefense, went defunct and their projects taken over by
Demarc.  In coordination with Demarc, this project is now back into active
development and is now housed on SourceForge.


Version 1.0 is the initial re-release of the latest available code from 
SiliconDefense and will be the stating point for future development.


The remainder of this document, as well as most other documentation in this
release at this time, are still the originals from SiliconDefense.  Once I 
get this further along I will release a new code base that contains all 
necessary updates to code and documentation to show the current state of code
ownership and responsible parties.


Ed Davison
edavison@gmail.com


Original Documentation
----------------------------------


Included in this release is:

snortsnarf.pl   -- the main SnortSnarf program
Usage           -- information on using SnortSnarf 
COPYING         -- GNU General Public License (the license for this release)
Changes         -- Changes since previous versions
README          -- this file
new-annotation-base.xml -- an empty annotation base
cgi/            -- directory containing CGI scripts for SnortSnarf
include/        -- directory containing files included by SnortSnarf
utilities/      -- directory containing utilities for SnortSnarf
nmap2html/      -- directory containing nmap2html files
sisr/           -- directory containing SISR files
sisr/cgi/       -- directory containing CGI scripts for SISR
sisr/include/   -- directory containing files included by SISR
sisr/modules/   -- directory containing SISR Pipeline modules
Time-modules/   -- David Muir Sharnoff's time modules (see README to install)


To run SnortSnarf:
   snortsnarf.pl <options> <input1 input2 ...>
   
Inputs can either be snort alert files or a Snort Mysql database such as
snort:@localhost.

See Usage for information about the input sources, the options, and what is
generated.  See the top of the utility scripts for their documentation.  See
README.nmap2html for information about nmap2html and README.SISR for
information about SISR.

This should run under most varieties of Unix.  Versions have been known to run
on OpenBSD and RedHat Linux.

snortsnarf.pl runs under Windows NT (at last report).  The CGI scripts, the
annotation feature, IPAddrContact, and nmap2html have not been tested on
Windows but are expected to work (let us know if you try them).  The file and
directory utilities in the utilities directory are not especially useful under
Windows and have not been tried.  SISR will not work under Windows.

One note.  snortsnarf.pl uses alot of memory when it is running.  If it is
taking alot of time to run for you, that probably means that you
over-stressing available memory.  You probably want to add more (preferably
physical) memory or segment your log file and run snortsnarf.pl on each.
Even better than segmenting, consider using the input filters described in
the Usage file such as -minprio, -mintime, and -maxtime. Perhaps also cut
down on your alerts with high false positives.  As long as you have enough
swap space, SnortSnarf will finish (eventually).


Installation (minimal)
----------------------
Copy the contents of the 'include' directory to someplace where it will be
found when snortsnarf.pl is run (e.g., your "site_perl" directory or the
current directory).  You can also place/leave these in './include/'.  Be sure
to move the 'include/SnortSnarf' directory there as well.

You may also need to install the time modules written by David Muir Sharnoff
(muir@idiom.com).  Version 100.010300 is included in this distribution for
your convenience (see the Time-modules directory).  You can also grab the
latest version from CPAN:

  http://search.cpan.org/search?module=Time::JulianDay

See the modules' provided README file for installation and more information. 
It should be quick and easy to install (just the usual 'perl Makefile.PL;
make; make test; make install').  Windows users may just want to copy the
Time directory to <perldir>\site\lib.


Installation (annotations)
--------------------------
If you wish to use the annotations feature of SnortSnarf, you will need to:
  +  follow the directions above for the minimal installation
  +  place the contents of the cgi directory in a directory where it
  will be executed by your web server as a CGI script, e.g., in your "cgi-bin"
  directory.
  +  set up a directory to store the annotations in persistently, e.g., by
  running the setup_anns_dir.pl utility or copying new-annotation-base.xml to
  a directory (giving it an appropriate name) and setting up the permissions
  +  if needed, install the XML::Parser Perl module
(See also the "Annotations" section of the Usage file.)


Installation (SISR)
-------------------
Follow one of the installation directions above plus the installation
directions in README.SISR.


Installation (database input)
-----------------------------
Database input is done through SnortDBInput by Ed Davison (Ed.Davison@bus.utexas.edu).  SnortDBInput is included in this distribution, but you might find a newer version on the SnortDBInput web page:

  http://www.bus.utexas.edu/services/cbacc/dbsupport/snortdbinput/

Also refer to this web page for installation help.


Mailing Lists
-------------
You are invited to sign up for one or both of the SnortSnarf mailing lists.

SnortSnarf-users:  A list for users to talk about SnortSnarf
  http://www.silicondefense.com/mailman/listinfo/snortsnarf-users
  snortsnarf-users@list.silicondefense.com
   
SnortSnarf-devel:  A gathering place for SnortSnarf developers
  http://www.silicondefense.com/mailman/listinfo/snortsnarf-users
  snortsnarf-devel@list.silicondefense.com

You can share your questions and ideas regarding SnortSnarf on the approriate
one of these lists.


Contributions
-------------
We welcome your complaints, kudos, and especially improvements and bugfixes.  
We wish for this to be a useful as possible, so your feedback and assistance
is important.  You may reach us at hoagland@SiliconDefense.com.

Thank you and happy SnortSnarfing!

-- Jim Hoagland (hoagland@SiliconDefense.com)
   Stuart Staniford (stuart@SiliconDefense.com)
   Joe McAlerney (joey@SiliconDefense.com)
