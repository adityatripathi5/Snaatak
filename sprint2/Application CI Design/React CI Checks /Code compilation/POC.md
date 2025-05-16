![image](https://github.com/user-attachments/assets/a7569945-b2bf-424a-89e3-3b3f99034cf0)


# POC - React Code Compilation via CI

---

## Table of Contents

1. [Objective](#objective)
2. [Pre-requisites](#pre-requisites)
3. [Step-by-Step Guide](#step-by-step-guide)
4. [Contact Information](#contact-information)
5. [References](#references)

---

### Objective: Compile and verify a React project

The objective of this POC is to demonstrate how to compile a simple React application into a production-ready static build. 

## Pre-requisites:

| **Specification** | **Details**                         |
| ----------------- | ----------------------------------- |
| OS                | Ubuntu-based runner (CI)            |
| Node.js Version   | >= 16                               |
| React App         | Create using `npx create-react-app` |
| CI Tool           | GitHub Actions                      |

### Step-by-Step Guide:

**Step 1**: Clone the React app

```bash
git clone https://github.com/your-org/react-ci-demo.git
cd react-ci-demo
```
![Screenshot 2025-05-16 145357](https://github.com/user-attachments/assets/d820d2be-0e7b-4230-8573-a0bf7ad9ea9c)


**Step 2**: Install dependencies

```bash
npm install
```
![Screenshot 2025-05-16 145456](https://github.com/user-attachments/assets/92e04e9a-93b8-4110-8a10-d6d7439a7d4f)


**Step 3**: Run build manually

```bash
npm run build
```

![Screenshot 2025-05-16 145846](https://github.com/user-attachments/assets/61fb44d5-11fb-4ba4-96f7-b1dc19325015)
![Screenshot 2025-05-16 145953](https://github.com/user-attachments/assets/2b772b88-b5e7-4dee-bd53-23b4be8fcbc7)

# Contact Information

| **Name**    | **Email**                                                                         |
| ----------- | --------------------------------------------------------------------------------- |
| Aditya Tripathi | [aditya.tripathi.snaatak@mygrurukulam.co](aditya.tripathi.snaatak@mygrurukulam.co) |

---

# References

| **Link**                                                                                                 | **Description**     |
| -------------------------------------------------------------------------------------------------------- | ------------------- |
| [create react app.dev getting-started](https://create-react-app.dev/docs/getting-started/) | Official CRA Docs   |
| [vitejs.dev guide](https://vitejs.dev/guide/)                                                   | Vite Documentation  |
| [github actions](https://docs.github.com/en/actions)                                 | GitHub Actions Docs |
| [babeljs.io](https://babeljs.io/)                                                               | Babel Compiler      |
| [webpack.js.org guide](https://webpack.js.org/)                                                       | Webpack Guide       |
