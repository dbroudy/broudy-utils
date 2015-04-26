# broudy-utils
A bunch of Linux (and some MacOS) utils in Bash (and some Perl, Python)

##Introduction
These files represent some scripts that I've found useful over the years. Some
are really simple and I just include them to a have a single point of
distribution. Others might make good starting point for things you want to
accomplish. I used a liberal license so you can use them as you see fit.

##Configuration
The simpler scripts generally don't have much configuration. They may even have
assumptions about my environment and harded coded paths (Oi, The Horror!). The
more sophisticated scripts (e.g. the ones you might actually want to reuse) try
to have arguments, and might even validate that you're passing something
logical when you call them.

##Usage
It's doubtful that you'll want to clone this whole repo and use it wholesale,
but I clone this to /broudy/common on all my servers and add /broudy/common/bin
to my path.

##Scripts
Here's a listing of the scripts:

###Backup Scripts
  * [bin/ebs_backup](bin/ebs_backup)
  
    Wrapper around [ec2-consistent-snapshot](https://github.com/alestic/ec2-consistent-snapshot) for managing AWS EBS volume  Snapshots, including EBS
    volumes that are used as physical volumes in an LVM configuration. This script also manages retention periods of the snapshots.

  * [bin/db_backup](bin/db_backup)

    Backup variables types of databases to a local backup directory. I like to
    do this for quick mid-day backups as these tend to change a lot more often
    than the filesystem.

  * [bin/full_backup](bin/full_backup)

    Old script I used when I had tapes. Also takes a snapshot using LVM.

  * [bin/inc_backup](bin/inc_backup)
    
    Old incremental script I used when I had tapes.

  * [bin/remote_backup](bin/remote_backup)

    Simple script for backing up a remote system. This is most useful for
    something with a small filesystem, like a border gateway / router.

  * [bin/lv_backup](bin/lv_backup)

    Backups based purely on LVM Snapshots. 

  * [bin/update_backup](bin/update_backup)
    
    Backup script from my brief dalliance with AFS(http://www.openafs.org)

###Spam Utilities
  * [bin/dovecot-sa-learn](bin/dovecot-sa-learn)

    Used as a pipe backend to dovecot's antispam system:

    ```
      antispam_pipe_tmpdir = /tmp

      antispam_pipe_program = /broudy/common/bin/dovecot-sa-learn
      antispam_pipe_program_args =
      antispam_pipe_program_spam_arg = --spam
      antispam_pipe_program_notspam_arg = --ham
    ```
    
  * [bin/spam_learn](bin/spam_learn)

    Trains amavis (spam assassin) via a Maildir with a Junk folder

###Kerberos Admin
  * [bin/kdc_prop](bin/kdc_prop)

    Script to propegate KDC information to slaves. I found this problematic
    with NATs and don't use it anymore.

  * [bin/kdc_repl](bin/kdc_repl)

    Replicate KDC information via AFS.

###File Distribution

  * [bin/update_apps](bin/update_apps)

    Part of a scheme I had to maintain an automounted directory of
    platform-specific (uname -sm) compiled applications. This linked in the
    platform independent scripts.

  * [bin/logcheck_diff](bin/logcheck_diff)

    Part of a scheme I had to distribute configuration (mostly /etc) files
    globally. Long before things like Chef and Puppet.

  * [bin/exportweb](bin/exportweb)

    SVN hook to deploy web application.

  * [bin/updateweb](bin/updateweb)

    SVN hook to deploy web application.

###Miscellaneous
  * [bin/diff_inc](bin/diff_inc)

    No idea what this was supposed to do, but I'm sure I found it useful at
    some point.


Copyright (C) 2015  BroudyNET LLC
