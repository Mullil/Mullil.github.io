---
layout: default
---

# Course introduction

The course teaches the student to work on the command-line. The course starts with basics of the command-line and text editors, and on the later weeks the student is introduced to working on a remote server, text processing, installing programs, writing Bash scripts and version control for example. On the final week many of the introduced topics are used on a final project.

| weeks      | topics      |
| ---------- | ----------- |
| Week 1     | Introduction to command line environments |
| Week 2     | Navigating a UNIX system |
| Week 3     | Basic corpus processing |
| Week 4     | Advanced corpus processing |
| Week 5     | Scripting and configuration files |
| Week 6     | Installing and running programs |
| Week 7     | Version control |
| Week 8     | Final project |

## Week 1

The topics of the first week include the basic commands related to directories and files. and using a text editor. I was already familiar with almost all of the commands introduced on this week, because I had already worked on a command-line environment for a few months before the course. I learned the wget-command on this week however.

Some of the commands taught on the first week:

* `cat` this command shows the contents of the file on the terminal

* `mv` this command can be used to move files/directories or rename files/directories

* `ls` this command shows the files and subdirectories in a directory

* `cp` this command copies a file/directory

* `less` this command shows the contents of a file


## Week 2

The second week's material teaches more commands to work with directories, how to use gzip and tar, changing file permissions, finding and killing processes and working on a remote server. On this week's topics processes, file permissions and remote servers were entirely new to me, so I learned how those work.

Some of the commands taught on the second week:

* `chmod` this command can be used to change permissions of a file or a directory

* `killall` this command can be used to kill the processes having a common name

* `scp` this command can be used to copy files/directories from a remote server


## Week 3

The third week's material teaches about different encoding systems, such as ASCII and utf-8, converting text files suitable for UNIX or Windows, counting words, characters and lines in a text file, and many more commands for basic corpus processing. Many of the topics introduced in this week were new to me.

Some of the commands taught on the third week:

* `tail` this command shows the last lines of a file. The amount of lines depends on the number following the command.

* `head` this command does the same as tail but for the first lines

* `dos2unix` this command converts a Windows text file to a UNIX text file

* `tr` this command can be used to replace and remove characters from a text file


## Week 4

The fourth week's material teaches more about corpus processing, using regular expressions and the sed-command. On this week I learned to make a word frequency list from a text line, to make files into sentence per line format and to transform a text file into a word n-gram list. Many of the things on this week were new to me, and I found the sed-command a bit challenging.

Some of the commands taught on the fourth week:

* `diff` this command can be used to find the difference between files

* `cat file.txt | tr -s '\n\t\r ' '\n' | tr -dc "A-Za-z0-9'\n" | sort | uniq -c | sort -nr | grep "word"` this command can be used to make a frequency list from a file and find how many times word occurs in a text file

* `tr 'A-Z' 'a-z'` this command can be used to change the characters of a file into lower case


## Week 5

The fifth week's material teaches the basics of environment variables and writing scripts. For example, this week I made little changes to my working environment with the .bashrc file. Later on I also managed to accidentally change my PATH variable in a way that almost none of my commands were working, so that is something I learned to handle carefully.

Some of the commands/scripts taught on the fifth week:

* `chmod +x script.sh` this can be used to make a script file executable

* ```bash
#!/bin/bash
file=$1
while read -r line;
do
    if [[ $line == [^aeiouy][aeiouy][^aeiouyw] ]]; then 
               echo "${line}${line: -1}er" 
    elif [ ${line: -1} == "y" ]; then 
               echo ${line%y}ier 
    elif [ ${line: -1} == "e" ]; then 
               echo ${line}r 
    else 
               echo ${line}er      fi done < $1
``` this script makes adjectives into comparative form


## Week 6

The sixth week's material teaches to install and run programs, using the python virtual environment and writing and running a Makefile. I had already experience with installing and running programs and with the python virtual environment, which I had used in a programming project. Makefile was new for me however.

Some of the commands taught on the fifth week:
* `pip install` this command is used to install python modules

* ```
BOOKS=alice christmas_carol dracula frankenstein heart_of_darkness life_of_bee moby_dick modest_propsal pride_and_prejudice tale_of_two_cities ulysses
FREQLISTS=$(BOOKS:%=results/%.freq.txt)
SENTEDBOOKS=$(BOOKS:%=results/%.sent.txt)
NO_MD_BOOKS=$(BOOKS:%=data/%.no_md.txt)
all: $(FREQLISTS) $(SENTEDBOOKS) results/all.freq.txt results/all.sent.txt
clean:
    rm -f results/* data/*no_md.txt
%.no_md.txt: %.txt
    python3 src/remove_gutenberg_metadata.py $< > $@
(results/%.freq.txt: data/%.no_md.txt
    src/freqlist.sh $< > $@
results/%.sent.txt: data/%.no_md.txt
    src/sent_per_line.sh $< > $@
data/all.no_md.txt: $(NO_MD_BOOKS)
    cat $^ > $@
no_md: $(NO_MD_BOOKS)
``` this Makefile can be used to remove metadata from books, make frequency lists and make text files into sentence per line format


## Week 7
The seventh week's material teaches version control with git. The topics taught include making a repository, cloning a repository, creating a new brancg, adding files to a local repository, commiting changes and pushing the changes to Github. I had already used version control in a project of mine, but I had not made new branches, so that is something I learned.

Some of the commands taught on the sixth week:

* `git clone` this command is used to clone a repository

* `git commit -m "commit message"` this command is used to make a commit with a message

* `git push` this command is used to push changes into the repository

## Final project
The material for the final project teaches using GitHub pages and Jekyll, forking a repository, running a server locally and formatting code in markdown. I had not used GitHub pages before, so this is something I learned. I also learned some basics about markdown.

a command I learned:

* `bundle exec jekyll serve` this command starts a local server for a Jekyll site.


![Image](https://imgs.xkcd.com/comics/computer_problems.png)
[https://xkcd.com/722/](https://xkcd.com/722/)
