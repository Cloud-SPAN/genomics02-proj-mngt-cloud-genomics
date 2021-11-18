---
layout: lesson
root: .
---
Good data organisation is the foundation of any research project. It sets you up well for an analysis and makes it easier to come back to the project later. It also allows you to share your work with collaborators, including your most important collaborator - future you.

![Person working at a computer with an offstage person asking "How is the analysis going?" The person at the computer replies "Can't understand the date...and the data collector does not answer my emails or calls" Person offstage: "That's terrible! So cruel! Who did collect the data? I will sack them!" Person at the computer: "um...I did, 3 years ago"](fig/future_you.png){:height="500px"}

Organising a project that includes sequencing involves many components. There's the "metadata" about the experimental setup and conditions, the measurements of experimental parameters, the sequencing preparation and sample information, the sequences themselves and the files and workflow of any bioinformatics analysis. 

Much of the information in a sequencing project is digital, and we need to keep track of our digital records in the same way we have a lab notebook and sample freezer. 

In this lesson, we'll go through the project organisation and documentation needed for an efficient bioinformatics workflow. This will make you a more effective bioinformatics researcher and prepare your data and project for publication. Grant agencies and publishers increasingly require this information.

In this lesson, we'll be using data from a famous study of experimental evolution using _E. coli_. [More information about this dataset is available here](https://cloud-span.github.io/genomics02-proj-mngt-cloud-genomics/data/index.html). In this study there are several types of files:

- spreadsheet data from the experiment that tracks the strains and their phenotype over time
- spreadsheet data with information on the samples that were sequenced - the names of the samples, how they were prepared and the sequencing conditions
- the sequence data

Throughout the analysis, we will generate more files from the steps in the bioinformatics pipeline and documentation on the tools and parameters that we used.

> ## Getting Started
>
> This lesson assumes no prior experience with the tools covered in the course.
> However, learners are expected to have some familiarity with biological concepts,
> including the concept of genomic variation within a population. 
>
> This lesson is part of a course that uses data hosted on an Amazon Machine Instance (AMI). Workshop participants will be given information on how to log-in to the AMI during the course.
> Information on preparing for the course is provided on the [Cloud-SPAN Genomics Course setup page](https://cloud-span.github.io/genomics01-intro/setup.html).
{: .prereq}
