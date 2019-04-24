
<!-- ![](images/100/Picture100-lab.png)   -->

## Introduction

This is the first of several labs that are part of the **Continous Code Inspection with Sonar Qube.** This workshop will walk you through how to manage application lifecycle and do code review using sonarQube.

You will take on 2 Personas during the workshop. The **Lead Developer Persona**, who manages a team of developers writing and maintaining production applications and Richard **Devops manager** persona who's current challenge is providing the resources to host current applications on-premises.


**_To log issues_**, click here to go to the [github oracle](https://github.com/oracle/learning-library/issues/new) repository issue submission form.

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

- Click on **Edit all rules**

    ![](images/050/lab100_Create_VCN_6.png)

- Scroll down when and click **Another Ingress Rule**

    ![](images/050/lab100_Create_VCN_7_1.png)

- Add source CIDR ```0.0.0.0/0``` and Destination Port Range ```9000```

    ![](images/050/lab100_Create_VCN_7_2.png)

- Scroll and click on **Save Securtiy List Rules**   

    ![](images/050/lab100_Create_VCN_7_3.png)

### **STEP 5**: Create Instance

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