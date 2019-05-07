<!-- ![](images/200/Picture200-lab.png)   -->

## Introduction

This is the first of several labs that are part of the **Continous Code Inspection with Sonar Qube.** This workshop will walk you through how to manage application lifecycle and do code review using sonarQube.

**_To log issues_**, click here to go to the [github oracle](https://github.com/oracle/learning-library/issues/new) repository issue submission form.

## Objectives

- Deploy the SonarQube server to the Compute Instance
- Verify the Server Deployment and run analysis

## Required Artifacts

For this lab you will need Oracle Cloud account and Developer Cloud service instance.

## Deploying SonarQube application to Compute Instance

### **STEP 1**: Create build job to deploy SonarQube docker image in Compute Instance.

-  Click on **Create Job** 

    ![](images/200/lab200_createBuildJob_1.png) 

- Give the name for Job. For sake of simplicty we name it deploySonarQube. Make sure to select template.

    ![](images/200/lab200_createBuildJob_2.png)

- Click on **Before Build** in Job Configuration and then click on **Add Before Build Action** and then select **SSH Configuration**.

    ![](images/200/lab200_createBuildJob_3.png)

- Paste the Private Key for the Public key used to create Compute Instance in Lab 050. Also select **Setup files in ~/.ssh for command-lins tools**

```
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAk5p0D6ab7j9eTOY8060aDM1qREQyFfa9BKtZo/uaxJBaVmkR
3HIJBmUaY0wXKlp/N1BhtW5n3w3QsuBJFlsnTbuSZZdy9jBaxfUwT4OGY9jIdlec
dw0KLM8qQx4hpe7Kdc/ixmKTwpnT3Ls/0qy2zKyttl+ox7RGSV+emH2eRRFSoojr
KvwHuPM28RFFCmQEOWHVkiy4mjgJqTKntqkL8okYs9DwLEKfKj+qRo6scTAWWnGR
pTwg7qw+hOV8Yf1fky/ENF+9zdRXsZSLjuMeSqACUHUEK0kREybjUQtYewTTQJ/b
tCW8vVNKqNtFLYC0G6QUp29BaC7sFMZj1KXP6wIDAQABAoIBAAT6NmO4uJVmKaXq
Na7lrXU1EBpROmcnNOSNaq5u858hRwqW7HVEmy1OB3/FtxpEhvm0ijb2DCanbpw5
l/1bAY5LfvpSCxxmMQlv5TspMkT3sHrdJXeWRvuP2Nr+jx/rV4R1iC4scNMlINHW
tqZCEMACKrF1tFlXqO8cfFqkEcw+ZjC/2ywkiq2GMA6l41p3iij0vtX5tZ86x9Eb
LSv/d4xzJBRSnr93eJ21SEVP/wCWerWpAYbVUhA1LXz09G4U9d71oWs1Uuxdeeu4
WxupUNsJcR6df1eVIHFKVSXsIAapQNdeML//FSO7ZN3MZNglCMElRvbkw5yJN0Jf
Ee5FcTECgYEAwqn2k6SwLDWPeMI/PEr5Z++6OjL/uCHjBrvWVPQeLlBs6sWqpOSU
3DbTKXZNQePpJR8yZVyCfVDpFDY9iO/gPV1uKPFV+Mt6SIuyfsC1rxgaipJosxSP
qK13nvKRD4zUVDTVZ1A6cWf3qXxQxpfcINCcktRUku6V9mv9OtLM4rUCgYEAwhx5
yyFRyTQOiQhebbdvonxJVvHDLGEeNxEns3a2AnqlRO2a7xBIgqP4qyQXNw1z9+8P
FDVl5p/vc0Tf2v/4EjvWadFuiFi4UUSp45C8FfZAaSPpzV9qZ2wU69cITqGWuOSE
tQF6Gw0DhiliG9Q1f8/GZNh21FGnWN0bI0qqbB8CgYAKCJyvC4QRI0mb3ddIkky8
sLyWl15a7VQ4WqI3isWreXXDvCCJk0ag+ypzLqfYx5iS00LTuqr3Lp507j7JuiOC
xjgRYC8gPcy1xI2UvvYeak2j6tv+rwagmSBbTwFvHcEr/fUp+BarFcLMN54qPlWY
U2heoRci461TIEnTKF5rKQKBgAz8Gqmb8PykntRL2wU74BvedIl8YrH1TTAh1aYL
quE/kw6pVlPnovIaRegs4eCs5bUQKNIRQF/NExeC4/aiaNXPauhpOhuk06+cCEFQ
zUQq1OQzotA6McP5Vuzv1X5tEMgNgVMaZjCpDjNLUWTLLUj/fSYB1PEfBTLMl6Qk
uoHBAoGBAMH8/LbPs5yNM0YUZAuNijmqK8JnRAXdHb14m4/1kJvItx6sxoBtiWgm
ryq4/XTyF5j9XsEF3v5wSot9aFLPUpfndaCLvFKgptUhICHTuPmBFhKX9yZbf2Iz
sawLIbtlGQwtd8mO8uHFHW8kMEDei/qL+WhgimdeJeF2k8Xv939N
-----END RSA PRIVATE KEY-----
```
- Note: You can use your own keys but to keep the lab guide easy we are providing one for you.

    ![](images/200/lab200_createBuildJob_4.png)

- Next, click on **Steps** and then **Add Step** and select **Unix Shell**.

    ![](images/200/lab200_createBuildJob_5.png)

- Paste the following commands in the Unix Shell

```
ssh -o StrictHostKeyChecking=no opc@PUT_YOUR_PUBLIC_IP_ADDRESS_OF_THE_INSTANCE_CREATED_IN_LAB_050 << EOF
sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
sudo yum -y install docker-ce docker-ce-cli containerd.io
sudo systemctl start docker
sudo docker pull sonarqube
sudo firewall-cmd --zone=public --permanent --add-port=9000/tcp
sudo firewall-cmd --reload
sudo docker run --detach -p 9000:9000 sonarqube
exit
EOF
```
- NOTE: In the above commands what we are doing is: SSH into the instance -> install docker in instance -> start docker -> pull sonarQube docker image -> open firewall -> open port and run image

    ![](images/200/lab200_createBuildJob_6.png)

- Click **Save**

    ![](images/200/lab200_createBuildJob_7.png)

### **STEP 2**: Run the build job and check server deployment

- Click on **Build now**

    ![](images/200/lab200_createBuildJob_8.png)

- Once the build start running click on **Build Log** to check the log and see what steps are being performed.

    ![](images/200/lab200_runBuildJob_1.png)

- Scroll down till the end of log to see success message.

    ![](images/200/lab200_runBuildJob_2.png)

### **STEP 3**: Configure Developer Cloud Service to use SonarQube

- Click on **Project Administration** and then click on **Add SonarQube Server Connection**

    ![](images/200/lab200_configureSonar_1.png)

- In the form fill out details. Username and Password is **admin**. Then click **Create**

    ![](images/200/lab200_configureSonar_2.png)

- Once added let's test if the connection works. Click on **Test Connection** and then check the message for the status.

    ![](images/200/lab200_configureSonar_3.png)

- Go back to Build tab and click on the build created in Lab 100 and click on **Configure**

    ![](images/200/lab200_configureSonar_4.png)

- Click on **Before Build**, then click on **Add Before Build Action** and select **SonarQube Settings**.

    ![](images/200/lab200_configureSonar_5.png)

- Select the Sonar Server which we created for the dropdown list.

    ![](images/200/lab200_configureSonar_6.png)

- Go the **Steps** and the click **Add Step** and select **Maven**.

    ![](images/200/lab200_configureSonar_7.png)

- Here add the sonarQube server URL using the following command and then save once done.

```
sonar:sonar -Dsonar.host.url=SONARQUBE_SERVER_URL
```

- NOTE: Make sure to change the URL in the above command. It should Public IP address of the compute instance and the port which 9000.

    ![](images/200/lab200_configureSonar_8.png)

- Click on **Build Now** and once the job is running click on **Build Log**

    ![](images/200/lab200_runBuild_1.png)

- Check the logs, scroll down to see the status.

    ![](images/200/lab200_runBuild_2.png)

- Check the IP to see the dashboard.


### **STEP 4**: Check the analysis

- To check the anaylsis done by SonarQube, go to the SONARQUBE_SERVER_URL.

    ![](images/200/lab200_soarqube_dashboard.png)

- Login using username and password as admin.

    ![](images/200/1.png)

- Click on the **Projects** and there you click on jersey-example.

    ![](images/200/2.png)

- You will see the analysis report in the overview, to check the Issues click on Issues.
    ![](images/200/3.png)

- On the left side there are all the bugs reported in the code.
    ![](images/200/4.png)