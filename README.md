extract-mbz
===========

Extract content from Moodle backup files (.mbz)

Background: 
Working on a request from a professor I was surprised to find that there wasn't yet a tool to extract a Moodle backup archive, much as bFree does for Blackboard archives. After finding only this proof of concept python script on the web (http://www.reades.com/2012/11/29/mb-archives/) I figured I'd take a stab at it. My initial release efforts (I've used it for a few extract requests already) are here. Documentation is below and my python script is attached. 

And lest I seem too dismissive, I owe my efforts to Jon Reades and his proof of concept python script. Thanks!

Status:
This will not work with Moodle backup files created since v2.9; the course backup file format has changed from .zip to .tar.gz 
I have a working version for .tar.gz under final development. 

I have really been simply hacking at this, learning intermediate Python as I go, extracting "targets of opportunity" from the backup archive as they seem useful and easy. Right now this is still a command line script which needs a lot of work, but it does grab most of the files in a Moodle course and all the URLs. The files are simply dumped into appropriate folders with their original names (or simple conflict resolution of their name). The URLs are collected into an HTML file. A log file is generated with more information. 

There are many more useful items for retrieval (student roster, grades, ...) and more improvements to be made. See details below. 

I've tested it so far on:

    Mac OS 10.7.5 with the native Python
    Windows 7 with Python.Org Python

extracting Files and URLs.
Requirements:
Python 2.7 (and for the uninitiated, note that newer is not better - Python 3 does not run a v2.7 program!) 

    Installed with most Mac OS X versions

    Available for download for Windows from Python.Org

Usage:

    Create a directory (folder) for your archive
    Unzip your Moodle .mbz file into that directory (note that these archives are "flat" - if you extract them in a directory the contents will be in that directory with everything else; you may be used to archives which include a subdirectory into which the contents are unzipped)
    Command line - <path-to-python-program-if-needed>python extract-mbz.py <your-mbs-directory> 
        Command line help - use a question mark as the parameter - <path-to-python-program-if-needed>python extract-mbz.py ?  

Technical Background:
As already stated, I've been hacking at this so far, and not using detailed specifications to develop this tool. The proof of concept showed me how to get files and I figured out how to get URLs by looking at the .xml files. This probably won't work for more complex data structures such as grades so we'll need to understand the details of the Moodle Backup process. 

As expected, Moodle uses an xml format to create course backups. The xml files and related documents are compressed in a .zip format archive. One uses any unzip-compatible program to retrieve the contents. 

http://docs.moodle.org/dev/Backup_2.0_for_developers

Information page: https://sites.google.com/a/colgate.edu/dwheeler/Home/extract-mbz
