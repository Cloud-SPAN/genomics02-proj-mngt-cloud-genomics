---
title: "Why of cloud computing"
teaching: 5
exercises: 0
questions:
- What is cloud computing?
- What are the tradeoffs of cloud computing?
objectives:
- Understand benefits of working on a remote computer system
keypoints:
- Cloud computing increases processing speed and efficiency
---
## Working on a Remote Machine

There are a number of reasons why accessing a remote machine is valuable to scientists working with large datasets. Many analyses (especially in 'omics) are too large to run on  our laptops or desktops. These analyses require larger machines, often several machines linked together, and remote access is the only practical solution.

Computational power has become a commodity and entire companies have been built around a business model that allows you to "rent" one or more linked computers for as long as you require, at relatively low cost. This is the basic principle behind the **cloud**. You define your computational requirements and off you go.

### When should I use the cloud?

You'll know you need to start working on the cloud when:

- Your computer does not have enough resources to run the desired analysis (memory, processors, disk space, network bandwidth).
- Your computer is taking hours or days to get through an analysis.
- It is not possible to install the software needed on your computer (no version for your operating system, conflicts with other existing applications, etc.)
- You cannot afford the infrastructure (hardware, bandwidth, power supply, administrator) required to acquire and maintain sufficiently large computers for your analysis.
- You need to continue working on your analyses while you travel.

The cloud is a part of our everyday life (e.g. using Amazon, Google, Netflix, or an ATM involves remote computing). The topic is fascinating, but this lesson says '5 minutes or less' so let's get connected.

<div id="imagesrow">
    <img class="styfigrow" src="../fig/cloud-interconnected-resources.png" alt="Cloud interconnected resources" width="450"/>&nbsp;&nbsp;&nbsp;&nbsp;
    <img class="styfigrow" src="../fig/cloud-is-the-internet.png" alt="The Cloud is the Internet" width="350"/>  
</div>

### Choosing a cloud platform

The most important thing about the **cloud** is choice - instead of purchasing a physical computer, you can obtain on-demand computing at almost any scale. This power comes with advantages and disadvantages:

**Advantages of Cloud Computing**

* Access large amounts of computing power on demand
* Full administrative rights - install anything
* Use pre-configured "images" (machine snapshot where operating system and software are already installed)
* Your local operating system doesn't matter - once you connect to the cloud you can run any UNIX software

**Disadvantages of Cloud Computing**

* It takes time to upload data and download results
* Cloud computing costs money (you must keep track of your costs)
* If you need help, you may not have a local system administrator
* Images may be poorly documented (you may not be clear on what is installed, or how to use it)
* Form of payment (credit card)*
* Understanding of Amazon's billing and payment (See: [Getting started with AWS Billing and Cost Management](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-getting-started.html))

\* You can use some of Amazon Web Services (AWS) for free, and there are also AWS Cloud Credits for Research (See: [https://aws.amazon.com/research-credits/](https://aws.amazon.com/research-credits/) ). The free level of service *will not* be sufficient for working with the amount of data we are using for our lessons.


### Cloud platform choices

There are several cloud providers to choose from. Some scientific clouds may either be free or allocate resources competitively. Commercial clouds can be very powerful, but choice can be overwhelming. We will come back to this at the end of the lesson, but for right now, we're going to continue using the Amazon Web Services as our resource.

Learn more about cloud computing in bioinformatics<br>
Fusaro, V. A., Patil, P., Gafni, E., Wall, D. P., & Tonellato, P. J. (2011). Biomedical cloud computing with Amazon Web Services. PLoS Computational Biology, 7(8), e1002147. https://doi.org/10.1371/journal.pcbi.1002147

Navale, V., & Bourne, P. E. (2018). Cloud computing applications for biomedical science: A perspective. PLoS Computational Biology, 14(6), e1006144. https://doi.org/10.1371/journal.pcbi.1006144
