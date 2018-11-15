![](images/100/200.png)  
Updated: November 15th, 2018

## Introduction

In this lab you will setup GIT with your IntelliJ IDE.

## Objectives

- Setup GIT with IntelliJ IDE


# Lab: 200
## In this lab you will setup GIT with your IntelliJ IDE. 
* Download [Git](https://git-scm.com/downloads)
* Download [IntelliJ](https://www.jetbrains.com/idea/download/#section=mac)

### **STEP 1**: Go to __IntelliJ preferences --> Version Control --> Git__
![](a1screeenshots/Screen%20Shot%202018-10-29%20at%203.24.57%20PM.png)
![](a1screeenshots/Screen%20Shot%202018-10-29%20at%203.25.11%20PM.png)

* You are now going to configure the path to the Git executable. Your Git executable path should be: 
```
/usr/local/bin/git
```
If this does not work, open up the terminal and type in:
```
which git
```
This should give you the path to your git executable. 
* Click on __OK__ 

### **STEP 2**: Go back to your project on __Autonomous Developer Cloud Service__ and click on __code__.
* Click the "http" button. Copy this link as we will need it to allows our IntelliJ IDE to commit, push, and pull changes to our code repo.
![](a1screeenshots/Screen%20Shot%202018-10-29%20at%203.35.38%20PM.png)

* Go back to __IntelliJ IDE__ and click on __VCS --> Checkout from Version Control --> Git__
* Insert copied Git URL from Autonomous DevCS and paste into IntelliJ. Click on test and then enter your credentails that you used to log into your cloud tenancy. 
![](a1screeenshots/Screen%20Shot%202018-10-29%20at%203.30.04%20PM.png)
![](a1screeenshots/Screen%20Shot%202018-10-29%20at%203.30.31%20PM.png)

* Clone the repo and open the project within IntelliJ. From there go into the index.jsp file and change the output.
* Save your changes
* Click on __VCS --> Git --> Push__
![](a1screeenshots/Screen%20Shot%202018-10-30%20at%208.53.53%20AM.png)

* __Commit__ and __push__ your changes. Once that is complete go back to your Autonomous DevCS project, click 'project' on the left hand side and see that your changes have been committed. 
![](a1screeenshots/Screen%20Shot%202018-10-30%20at%208.56.22%20AM.png)
![](a1screeenshots/Screen%20Shot%202018-10-30%20at%208.56.35%20AM.png)
![](a1screeenshots/Screen%20Shot%202018-10-30%20at%208.56.35%20AM.png)


* __NOTE__: Go back to your Autonomous Developer Cloud Service project, go to the sidebar to confirm you are in project. You should see that your changes from IntelliJ have been recognized. You should also be able to see the changes in the 'code' section. 
