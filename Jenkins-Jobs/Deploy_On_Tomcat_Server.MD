# Deploy on a Tomcat Server
# *Jenkins Job name:* `Deploy_on_Tomcat_Server`

### Pre-requisites

1. **Jenkins Server**: Ensure that Jenkins is installed and running.
2. **Tomcat Server**: You should have a Tomcat 10.1.30 server installed on an Ubuntu 24.04 EC2 instance as outlined in the [Tomcat Setup Guide](#).

### Adding Deployment Steps

1. **Install 'Deploy to Container' Plugin**  
   This plugin is required to deploy the build artifacts to the Tomcat server.

   - To install the plugin without restarting Jenkins:
     - Navigate to `Manage Jenkins` > `Manage Plugins` > `Available` > Search for `Deploy to Container Plugin` and install it.

2. **Jenkins Should Access the Tomcat Server**  
   Jenkins needs access to the Tomcat server to deploy build artifacts. You will set up credentials on Jenkins to enable this process.

   - **Set Up Credentials:**
     - Go to `Credentials` > `Jenkins` > `Global credentials (unrestricted)` > `Add Credentials`.
     - Use the following details:
       - **Username**: `deployer`
       - **Password**: `deployer` (or the password you set in `tomcat-users.xml`).
       - **ID**: `deployer`
       - **Description**: `User to deploy on Tomcat VM`

### Steps to Create the "Deploy_on_Tomcat_Server" Jenkins Job

1. **From the Jenkins Home Page:**
   - Click `New Item`.
   - Enter an item name: `Deploy_on_Tomcat_Server`.
   - Under "Copy from", select: `My_First_Maven_Build` (or the appropriate base job).
   - Click `OK`.

2. **Source Code Management**:
   - Repository: `https://github.com/yankils/hello-world.git`
   - Branches to build: `*/master`.

3. **Poll SCM**:
   - Set the poll schedule to trigger builds periodically:  
     - `* * * *` (every minute for testing purposes; adjust as needed for production).

4. **Build**:
   - Root POM: `pom.xml`.
   - Goals and options: `clean install package`.

5. **Post-build Actions**:
   - Select `Deploy war/ear to a container`.
   - Set the following:
     - **WAR/EAR files**: `**/*.war`.
     - **Containers**: Select `Tomcat 8.x` (compatible with Tomcat 10.1.30).
     - **Credentials**: Choose the `deployer` credentials you created earlier.
     - **Tomcat URL**: `http://<PUBLIC_IP>:8080`.

### Save and Run the Job

- Once the job is configured, save it.
- Click `Build Now` to trigger the job.
- Jenkins will deploy the WAR file to your Tomcat server running on the public IP of your EC2 instance.
