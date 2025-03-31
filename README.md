

# Jenkins Installation Guide 🚀

This guide will walk you through the steps to **install Jenkins** and set up a **Docker pipeline** on your Linux machine.

---

## Pre-Requisites ⚙️

- **Java (JDK 17 or higher)**

---

## Step 1: Install Java ☕️

Jenkins requires Java to run. Follow the steps below to install **OpenJDK 17**:

### 1.1 Update your package list and install Java:

```bash
sudo apt update
sudo apt install openjdk-17-jre
```

### 1.2 Verify Java Installation:

```bash
java -version
```

You should see output showing the installed Java version, like this:

```bash
openjdk version "17.0.x" 2021-xx-xx
```

---

## Step 2: Install Jenkins 🔧

### 2.1 Add Jenkins Repository

First, add the **Jenkins repository** and the Jenkins **GPG key**:

```bash
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
```

Then, add the Jenkins repository:

```bash
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

### 2.2 Update the Package List and Install Jenkins:

```bash
sudo apt-get update
sudo apt-get install jenkins
```

---

## Step 3: Access Jenkins 🌐

Once Jenkins is installed, you can access the Jenkins web interface via:

**URL**: [http://localhost:8080](http://localhost:8080)

1. **Retrieve the Jenkins Admin Password**:

   Run the following command to retrieve the admin password:

   ```bash
   sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   ```

2. **Log in**: Use the password to log into the Jenkins web interface.

---

## Step 4: Jenkins Setup 🛠️

### 4.1 Install Suggested Plugins

Once you log in to Jenkins, you’ll be prompted to **install the suggested plugins**. Choose **"Install suggested plugins"**.

![Install Plugins](https://user-images.githubusercontent.com/43399466/215959294-047eadef-7e64-4795-bd3b-b1efb0375988.png)

Wait for Jenkins to finish installing the plugins.

<img width="1291" alt="Screenshot 2023-02-01 at 10 59 31 AM" src="https://user-images.githubusercontent.com/43399466/215959398-344b5721-28ec-47a5-8908-b698e435608d.png">

### 4.2 Create the First Admin User

You will be prompted to create your first **admin user**. This step is optional, but creating an admin user is recommended for future use cases.

- **Fill in the details** for your admin user and click **Save and Finish**.

![Admin User Creation](https://github.com/user-attachments/assets/bf26839a-ace6-495f-80e3-abdfcd396ebd)

### 4.3 Final Configuration

Jenkins will show the URL to access your Jenkins instance. If installed locally, it will display:

```
http://localhost:8080
```

Click **Save and Finish**.

![Final Setup](https://github.com/user-attachments/assets/876125aa-fedb-4fac-b0cd-b3741d27dd57)

🎉 You’ve successfully installed Jenkins! You can now start using Jenkins for your CI/CD workflows.

![Jenkins Installation Complete](https://user-images.githubusercontent.com/43399466/215961440-3f13f82b-61a2-4117-88bc-0da265a67fa7.png)

---

## Step 5: Install Docker Pipeline Plugin in Jenkins 🐳

To use Docker in your Jenkins pipeline, you need to install the **Docker Pipeline** plugin.

### 5.1 Install Docker Pipeline Plugin

1. Log in to Jenkins.
2. Go to **Manage Jenkins** > **Manage Plugins**.
3. In the **Available** tab, search for **"Docker Pipeline"**.
4. Select the plugin and click the **Install** button.
5. After the installation, restart Jenkins.

![Docker Pipeline Plugin](https://github.com/user-attachments/assets/94ea92ac-aa33-4597-8e9a-1cf5d581b420)

Wait for Jenkins to restart after the plugin installation.

---

## Step 6: Docker Slave Configuration ⚙️

To run Docker containers on Jenkins, you need Docker installed on your machine.

### 6.1 Install Docker 🐋

Run the following commands to install Docker:

```bash
sudo apt update
sudo apt install docker.io
```

### 6.2 Grant Jenkins User Docker Permissions

You need to grant the **Jenkins** and **Ubuntu** users permission to run Docker commands.

```bash
sudo usermod -aG docker jenkins
sudo usermod -aG docker ubuntu
sudo systemctl restart docker
```

---

## Step 7: Restart Jenkins 🔄

After completing the Docker configuration, it is recommended to restart Jenkins to ensure all settings are properly applied.

```bash
sudo systemctl restart jenkins
```

---

## Conclusion 🎉

We have now successfully installed Jenkins and set it up to use Docker in our pipeline.🚀

---
