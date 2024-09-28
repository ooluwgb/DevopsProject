# Deploy on Docker Host Server using Jenkins
# *Jenkins Job name:* `Deploy_on_Docker_Host`

### Pre-requisites

1. **Jenkins Server**: Ensure that Jenkins is installed and running.
2. **Docker-host Server**: Ensure that Docker is installed and running on the remote host.

### Integration between Docker-host and Jenkins

1. **Install "Publish Over SSH" Plugin**:
   - Navigate to `Manage Jenkins` > `Manage Plugins` > `Available` and search for **Publish Over SSH**. Install the plugin to enable SSH connections from Jenkins to the Docker host.

2. **Enable Connection Between Docker-host and Jenkins**:
   - Set up the SSH connection to allow Jenkins to send artifacts to the Docker-host:
     - Go to `Manage Jenkins` > `Configure System` > **Publish Over SSH** > **SSH Servers**.
     - Set up the SSH server:
       - Name: `docker-host`
       - Hostname: `<ServerIP>`
       - Username: `dockeradmin`
       - In **Advanced**, choose "Use password authentication, or use a different key".
       - Enter the password: `*******`.

### Steps to Create "Deploy_on_Docker_Host" Jenkins Job

1. **Create a New Job**:
   - From the Jenkins home page, select **New Item**.
   - Enter the job name: `Deploy_on_Docker_Host`.
   - Select **Copy from**: `Deploy_on_Tomcat_Server` (or another similar job).
   - Click **OK**.

2. **Configure the Jenkins Job**:
   - **Source Code Management**:
     - Repository: Use your forked **application repository** for the deployment.
     - Branches to build: `*/main` (or `*/master` based on your setup).

   - **Poll SCM**:
     - Set the poll schedule to trigger builds based on SCM changes:  
       - `* * * *` (every minute for testing purposes; adjust as needed).

   - **Build**:
     - Root POM: `pom.xml`.
     - Goals and options: `clean install package`.

3. **Post-build Actions**:
   - **Send build artifacts over SSH**:
     - Under **SSH Publishers**:
       - SSH Server Name: `docker-host`.
       - **Transfers**:
         - Source files: `webapp/target/*.war`.
         - Remove prefix: `webapp/target`.
         - Remote directory: `/home/dockeradmin/` (or any other relevant directory).

4. **Deploy Using Docker**:
   - After transferring the `.war` file to the Docker-host, you can configure the Docker host to automatically run a container from the artifact using a deployment script:
     - For example, use the following as an **Exec command** in Jenkins:
       ```sh
       docker stop simple-devops-container || true
       docker rm simple-devops-container || true
       docker run -d --name simple-devops-container -p 8080:8080 -v /home/dockeradmin/*.war:/usr/local/tomcat/webapps/ROOT.war tomcat:10.1.30
       ```

### Save and Run the Job

- After configuring the job, click **Save**.
- Click **Build Now** to trigger the job.
- Jenkins will build the project, transfer the WAR file to the Docker-host server, and deploy it using Docker.

---

### Important Notes:

- Ensure your Docker-host server is properly configured and reachable from Jenkins.
- Use your own repository URLs and credentials where needed.
- Make sure to configure the Docker container to suit your deployment needs, including ports and volume mappings.
