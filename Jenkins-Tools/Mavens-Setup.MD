# Setting Up Maven in Jenkins

Follow these step-by-step instructions to set up Maven in Jenkins by installing the Maven tool and the Maven Plugin.

---

## **Step 1: Install Maven Tool**

1. Go to **Manage Jenkins** from the Jenkins dashboard.  
2. Select **Global Tool Configuration**.
3. Scroll down to the **Maven** section and click on **Add Maven**.
4. Provide a name for the Maven installation, such as `Maven`.
5. Check the **Install automatically** box.
6. Set the version to the latest available version, for example, `3.8.6`.
7. Click **Apply** and then **Save** to save the Maven tool configuration.

---

## **Step 2: Install Maven Plugin**

1. From the Jenkins dashboard, go to **Manage Jenkins** again.
2. Select **Manage Plugins**.
3. In the **Available** tab, search for `Maven` in the search bar.
4. Look for the **Maven Integration** plugin and select it.
5. Click on the **Install without restart** button.
6. Wait for the installation to complete.
7. Once installed, a message will appear prompting you to restart Jenkins.
8. Click on the **Restart Jenkins** button to apply the changes.

---

Once these steps are complete, Maven will be fully set up and ready to use in Jenkins for your projects.

