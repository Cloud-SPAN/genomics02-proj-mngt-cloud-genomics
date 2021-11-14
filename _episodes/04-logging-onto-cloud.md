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

To access your pre-configured AWS instance for this course, you'll need:
- the name of your instance 
- the file with the login key to access your instance
- the **Terminal** application
  - Terminal is readily available in MacOS and Linux computers.  
  - **Windows** users should have already installed *Git Bash* which includes the Git Bash *Terminal*. If not, please follow the directions in the [Setup](../setup).
- the *secure shell* (**ssh**) application 
  - ssh is readily available in MacOS, Linux and Windows. **Windows** user need to use ssh through the Git Bash Terminal. 
  - as the name implies, **ssh** provides you with a secure way to use a remote *shell*, which is just another name for the *Terminal* and the *command line interface*, or CLI!  

You will have received an email with the name of your AWS instance and the login key file. The name of your instance and of the login key file will be something like this:

- **instanceNN-gc.cloud-span.aws.york.ac.uk**
- **login-key-instanceNN.pem**

where NN will be a number between 01 and 37. 

We need to prepare the login key file and make it accessible to ssh so that ssh can authenticate you to your AWS instance. Follow the steps below: 


{% comment %}

## Connection Protocols

We will use a protocol called Secure Shell (SSH) that, as the name implies, provides you
with a secure way to use a [shell](http://swcarpentry.github.io/shell-novice). In our case,
the shell will be running on a remote machine. This protocol is available for every
operating system, but sometimes requires additional software.

## Logging onto a cloud instance

**Please select the platform you wish to use for the exercises: <select id="id_platform" name="platformlist" onchange="change_content_by_platform('id_platform');return false;"><option value="aws_unix" id="id_aws_unix" selected> AWS_UNIX </option><option value="aws_win" id="id_aws_win" selected> AWS_Windows </option></select>**


<div id="div_aws_win" style="display:block" markdown="1">

#### Connecting using PC

*Prerequisites*: You must have an SSH client. There are several free options but you should have installed [PuTTY.exe](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) at the begining of the workshop, and we're going to continue using that.


1. Open PuTTY
2. Paste in the 'Host Name (or IP address)' section the IP address provided by your instructor (or the IP address of an instance you have provisioned yourself)

    *Keep the default selection 'SSH' and Port (22)*

    ![The location of the Host Name, Port, and Connection Type fields in the PuTTY Configuration](../fig/putty_screenshot_1.png)

2. Click 'Open' 
    
    You will be presented with a security warning

    ![Screenshot showing a security warning after opening a PuTTY session.](../fig/putty_screenshot_2.png)

3. Select 'Yes' to continue to connect
3. In the final step, you will be asked to provide a login and password
    
    **Note:** When typing your password, it is common in Unix/Linux not see any asterisks (e.g. `****) or moving cursors. Just continue typing

    ![Screenshot of a command line window demonstrating how to type passwords in Unix/Linux](../fig/putty_screenshot_3.png)

You should now be connected!

</div>


<div id="div_aws_unix" style="display:block" markdown="1">

{% endcomment %}

### I. Open a Terminal and create a directory for the course

1. **Open terminal** (or Git Bash terminal if you are a Windows user). 

    Search for 'Terminal' or look for the terminal icon and click (or double click) on it:

    This is the Git Bash terminal icon (Windows users):   

    <img src="../fig/icon-git-bash2.png" alt="GIT BASH terminal" width="50"/> 

    The terminal icon in Mac and Linux will look like the following:
    
    <img src="../fig/icon-mac-terminal.png" alt="Mac terminal" width="50"/><img src="../fig/icon-linux-terminal.png" alt="Linux terminal" width="50"/> 

    Once the terminal opens, it will display/output the **command prompt** to signal that it is ready to accept commands (instructions). The **command prompt** is 1 or 2 lines depending on your operating system (Windows, Linux, MacOS) and will be similar to the following.

    Typical command prompt for Windows Git Bash users:

    ~~~
    username@machineid MINGW64 ~
    $
    ~~~
    {: .output}

    Obviously "username" and "machineid" in the Code box above will be different when you open a terminal and will correspond to the actual username and machine name you are using. 

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

2. **Find out where you are and what is therein**

   Once the terminal opens, **you will be** in your **home** directory. To see your home directory, type the **pwd** (print working directory) command and press the **Enter** key (**↵**) to the command prompt (we will only show the end of the prompt **$** from now on):

    ~~~
    $ pwd↵	
    ~~~
    {: .bash}

    *Don't type the* **$**.

    The output of **pwd** will be as follows.

    For Windows users:
    ~~~
    /c/Users/yourusername
    ~~~
    {: .output}

    For Linux users:
    ~~~
    /home/yourusername
    ~~~
    {: .output}

    For MacOS users:
    ~~~
    /Users/yourusername
    ~~~
    {: .output}

    That output means that your home directory is named yourusername (you will see your actual username), and that it is a subdirectory within the **parent** directory *Users*, in Windows and MacOS, and within the parent directory *home* in Linux.

    Let's see what is in your home directory. Type the **ls** (list files) command and press Enter

    ~~~
    $ ls↵	
    ~~~
    {: .bash}

    This is a typical output of **ls** in a Linux machine but Windows users are likely to see a very long list of files and directories:

    ~~~
    bin  Desktop  docs  Downloads  machines-other  mail  pendings  snap  software  tmp
    ~~~
    {: .output}

    Within your home directory you will find the typical directories like: Desktop, Documents Downloads, etc.
    
    *\*\*\*It just helps to get things organised and accessible to sort them into directories.* So, for you to keep all the resources for this course in the same place ..

3. **Create a directory for the course and move to it**

    You can create a directory and move to it by typying the following commands (recall to press Enter ↵ after each command):

    ~~~
    $ mkdir cloudspan			
    $ cd cloudspan
    ~~~
    {: .bash}

    The command **mkdir** stands for "make a directory"; and you must specify the name of the directory.

    The command **cd** stands for "change (to) directory"; and you must specify the name of the directory.

    The directory *cloudspan* will be created in your home directory (where other directories such as *Desktop*, *Documents*, *Downloads*, .. are located) because (1) when you open a terminal you are placed in your home directory by default, and (2) where you are is your working directory (recall that pwd stands for print working directory), meaning that whatever command you issue will operate relative to your working directory unless you specify otherwise. Hence, **mkdir** assumed you wanted to create cloudspan in your (home) working directory and cd looked for cloudspan in your working directory to change to it.

    We used cloudspan in the example above but **you can use another name** for your directory for the course and you can create it within another directory. Choose your directory name for the course so you can easily recall it and it helps you get your things organised. And change to it. For example:

    ~~~
    $ mkdir -p Documents/genomicscourse			
    $ cd Documents/genomicscourse
    ~~~
    {: .bash}

    Or
    ~~~
    $ mkdir -p courses/york/genomics
    $ cd courses/york/genomics
    ~~~
    {: .bash}

    The option **-p** instructs mkdir to create sub-directories if and as required. 

    After you enter the command *cd cloudspan* (or *cd directoryyoucreated*), your **working directory will be** *cloudspan* or *directoryyoucreated*. 


### II. Download and prepare the private key file to login to your AMI instance

1. **Download your login key file**

    In the email you received from the Cloud-SPAN team:
    - Click on the embedded link to download (⬇) the file
    - MacOS users may have to click on “download” when the file says it can’t be opened.


    **NB**: 

    If your browser asks you “where do you want to download the file?”, choose the directory for the course you just created and to which you should have already moved (at the end of Step I.3). If this is the case, then go to “3. Prepare your private key file” below.

    Otherwise continue with the next step 2.

2. **If necessary, move the login key file you downloaded to the directory you created for the course**

    If your browser did not ask you where to download your login key file, you need to find out where it was dowloaded and move it to your working directory (the one you created for the course). You can:
    
    - find the file with the **File Manager** (or similar application) and get its location.
    - or through the **browser**, on the bar shown by the browser at the bottom of the screen when the download finished, **right** click on the name of your login key file, and then (left) click on “Show in folder”. Once it is shown in a folder, right click on the file name/icon, and then (left) click on Properties.  The location of the file will be shown as (for example):  

    ~~~
    Location:           C:\Users\username\Downloas\login-key-instanceNN.pem         // Windows users
    Parent folder:      /home/username/Downloads/login-key-instanceNN.pem.pem       // Linux users
    Parent folder:      /Users/username/Downloads/login-key-instanceNN.pem.pem      // MacOS users 
    ~~~
    {: .output}
    
    Move the file to the directory your created for the course with the **mv** (move) command:

    ~~~
    $ mv ~/Downloads/login-key-instanceNN.pem .			
    ~~~
    {: .bash}

    *Don't forget to replace NN with the actual number in your login key file*. 
    
    The character **~** represents your home directory, so you are specifying the full location for your login key file.
    
    The character dot **.** at the end of the command represents your current location or working directory, which should be the directory you created for the course (if this is not the case, the following commands will fail -- just go back and start again). 

    Note that the full location of the file in Windows is shown with inverted slashes **\\** but the command mv uses "normal" slashes **/** for all users including Windows Git Bash users. This is correct. Git Bash emulates as much as possible the Bash shell, which was originally developed for Unix systems where file locations (called file paths in Unix) use normal slashes **/** to separate the names of directories and files in a file path.
   
3. **Prepare your login key file**

    Change the access permissions of the file thus:

    ~~~
    $ chmod 400 login-key-instanceNN.pem 
    ~~~
    {: .bash}

    Obviously change NN for whatever number is in your key file name.

    The **chmod** command makes your login key file accessible only to you (and not-accessible to any other potential users of your computer), a condition that is required and checked by the program ssh that you will use next to login to your AWS AMI instance. You will learn about file access permissions later in the course.

### III. Login to your instance with ssh:

1. Copy and paste the following command to your terminal but replace `NN` with the number in your login key file name.

    ~~~
    $ ssh -i login-key-instanceNN.pem  csuser@instanceNN-gc.cloud-span.york.ac.uk
    ~~~
    {: .bash}

    *Be sure to replace NN twice.*

    The **-i** option tells ssh the identity file containing the key to send to your AWS instance for it to check you have access to connect as an ssh client. We know the file is in your current working directory (the one you created for the course), and ssh looks for the file in your current working directory because you are only specifying the file name. 
    
    If the identity file were somewhere else, we would have had to specify the full path name or a relative path name, which you will learn more about later in the course.  

2. The terminal will display a security message, after you enter the ssh command, similar to the one below: 

    ~~~
    The authenticity of host 'instance06-gc-cloud-span.york.ac.uk (52.211.132.120)' can't be established.ECDSA key fingerprint is SHA256:8N054prkkCeM4GCDSsa0AUnSQw5ngBQHbOR40FqfqLg.
    Are you sure you want to continue connecting (yes/no/[fingerprint])? 
    ~~~
    {: .output}

    Type **yes** to continue and get connected to your AWS instance.

    The terminal will display a few more messages and at then the prompt of the remote Linux machine that is your AWS instance:

    ~~~
    ...
    csuser@instance05-gc.cloud-span:~ $
    ~~~
    {: .output}

    Note that you didn't have to type a password to login to your instance, as your are using you login-key file for authentication.

{% comment %}
</div>
{% endcomment %}

### IV. Logging off your cloud instance

Logging off your instance is a lot like logging out of your local computer but it doesn't shut the computer off. **Be aware that AWS instances accrue charges whenever they are running, even if you are logged off**. Today, however, you do not need to worry about this.

To log off, use the `exit` command in the same terminal you connected with. This will close the connection, and your terminal will go back to showing your local computer prompt, for example:

~~~
csuser@instance05-gc.cloud-span $ exit

Amanda-MacBook-Pro-3 $
~~~
{: .bash}

### V. Subsequent logins to your AWS instance

To login back to your instance, open a terminal, move to the directory you created for the course, and ssh as before:

~~~ 
$ cd directory-you-created-the-first-time
$ ssh -i login-key-instanceNN.pem  csuser@instanceNN-gc.cloud-span.york.ac.uk
~~~
{: .bash}