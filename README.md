# Keystone
Initial Commit in February 2014
Martin Murfitt <mmurfitt@trustwave.com>
http://www.trustwave.com
http://www.spiderlabs.com

INTRODUCTION
============

The Keystone Rocks is a series introducing tools for data manipulation during
penetration tests. Each tool has its own section which is documented in this
README file. The tools introduced by each section are listed below.

Please note, each tool may be updated in the future if improvements are made to
it. We suggest cloning the entire repository to ensure each is up to date.

INDEX

Part 1
======
ipsort		Perl script to identify IP addresses and print them out
scomm		A wrapper around the UNIX utility "comm" to avoid sorting files

# ipsort

INTRODUCTION
============

It's extremely useful to be able to grep for IP addresses. This is used so often
we don't want to have to formulate a regex to discover them repeatedly, so this
tiny utility can be used in general contetx to pull out IPv4 IP addresses and
print them out.

REQUIREMENTS
============
perl

USAGE
=====
ipsort <file> [file2...fileN] or cat <file> [file2...fileN] | ipsort

Options:
    -c or --commas   Separate the list by space-separated commas, rather than
    one IP per line.
    -u or --unique   Uniquely sort the list as well, to avoid duplicate IPs.
    -s or --string   Use this string to separate the IPs. Eg. -s :
    -m or --multiple Search for multiple IP addresses per line.
    -h or --help     Display this usage message.

Examples:
   ipsort fileone.txt filetwo.txt filethree.txt
   cat results.txt | ipsort -um > discoveredips.txt

# scomm

INTRODUCTION
============

comm on its own is a very useful standard UNIX utility but only works if the
files being compared are sorted in lexical order.  As that's usually not the
case, scomm is designed as a useful replacement for comm (as a wrapper to it
rather than a standalone program).

REQUIREMENTS
============
comm
sort

USAGE
=====
scomm <file1> <file2> [-123] [-u for unique]

The options -123 can be used in any combination and suppress the output of one
of the three columns, which are:

1 - Lines unique to file1
2 - Lines unique to file2
3 - Lines common to both files

E.g.
To show only lines unique to file1, do scomm file1 file2 -23
To show only lines common to both files, do scomm file1 file2 -12

The option -u may be passed, either after any -123 options or at the end of the
line. This passes the "-u" option to the sort utility first - useful for
ignoring duplicate lines.

COPYRIGHT
=========

ipsort - find, sort and print IP addresses
scomm  - Sorted compare, a wrapper/replacement for comm
Martin Murfitt
Copyright (C) 2014 Trustwave
 
This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
 
You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>





