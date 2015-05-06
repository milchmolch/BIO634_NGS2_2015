# BIO634 Next-Generation Sequencing 2 – Advanced Course: Transcriptomes, Variant Calling and Biological Interpretation

## University of Zurich
## URPP Evolution in Action
![URPP logo](Logo_URPP_Kreisganz_kl2.png)

Stefan Wyder & Heidi Lischer

stefan.wyder@uzh.ch
heidi.lischer@ieu.uzh.ch



## Table of Content

###Day 1

		 |               |  |
-----------------|---------------|--|
9.00 - 9.15 | **Welcome&Introduction** | SW&HL
9.15 - 11.00 | **RNA-seq** | HL
|| Hands-on ||
11.00 - 12.00 | **Making sense of gene lists** | SW
13.00 - 14.00 | *Talk:* Prof. Kentaro Shimizu (UZH): Ecological Applications of RNA-seq ||
|||
14.00 - 17.30 |	**Linux/Shell basics** | |				
|| Short Refresher | SW
|| Working with files, working with text | SW
|| Introduction to shell scripting | HL


###Day 2

                 |               |  |
---------------- | ------------- |--|
9.00 - 11.00 | **Variant Calling 2** | SW
|| Theory ||
|| Hands-on ||
||||
13.00 - 14.00 |  *Talk:* Alexandra Jansen van Rensburg (UZH): RAD-Seq ||
14.00 - 15.00 |	*Talk:* Dr. Martin Fischer (ETH): Detection of signatures of selection ||
15.00 - 17.30 | Exercises, Repetition | SW&HL


## Recommended books

- [Haddock & Dunn. Practical Computing for Biologists. Sinauer Associates 2011.](http://practicalcomputing.org)  
  A good book that covers the shell/command line, programming in python & bash, databases, regular expressions. 
  Suitable for self-study and as a reference book.

- [Vince Buffalo. Bioinformatics Data Skills. O'reilly 2015](http://shop.oreilly.com/product/0636920030157.do)  
  This practical book teaches the skills that scientists need for turning large sequencing datasets into reproducible and robust biological findings.
  Also covers methods on Sequence and Alignment Data. 
  More advanced than Haddock & Dunn and progresses with faster pace.


## Recommended websites

- [http://software-carpentry.org/](Scientific Computing Resources for learning bash shell, programming in python, R, ...)


## Installation Instructions for the Virtual Machine

We will reuse the Virtual Machine (VM) of the first NGS course BIO610. However, we need to download the data for this course.


### Download the data for this course

- Start the VM and login
- Open the terminal
- Download the file by typing `wget url` (Note to myself: Use URL shortener)
- Unzip the file: `unzip data_NGS2.zip`


### If you have *not* yet installed VM 
- Download the virtual machine manager VirtualBox, from [virtualbox.org](https://www.virtualbox.org/). Make sure you pick the right operation system for your laptop. 
- Install VirtualBox on your machine
- Download the VM image (~2 GB) from dropfiles.uzh. Ask for the link.
- Run VirtualBox and do `File | Import Appliance` from the menu. Choose the VM image you just downloaded (file with extension .OVA). This will trigger a menu where you can change the Appliance settings. We recommend giving the VM as much memory as you can given your local machine (about 2/3 of the total memory, but between 2-4 GB). Start the import process.

Now you can start the VM by selecting it in the list and clicking on the Start button. Login and proceed with the instructions 
