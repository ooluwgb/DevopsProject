# Jenkins-job Instructions

Welcome to the **Jenkins-job** directory! Here, you will find the step-by-step projects that will guide you through the deployment of the application.

## Important Notes:

1. **Follow the Numbering**: The projects are numbered for a reason. You should follow the order of the numbering starting from **001-**, then moving to **002-**, and so on, as each project builds upon the previous one.

2. **Maven Setup**: This project requires the setup of Maven. Please refer to the **Jenkins-Tool/001-Mavens-Setup.MD** directory in the instructional repository for setting up Maven before proceeding with any Jenkins jobs.

3. **Repository References**: These repositories are not under your registry by default. Every time you need to set up a repository URL or push code, ensure that you are referencing **your personal repository** URLs and not the default ones listed in the instructions.

4. **Use Your Own Repository**: Make sure to use your own application repository when setting up the Jenkins jobs. Your personal repository URLs should replace any default URLs provided in the instructions.

Make sure to complete each project fully before moving on to the next one.

---

### **Steps to Configure the Jenkins Job:**

1. **Login to Jenkins console**  
   Ensure that your Jenkins server is running and accessible via your browser.

2. **Create a new Jenkins job:**  
   - In Jenkins, click on **New Item**.
   - Enter the job name as `My_First_Maven_Build`.
   - Select **Maven project** and click **OK**.

3. **Configure the Jenkins Job:**  
   - Under **Source Code Management**, select **Git**.
   - In the **Repository URL** field, enter the URL of your cloned repository for the application. This will be something like:  
     `https://github.com/<your-username>/<your-application-repo>.git`  
   Replace `<your-username>` with your actual GitHub username.
   - In **Branches to build**, enter:  
     `*/master` or `*/main`, depending on your repository setup.

4. **Configure Build Settings:**  
   - Under the **Build** section.
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
- Use your forked **Application Repository** for configuring and running the Jenkins job.
