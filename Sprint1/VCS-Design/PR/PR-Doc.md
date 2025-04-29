![image](https://github.com/user-attachments/assets/8619a717-9098-4077-9d96-93f4469e04b2)

| Author          | Created on | Version   | Last updated by |  Internal Reviewer | L0  | L1  | L2  |
|-----------------|------------|-----------|------------------|--------------------|-----|-----|-----|
| Aditya Tripathi | 28-04-25   | version 1 | N/A              | Priyanshu        | Khushi | Rishabh | Piyush |

## Table of Content
1. [Introduction](#introduction)
2. [Feature](#features)
3. [Why Pull Request](#why-pull-request)
4. [Steps to Create a Pull Request](#steps-to-create-a-pull-request)
5. [PR Rules](#pr-rules)
6. [Advantages of Pull Requests](#advantages-of-pull-requests)
7. [Disadvantages of Pull Requests](#disadvantages-of-pull-requests)
8. [Best Practices](#best-practices)
9. [Conclusion](#conclusion)
10. [Contact Information](#contact-information)
11. [References](#references)



### Introduction

A **Pull Request (PR)** is like asking permission to add your changes to a project on GitHub. When you make changes to a project, you can send a PR to the project’s owners or team, who can then review, discuss, and approve your changes. It helps people work together and improve the project.




### Features

| Feature                  | Description                                                                                      |
|--------------------------|--------------------------------------------------------------------------------------------------|
| **Code Review**           | Team members check the code changes before adding them to the project.                           |
| **Discussion & Feedback** | Developers talk about the changes and give suggestions.                                          |
| **Continuous Integration**| Automatically test the changes to make sure they don’t break anything in the project.            |
| **Merge Control**         | Maintainers decide when and how to add the changes to the main project.                          ||


### Why Pull Request

| Reason              | Description                                                                                  |
|---------------------|----------------------------------------------------------------------------------------------|
| **Collaboration**    | Helps multiple developers work together on the same project.                                |
| **Quality Assurance**| Makes sure changes are checked and meet the project’s standards.                             |
| **Transparency**     | Keeps track of changes and why they were made.                                               |
| **Feedback Loop**    | Lets others give feedback to improve the code.                                               |
| **Version Control**  | Helps control when changes are added to the main project.                                    |


# Steps to Create a Pull Request
**Please refer to the reference link for the installation and flowchart**
| Link         | Description         |
|--------------|------------------------|
| [PR POC](LINK)          | POC  |
#

# PR Rules

When creating Pull Requests, please adhere to the following rules to ensure clarity and efficiency:

*   **Keep it Small:** Each PR should address a single concern or feature. Avoid large, complex PRs.
*   **Clear Title and Description:** The title should summarize the change concisely. The description should explain the *what* and *why* of the change, linking to relevant issues if applicable (e.g., `Fixes #123`).
*   **Self-Review First:** Review your own code for potential issues, typos, or debugging code before submitting.
*   **Ensure Tests Pass:** Run all relevant tests locally and ensure they pass before submitting the PR. CI checks must pass before merging.
*   **Request Appropriate Reviewers:** Tag the relevant team members or code owners who should review the PR.
*   **Respond to Feedback:** Address comments and feedback from reviewers promptly. Engage in constructive discussions.
*   **Update Your Branch:** Keep your feature branch updated with the latest changes from the main branch to minimize merge conflicts.

# Advantages of Pull Requests

| **Advantage**                  | **Description**                                                                                   |
|--------------------------------|---------------------------------------------------------------------------------------------------|
| **Increased Collaboration**     | Facilitates discussions and teamwork by allowing developers to collaborate on code changes.       |
| **Reduced Errors**              | Enables multiple developers to review and test code, identifying bugs and security issues early.  |
| **Learning Opportunities**      | Provides a platform for developers to learn new skills and stay updated by reviewing others' code.|
| **Transparency**                | Offers visibility into code changes and their purpose, improving accountability.                 |
| **Better Onboarding**           | Helps new developers understand the codebase and standards effectively through code reviews.      |
| **Centralized Progress Tracking**| Acts as a hub for managers to monitor changes, provide feedback, and track development progress.  |

# Disadvantages of Pull Requests

| **Disadvantage**               | **Description**                                                                                   |
|--------------------------------|---------------------------------------------------------------------------------------------------|
| **Merge Conflicts**            | Increased chances of merge conflicts due to developing code in branches, leading to more time spent resolving divergent code. |
| **Testing and Reviewing**      | Difficulty in testing and reviewing multiple dependent pull requests, with no integrated environment to validate changes together. |
| **Superficial Reviews**        | Reviews can be shallow, focusing on minor issues (like naming or indentation) instead of deeper code quality concerns. |
| **Slow Feedback**              | Delays in receiving feedback, which can slow down the development process.                       |
| **Low-Quality Reviews**        | Reviews can become superficial with disproportionate feedback on small versus large code changes. |
| **Discouraged Refactoring**    | Engineers may avoid refactoring to keep pull requests smaller, leading to lower code quality.     |


# Best Practices

## Pull Request Best Practices

Here are some key things to keep in mind when creating pull requests:

| **Best Practice** | **Description** | **In Practice** |
| :---------------------------- | :------------------------------------------------------- | :------------------------------------------------------------------------------ |
| **Small & Focused Changes** | Make each pull request about one specific fix or feature. | Break big tasks into smaller, manageable chunks. Each PR should do one thing. |
| **Clear Explanations** | Tell people what your changes do and why.                 | Write a good title and description in your pull request. Link to related issues. |
| **Get Your Code Checked** | Ask teammates to review your code before merging.        | Tag specific people to review your pull request and give feedback.           |
| **Test Before You Submit** | Make sure your code works before submitting it.          | Run tests on your own computer first. Make sure automated checks pass.        |

 ### Conclusion
Pull requests are a powerful tool that can significantly enhance the quality, efficiency, and collaboration of software development teams. By embracing PRs as a core part of their workflow, teams can deliver higher-quality software, faster.

### Contact Information

| Name         | Email address          |
|--------------|------------------------|
| Aditya Tripathi          | aditya.tripathi.snaatak@mygurukulam.co     |


### References
| Links                                             | Descriptions                                                    |
|---------------------------------------------------|-----------------------------------------------------------------|
|[Rules to PR](https://medium.com/google-developer-experts/how-to-pull-request-d75ac81449a5)|Pull Request rules that one should follow before creating a PR |
|[How to create a PR](https://nemuelw.medium.com/how-to-create-a-pull-request-bed0566d8733)| Pull Request steps to follow while creating one|
