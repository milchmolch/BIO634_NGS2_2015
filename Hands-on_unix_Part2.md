# Exercises Linux Tutorial - Part 2


## Stefan Wyder

### URPP Evolution
### University of Zurich

---------------

Many thanks to Gregor Roth (von Mering group / IMLS, UZH) who agreed to share some exercises.

## Connecting to a remote host, transferring files

**Command**

**Task**


Command | Meaning |
-- | ---|
ssh -X *user*@*hostname* | Connect to server
scp \<what\> \<towhere\> | Transfer file from/to server
sftp *user*@*hostname* | Transfer file from/to server (interactive)|


`ssh` ("secure shell") is a secure protocol for remote login and also for executing commands in a remote machine. To connect to a remote machine using `ssh`, simply type:

$ **ssh** username@130.60.201.40

inside your local computer shell. You will be asked for the password and after you successfully login, you can work with the remote machine in the same way as you work on your local machine. (You are dropped at your home directory). But ssh can’t transfer files, for that you can use another program called `sftp`. Disconnect before you go on to the next step (Ctrl+d).

$ **sftp** username@130.60.201.40

After you are connected, you can use “cd”, “mkdir”, “rm” to navigate around and manipulate files on the remote computer. To upload a file from your local computer to the remote computer, simply use “put *filename*”. Filename here refers to a file on your local computer that will be uploaded to the remote computer.

### Exercise
1. Create a new file with **nano** on your local computer. Save a few lines of text to the file. 
2. Connect to the remote server using **sftp** and upload the file using the **put** command inside the sftp session.
3. Login to the remote server and inspect the file content using `more`.


## Writing and executing a perl script

Many scripts in bioinformatics are written in perl. You have used the **nano** editor from the first exercise in part 1 of the Tutorial. Try to copy/paste the below simple perl program into a file and execute it. The hello world perl script:
```
\#!/usr/bin/perl
print "Hello World.\\n";
```
Copy the above 2 lines and save them to the file `hello.pl`. The first line tells the Unix shell to interpret the program with **perl**. In order to run the program you can either start it with:
```
$ perl hello.pl
```
The output on the screen should be `Hello World`.

Optionally you can make your file executable by typing:
```
$ chmod +x hello.pl
```
And now you can simply type:
```
$ ./hello.pl
```
Note the `./` at the start of the command. This is because the directory where we stored `hello.pl` is not in the system variable `$PATH`.

### Exercise
Check the file's permissions using `ls -l`. Remove the permission to execute it and check the permissions again.

 
## Compressing/Decompressing files

### File compression and decompression**


**Command** | **Meaning** |
---|----
**gzip** *filename* | compress file with gzip (adds .gz extension) |
**gunzip** *filename.gz* | decompress file with gzip (removes .gz extension) |
**zmore** *filename.gz* | display file content of a gzip compressed file
**zless** *filename.gz* | display file content of a gzip compressed file
**tar xfz** *filename.tar.gz* | extract/decompress files from tar.gz archive
**tar** **zcvf** *archive.tar.gz folder\_to\_compress* | creates archive.tar.gz
**unzip** *filename.zip* | unzip archive
**zgrep** *pattern* filename.gz | search text/pattern in a compressed file


### Exercise
Use the program **wget** to download the FASTA file of proteins from:

[ftp://ftp.ensembl.org/pub/release-71/fasta/homo\_sapiens/pep/Homo\_sapiens.GRCh37.71.pep.all.fa.gz](ftp://ftp.ensembl.org/pub/release-71/fasta/homo_sapiens/pep/Homo_sapiens.GRCh37.71.pep.all.fa.gz)

When downloaded, **gunzip** the file. Then count how many proteins are in the file.

Now **gzip** the file and try to count the number of proteins without using **gunzip** directly from the compressed file.


## Exercise: Download and install bowtie2 software

Bowtie2 is a short-sequence read aligner (e.g. 150nt long). The reads are aligned to a reference sequence (e.g. human genome).

Make a new \~/software directory and download bowtie2 source code using **wget** from this link:

[http://downloads.sourceforge.net/project/bowtie-bio/bowtie2/2.1.0/bowtie2-2.1.0-source.zip](http://downloads.sourceforge.net/project/bowtie-bio/bowtie2/2.1.0/bowtie2-2.1.0-source.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fbowtie-bio%2Ffiles%2Fbowtie2%2F2.1.0%2F&ts=1368102757&use_mirror=heanet)

Unzip the file, change to the unzipped folder and compile the source by running **make**:

$ make

You have compiled your first program. If you got an error message first install the gcc compiler on your system (see Appendix) and then repeat make. You can now try to run bowtie2:

$ ./bowtie2

Since bowtie2 directory is not in the \$PATH environment variable (a list of directory locations which Unix searches for commands when you try to run them), you can only run it from the bowtie2-2.1.0 folder or by providing the full path (e.g under Linux: /home/swyder/software/bowtie... or under Mac OS X: /Users/swyder/software/bowtie). You can add the bowtie2 folder to the \$PATH:

$ export PATH=\$PATH:/home/**username**/software/bowtie2-2.1.0

Now you can simply type “bowtie2” anywhere (in any directory) and the **shell** will find the **bowtie2** software. The modification to \$PATH affects only the current window until it is closed – you have to add it to \~/.bash\_profile to make it permanent.


## Exercise: Try out your package manager

You can often save time and work using the package manager as compiling software from source can be painful and time-consuming. The package manager helps you to install, upgrade and remove software. But first we have to check whether a software is available in the repositories. Try out the package manager of your system:

For Ubuntu users:

The Linux package management systems are comprehensive (for Ubuntu > 35'000 software packages), powerful and still easy to use – one of the advantages of the Linux world. It also checks automatically for software updates and your system will propose you from time to time to upgrade your system.
You can interact with the package manager using a graphical user interface or the command line. There is a sort of App Store called "Ubuntu Software Center" which includes software reviews. To run it, click on topmost icon in the dock on the left and type "Ubuntu Software Center" in the search field. Try it.





## Appendix

### Installation of the gcc compiler for C/C++

Typically open-source software is written in C/C++, to compile it from source (and make a binary) one needs a compiler. If its not available on your system, you have to install it

**Linux**: install the C++ compiler using the package manager is very easy, under Ubuntu simply type in the terminal: sudo apt-get install g++ . Of course we could install the package also by using the "Ubuntu Software Center".



### Getting help

Command | Description
---|------
**man** *command*|display manual page of command|
*command* **-h**|display shorter manual page of command (only GNUtools, not in Mac OS X)|
*Program* **--help**|display help / usage information for software/scripts|
*Program* **-h**|display help / usage information for software/scripts|

**File and folder manipulation**

Command | Description
---|------
**pwd**|display current folder|
**ls -l** *path*|list files and folders|
**cd** *path*|change folder to path|
**cd** \~|change folder to home folder|
**mkdir** *dir\_name*|make folder|
**rmdir** *dir\_name*|remove folder|
**cp** *source* *dest*|copy file/folder and all its contents|

**File compression and decompression**

Command | Description
---|------
**gzip** *filename*|compress file with gzip (adds .gz extension)|
**gunzip** *filename.gz*|decompress fildecompress file with gzip (removes .gz extension)|
**zmore** *filename.gz* | |
**zless** *filename.gz*|file decompress display file content of a gzip compressed file|
**tar xfz** *filename.tar.gz*|extract/decompress files from tar.gz archive|
**tar** **zcvf** *archive.tar.gz folder\_to\_compress*|creates archive.tar.gz|
**unzip** *filename.zip*|unzip archive|
**zgrep** *pattern* *filename.gz*|search text/pattern in a compressed file|

**Text processing**

Command | Description
---|------
**grep** *pattern* *filename*|search text/pattern|
**cut**|extract column|
**tr**|substitute/delete text/pattern|
**less**|display file content|
**wc**|count number of lines in file|
**sort**|sort lines|
**uniq**|remove lines occurring more than once|
**comm** *filename*|compress file with gzip (adds .gz extension)|

**Network and file transfer**

Command | Description
---|------
**wget** URL|download file (also html page) and save to current folder|
**ssh** –X *username@host*|remote login to host with username
| disconnect by Ctrl+d|
**sftp** username@host|remote login to host with username and transfer files|
**scp** source target|copy files from/to host
scp username@host:\~/path/*file* .|
scp *file* username@host:\~/path*/file*| 

**Permissions and Ownership**

These commands also work on directories

Command | Description
---|------
**chmod** ug+rx *filename*|Set write and execute permissions to user and group|
**chown** user *filename*|changes user ownership|
**chgrp** group *filename*|changes group ownership|
**chown** user:group *filename*|changes user & group ownership|

**System information & processes**

Command | Description
---|------
**uname -a**|display system information|
**df -h**|list mounted disks with available space|
**du -h** *path*|show space usage|
**top**|display running processes|
**kill** *pid*|kill process|

“**vi” editor**

Command | Description
---|------
**$ vi** *filename*|start editing file with vi|
**i**|switch to “insert” mode|
**ESC**|switch to “command” mode|
**:w**|save|
**:q**|quit|
**:x**|save and quit|
**/\<pattern\>**|search for pattern, \<n\> gives you the next match|
**:q!**|quit without saving changes|
