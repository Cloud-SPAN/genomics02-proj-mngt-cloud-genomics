---
title: "Logging onto the Cloud"
teaching: 5
exercises: 40
questions:
- How do I connect to an AWS instance?
objectives:
- Log onto to a running instance
- Log off from a running instance
keypoints:
- You can use one set of log-in credentials for many instances
- Logging off an instance is not the same as turning off an instance
---

<script language="javascript" type="text/javascript">
function set_page_view_defaults() {
    document.getElementById('div_aws_win').style.display = 'block';
    document.getElementById('div_aws_unix').style.display = 'none';
};

function change_content_by_platform(form_control){
    if (!form_control || document.getElementById(form_control).value == 'aws_win') {
        set_page_view_defaults();
    } else if (document.getElementById(form_control).value == 'aws_unix') {
        document.getElementById('div_aws_win').style.display = 'none';
        document.getElementById('div_aws_unix').style.display = 'block';
        document.getElementById('div_hpc').style.display = 'none';
        document.getElementById('div_cyverse').style.display = 'none';
    } else {
        alert("Error: Missing platform value for 'change_content_by_platform()' script!");
    }
}

window.onload = set_page_view_defaults;
</script>

## Important Note

This lesson covers how to log into, and out of, an *already running* Amazon instance.

## Background to AWS

An Amazon Web Services (AWS) instance is a **remote computer** that runs on AWS infrastructure and that is accessible from any laptop or desktop as described below. Setting up a new AWS instance requires a credit card, an AWS account, and up to a day of verification time. 

To save time, your instructor has launched an AWS instance for you prior to the course, and connected it to our lesson data and software analysis tools. It all works as follows.

We have a pre-configured copy of the data and software analysis tools needed for this course that is always available to attach to a new AWS instance that is accessible to you as long as you have the log-in credentials to open it.

To login into your AWS instance for this course, you'll need:
- the name of your instance and a login key file, both of which you received via email
- the shell/terminal application ---- **Windows users** should have already installed the *Git Bash* shell; otherwise follow the directions in the [Setup](../setup)
- the *secure shell* (**ssh**) application, which is readily available in MacOS, Linux and Windows. **Windows users** will use ssh through Git Bash. 

As the name implies, **ssh** provides you with a secure (encrypted) way to use a remote *shell*, as simple as this:

 ~~~
 $ ssh -i login-key-instanceNN.pem  csuser@instanceNN-gc.cloud-span.aws.york.ac.uk
 ~~~
 {: .bash}

A few seconds after you enter that command to the shell in your computer, you will be logged into your AWS instance and start using a (Linux) shell running in your instance.

But before that, it is most convenient that, to keep things tidy and easily accessible, you first create a folder (or directory) to keep in there everything related to the course: your login key file, your notes, data, etc.  We will then download your login key file to that folder and change its access permissions for the reasons given below. Finally we will login into your instance with ssh.

## Create a folder for the course and download therein your login key file

1. **Create the folder** *cloudspan* in your *Desktop*.

   In your Desktop, click the right button of the mouse to open the File Explorer/Manager menu, and then left click on New and then on Folder, in Windows, or New Folder in Linux Gnome.

   Name the folder cloudspan.

   Later you can change the name of the folder and move it somewhere else.

2. **Download your login key file** to the folder you just created.

   Click on the link embedded in the email you received from the Cloud-SPAN team.
   
   Mac users may need to Click on 'download' when the file says it can't be opened.

   If your browser asks you "where do you want to download the file?", choose the directory for the course you just created.

   Otherwise, drag and drop your login key file from wherever it was downloaded to the folder for the course you created.

## Open a Terminal and change the access permissions of your login key file

1. **Open terminal** (or Git Bash terminal if you are a Windows user). 

    Search for 'Terminal' or look for the terminal icon and click (or double click) on it:

    This is the Git Bash terminal icon (Windows users):   

    <img src="../fig/gitbash-launch-icon.png" alt="GIT BASH terminal" width="50"/> 

    The terminal icon in Mac and Linux looks like the following:
    
    <img src="../fig/icon-mac-terminal.png" alt="Mac terminal" width="50"/>
    <img src="../fig/icon-linux-terminal.png" alt="Linux terminal" width="50"/> 

    Once the terminal opens, it will display/output the **command prompt** to signal that it is ready to accept commands (instructions). The **command prompt** is 1 or 2 lines depending on your operating system (Windows, Linux, MacOS) and will be similar to the following.

    Typical command prompt for Windows Git Bash users:

    ~~~
    username@machineid MINGW64 ~
    $
    ~~~
    {: .output}

    Obviously "username" and "machineid" in the Code box above will be different when you open a terminal and will correspond to the actual username and the name of the machine you are using. 

    The character **$** is the typical ending of user prompts (the ending of admin users prompts is typically **#**). Commands you type will follow the **$**.

    Typical command prompt for Linux users:

    ~~~
    username@machineid:~ $
    ~~~
    {: .output}

    Typical command prompt for MacOS users:

    ~~~
    machineid:~ username $
    ~~~
    {: .output}

2. **Move to the folder you created for the course**

   Once the terminal opens, **you will be** in your **home** folder (directory). 
   
   Your home folder holds all your files and other folders such as the Desktop, Downloads, Documents, etc.

   Move to the folder you created by typing the following and pressing the **Enter** key (**↵**) in front of the command prompt:

    ~~~
    $ cd Desktop/cloudspan↵	
    ~~~
    {: .bash}

    *Don't type the dollar character* $.

    The command **cd** stands for "change (to) directory", and you must specify the name of the directory you want to move to. 

    In the command above, we have specified *to change to* a directory within a directory.

    We only showed the end of the command prompt **$** above, and do so below too. *Recall not to type it and to press the Enter key  at the end*.

3. **Change the access permissions of your login key file**

    Enter the following command to change the access permissions of your file but **replace** NN with the actual number in your file name:
    ~~~
    $ chmod 400 login-key-instanceNN.pem 
    ~~~
    {: .bash}

    The command **chmod** (change access mode) makes your login key file accessible to you only (and non-accessible to any other potential users of your computer), a condition that is required and checked by the program ssh that you will use next to login to your AWS AMI instance. You will learn about file access permissions later in the course.

## Login into your instance with ssh

1. Copy and paste the following command to your terminal but replace `NN` with the number in your login key file name.

    ~~~
    $ ssh -i login-key-instanceNN.pem  csuser@instanceNN-gc.cloud-span.aws.york.ac.uk
    ~~~
    {: .bash}

    *Be sure to replace NN twice.*

    The **-i** option tells ssh the identity file containing the key to send to your AWS instance for it to check you have access to connect as an ssh client. We know the file is in your current working directory (the one you created for the course), and ssh looks for the file in your current working directory because you are only specifying the file name. 
    
    If the identity file were somewhere else, we would have had to specify the full path name or a relative path name, which you will learn more about later in the course.  

2. The terminal will display a security message, after you enter the ssh command, *similar* to the one below: 

    ~~~
    The authenticity of host 'instance06-gc-cloud-span.aws.york.ac.uk (52.211.132.120)' can't be established.ECDSA key fingerprint is SHA256:8N054prkkCeM4GCDSsa0AUnSQw5ngBQHbOR40FqfqLg.
    Are you sure you want to continue connecting (yes/no/[fingerprint])? 
    ~~~
    {: .output}

    Type **yes** to continue and get connected to your AWS instance.

    The terminal will display a few more messages and at then the prompt of the remote Linux machine that is your AWS instance:

    ~~~
    ...
    csuser@instance05-gc:~ $
    ~~~
    {: .output}

    Note that you didn't have to type a password to login to your instance, as your are using you login-key file for authentication.

## Logging off your cloud instance

Logging off your instance is a lot like logging out of your local computer but it doesn't shut the computer off. **Be aware that AWS instances accrue charges whenever they are running, even if you are logged off**. Today, however, you do not need to worry about this.

To log off, use the `exit` command in the same terminal you connected with. This will close the connection, and your terminal will go back to showing your local computer prompt, for example:

~~~
csuser@instance05-gc:~ $ exit
~~~
{: .bash}
~~~
logout
Connection to instance05-gc.cloud-span.aws.york.ac.uk closed.
Amanda-MacBook-Pro-3 $
~~~
{: .output}

## Subsequent logins to your AWS instance

To login back to your instance, open a terminal, move to the directory you created for the course, and ssh as before:

~~~ 
$ cd Desktop/cloudspan
$ ssh -i login-key-instanceNN.pem  csuser@instanceNN-gc.cloud-span.aws.york.ac.uk
~~~
{: .bash}
