![](images/300/Picture-lab.png)  
Updated: Date

## Introduction

This part of the lab will help you create your external Jenkins web server and connect it via webhooks with Autonomous Developer Cloud Service. 

## Objectives

- Configure Jenkins Server
- Successfully deploy Jenkins Server
### **STEP 1**: Download [Jenkins](https://jenkins.io/download/) 2.149
* Jenkins will then ask for the __administration password__. To get this password type in the terminal
```
sudo cat /Users/Shared/Jenkins/Home/secrets/initialAdminPassword
```
* Copy the password in terminal and past is in the __Administration Password__ field. 
![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.56.05%20PM.png)
* Click "install suggested plugins". This process may take a few minutes to complete. Until this is done feel free to browse Oracle's Autonomous Developer Cloud Services to make yourself familiar with all the different offerings. 

### **STEP 2**: Setup admin information and continue. 
* Go to __configure --> Global Tool Configuration__, install the following plugins:
  * Unleash Maven Plugin
  * Notification Plugin
  * Build Authorization Token Root Plugin
  ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.44.36%20PM.png)
  ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.44.54%20PM.png)
  ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.45.10%20PM.png)
  * __Note__: Be sure to restart your server after installing the plugins. 
  
* Configure Git, Java, and Maven settings: Go to __Manage Jenkins --> Global Tool Configuration__
 * For Git give any name you want and then set your path to your git.exe. To find this path go into terminal and type in
 ```
 which git
 ```
 * For Java give any name you want and then set the path of JAVA_HOME. To find this path go into terminal and type in
 ```
 /usr/libexec/java_home
 ```
 * For Maven, choose install automatically. 
 ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.43.58%20PM.png)
 ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.44.12%20PM.png)
 
* Go to the Jenkins Dashboard page and click __create new jobs__ and or __new item__ to create a job. 
  * __Enter an item name__: AutoDevCS_JavaApp
  * __Job type__: Maven
  * Press __OK___
  ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-31%20at%201.56.43%20PM.png) Ignore red text in the picture above ^^^.
  
* In the __description__ field of the __general__ tab on the Configuration page, enter a desrciption of the job that you see fit.
![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-31%20at%202.00.04%20PM.png)

* Click the __Source Code Management__ tab.
  * Select the __git__ options
  * Enter the __Oracle Autonomous Developer Cloud Service Git repository URL__.
  * In the __credentials__ section click __add-->Jenkins__ and provide your Oracle Autonomous Developer Cloud Service credentials. 
  * Click __Add__ when you are done. If you are receiving a red error please make sure you have entered your credentials correctly. The error message should disappear after Jenkins verifies your credentials. 
  * __Note__: Make sure that you select the credentials you have just created. 
  ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.46.18%20PM.png)
  
* Click the __Build__ tab.
  * Root POM: __HelloWorld/pom.xml__
  * Goals and options: __clean install__
  ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.46.40%20PM.png)
  
* Click the __Post-build Actions__ tab
  * Click the __Add post-build action__ button and select the __Archive the artifacts__ options.
  * You will now see a __Files to archive__ field enter: __HelloWorld/*.war__
  ![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.46.40%20PM.png)
  
* Click the __Build Triggers__ tab
  * Select the __Trigger builds remotely__ check box
  * In the __Authentication token__ field enter: __my_auth_token__
* Click __save__

![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-30%20at%202.46.25%20PM.png)


### **STEP 3**: Go to your terminal and type the command:
```
ssh -R 80:localhost:8080 ssh.localhost.run
```
This will allow your external Jenkins server to connect to the internet. You can now log into your Jenkins server using the new url provided. 

![alt text](https://github.com/blakeramos/JavaWebApp/blob/master/a1screeenshots/Screen%20Shot%202018-10-31%20at%208.50.11%20AM.png)

* __Note__: If you aren't seeing your changes in your Autonomous DevCS project you might need to restart you server because of a broken pipe. Just re-type in the terminal command in the above picture and it should start to work again. 
