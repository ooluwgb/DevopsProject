### **Steps to Reconfigure the Jenkins Job for Git SCM Trigger:**

1. **Open the Existing Jenkins Job**  
   - In Jenkins, navigate to your job (`My_First_Maven_Build`) and click on **Configure** to modify the job settings.

2. **Enable Git SCM Polling for Automatic Build Trigger**  
   - Scroll down to the **Build Triggers** section.
   - Check the option for **GitHub hook trigger for GITScm polling** to enable Jenkins to automatically poll Git for new commits.

3. **Configure Webhook in Your GitHub Repository**  
   - Go to your forked repository on GitHub (e.g., `https://github.com/<your-username>/<your-application-repo>.git`).
   - Click on the **Settings** tab of your repository.
   - In the left sidebar, click on **Webhooks**, then click on **Add webhook**.
   - In the **Payload URL** field, enter your Jenkins server URL followed by `/github-webhook/`, which should look something like this:  
     `http://<your-jenkins-server>/github-webhook/`
   - Set the **Content type** to `application/json`.
   - Choose **Just the push event** under "Which events would you like to trigger this webhook?".
   - Click **Add webhook**.

4. **Save the Jenkins Job Configuration**  
   - Once you have set the **GitHub hook trigger for GITScm polling**, click **Save** in Jenkins to save the updated job configuration.

5. **Test the Automatic Build Trigger**  
   - Push a new commit to your GitHub repository.
   - Jenkins should automatically trigger a new build after detecting the new push.

---

### **Important Notes:**

- Ensure that your Jenkins server is properly configured to receive webhooks from GitHub.
- Verify that the webhook status on GitHub is successful and triggering builds as expected.
