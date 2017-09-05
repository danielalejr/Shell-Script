#!/bin/bash

# the aim of this of this script is the extraction of Domain and ip columns of the shells founds 

# the archive Shellslist.csv is ubicated in ~/Documents/script/Shellslist.csv you can change this.

# The information is organized in columns separated by "," and organized like follows:
#IP,URL,PASS,EN/SU,Customer,Date,Agent. We are interested in the first and second columns.

Dir=$1

# Only the Ip
awk -F',' '{ print $1}' $Dir | sort -u > IP.txt
# Only the Domain
awk -F',' '{ print $2}' $Dir | sort -u > Domain.txt
# The Domain and the Ip
awk -F',' '{ print $1 " " $2 }' $Dir | sort -u >IP_Domain.txt
# The list of shells
cat Domain.txt | rev | awk -F'/' '{ print $1}' | rev | sort -u | cat -n > shells.txt
