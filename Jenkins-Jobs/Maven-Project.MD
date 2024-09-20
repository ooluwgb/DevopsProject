# Create a First Maven Jenkins Job to Build Hello World Project  
**Jenkins Job Name:** `My_First_Maven_Build`

We have learned how to work with Git and Jenkins independently. Now, it's time to integrate them together for a simple DevOps project. Follow the steps below to complete this task. You will enjoy the process!

---

### **Pre-requisites:**

- A running Jenkins server. Make sure Jenkins is updated to the latest version.
- Install the latest version of Maven on your Jenkins server (if it's not already installed). You can verify this under `Manage Jenkins` > `Global Tool Configuration` > `Maven`.
- If not installed follow the Instruction to install MAVENS in the Jenkins-Tool directory in this repository.

---

### **Fork the Repository:**

1. Go to the repository [DevopsProject](https://github.com/ooluwgb/DevopsProject.git).
2. Click the "Fork" button at the top right of the GitHub page to create a copy of the repository in your own GitHub account. This forked repository will now be under your username.

---

### **Steps to Create "My_First_Maven_Build" Jenkins Job:**

1. **Login to Jenkins console**  
   Ensure that your Jenkins server is running and accessible via your browser.

2. **Create a new Jenkins job:**  
   - In Jenkins, click on **New Item**.
   - Enter the job name as `My_First_Maven_Build`.
   - Select **Freestyle project** and click **OK**.

3. **Configure the Jenkins Job:**  
   - Under **Source Code Management**, select **Git**.
   - In the **Repository URL** field, enter the URL of your forked repository. This will be something like:  
     `https://github.com/<your-username>/DevopsProject.git`  
   Replace `<your-username>` with your actual GitHub username.
   - In **Branches to build**, enter:  
     `*/master` or `*/main`, depending on your repository setup.

4. **Configure Build Settings:**  
   - Under the **Build** section, select **Invoke top-level Maven targets**.
   - In the **Root POM**, enter: `pom.xml`.
   - In the **Goals and options**, enter: `clean install package`.

5. **Save the Jenkins Job**  
   Once everything is configured, click on **Save** to finish creating the job.

6. **Build the Job:**  
   - On the Jenkins dashboard, click on your job name (`My_First_Maven_Build`).
   - Click on **Build Now** to trigger a build.
   - After the build completes, check the **Console Output** to verify that it runs successfully.

---

### **Testing:**

- After the build completes, you should see a **Success** status on the Jenkins dashboard.
- Verify that the generated artifacts (e.g., `.jar` or `.war` files) are present by checking the workspace or any configured post-build actions.

---

Make sure to review all your configurations and ensure Jenkins and Maven are using the latest versions to avoid compatibility issues. If necessary, update Jenkins plugins and tools through the **Manage Jenkins** section.

--- 
