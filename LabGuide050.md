
<!-- ![](images/100/Picture100-lab.png)   -->

## Introduction

This is the first of several labs that are part of the **Continous Code Inspection with Sonar Qube.** This workshop will walk you through how to manage application lifecycle and do code review using sonarQube.

**_To log issues_**, click here to go to the [github oracle](https://github.com/oracle/learning-library/issues/new) repository issue submission form.

## Setup trial account

### **STEP 1**: Acquire an Oracle Cloud Trial or Workshop Account

- Bookmark this page for future reference.

- Please click on the following link to create your Free Account, and complete all the required steps to get your free Oracle Cloud Trial Account. When you complete the registration process you'll receive a $300 credit that will enable you to complete the lab for free. Additionally, you'll have 1000s of hours left over to continue to explore the Oracle Cloud.

    - Soon after requesting your trial you will receive the following email. You may begin working on Lab 100 before you receive this email, but you will not be able to start Lab 200 until you have received it.

    ![](images/050/100_1_1.png)

    ***setup a password***

### **STEP 2**: Login to your Oracle Cloud Account
- From any browser, go to the URL:
    `https://cloud.oracle.com`

- click **Sign In** in the upper right hand corner of the browser

    ![](images/050/Picture100-1.png)


- Enter your identity domain and click **Next**

    **NOTE:** The **Identity Domain** should come from your Trial confirmation email.

    ![](images/050/1.png)

- Once your Identity Domain is set, enter your User Name and the Password you set after your confirmation e-mail and click **Sign In**

    ![](images/050/2.png)

- You will be presented with a Dashboard displaying the various cloud services available to this account.

    ![](images/050/3.png)

- Click on the hamburger menu on the top left corner and scroll down and click on **My servcies dashboard** which will take you to the service dashboard page.

     ![](images/050/4.png)

- If all your services are not visible, **click** on the **Customize Dashboard**, you can add services to the dashboard by clicking **Show.** For this workshop, you will want to ensure that you are showing at least the **Java, Application Container, Database and Storage Classic** cloud services. If you do not want to see a specific service, click **Hide**

    ![](images/050/5.png)

    ![](images/050/6.png)

### **STEP 3**: Create Developer cloud service instance

- Once you see developer tab in the page, click on hamburger menu and then open service console.

  ![](images/050/7.png)

### **STEP 4**: Create Compartment

- Click on the hamburger menu on the top left and then scroll to **identity** and then click **Compartments** .

    ![](images/050/lab100_Create_Compartment.png)

- Click on create compartment

    ![](images/050/lab100_Create_Compartment_1.png)

- Fill out the details Name, description and then click **Create Compartment**

    ![](images/050/lab100_Create_Compartment_2.png)


### **STEP 5**: Create VCN and edit security rules

- Once the Compartment is ready, we will create VCN. Click on the hamburger menu on the top left, **Networking** and then click on **Virtual Cloud Networks**

    ![](images/050/lab100_Create_VCN_1.png)

- Make sure to select **sonarQube** compartment and then click on **Create Virtual Cloud Network**

    ![](images/050/lab100_Create_VCN_2.png)

- Fill out Name and make sure to click on the second option **CREATE VIRTUAL CLOUD NETWORKS PLUS RELATED RESOURCES**
    ![](images/050/lab100_Create_VCN_3.png)

- Scroll down and click **Create Virtual Cloud Network**  

    ![](images/050/lab100_Create_VCN_3_1.png)

- Once you see the VCN created click on it and then click on **Security List**

    ![](images/050/lab100_Create_VCN_4.png)

- By default one security list is created when you create the VCN, click on it.

    ![](images/050/lab100_Create_VCN_5.png)

- Click on **Add Ingress Rules**.
    ![](images/050/9.png)

- Enter Source CIDR 0.0.0.0/0 and destination port range **9000,8080**. We are opening port 9000 which is default port for running sonarQube which we will deploy in next lab and port 8080 which is default for our web service which we will deploy in lab 400.

    ![](images/050/10.png)

- Once saved you can see the Ingress Rules as below.

    ![](images/050/11.png)


### **STEP 6**: Create Instance

- Click on the hamburger menu on top right, then Compute and then click on **Instances**.

    ![](images/050/lab100_Create_Instance_1.png)

- Once you see the instances page, make sure to select right compartment and then click on **Create Instance**

    ![](images/050/lab100_Create_Instance_2.png)

- Give name of the instance, select availability domain.

    ![](images/050/lab100_Create_Instance_3.png)

- Choos the public key provided or paste it.

    ![](images/050/lab100_Create_Instance_3_2.png)

- Click **Create**

    ![](images/050/lab100_Create_Instance_3_3.png)

- Repeat the process and create one more instance named **JavaWebService**.