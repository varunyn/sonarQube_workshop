

## Introduction

This is the first of several labs that are part of the **Continous Code Inspection with Sonar Qube.** This workshop will walk you through how to manage application lifecycle and do code review using sonarQube.

## Objectives

- Fix the issue in code
- Run the job to see the new analysis
- Close issue.

## Required Artifacts

For this lab you will need Oracle Cloud account and Developer Cloud service instance.

## Fixing the issue in code

### **STEP 1**: Check for the issue in SonarQube

- Continuing the previous lab, go to the issues page in sonarQube, for this workshop we will solve the issue type Bug.

    ![](images/300/1.png)

- As you can see there are two issues shown under bug category with severity Critical and Major. 

    ![](images/300/2.png)

- Click on the first issue and check for the error message. As you see the error message, you can select the type of issue, severity, whether the issue is solved or still open, who is it assign to and how many minutes it might take to fix the issue.

    ![](images/300/3.png)

### **STEP 2**: Create issue in Developer Cloud Service

- We will generate new issue based on the error messagee seen in the previous step. Click on **Issues** in the left panel and then click on **Create Issue**.

    ![](images/300/4.png)

- Fill out the form as shown in the below image.

    ![](images/300/5.png)

- Repeat the process and create another issue.

### **STEP 3**: Edit code in DevCS git repo

- Click on **Git** in left panel to see the code repository.

    ![](images/300/6.png)

- Go to the file SampleStreamExample.java , path as shown in following image and  click on pencil icon to edit.
    ![](images/300/7.png)

- Go to line 114 and add word **throw** before the line.

    ![](images/300/8.png)

- Repeat the process and go to file TwitterService.java, path as shown in following image and click on pencial icon to edit.

    ![](images/300/9.png)

- Go to line 86 and remove **return**. 
Reason of error: Using return, break, throw, and so on from a finally block suppresses the propagation of any unhandled Throwable which was thrown in the try or catch block.
    
    ![](images/300/10.png)

### **STEP 4**: Check the SonarQube for issue fix

- With the job already configured to run automatically on commit, go to SonarQube server dashboard. And you can see there are zero bugs shown.

    ![](images/300/11.png)

- To confirm open issues page and click on bug.

    ![](images/300/12.png)
   
### **STEP 5**: Close the issue in Developer Cloud Service

- Go back to Developer cloud service and click on **Issues** in left panel.

    ![](images/300/13-1.png)

- Select the issue and then click on **Update Selected**

    ![](images/300/13.png)
    
- In the form check the Status and select Resolved . Also check Resolution and select Fixed from dropdown, click **Next** when finished and then Save to close the issue.
    ![](images/300/14.png)
    ![](images/300/15.png)




