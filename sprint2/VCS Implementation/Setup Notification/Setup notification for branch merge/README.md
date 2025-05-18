# Setup notification for Branch Merge


##  **Author Information**

| **Author**      | **Created on** | **Version** | **Last updated by** | **Internal Reviewer** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer** |
| --------------- | -------------- | ----------- | ------------------- | --------------------- | --------------- | --------------- | --------------- |
| Aditya Tripathi | 18-05-25       | 1           | Aditya Tripathi     | Priyansh              | Priyanka        | Rishabh         | Piyush          |




## Table of Contents 


1. [Introduction](#introduction)
2. [Pre-requisites](#pre-requisites)
3. [Workflow](#workflow)
4. [Steps to Set up Branch Merging Notification for Slack](#steps-to-set-up-branch-merging-notification-for-slack)
   * [1. Sign in to GitHub](#1-sign-in-to-github-go-to-githubhttpsgithubcom-and-log-in-to-your-account)
   * [2. Create a Repository](#2-create-a-repository-for-which-you-want-to-configure-notifications-for-branch-merge-notification)
   * [3. Open Repository Settings](#3-now-click-on-the-repository-you-created-and-navigate-to-the-settings-tab-at-the-top)
   * [4. Generate a Webhook URL for Slack](#4-generate-a-webhook-url-for-slack)
   * [5. Add Webhook to a Slack Channel](#5-add-webhook-for-a-channel)
   * [6. Create GitHub Actions Workflow](#6-create-github-actions-workflow-for-slack-notification-on-merge)
   * [7. Save Webhook URL in GitHub Secrets](#7-copy-the-webhook-url--save-it-in-github-secrets-as-slack_webhook_url)
   * [8. Commit and Push the Workflow File](#8-commit-and-push-the-workflow-file)
   * [9. Verify Slack Notification](#9-verify-slack-notification)
5. [Steps to Set up Branch Merging Notification for Email](#steps-to-set-up-branch-merging-notification-for-email)
6. [Conclusion](#conclusion)
7. [Contact Information](#contact-information)
8. [References](#references)




     
##  Introduction 
This document aims to set up automated notifications via email and Slack when a branch is merged into the main branch of a GitHub repository. It also defines how to restrict branch merges to specific authorized users, ensuring only designated contributors can merge branches into the main branch. Additionally, it outlines the process of configuring branch protection rules to enforce these restrictions.


##  Pre-requisites

| Requirement               | Description                                                  |
| ------------------------- | ------------------------------------------------------------ |
| GitHub Repository         | Hosted repo (public/private) on GitHub                       |
| Admin Access              | Required to configure branch protection rules                |
| Slack Workspace           | Access to the Slack workspace + incoming webhook integration |
| Email Addresses           | List of email recipients for merge alerts                    |

##  Workflow

![Screenshot 2025-05-15 091507](https://github.com/user-attachments/assets/aea8996e-cc24-4e4f-a51d-da2c166e0a91)




##  Steps to Set up Branch Merging Notification for Slack

### 1. Sign in to GitHub: Go to [GitHub](https://github.com) and log in to your account.

![image](https://github.com/user-attachments/assets/90deb434-b203-40a8-b1b0-9246c78751c1)


### 2. Create a repository for which you want to configure notifications for Branch Merge Notification

<img width="941" alt="image" src="https://github.com/user-attachments/assets/fc6628f0-6490-4be8-bcd4-468c17c87c36">


### 3. Now, click on the repository you created and navigate to the Settings tab at the top.

<img width="941" alt="image" src="https://github.com/user-attachments/assets/92f65faf-9314-4610-b4c7-dd7ec910d7a3">


### 4. Generate a Webhook Url for Slack

- **Go to** https://api.slack.com/apps

- **Create a new app → Enable Incoming Webhooks**

![Screenshot 2025-05-14 203053](https://github.com/user-attachments/assets/c432a989-382c-4a98-9a22-2afff7251c5f)


---

### 5. **Add webhook for a channel** 
![Screenshot 2025-05-14 211925](https://github.com/user-attachments/assets/06793758-22a9-4c83-b2c6-9dd707d8b1d8)



---

### 6. **Create GitHub Actions Workflow for Slack Notification on Merge**

   - Create the Workflow Directory and File in your repo  -->  **.github/workflows/notify-on-merge.yml**
 
   - **Add the Workflow Code**
     ![Screenshot 2025-05-14 212427](https://github.com/user-attachments/assets/c6d29c2c-4b48-479f-b5bb-e3c77e64cbab)


---

### 7. **Copy the Webhook URL → Save it in GitHub Secrets as SLACK_WEBHOOK_URL**
![Screenshot 2025-05-14 203500](https://github.com/user-attachments/assets/af1c9726-6696-4c2e-9701-fabc20111e95)


---

 ### 8. **Commit and Push the Workflow File**
**Once you add the workflow file, every time a commit is pushed to the specified repo (e.g., branch-merge-notification-demo), the GitHub Action will send an slack notification on your channel.**
 
 -  ![Screenshot 2025-05-15 084754](https://github.com/user-attachments/assets/b03078a0-4f2f-4e5c-8887-94ed133eeb8c)

 -  ![Screenshot 2025-05-15 084828](https://github.com/user-attachments/assets/0f4687c1-50bb-43c4-883f-20f99c4a4c15)


   



### 9. Verify Slack Notification


 
![Screenshot 2025-05-14 203250](https://github.com/user-attachments/assets/58de36e7-e0de-434d-a6d0-de5c7b91e1ee)


---

##  Steps to Set up Branch Merging Notification for Email

> **Follow Documentation**: [Email Setup](
https://github.com/snaatak-Downtime-Crew/Documentation/tree/SCRUMS-139-Vardaan/vcs_design%20%2B%20poc/implementation/notification/code-commit)



##  Conclusion

In this document, we implemented Slack and Email notifications for branches that merge into the main branch, with specific merging permissions restricted to authorized users. We encountered a limitation in enforcing branch protection rules on private repositories under the free GitHub plan, which requires an upgrade to a GitHub Team or Enterprise account. As a workaround, manual review processes and Git hooks were suggested to control merges. The final setup ensures notifications and proper authorization for merging branches into the main branch.



## Contact Information

| Name         | Email Address                                 |
|--------------|-----------------------------------------------|
| Aditya Tripathi | aditya.tripathi.snaatak@mygurukulam.co           |


 
#  References 
|links | Description |
|-------|------------|
|[Link](https://youtu.be/oMU9MUIXPyI?feature=shared)%7C**Rainbow talks** |
|[Link](https://www.youtube.com/watch?v=qToZN5S67AM)%7C **SDet Automation**|
|[Link](https://tinyurl.com/bdpf3ajc)%7C**GIT**%7C
