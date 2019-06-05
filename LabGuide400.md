

## Introduction

This is the fourth of several labs that are part of the **Continous Code Inspection with SonarQube.** This workshop will walk you through how to manage application lifecycle and do code review using SonarQube.

**_To log issues_**, click here to go to the [github oracle](https://github.com/oracle/learning-library/issues/new) repository issue submission form.

## Objectives

- Create docker image and push it to Docker Hub.
- Create compute instance using Docker image.
- Test the application.

## Required Artifacts

For this lab you will need Github and Oracle Cloud account Hub Accounts. Use the following links to set up:

## Deploying the Application to Compute Instance

### **STEP 1**: Create Build Job to Create and Push Docker Image to Registry

- Continuing the previous lab, make sure to be in Developer Cloud Service Instance.
- Create Build Job. Click on **Builds** in left panel and then click **Create Job**.

    ![](images/400/1.png)

- Give name to job and select template.

    ![](images/400/2.png)

- Click on **git** in the Job configuration, click on **add Git** and then make sure to select correct git repository.

    ![](images/400/3.png)

- Click on **Steps** , **Add step** , select Docker and then **Docker login**.

    ![](images/400/4.png)

- Enter username and password of the docker hub account. **Note: If you don't have docker account, create one from [Docker Hub website](https://hub.docker.com)**

    ![](images/400/5.png)

- Again click on **Steps** , **Add step** , select Docker and then **Docker build**.

    ![](images/400/6.png)

- Enter Registry host, desired name for the image (twitter-feed), tag (latest) and source (we have it in git repo)

    ![](images/400/7.png)

- Once again click on **Steps** , **Add step** , select Docker and then **Docker push**.

    ![](images/400/8.png)

- Enter registry host and name of the image and then click **Save** on top of the page.

    ![](images/400/9.png)

- Click on **Build Now** to run the job and see the build logs to see if it is successful.

    ![](images/400/9-1.png)

- To confirm go to [Docker Hub website](https://hub.docker.com) and click on **repositories** in navigation bar.

    ![](images/400/10.png)

### **STEP 2**: Create Build Job to Run Docker Image in Compute Instance

- Create another Build Job. Click on **Builds** in left panel and then click **Create Job**.

    ![](images/400/1.png)

- Give name to job and select template.

    ![](images/400/11.png)

- Click on **Before Build** in Job configuration, **Add Before Build Action** and then select **SSH configuration**.

    ![](images/400/12.png)

- Paste the private key provided in git repo or paste the below key and select option **Setup files in ~/.ssh for command line tools**.

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

    ![](images/400/13.png)

- Click on **Steps**, **Add Step** and select **Unix Shell**.

    ![](images/400/14.png)

- Paste the below command to the shell.

  _NOTE: Replace the IP address with the IP address of your JavaWebService compute image created in lab 050, docker image name from your docker hub._

  ```
  ssh -o StrictHostKeyChecking=no opc@ENTER_THE_IP_ADDRESS_HERE_OF_JavaWebService_INSTANCE << EOF
  sudo yum install -y yum-utils \
    device-mapper-persistent-data \
    lvm2
  sudo yum-config-manager \
      --add-repo \
      https://download.docker.com/linux/centos/docker-ce.repo
  sudo yum -y install docker-ce docker-ce-cli containerd.io
  sudo systemctl start docker
  sudo docker pull DOCKER_IMAGE_NAME
  sudo firewall-cmd --zone=public --permanent --add-port=8080/tcp
  sudo firewall-cmd --reload
  sudo docker run --detach -p 8080:8080 DOCKER_IMAGE_NAME
  exit
  EOF
  ```



- Paste the commands in Unix Shell and click **Save**.

    ![](images/400/15.png)

- Click on **Build Now** to run the Job. Check the logs for message.

    ![](images/400/16.png)

- To confirm everything is deployed successfully. Go to your **IP_address:8080/statictweets**.

    ![](images/400/17.png)
