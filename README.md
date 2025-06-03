# Jenkins-CI/CD-project with Mohit Soni (mohitsoniv).
# jenkins-cicd 

This page will guide different steps required to setup a Jenkins and its pre-requisites. 
-----
# Install Java 17 
```
sudo apt-get update
```
```
sudo apt-get install openjdk-17-jdk -y
```

## Check Installation
- java -version

-------

# Installing Jenkins on Ubuntu 22.04

## For more details plese visit - https://pkg.jenkins.io/debian-stable/

### Steps to install Jenkins

Open terminal and execute below command

```
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
```
```
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```
```
 sudo apt-get update
```
```
sudo apt-get install jenkins -y
```

## Enable Jenkins Service
```
sudo systemctl enable jenkins
```
```
sudo systemctl start jenkins
```
```
sudo systemctl status jenkins
```

## Get Initial Admin password
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

------ 

# Git 

## Installation 
- sudo apt-get update
- sudo apt-get install git-core
- git --version

## Generating SSH Key
- ssh-keygen      ----- generate key
- eval "$(ssh-agent -s)"  -- Start Agent
- ssh-add ~/.ssh/id_rsa   --- Add key in agent
- cat < ~/.ssh/id_rsa.pub 

------  
-----


# Install Maven

Download the Maven zip file at the below URL if you want to play with Maven on your local machine. If you want to use it on Jenkins then you can install Maven directly from Jenkins console.

Using package
- sudo apt-get install maven -y


##OR
Using zip file
- mkdir tools
- cd tools
- wget https://dlcdn.apache.org/maven/maven-3/3.9.4/binaries/apache-maven-3.9.4-bin.zip
- unzip apache-maven-3.9.4-bin.zip

Check Installation
- mvn --version

-----

# Upgrade Jenkins on Ubuntu
Follow the below steps to upgrade the Jenkins instance to the latest in the current lab. 

### STOP Jenkins Service
- sudo /etc/init.d/jenkins stop

### Rename the Jenkins war file to war.old
- cd /usr/share/jenkins
- sudo mv jenkins.war jenkins.war.old
  

### Download latest war file
- sudo wget https://updates.jenkins-ci.org/latest/jenkins.war

### START Jenkins Service
- sudo /etc/init.d/jenkins start


------

# Git Practice commands

Below are some commands commonly used with Git to manage your code in repository. 
### Clone a git repo
- git clone <git url>

### Create a new branch
- git branch <branch name>

### Switch branch
- git checkout <branch name>

### Create and switch branch
- git checkout -b <branch name>

### Push the newly created branch to the remote 
- git push -u origin <branch name>

### Push change to remote branch
- git push

### Pull change to remote branch
- git pull

### Commit the change to the local branch
- git commit -m "Comment here"

### Adding a file to the stage area or index
- git add filename

### Remove a file to the stage area or index
- git rm --cached filename

### Remove all the uncommitted changes 
- git reset --hard

--------

### Install Docker using the below URL
- https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04
Run the below command to run Jenkins as a docker container
- docker run  --name jenkins -p 8080:8080 -p 50000:50000 -v jenkins:/var/jenkins_home -d jenkins/jenkins:lts-jdk17
- sudo docker logs jenkins



## Run SonarQube as Docker Container
- docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube


----------

### Installing Docker

- https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04

  # 
----  

# Email Notification
There are 2 plugins to send email notification. Email Notification and Extended Email. We will prefer to use Email extended as it provides more features and control on Email notification.

Follow below steps to configure and send email notification

## Setup Google Account to generate App Password
For integrating google email with jenkins, we need to generate a App password. The normal password for gmail will not work with integration. 
To generate google app password, we need to enable 2 MFA. Please follow below steps to generate a app password.

```
- Navigate to Google account --> Profile Pic --> Manage Account

- Select Security and Enable 2 factor authentication if you have not done it
	○ You can follow instruction and choose different option instead of phone number
	○ It will give you option to prompt on your device after login
	○ If you device doesn't appear on page, then Add your google account in your mobile phone

- Once 2MFA is enable navigate back to security Tab and click on 2 Step Verification in Right Pane

- On bottom of the page you will find App Password

- Create a new App password for Jenkins
```
## Setup Jenkins Email Extended Plugin
Navigate to Manage Jenkins--> System--> Extended Email and add following details

```
smtp server : smtp.gmail.com
Smtp port : 465
- Advance
	□ Add Credentials for Google username and App password generated above
	□ Use SSL

Default user email suffix : @gmail.com

ListID : Leave it blank

Default Recipients : ****@gmail.com

Reply To List : noreply@gmail.com

Leave everything as Default

Chose Appropriate Default Triggers
```

## Setup Jenkins Email Notification Plugin

Navigate to Manage Jenkins--> System--> Email Notification and add following details
```
smtp server : smtp.gmail.com
Default user email suffix : @gmail.com
- Advance 
Use SMTP Authentication
Add Credentials for Google username and App password generated above
Use SSL
SMTP Port : 465
Reply To List : noreply@gmail.com
Charset : UTF-8 (by default it is UTF-8)
Test e-mail recipient : <enter recipient email id >
```
## Configure Job to send Email
- Add Extended Email as post Build action to receive emails
- Select Always Triggers


-----

# Slack Notification

To send Slack notifications from Jenkins, you can use the "Slack Notification" plugin. We will configuration at both end Slack and Jenkins. In slack we will need to setup an app and generates token for it. This token will be used in Jenkins to connect with Slack and send notification.

## Slack Configuration
```
1. Create a Slack account if you don't have one. Set up a Slack workspace if you haven't already.

2. To create an app in slack you have required permissions, otherwise you will not be able to see app options

3. Navigate to workspace in Slack-->Settings & adminstration--> Manage apps

4. Click on Build button on top right corner of the page, to create a new App

5. Click on Create New App --> From Scratch --> Provide your prefered name and select your worksace --> Create App

6. You will be landed on the Basic Information page, navigate to "OAuth & Permissions" menu item on left pane

7. On OAuth & Permissions page, under User Token Scope --> click on Add an OAuth Scope

8. Type and select chat:write

9. On top of same page, under section "OAuth Tokens for your workspace" --> click on "Install to workspace" button to generate token

10. Click Allow

11. On slack workspace add a public channel as "Notification"

OR

We can add a existing Jenkins CI app.
1. Navigate to workspace in Slack-->Settings & adminstration--> Manage apps
2. Search "Jenkins CI" in the search App Directory box on top of the page
3. Click on Add to Slack button
4. Choose channel from the dropdown box --> Click on Add Jenkins Ci Integration

```
## Jenkins Configuration
```
1. Install "Slack Notification" plugin

2. Navigate to Manage Jenkins --> System

3. Under Slack section, Add workspace name. The workspace name can find from your workspace url, like if your workspace url is https://training-7u81625.slack.com, then your workspace name will be training-7u81625

4. Add your slack token, generated above, as secret text credentials in Jenkins

5. Specify channel name, created above.

12. Check the checkbox "Custom slack app bot user"

13. Apply and Save
```
## Configuring Jenkins Job
```
1. Add a PostBuild Action --> Select Slack notification
2. Check "Notify Build Start" & "Notify Success" --> Apply & Save
```

That's it! You should now have Jenkins configured to send Slack notifications for your builds.


