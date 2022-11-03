# Customer use-cases with Terraform

In this lab the focus will be on using Terraform as a way to provide operational rigor to your network device configurations. You will learn how to install and use Terraform on Cisco network solutions like ACI.

## 1. Install Visual Studio Code

Terraform uses structured files that require editing. To assist you in this process the best tool is some editor that understands the Terraform semantics. For this lab you will be using a web based integrated development environment that uses the code that is inside Microsofts Visual Studio Code. When Microsoft wrote Visual Studio Code it built the IDE on top of a platform called electron. This allowed for cross platform development and is based on javascript.

Visual Studio Code can be installed on variety of operating systems, please download the package suitable for your environment and follow the installation process in the wizard:

    https://code.visualstudio.com/

Visual Studio Code has three panes that you will be using:
- The left pane with the files
- The right pane with the file contents
- The bottom pane will be leveraging the Terminal to issue commands

### 1.1 Open a new terminal in the IDE

To get started, first you have to open a terminal windows in the IDE to access the underlying operating system and work the lab. On the menu bar click the *Terminal* tab to open *New Terminal*

    <img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/visual-terminal.png" width = 800>

Terminal will open at the bottom of the screen. This will be the area that you will execute all the terraform commands after making changes to terraform files.

## 2 Create the working directory

Terraform uses directory structures as a way to organize its automation structure. This is due to the fact that Terraform treats everything in a directory as a unit and reads all the `.tf` files before execution.
The first step is to create a directory called *ACI* for the terraform files. Using the IDE you can create folders. This directory will live under the ACI folder. There are various ways to create these in visual studio code: using the contextual menu (1a and 1b) or using the icons (2):

    <img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/visual-new-folder.png" width = 800>
    <img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/visual-new-folder2.png" width = 800>

In that directory create the first terraform file called `access_policies.tf`

## 2. Second section
