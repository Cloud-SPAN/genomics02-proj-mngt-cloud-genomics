---
title: "Planning for NGS Projects"
teaching: 20
exercises: 10
questions:
- "How do I plan and organise a genome sequencing project?"
- "What information does a sequencing facility need?"
- "What are the guidelines for data storage?"
objectives:
- Understand the data we send to and get back from a sequencing center.
- Make decisions about how (if) data will be stored, archived, shared, etc.   
keypoints:
- "Data being sent to a sequencing center also needs to be structured so you can use it."
- "Raw sequencing data should be kept raw somewhere, so you can always go back to the original files."
---

There are a variety of ways to work with a large sequencing dataset. You may be a novice who has not used
bioinformatics tools beyond doing BLAST searches. You may have bioinformatics experience with other types of data and are now working with high-throughput (NGS) sequence data for the first time. 

In the most important ways, the methods and approaches we need in bioinformatics are the same ones we need at the bench or in the field.

**Planning, documenting, and organising** are the key to good reproducible science.  

> ## Discussion
>
> Before we go any further, here are some important questions to consider. If you are learning at a workshop, please use the padlet to share your ideas.  
> It's okay if you don't have answers to these questions yet. This course should help you find some of the answers.
>
> - What challenges do you think you will face with a large sequence dataset?  
> - How or where will you save and share your sequence files?  
> - How will you analyse your data - what software, what computer?
{: .challenge}

# Sending samples to the facility

The first step in sending your sample for sequencing will be to complete a form documenting the metadata for the
facility. Let's take a look at this [example submission spreadsheet](https://docs.google.com/spreadsheets/d/1rHHpzQTuJFuybdhO0c40K6nKE6Hal-QB2ioMEQH3L3k/edit?usp=sharing), which is a Google Sheets document.

> ## Exercise
> If you are attending an instructor-led workshop, discuss these questions in your breakout room:
> 1. How would you improve the naming of columns and samples?
> 2. What errors do you see in the data?
> 3. Are there any types of error that would be difficult to spot? Is there any way you can test these to find thems
>
> Nominate someone from your group to summarise your ideas for each question on the Padlet.
>
> > ## Solution
> > Improvements in names
> > - Shorten client_sample_id names, and maybe just call them "names"
> >   - For example: "wt" for "wild-type". Also, they are all "1hr", so that is superfluous information
> > - The prep_date and ship_date might not be needed
> > - Use "microlitres" for "Volume (µL)" etc.
> > - Volume and concentration column headers have unusual (not allowed) characters
> > - Format of client_sample_id changes and cannot have spaces, slashes, non-standard ASCII characters
> >
> > Errors:
> > - Capitalization of the replicate column changes
> > - Volume, concentration, and RIN column decimal accuracy changes
> > - The prep_date and ship_date formats are different, and prep_date has multiple formats
> > - Are there others not mentioned?
> >
> > Errors hard to spot:
> > - No space between "wild" and "type", repeated barcode numbers, missing data, duplicate names
> > - Find by sorting, or counting
> >
> {: .solution}
{: .challenge}

# Getting data from the facility

When the data come back from the sequencing facility, you will receive some documentation (metadata) as well as
the sequence files themselves. Take a look at this [example](https://docs.google.com/spreadsheets/d/1IyNShMHu0IDbwij4ZdcXtOh5_V53KBcwu1i70Dfaa3g/edit?usp=sharing), another Google Sheets document:

> ## Exercise
> Think about the following and add your ideas to the Padlet:
> 1. How are the samples organised?
> 2. Are you able to relate file names to the sample names you submitted?
> 3. What do the \_R1/\_R2 extensions mean in the 'filename' column?
> 4. What does the '.gz' extension on the filenames indicate?
> 5. What is the total file size - what challenges might this create?  
>
> Don't worry if you're not sure about an answer - just have a go! If you have time, you can use the internet to look up an answer to question 4.
>
> > ## Solution
> >
> > 1. Samples are organised by sample_id
> > 2. To relate filenames use the sample_id, and do a VLOOKUP on submission sheet
> > 3. The \_R1/\_R2 extensions mean "Read 1" and "Read 2" of each sample
> > 4. The '.gz' extension means it is a compressed "gzip" type format to save disk space
> > 5. The size of all the files combined is 1113.60 Gb (over a terabyte). This is big! To transfer files this large you should validate the file size following transfer. Absolute file integrity checks following transfers and methods for faster file transfers are possible but beyond the scope of this lesson.
> >
> {: .solution}
{: .challenge}

# Storing data

The raw data you get back from the sequencing center is the foundation of your sequencing analysis. You need to keep this data, so that you can always come back to it if there are any questions or you need to re-run an analysis, or try a new analysis approach.

### Guidelines for storing data

- Store the data in a place that is accessible by you and other members of your lab. At a minimum, you and the head of your lab should have access.
- Store the data in a place that is redundantly backed up. It should be backed up in two locations that are in different physical areas.
- Leave the raw data raw. Keep a copy of the original data which you do not modify, and instead do your analysis on a different copy. If you modify the data, you'll never be able to access those original files. 
  - We will cover how to avoid accidentally changing files in a later lesson in this workshop: [(see File Permissions)](https://cloud-span.github.io/genomics04-data-preparation-organisation/01-writing-scripts/#file-permissions).

#### Some data storage solutions

If you have a local high performance computing center or data storage facility on your campus or with your organisation, these are ideal locations. Get in touch with the people who support those facilities to ask for information.

If you do not have access to these resources, you can back up on hard drives. Have two backups, and keep the hard drives in different physical locations.

You can also use resources like [Amazon S3](https://aws.amazon.com/s3/),  [Microsoft Azure](https://azure.microsoft.com/en-us/pricing/details/storage/blobs/),  [Google Cloud](https://cloud.google.com/storage/) or others for cloud storage. The [open science framework](https://osf.io) is a free option for storing files up to 5 GB.

# Summary

Before analysis of data has begun, there are already many potential areas for errors and omissions. 
Keeping organised and keeping a critical eye can help catch mistakes.

One of the goals of this course is to help you achieve *competency* in working with bioinformatics. This means that you can accomplish routine tasks, under normal conditions, in an acceptable amount of time. 

An expert might be able to get to a solution on instinct alone. However, taking your time, using Google or another Internet search engine and asking for help are all valid ways of solving your problems. As you complete the lessons you'll be able to use all of those methods more efficiently.  

> ## Where to go from here?
>
> More reading about core competencies
>
>L. Welch, F. Lewitter, R. Schwartz, C. Brooksbank, P. Radivojac, B. Gaeta and M. Schneider, '[Bioinformatics Curriculum Guidelines: Toward a Definition of Core Competencies](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3945096/)', PLoS Comput Biol, vol. 10, no. 3, p. e1003496, 2014.
>
> {: .source}
{: .callout}
