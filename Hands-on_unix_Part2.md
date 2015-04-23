#Exercises Linux Tutorial - Part 2

![](Unix_Part2_html_c773f128.jpg)

##Stefan Wyder

###URPP Evolution
###University of Zurich

---------------

Many thanks to Gregor Roth (von Mering group / IMLS, UZH) who agreed to share some exercises.

![](Unix_Part2_html_a660a3f5.png)
##Exercise 1: connecting to a remote host, transferring files

**Command**

**Task**

ssh -X *user*@*hostname*

Connect to server

scp \<what\> \<towhere\>

Transfer file from/to server

sftp *user*@*hostname*

Transfer file from/to server

(interactive)

ssh ("secure shell") is a secure protocol for remote login and also for executing commands in a remote machine. To connect to a remote machine using ssh, simply type:

\$ **ssh** username@130.60.201.40

inside your local computer shell. You will be asked for the password and after you successfully login, you can work with the remote machine in the same way as you work on your local machine. (You are dropped at your home directory). But ssh can’t transfer files, for that you can use another program called sftp. Disconnect before you go on to the next step (Ctrl+d).

\$ **sftp** username@130.60.201.40

After you are connected, you can use “cd”, “mkdir”, “rm” to navigate around and manipulate files on the remote computer. To upload a file from your local computer to the remote computer, simply use “put *filename*”. Filename here refers to a file on your local computer that will be uploaded to the remote computer.

||
|![](Unix_Part2_html_15e79550.jpg)|Create a new file with **nano** on your local computer. Save a few lines of text to the file. Connect to the remote server using **sftp** and upload the file using the **put** command inside the sftp session.|

For Windows Users only:

To work on a server you don't need to first start Linux in a Virtual Machine and to connect from there. There is an alternative by using PuTTY, a SSH client.

1.  Download and install PuTTY
    [http://www.chiark.greenend.org.uk/\~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

2.  Download and install Xming (graphics emulation)

[http://www.straightrunning.com/XmingNotes/\#head-13](http://www.straightrunning.com/XmingNotes/#head-13)

For file transfer use Use WinSCP or FileZilla

![](Unix_Part2_html_a660a3f5.png)
##Exercise 2: Writing and executing a perl script

Many scripts in bioinformatics are written in perl. You have used the **nano** editor from the first exercise in part 1 of the Tutorial. Try to copy/paste the below simple perl program into a file and execute it. The hello world perl script:

\#!/usr/bin/perl
print "Hello World.\\n";

Copy the above 2 lines and save them to the file “hello.pl”. The first line tells the Unix shell to interpret the program with **perl**. In order to run the program you can either start it with:

\$ perl hello.pl

The output on the screen should be “Hello World.”

Or you can make your file executable by typing:

\$ chmod +x hello.pl

And now you can simply type:

\$ ./hello.pl

Note the “./” at the start of the command. This is because the directory where we stored hello.pl is not in the system variable \$PATH.

Check the file's permissions using ls -l. Remove the permission to execute it and check the permissions again.

![](Unix_Part2_html_a660a3f5.png) 
##Exercise 3: Compressing/Decompressing files

**File compression and decompression**

**Command**

**Meaning**

**gzip** *filename*

compress file with gzip
(adds .gz extension)

**gunzip** *filename.gz*

decompress file with gzip
(removes .gz extension)

**zmore** *filename.gz*
**zless** *filename.gz*

display file content of a gzip compressed file

**tar xfz** *filename.tar.gz*

extract/decompress files from tar.gz archive

**tar** **zcvf** *archive.tar.gz folder\_to\_compress*

creates archive.tar.gz

**unzip** *filename.zip*

unzip archive

**zgrep** *pattern* filename.gz

search text/pattern in a compressed file

Use the program **wget** to download the FASTA file of proteins from:

[ftp://ftp.ensembl.org/pub/release-71/fasta/homo\_sapiens/pep/Homo\_sapiens.GRCh37.71.pep.all.fa.gz](ftp://ftp.ensembl.org/pub/release-71/fasta/homo_sapiens/pep/Homo_sapiens.GRCh37.71.pep.all.fa.gz)

When downloaded, **gunzip** the file. Then count how many proteins are in the file (![](Unix_Part2_html_cd372b94.png)use **grep** and **wc**).

Now **gzip** the file and try to count the number of proteins without using **gunzip**.

For Mac OS X users only:

On Mac OS X wget is not available by default, you can install it with your favorite package manager e.g if you have installed homebrew, simply type: brew install wget
Alternatively, if you don’t want to install wget, use a web browser to download the file.

![](Unix_Part2_html_a660a3f5.png)
##Exercise 4: Write a simple bash script

Often, you would like to run the same command with different parameters. As an exercise, write a simple bash script that will output numbers from 1 to 100. Use a **for** loop.

\#!/bin/bash

for i in {1..100}

do

echo \$i

done

Save the above code to a file (e.g. script.sh), make the file executable (+x flag) and run it.

![](Unix_Part2_html_15e79550.jpg)What is the output?

![](Unix_Part2_html_a660a3f5.png) 
##Exercise 5: Iterating over files

First lets prepare some files: Make a new directory called FASTAS and change into the new directory.

Copy 10 Fasta files from the server by typing:

\$ scp [studi15@130.60.201.40:\~/FASTAS/\*](mailto:studi15@130.60.201.40:~/FASTAS/seq*) .

By using the same concept (**for** loop) from exercise 4, can you try to iterate over all fasta files in a directory, print their name and the sequence length in each file?

![](Unix_Part2_html_cd372b94.png)for filename in \*.fasta

1. Use **wc** to count the sequence length in each file. Make sure not to include the sequence header

2. Count the number of Methionines (M) in each sequence (use grep -o)

![](Unix_Part2_html_a660a3f5.png)
## Exercise 6: Reading in argument

We often need to pass information to our script (e.g. for a cut-off, a parameter or an input file).

\#!/bin/bash

firstarg=\$1

secondarg=\$2

echo "You have entered \\"\$firstarg\\" and \\"\$secondarg\\""

The backslash in front of " is needed for escaping as " is used a string delimiter.

Try to write a shell script which takes as argument a filename. The script shall then display all Arabidopsis genes contained in the file. Use as input file TAIR10\_GFF3\_genes.gff from part 1 of the tutorial.

![](Unix_Part2_html_a660a3f5.png) 
## Exercise 7: Download and install bowtie2 software

Bowtie2 is a short-sequence read aligner (e.g. 150nt long). The reads are aligned to a reference sequence (e.g. human genome).

Make a new \~/software directory and download bowtie2 source code using **wget** from this link:

[http://downloads.sourceforge.net/project/bowtie-bio/bowtie2/2.1.0/bowtie2-2.1.0-source.zip](http://downloads.sourceforge.net/project/bowtie-bio/bowtie2/2.1.0/bowtie2-2.1.0-source.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fbowtie-bio%2Ffiles%2Fbowtie2%2F2.1.0%2F&ts=1368102757&use_mirror=heanet)

Unzip the file, change to the unzipped folder and compile the source by running **make**:

\$ make

You have compiled your first program. If you got an error message first install the gcc compiler on your system (see Appendix) and then repeat make. You can now try to run bowtie2:

\$ ./bowtie2

Since bowtie2 directory is not in the \$PATH environment variable (a list of directory locations which Unix searches for commands when you try to run them), you can only run it from the bowtie2-2.1.0 folder or by providing the full path (e.g under Linux: /home/swyder/software/bowtie... or under Mac OS X: /Users/swyder/software/bowtie). You can add the bowtie2 folder to the \$PATH:

\$ export PATH=\$PATH:/home/**username**/software/bowtie2-2.1.0

Now you can simply type “bowtie2” anywhere (in any directory) and the **shell** will find the **bowtie2** software. The modification to \$PATH affects only the current window until it is closed – you have to add it to \~/.bash\_profile to make it permanent.

![](Unix_Part2_html_a660a3f5.png) 
##Exercise 8: Try out your package manager

You can often save time and work using the package manager as compiling software from source can be painful and time-consuming. The package manager helps you to install, upgrade and remove software. But first we have to check whether a software is available in the repositories. Try out the package manager of your system:

For Ubuntu users:

The Linux package management systems are comprehensive (for Ubuntu \> 35'000 software packages), powerful and still easy to use – one of the advantages of the Linux world. It also checks automatically for software updates and your system will propose you from time to time to upgrade your system.
You can interact with the package manager using a graphical user interface or the command line. There is a sort of App Store called "Ubuntu Software Center" which includes software reviews. To run it, click on topmost icon in the dock on the left and type "Ubuntu Software Center" in the search field. Try it.

For Mac OS X users:

Unfortunately the package managers for Mac OS X are lagging behind the Linux world. But if you work regularly on the command line you will need a package manager. The best one in my opinion is homebrew. To install it, you first need to install the command line tools from XCode (see Appendix). Once they are installed go to the homebrew website and follow the instructions there.
Check for some software you know whether it is available under homebrew (or in your package manager of choice). To check bowtie2 e.g. type in the terminal:

\$ brew search bowtie2

\$ brew install *PackageName
*

To get help on brew, simply type brew

![](Unix_Part2_html_a660a3f5.png)
##Exercise 9: Exploring a FASTA format file

*Moraxella catarrhalis* (http://www.ncbi.nlm.nih.gov/nuccore/NC\_014147) is an interesting Gram-negative Gammaproteobacterium and a human pathogen of the respiratory tract. The whole genome sequence is already available on the server in the Morax/NC\_014147.fasta file. The FASTA format is widely used in sequence distribution, see the description at [http://en.wikipedia.org/wiki/FASTA\_format](http://en.wikipedia.org/wiki/FASTA_format).

Use **grep** to find out how many chromosomes are present in the file. Use **grep** (![](Unix_Part2_html_cd372b94.png)-v) to only print out the genomic sequence. How large is the genome?

Now look at the RNA-seq data sample stored in the Morax/rnaseq.fasta.gz file. This file includes qualities for each nucleotide (see FASTQ description at [http://en.wikipedia.org/wiki/FASTQ\_format](http://en.wikipedia.org/wiki/FASTQ_format)).

![](Unix_Part2_html_15e79550.jpg)How many reads are in the file?

![](Unix_Part2_html_a660a3f5.png)
## Exercise 10: Searching for short sequences in the *Moraxella catarrhalis* genome

![](Unix_Part2_html_15e79550.jpg)Is the sequence “CTGTATCACCGATTT” present in the *Moraxella* genome (Morax/ NC\_014147.fasta)?

![](Unix_Part2_html_cd372b94.png)You can simply use **grep** to find out.

You can also use **bowtie2**. First build the index of the *Moraxella* reference genome. The format is: “bowtie2-build \<fasta\_file\> \<custom\_index\_name\>”. In the Morax folder, you could use:

\$ bowtie2-build NC\_014147.fasta Morax

Once the index is created (you do this only once for each reference genome, i.e. each FASTA file), you align one read (sequence) to the genome by typing:

\$ bowtie2 Morax -ac CTGTATCACCGATTT \> Morax.sam

Explore the SAM results file with “less -S”. The parameter “-S” prevents line wraps, so you can see one alignment per line.

![](Unix_Part2_html_15e79550.jpg)Does **bowtie2** find more alignments compared to grep? Why could that be?

![](Unix_Part2_html_a660a3f5.png)
## Exercise 11: Alignment of RNA-seq sample reads to the *Moraxella catarrhalis* genome

To align the RNA-seq reads in the rnaseq.fastq file, you first need to index the *Moraxella catarrhalis*genome. Use bowtie2-build to create an index with name **Morax**.

\$ bowtie2-build fasta\_file custom\_index\_name

After you created the index, you can align the reads by typing:

\$ bowtie2 Morax -U rnaseq.fastq.gz \> Morax2.sam

The results are returned in SAM format and stored to the Morax2.sam file. How many reads align?

Check what are the options of bowtie2. Use Bowtie2 manual ([http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml](http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml)) to explore and change parameters. How do different parameters influence your results?

##Appendix

###Installation of the gcc compiler for C/C++

Typically open-source software is written in C/C++, to compile it from source (and make a binary) one needs a compiler. If its not available on your system, you have to install it

![](Unix_Part2_html_2d55ac32.gif)**Linux**: install the C++ compiler using the package manager is very easy, under Ubuntu simply type in the terminal: sudo apt-get install g++ . Of course we could install the package also by using the "Ubuntu Software Center".

**Mac OS X**: Depending on the version of Mac OS X you are using installation differs. First you have to install the command line tools of XCode, you have 3 different options:

**Option 1** (easy, but large download of 2Gb, only if you have enough free disk space): install the whole Xcode via the the App Store. In XCode select \<Preferences | Downloads\< then \<Command Line Tools\>

**Option 2** (a bit more steps, but you save a lot of disk space):
Go to [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) choose \<View downloads\>, log in (or register first, its free), type \<command line tools\> in the search field, then select the correct version for your version of Mac OS X, download and install it.

**Option 3** (not tested):
OSX GCC Installer

Go to https://github.com/kennethreitz/osx-gcc-installer/ and follow the instructions there

###Getting help

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
**kill (-9)** *pid*|kill process|

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
