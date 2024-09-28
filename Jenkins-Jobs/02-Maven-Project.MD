### Fork the Repositories:

1. Go to the repository [DevopsProject](https://github.com/ooluwgb/DevopsProject.git).
   - Click the **Fork** button at the top right of the GitHub page to create a copy of the repository in your own GitHub account. This forked repository will now be under your username.
   - This is the repository where you will follow the instructions and document your progress.

2. Next, go to the repository [MAVENS-JENKINS-PROJECT](https://github.com/ooluwgb/MAVENS-JENKINS-PROJECT.git).
   - Click the **Fork** button at the top right to create a copy of this repository in your own GitHub account.
   - You will be using this forked repository for the Jenkins job configuration.

---

### **Steps to Configure the Jenkins Job:**

1. **Login to Jenkins console**  
   Ensure that your Jenkins server is running and accessible via your browser.

2. **Create a new Jenkins job:**  
   - In Jenkins, click on **New Item**.
   - Enter the job name as `My_First_Maven_Build`.
   - Select **Mavens project** and click **OK**.

3. **Configure the Jenkins Job:**  
   - Under **Source Code Management**, select **Git**.
   - In the **Repository URL** field, enter the URL of your forked repository for the MAVENS-JENKINS-PROJECT. This will be something like:  
     `https://github.com/<your-username>/MAVENS-JENKINS-PROJECT.git`  
   Replace `<your-username>` with your actual GitHub username.
   - In **Branches to build**, enter:  
     `*/master` or `*/main`, depending on your repository setup.

4. **Configure Build Settings:**  
   - Under the **Build**.
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

### **Important Notes:**

- Ensure that you follow the instructions in your own fork of the **DevopsProject** repository.
- Use your forked **MAVENS-JENKINS-PROJECT** repository for configuring and running the Jenkins job.
