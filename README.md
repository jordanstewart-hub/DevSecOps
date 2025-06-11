# Part 1 DevSecOps Project: Set Up a Web App in the Cloud



**Author:** Jordan Stewart  
**Email:** jordanstewartbusiness@gmail.com

---

## Set Up a Web App Using AWS and VS Code

![Image](http://learn.nextwork.org/authentic_azure_zealous_melon/uploads/aws-devops-vscode_7a1de541)

---

## Introducing Today's Project!

Set Up a Web App in the Cloud:

💻 Launch an EC2 instance.

🔌 Use VS Code to set up a remote SSH connection to your EC2 instance.

☕️ Install Maven and Java and generate a basic web app.

💎 Edit code without VS Code

### Key tools and concepts

In the web app cloud setup project, the key services and concepts I learned included:

Amazon EC2: Launching and connecting to virtual servers.

Security Groups: Configuring inbound rules to allow SSH and HTTP access.

Key Pairs: Using .pem files for secure remote access.

SSH: Connecting to cloud instances from a local machine or WSL.

Linux Commands: Navigating directories, setting file permissions, and managing servers.

Web Server Deployment: Installing and configuring a web server (like Nginx or Apache) on EC2 to host the app.

Cloud Infrastructure Basics: Understanding how to provision and manage cloud resources for scalable app deployment

### Project reflection
Setting up a web app in the cloud through the Nextwork project was a valuable hands-on experience that strengthened my understanding of cloud infrastructure and deployment. I learned how to launch and connect to EC2 instances, configure security groups, and manage SSH key pairs securely. I also practiced deploying a basic web application on a cloud server and troubleshooting connectivity issues. This project helped me understand the end-to-end flow of deploying an app—from local development to cloud hosting—while emphasizing the importance of secure configurations and automation. It gave me confidence in working with cloud tools and laid a strong foundation for DevOps and cloud-based development.

---

## 1. Launching an EC2 instance

If EC2 is the service that creates virtual computers/servers, an instance is one of those computers/servers.

Picking an EC2 instance is like customizing a virtual computer that fits what is needed for this project. You can customize your EC2 instance's CPU, memory, storage, and networking capacity and more!

### I also enabled SSH

💡 What is SSH?
SSH i.e. Secure Shell is a protocol used to make sure only authorized users can access a remote server. When you connect to your EC2 instance later in this project, SSH verifies you have the correct private key that matches the public key on the server.

### Key pairs

💡 What is a key pair?
A key pair in EC2 is like the keys to your virtual computer. Just like you need a key to unlock and start your car, a key pair lets you securely access your EC2 instance.

It's made of two halves: a public key that AWS keeps, and a private key that you download.

When you use the private key, it verifies that you're the one allowed to access that specific virtual machine, keeping everything secure and just for you.

Once I set up my key pair, AWS automatically downloaded it as a .pem file. 

---

## 2. Set up VS Code

💡 What is VS Code?
Visual Studio Code (VS Code) is one of the most popular tools for creating and managing coding projects. You'll often hear people call VS Code an IDE (Integrated Development Environment), which means software that help you write and edit code. It's similar to how Microsoft Word or Google Docs help you write documents!


VS Code also comes with extra tools that will be displayed in this project to connect to virtual servers like EC2 instances.

![Image](http://learn.nextwork.org/authentic_azure_zealous_melon/uploads/aws-devops-vscode_53d05e68)

---

## My first terminal commands

The first command I ran for this project was: cd %USERPROFILE%\Desktop\DevOps


Icacls (which stands for Integrity Control Access Control Lists) is a tool for Windows that lets you decide who can open or change the files on your system. In these icacls commands, using:

/reset to remove default permission settings on the file

/grant:r "USERNAME:R" to give the current user read access to the secret key

/inheritance:r to make sure changes in the permissions of other files and the DevOps folder won't change the permission settings for this file.

I made sure to replace "USERNAME" with my Windows username.

![Image](http://learn.nextwork.org/authentic_azure_zealous_melon/uploads/aws-devops-vscode_9328ada1)

---

## 3. SSH connection to EC2 instance

To connect to my EC2 instance, I opened the terminal in VS Code and used the SSH command with my private key file and the instance’s public DNS.

### This command required an IPv4 address

💡 What is a Public IPv4 DNS?
A Public IPv4 DNS (which stands for Domain Name System) is the public address for your EC2 server that the internet uses to find and connect to it. The local computer you're using to do this project will find and connect to your EC2 instance through this IPv4 DNS.

![Image](http://learn.nextwork.org/authentic_azure_zealous_melon/uploads/aws-devops-vscode_e3069dca)

---

## 4. Install Maven & Java

💡 What is Apache Maven?
Apache Maven is a tool that helps developers build and organize Java software projects. It's also a package manager, which means it automatically download any external pieces of code your project depends on to work.

I'm using Maven today because it's really useful for kick-starting web projects! It uses something called archetypes, which are like templates, to lay out the foundations for different types of projects e.g. web apps.

I'll use Maven later on to help set up all the necessary web files to create a web app structure, so I can jump straight into the fun part of developing the web app sooner.

💡 What is Java? What is Amazon Correto 8?

Java is a popular programming language used to build different types of applications, from mobile apps to large enterprise systems.

Maven, which I just downloaded, is a tool that NEEDS Java to operate. So if I don't install Java, I won't be able to use Maven to generate/build the web app today.

Amazon Corretto 8 is a version of Java that I'm using for this project. It's free, reliable and provided by Amazon.

---

## 5. Create the Application

💡 Breaking down these commands ... What is mvn? 
When you run mvn commands, you're asking Maven to perform tasks (like creating a new project or building an existing one).

The mvn archetype:generate command specifically tells Maven to create a new project from a template (which Maven calls an archetype). This command sets up a basic structure for the project, so we don't have to start from scratch.

Some of the details I've specified in this command are:

-DartifactId=nextwork-web-project names your project

-DarchetypeArtifactId=maven-archetype-webapp specifies that you're creating a web application.

-DinteractiveMode=false runs the command without pausing for user input, so Maven will go ahead and install everything without waiting for your confirmation.


💡 Why are we installing Remote - SSH?
The Remote - SSH extension in VS Code lets you connect directly via SSH to another computer securely over the internet. This lets you use VS Code to work on files or run programs on that server as if you were doing it on your own computer, which will come in handy when we edit the web app in your EC2 instance!

Configuration details required to set up a remote connection include: 

Host: should match up with our EC2 instance's IPv4 DNS.

IdentityFile: should match up to project-keypair.pem's location in our local computer.

User: should say ec2-user

![Image](http://learn.nextwork.org/authentic_azure_zealous_melon/uploads/aws-devops-vscode_2939cf01)

---

## 6. Create the Application in VS Code via EC2 Instance

All the files and subfolders you see under nextwork-web-project are parts of a web app.

 Let's get to know some of these web app files/folders:

The src (source) folder holds all the source code files that define how our web app looks and works.

src is further divided into webapp, which are the web app's files e.g. HTML, CSS, JavaScript, and JSP files, and resources, which are the configuration files a web app might need e.g. connection settings to a database.

pom.xml is a Maven Project Object Model file. It stores information and configuration details that Maven will use to build the project. I'll use pom.xml later in this project series.

![Image](http://learn.nextwork.org/authentic_azure_zealous_melon/uploads/aws-devops-vscode_45f91fd7)

---

## Using Remote - SSH

💡 What is index.jsp? 
index.jsp is a file used in Java web apps. It's similar to an HTML file because it contains markup to display web pages.

However, index.jsp can also include Java code, which lets it generate dynamic content.

This is the code I used to edit index.jsp:

<html>

<body>

<h2>Hello Jordan!</h2>

<p>This is my NextWork web application working!</p>

</body>

</html>


![Image](http://learn.nextwork.org/authentic_azure_zealous_melon/uploads/aws-devops-vscode_7a1de541)

---

## Using nano

I used the command: cd ~/nextwork-web-project/src/main/webapp because it will take you directly to the folder containing index.jsp because it uses the full path.

A full path (or absolute path) means the command provides the exact location of a file or folder starting from the root directory (i.e. the ~ symbol), which is like the “starting point” on a server.

Using a full path ensures that you’ll end up in the final destination of that path, no matter where you were before.

Editing code in the terminal (using tools like Vim or Nano) is fast, lightweight, and always available on remote systems—great for quick fixes. However, it lacks advanced features. IDEs (like VS Code or IntelliJ) offer powerful tools like autocomplete, debugging, and visual file navigation, which boost productivity for larger projects. Terminal editors suit experienced users and simple tasks, while IDEs are ideal for deep development work.

![Image](http://learn.nextwork.org/authentic_azure_zealous_melon/uploads/aws-devops-vscode_a3324ad41)

---

