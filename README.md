# Connect-a-GitHub-Repo-with-AWS
This project demonstrates how to set up and manage a Git repository for a Java-based web application. The primary objective is to showcase best practices for tracking, versioning, and securely storing application code using Git and GitHub. As part of Project Two in the 7-Day DevOps Challenge,.

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-github)

**Author:** Sunday Obikoya  
**Email:** princelyob@gmail.com

---

## Connect a GitHub Repo with AWS

![Image](http://learn.nextwork.org/loving_pink_serene_kea/uploads/aws-devops-github_dd9d254e)

---

## Introducing Today's Project!

In this project, I will demonstrate how to set up a Git repository for my web app’s code. I’m doing this project to show how to manage, track, and store my Java web application using Git and GitHub. This is Project Two of the 7-Day DevOps Challenge, and by the end, all my web app code will be securely stored in GitHub.

### Key tools and concepts

During this project, I gained hands-on experience with essential cloud, development, and version control tools used in modern DevOps workflows. The primary services and tools included GitHub for hosting and managing a remote code repository, Amazon EC2 as a development instance for building and testing the application, SSH key pairs for secure authentication, and Visual Studio Code as the main development environment using Remote SSH.

Key concepts learned include setting up and managing a local Git repository, understanding the difference between Git as a distributed version control system and GitHub as a collaboration and repository hosting platform, and using core Git commands to stage, commit, and push code changes. I also learned how to configure a remote origin, work with upstream repositories, and manage branches to support organized and collaborative development workflows. The project reinforced best practices around secure access, version control, and cloud-based development.

### Project reflection

This project took approximately five hours to complete. The most challenging aspect was configuring Remote SSH between Visual Studio Code and the Amazon EC2 instance. One of the major issues I encountered was losing the remote connection, where running the SSH command in the terminal resulted in no response and appeared to be stuck. After debugging the issue, I discovered that the problem was related to my private key not being properly recognized. Once I corrected the SSH configuration and key permissions, the connection was successfully restored. Troubleshooting and resolving this issue was the most rewarding part of the project, and it allowed me to complete the README file I was working on.

I undertook this project today to practice and reinforce my DevOps and cloud computing skills, specifically in deploying and managing a Java web application on AWS using CI/CD principles. I wanted to gain hands-on experience with key tools such as GitHub, Amazon EC2, SSH key management, and VS Code Remote SSH, and to better understand how these components work together in a real-world development workflow.

Additionally, I aimed to improve my problem-solving and troubleshooting skills by encountering and resolving issues, such as SSH connection errors and key configuration problems. Completing this project also allowed me to document my process clearly in a README file, which strengthens my ability to communicate technical concepts effectively—an essential skill for both collaboration and professional development.

 AS SOOS AS POSIBLE

---

## Git and GitHub

Git is a version control system that works like a time machine and filing system for my code. It tracks every change I make, lets me revert to earlier versions if something breaks, and helps me organize my project as it grows.

I installed Git on my EC2 instance using the package manager. On Amazon Linux, this is done by running the commands:

sudo dnf update -y
sudo dnf install git -y


GitHub is a platform for version control and collaboration. It acts as a cloud-based storage space where I can host the various versions of my project that Git tracks. While Git helps me track changes in my code locally, GitHub allows me to store and manage those changes online. This makes it easy to access my work from anywhere and collaborate with other developers over the internet.

![Image](http://learn.nextwork.org/loving_pink_serene_kea/uploads/aws-devops-github_efaadbf7)

---

## My local repository

A repository (or "repo") is a storage space for your code in Git. It’s essentially a folder that contains all the files for your project, along with their complete version history. When you host a repo on a platform like GitHub, it allows you to collaborate with other developers and access your project from anywhere, since it’s stored in the cloud.

To begin using Git for version control, I first need to create a local repository on my computer.
When I run git init inside the directory (nextwork-web-project), it initializes the directory as a Git repository. From that point on, Git will start tracking changes made to the files in that directory, enabling version control for my project.


In Git, a branch is essentially a separate line of development within your project. It allows me to work on different features, bug fixes, or experiments without affecting the main codebase (typically called the "main" or "master" branch).
When I create a branch, I am making a copy of the code at that point in time. I can make changes, commit them, and test MY work independently. Later, I can merge the branch back into the main branch (or another branch) once I am satisfied with the changes.
Branches make collaboration easier because multiple people can work on different features or fixes simultaneously without interfering with each other’s work.


![Image](http://learn.nextwork.org/loving_pink_serene_kea/uploads/aws-devops-github_7bf21bae)

---

## To push local changes to GitHub, I ran three commands

### git add

First, I ran git remote add origin https://github.com/your-username/your-repo.git to link my local repository with my GitHub repo. Since they weren't connected, this command tells Git where the remote repo is located. The "origin" acts as a shortcut to the GitHub repo URL, so I don’t need to type it out every time I push changes.

Next, I ran git add . to stage all changes (new, modified, or deleted files) in the current directory and its subdirectories for the next commit. The dot (.) refers to the current directory. This command doesn't commit the changes but prepares them to be included in the next commit.




### git commit

The second command was  "git commit -m "Updated index.jsp with new content" 

The command saves the staged changes as a snapshot in my project's version history. This means I am officially recording the changes I've made, creating a new commit in the repository.

The -m flag allows to add a message that describes the changes made in this commit. The message helps  to understand what was updated without looking at the code itself.

This commit becomes part of the version history, so it can be review or revert to this version if needed later.

In simple terms, it’s like saying: "I want to save my current progress and document what I changed."


### git push

The third command I ran was "git push -u origin master
 Using"  '-u' means...

The third command I ran was "git push -u origin master" 

This command pushes my local changes to the remote GitHub repository (origin) on the master branch.

git push: Sends the changes from my local repository to the remote repository.

-u: Sets the upstream reference, linking my local branch (master) with the remote branch (origin/master). This allows Git to track the connection, so in the future, I can just use git push without specifying origin master.

origin: Refers to the remote GitHub repository.

master: Specifies the branch on GitHub where the changes will be pushed.

---

## Authentication

When I commit changes to GitHub, Git asks for my credentials ie my username (and password) to verify that I have the necessary permissions to push changes to the remote repository (origin) that my local repo is connected to. This authentication step ensures that only authorized users can make changes to the repository on GitHub.
It’s part of the security process, making sure that the right person is making the changes.


### Local Git identity

Git requires a name and email to identify who made each commit. This information becomes part of the commit’s metadata and is essential for collaboration and tracking changes.

Running git log showed the commit history of the repository. Specifically, it displayed:
•	The commit hash (unique identifier for each commit)
•	The author’s name and email
•	The date and time the commit was made
•	The commit message describing the change
This output allows to see what changes were made, who made them, and in what order, helping you track the project’s history and understand its development over time.


![Image](http://learn.nextwork.org/loving_pink_serene_kea/uploads/aws-devops-github_9a27ee3b)

---

## GitHub tokens

GitHub authentication failed when I entered my password.  This is because GitHub no longer supports password authentication for Git operations as part of their security best practices. Instead of using my GitHub password, I now need to use a Personal Access Token (PAT).
This change enhances security by ensuring that my authentication is more robust. A PAT works similarly to a password but can be scoped to specific permissions, reducing the risks associated with using your actual account password.


A token in GitHub (commonly called a Personal Access Token or PAT) is a secure string of characters that acts as an alternative to a password when authenticating with GitHub. In this project, I am using a token to securely authenticate access to the GitHub repository from the local repository.

I  set up a GitHub token by going through these following steps;

1) I went into my browser with GitHub open.

2) On my profile icon I select Settings.

3) I Select Developer settings at the very bottom of the left hand navigation panel.

4) I Select Personal access tokens.

5) I Select Tokens (classic).

6) I Select Generate new token.

7) I Select Generate new token (classic).

8) I Give my token a descriptive note,

9) I Lower the token expiration limit from 30 days to 7 days.

10) I Select the checkbox next to repo.

11) I Select Generate token.

![Image](http://learn.nextwork.org/loving_pink_serene_kea/uploads/aws-devops-github_fa11169d)

---

## Making changes again

I wanted to see Git working in action, so I went back to my GitHub tab and navigated to the src/main/webapp folder to view index.jsp. I had updated index.jsp in my VS Code environment; however, I could not see the changes in my GitHub repository because saving changes in VS Code only updates the local repository. The changes are not reflected on GitHub until they are committed and pushed.

I finally saw the changes reflected in my GitHub repository. After returning to my VS Code window, I staged the changes in the terminal using git add . and reviewed them with git diff --staged. I then committed the changes by running git commit -m "Add new line to index.jsp" and pushed them to GitHub using git push.

![Image](http://learn.nextwork.org/loving_pink_serene_kea/uploads/aws-devops-github_6becb2bc)

---

## Setting up a READMe file

A README file is a text file (usually named README.md) that explains what a project is about. It typically includes information such as the project’s purpose, how to run or use it, the technologies used, and any important notes for users or contributors.
As a finishing touch to my GitHub repository, I added a README file, which provides an overview of the project and helps others understand how to use or run it.
I added a README file by creating a README.md I ran “touch README.md”, adding the project details, and then staging, committing, and pushing the file to GitHub using Git commands.


My README is written in Markdown because it is a lightweight, platform-independent markup language that enables clear, structured, and readable technical documentation. Markdown is natively supported by version control platforms such as GitHub and GitLab, allowing documentation to be rendered consistently without additional tooling.

Special characters in Markdown are used to apply formatting and semantic structure to text. For example:

# is used to define headings and section hierarchy

* or _ are used for emphasis such as italics and bold text

` is used to format inline code and code blocks

- or * are used to create ordered and unordered lists

> is used for blockquotes

[]() is used to create hyperlinks

These formatting features improve readability, emphasize key technical details, and make the documentation easier to navigate and maintain.

My README file contains six structured sections that clearly document the project and guide the reader through its purpose, implementation, and usage:

Title / Welcome Page
Java Web App Deployment with AWS CI/CD
A brief welcome and overview introducing the project, which combines Java web application development with AWS CI/CD tools.

Table of Contents
Provides quick navigation to each section of the README for improved readability and accessibility.

Introduction
Describes the project’s objectives, scope, and the problem it addresses, giving context to the solution.

Technologies
Lists the tools, frameworks, and services used, including Java and AWS CI/CD components.

Setup
Outlines the steps required to configure, deploy, and run the application in the target environment.

Contact
Provides author or maintainer contact information for questions, collaboration, or feedback.

Conclusion
Summarizes the project, key outcomes, and potential next steps or improvements.

![Image](http://learn.nextwork.org/loving_pink_serene_kea/uploads/aws-devops-github_c94976902)

---

---
