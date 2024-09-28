# DevOps Project Repository

Welcome to the **DevOps Project** repository! In this repository, you will find all the necessary instructions, configuration files, and steps required to deploy an application. This project will guide you through setting up and automating the deployment process in a step-by-step manner using Jenkins, Docker, and other DevOps tools.

## Repository Structure

### 1. **Application Code Repository**

The **application** you will be deploying is stored in a separate repository:

- [Application Repository](https://github.com/ooluwgb/APPLICATION.git)

You will be working with this application during the deployment process, but all instructions and configuration files for setting up the deployment are located in this repository.

### 2. **Instructions and Configuration Files Repository**

This repository contains all the instructions and configuration files needed to complete the project. You are currently in the **DevOps Project** repository:

- [DevOps Project Repository](https://github.com/ooluwgb/DevopsProject.git)

In this repository, you will find a directory called `Jenkins-job/` which contains numbered projects. These projects are to be completed **in the order of their numbering**.

## Getting Started

### Step 1: Clone Both Repositories

You need to clone both the **application repository** and this **DevOps Project repository**:

```bash
# Clone the Application Repository
git clone https://github.com/ooluwgb/APPLICATION.git

# Clone the DevOps Project Repository
git clone https://github.com/ooluwgb/DevopsProject.git
```

### Step 2: Remove Existing Remote Origins and Set Your Own Remote

After cloning the repositories, you will need to remove the existing remote origins, generate your own remote repository on GitHub or another Git provider, and then add that remote to the cloned repositories.

#### Remove the Existing Remote Origin

Navigate to the directory where the repository is cloned and run the following commands to remove the existing remote origin:

```bash
# Navigate to the Application repository
cd APPLICATION/
# Remove the current remote origin
git remote remove origin

# Navigate to the DevOps Project repository
cd ../DevopsProject/
# Remove the current remote origin
git remote remove origin
```

#### Create Your Own Repository

Go to GitHub (or your preferred Git hosting provider) and create two new repositories (without readme.md files), one for the application code and one for the DevOps project.

#### Add Your New Remote Origin

After creating the repositories, you need to add them as the new remote origin for your cloned repositories:

```bash
# Add your personal remote origin to the Application repository
cd ../APPLICATION/
git remote add origin https://github.com/<your-username>/<your-application-repo>.git

# Add your personal remote origin to the DevOps Project repository
cd ../DevopsProject/
git remote add origin https://github.com/<your-username>/<your-devops-repo>.git
```

### Step 3: Push the Code to Your Repository

Once you have added your personal remote origin, you can push the code to your newly created repositories:

```bash
# Push the Application repository
cd APPLICATION/
git push -u origin main

# Push the DevOps Project repository
cd ../DevopsProject/
git push -u origin main
```

### Step 4: Follow the Instructions in This Repository

In the **DevOps Project** repository, you will find detailed steps and configurations for each project. Navigate to the `Jenkins-job/` directory and start working on the projects listed there.

Each project is numbered, and you should **follow the order** in which the projects are numbered, starting from **Project 1**, then moving to **Project 2**, and so on.

```bash
# Example:
cd Jenkins-job/
```

### Step 5: Deployment of the Application

The **application code** you'll be deploying is located in the **Application Repository** you cloned earlier. During the projects, you will be configuring the deployment pipeline to automate the deployment of this application.

### Key Points:

- Always refer to the **DevOps Project repository** for configuration files, instructions, and any scripts you need for your project.
- Work through the projects in the `Jenkins-job/` directory in the **exact order** they are numbered to ensure you follow the workflow correctly.
- The **Application repository** only contains the code for the application, while this repository holds all the instructions for deployment.

## Additional Notes:

- Make sure your Jenkins server is properly configured before starting the projects.
- Ensure all dependencies are installed and your environment is set up as outlined in the configuration files.
