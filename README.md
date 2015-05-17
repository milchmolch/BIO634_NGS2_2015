## BIO634 Next-Generation Sequencing 2 – Advanced Course: Transcriptomes, Variant Calling and Biological Interpretation

## May 18/19 2015


### University of Zurich
### URPP Evolution in Action
![URPP logo](Logo_URPP_kl2.png)

Stefan Wyder & Heidi Lischer

stefan.wyder@uzh.ch  
heidi.lischer@ieu.uzh.ch


## Table of Content

###Day 1


&nbsp;   | &nbsp; | &nbsp;
-------- | --- | --- 
9.30 - 9.40 | **Welcome & Introduction** | SW&HL
9.40 - 11.30 | **RNA-seq** <br /> [Presentation](RNAseq/RNAseq.pdf) \| [Hands-on](RNAseq/Exercises_RNAseq.pdf) | HL
11.30 - 12.00 | **Making sense of gene lists** <br /> [Presentation](GENE_LISTS/MakingSenseOfGeneLists.pdf)  \| [Hands-on](GENE_LISTS/Exercises_MakingSenseOfGeneLists.md)| SW
 | |
13.00 - 14.00 | *Talk:* Prof. Kentaro Shimizu (UZH): Ecological Applications of RNA Seq [pdf](TALKS/RNAseqShimizu2015.pdf) |
14.00 - 17.30 | **Linux & Shell** |
 | Short Refresher <br /> Working with files, working with text <br /> [Presentation](BASH_SHELL/LinuxBash.pdf) <br /> [Hands-on 1](BASH_SHELL/Hands-on_unix_Part1.md) \| [Hands-on 2](BASH_SHELL/Hands-on_unix_Part2.md) <br /> [List of important commands](BASH_SHELL/ImportantShellCommands.md) | SW
 | Introduction to shell scripting <br /> Presentation \| [Hands-on](BASH_SHELL/Exercises_BashScripting.pdf)| HL
 


###Day 2

&nbsp;   | &nbsp; | &nbsp;
-------- | --- | --- 
9.30 - 12.00 | **Variant Calling 2** <br /> [Presentation](VARIANT_CALLING/Variant_Calling2.pdf)  \| [Hands-on](VARIANT_CALLING/Exercises_Variant_Calling.md)| SW
 | |
13.00 - 14.00 | *Talk:* Alexandra Jansen van Rensburg (UZH): RAD-Seq | 
14.00 - 15.00 |	*Talk:* Dr. Martin Fischer (ETH): Detection of signatures of selection | 
15.00 - 17.30 | Exercises | SW&HL 


## Prerequisites for the course

- Basic command line 
- Basic knowledge about NGS data structure: reads, alignments (BAM), quality scores

or attendance of `Next-Generation Sequencing 1 – Introductory Course: Assembly, Mapping, and Variant Calling

## Recommended books (Computing Skills)

- [Haddock & Dunn. Practical Computing for Biologists. Sinauer Associates 2011.](http://practicalcomputing.org)  
  A good book that covers the shell/command line, programming in python & bash, databases, regular expressions. 
  Suitable for self-study and as a reference book.

- [Vince Buffalo. Bioinformatics Data Skills. O'reilly 2015](http://shop.oreilly.com/product/0636920030157.do)  
  This practical book teaches the skills that scientists need for turning large sequencing datasets into reproducible and robust biological findings.
  Also covers methods on Sequence and Alignment Data. 
  More advanced than Haddock & Dunn and progresses with faster pace.


## Recommended websites

- <http://software-carpentry.org/>  
  Scientific Computing Resources for learning bash shell, programming in python, R, …]
- [SEQanswers](http://seqanswers.com/) the NGS community (Questions&Answers, protocols, software lists, news) 
- [BioStars](https://www.biostars.org/) for questions about biocomputing and scripting for biologists
- [stackoverflow](http://stackoverflow.com/) for questions related to coding


## Directory structure

```
(Unix System hierarchical tree)

|--HOME--|
      ├─software
           ├── IGV_2.3.52/
           ├── freebayes/
           ├── picard-tools-1.130/
      ├─NGS2
	   ├─RNA-Seq
	   ├─VariantCalling2
        	├── Final_Results (with pre-computed results)
            ├── ref (reference files like genomes)
            └── scripts

( more folders will be added in this level during the workshop )
```


## Installation Instructions for the Virtual Machine

We will reuse the Virtual Machine (VM) of the first NGS course BIO610. However, we need to download the data for this course.


### Download the data for this course

- Start the VM and login
- Open a terminal
- Download the file by typing `wget url` (Note to myself: Use URL shortener)
- Unzip the file: `unzip data_NGS2.zip`


### If you have *not* yet installed the VM 
- Download the virtual machine manager VirtualBox, from [virtualbox.org](https://www.virtualbox.org/). Make sure you pick the right operation system for your laptop. 
- Install VirtualBox on your machine
- Download the VM image (~3 GB) from dropfiles.uzh. Ask for the link.
- Run VirtualBox and do `File | Import Appliance` from the menu. Choose the VM image you just downloaded (file with extension .OVA). This will trigger a menu where you can change the Appliance settings. We recommend giving the VM as much memory as you can given your local machine (about 2/3 of the total memory, but between 2-4 GB). Start the import process.

Now you can start the VM by selecting it in the list and clicking on the Start button. Login and proceed with the instructions 
