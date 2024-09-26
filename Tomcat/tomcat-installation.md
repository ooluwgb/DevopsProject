# Tomcat Installation on Ubuntu 24.04 EC2 Instance

## Pre-requisites

- AWS EC2 instance with **Java 11** installed.
- Make sure your security group allows inbound access on **port 8080** for Tomcat and **port 22** for SSH access.

---

## Step-by-Step Installation Guide

### 1. **Launch an EC2 Instance**
   - Launch an **Ubuntu 24.04** EC2 instance from the AWS Management Console.
   - Choose an appropriate instance type (e.g., t2.micro or t3.small) and assign a security group with access on port **8080 (for Tomcat)** and **22 (for SSH)**.
   - Note down the public IP address of the instance.

### 2. **Connect to the EC2 Instance**
   - Use SSH to connect to the EC2 instance:

     ```bash
     ssh -i /path/to/your-key.pem ubuntu@<Public_IP>
     ```

### 3. **Update and Upgrade the Server**
   - Update the package manager and upgrade installed packages:

     ```bash
     sudo apt update
     sudo apt upgrade -y
     ```

### 4. **Install Java 11**
   - Verify if **Java 11** is already installed by running:

     ```bash
     java -version
     ```

   - If Java 11 is not installed, install it by running:

     ```bash
     sudo apt install openjdk-11-jdk -y
     ```

   - Set **Java 11** as the default Java version:

     ```bash
     sudo update-alternatives --config java
     ```

### 5. **Install the Latest Apache Tomcat**

   - Navigate to the `/opt` directory, which is commonly used for storing third-party software:

     ```bash
     cd /opt
     ```

   - Create a directory for Tomcat:

     ```bash
     sudo mkdir tomcat
     cd tomcat
     ```

   - Download the latest stable version of **Tomcat 10.1.30** (you can find the latest version [here](https://tomcat.apache.org/download-10.cgi)):

     ```bash
     sudo wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.30/bin/apache-tomcat-10.1.30.tar.gz
     ```

   - Extract the downloaded tarball:

     ```bash
     sudo tar -xvzf apache-tomcat-10.1.30.tar.gz
     ```

   - Remove the tarball to save space:

     ```bash
     sudo rm apache-tomcat-10.1.30.tar.gz
     ```

   - Navigate to the **Tomcat bin** directory:

     ```bash
     cd apache-tomcat-10.1.30/bin
     ```

   - Make the startup and shutdown scripts executable:

     ```bash
     sudo chmod +x startup.sh
     sudo chmod +x shutdown.sh
     ```

### 6. **Create Symlinks for Tomcat Start/Stop**

   - Create symbolic links for easier management of the Tomcat service:

     ```bash
     sudo ln -s /opt/tomcat/apache-tomcat-10.1.30/bin/startup.sh /usr/local/bin/tomcatup
     sudo ln -s /opt/tomcat/apache-tomcat-10.1.30/bin/shutdown.sh /usr/local/bin/tomcatdown
     ```

### 7. **Start Tomcat**
   - Start the Tomcat server:

     ```bash
     tomcatup
     ```

   - You can verify Tomcat is running by checking the process:

     ```bash
     ps -ef | grep tomcat
     ```

### 8. **Configure Tomcat for Management Access**

   - Edit the `tomcat-users.xml` file to enable access to the **Manager** and **Admin** apps:

     ```bash
     sudo nano /opt/tomcat/apache-tomcat-10.1.30/conf/tomcat-users.xml
     ```

   - Add the following users and roles at the end of the file:

     ```xml
     <role rolename="manager-gui"/>
     <role rolename="admin-gui"/>
     <user username="admin" password="admin" roles="manager-gui,admin-gui"/>
     <user username="deployer" password="deployer" roles="manager-script"/>
     <user username="tomcat" password="s3cret" roles="manager-gui"/>
     ```

   - Save and exit the file (`Ctrl+O`, then `Ctrl+X`).

### 9. **Adjust Context Security Settings**

   - Tomcat’s **Manager** and **Host Manager** applications require some default settings to be disabled for security. Modify the `context.xml` files:

     ```bash
     sudo nano /opt/tomcat/apache-tomcat-10.1.30/webapps/manager/META-INF/context.xml
     sudo nano /opt/tomcat/apache-tomcat-10.1.30/webapps/host-manager/META-INF/context.xml
     ```

   - Comment out the following lines in both files:

     ```xml
     <!-- <Valve className="org.apache.catalina.valves.RemoteAddrValve" ... /> -->
     ```

   - Save and exit the file after commenting out the line.

### 10. **Restart Tomcat**
   - Restart the Tomcat service for changes to take effect:

     ```bash
     tomcatdown
     tomcatup
     ```

### 11. **Access Tomcat**
   - Access the Tomcat server from your browser by navigating to the **public IP** of your EC2 instance on **port 8080**:

     ```bash
     http://<Public_IP>:8080
     ```

   - You should see the Tomcat welcome page. To access the **Manager** or **Admin** web interfaces, use the credentials you added to the `tomcat-users.xml` file.

     - Manager app: `http://<Public_IP>:8080/manager`
     - Admin app: `http://<Public_IP>:8080/host-manager`

### 12. **Verify Installation**
   - Verify that Tomcat is properly installed by accessing the **Manager App** and ensuring that you can deploy applications or manage the server from the GUI.

---

### Notes:

- Ensure that **port 8080** is open in your EC2 security group, or you won’t be able to access the Tomcat server from your browser.
- Consider enabling firewall rules for added security to restrict access to the management interfaces.
