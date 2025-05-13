
---

# **Documentation and POC of Code Compilation in React CI Checks**

| **Author**  | **Created on** | **Version** | **Last updated by** | **Internal Reviewer** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer** |
| ----------- | -------------- | ----------- | ------------------- | ------------------ | --------------- | --------------- | --------------- |
| Aditya Tripathi | 12-05-25       |       1      | Aditya Tripathi        | Priyansh    | Priyanka           | Rishabh        | Piyush        |

![React Compilation Workflow](https://github.com/user-attachments/assets/sample-react-ci-diagram.png)

---

# Table of Contents

1. [**Introduction**](#introduction)
2. [**What is React Code Compilation?**](#what-is-react-code-compilation)
3. [**Why Compile React Code?**](#why-compile-react-code)
4. [**React Compilation Process**](#react-compilation-process)
5. [**Tools Used in React Compilation**](#tools-used-in-react-compilation)
6. [**Comparison with Other Frontend Frameworks**](#comparison-with-other-frontend-frameworks)
7. [**POC - React Code Compilation via CI**](#poc---react-code-compilation-via-ci)
8. [**Best Practices**](#best-practices)
9. [**Recommendations & Conclusion**](#recommendations--conclusion)
10. [**Contact Information**](#contact-information)
11. [**References**](#references)

---

# Introduction

React code must be transformed (compiled) from modern JavaScript (JSX, ES6+) into a format that browsers understand. This compilation step is crucial for production builds and is integrated into modern CI pipelines to ensure code correctness before deployment.

---

# What is React Code Compilation?

It’s the process of converting JSX and modern JavaScript (ES6+) into standard JavaScript. This is handled by tools like **Babel** and **Webpack** during CI checks to validate build integrity.

---

# Why Compile React Code?

| **Reason**             | **Description**                                                   |
| ---------------------- | ----------------------------------------------------------------- |
| **Browser Support**    | Converts modern JavaScript to be compatible with older browsers.  |
| **Code Optimization**  | Minifies, bundles, and removes unused code for faster load times. |
| **Build Verification** | Ensures no syntax or runtime issues before pushing to production. |

---

# React Compilation Process

| **Step**               | **Description**                                               |
| ---------------------- | ------------------------------------------------------------- |
| Transpile JSX          | JSX ➜ JS using Babel                                          |
| Bundle Modules         | Combine all files into one or more bundles using Webpack/Vite |
| Minification           | Remove comments, white space, and shorten code                |
| Build Validation in CI | CI runs `npm run build` to catch build errors early           |

---

# Tools Used in React Compilation

| **Tool**     | **Purpose**                           | **Why Used**                                             |
| ------------ | ------------------------------------- | -------------------------------------------------------- |
| **Babel**    | Transpile JSX and modern JS to ES5    | Ensures browser compatibility                            |
| **Webpack**  | Bundles JS, CSS, assets               | Optimizes delivery and performance                       |
| **Vite**     | Alternative to Webpack, faster builds | Fast dev server and modern tooling                       |
| **npm/yarn** | Package and build script runners      | Automates compilation with commands like `npm run build` |
| **ESLint**   | Code linting before build             | Avoids bad practices and ensures quality                 |
| **Jest**     | Unit testing (optional in CI)         | Tests run before build to verify correctness             |

---

# Comparison with Other Frontend Frameworks

| **Feature**        | **React**       | **Vue**        | **Angular** |
| ------------------ | --------------- | -------------- | ----------- |
| Compilation Tool   | Babel + Webpack | Vue CLI (Vite) | Angular CLI |
| CI Integration     | Easy            | Easy           | Complex     |
| Build Speed        | Fast (Vite)     | Very Fast      | Medium      |
| Tooling Complexity | Medium          | Low            | High        |

---

# POC - React Code Compilation via CI

### Objective: Compile and verify a React project via CI (GitHub Actions)

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

**Step 2**: Install dependencies

```bash
npm install
```

**Step 3**: Run build manually

```bash
npm run build
```

**Step 4**: Setup `.github/workflows/react-build.yml`

```yaml
name: React CI Build

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm install
      - run: npm run build
```

**Step 5**: Validate CI
Push changes → observe CI logs on GitHub Actions for build status.

---

# Best Practices

* Use **production mode** for final builds: `NODE_ENV=production`
* Add **build script** in `package.json`:

  ```json
  "scripts": {
    "build": "react-scripts build"
  }
  ```
* Use `.env` for env variables, not hardcoded values.
* Run **`npm audit`** and **`eslint`** as part of CI for security and code quality.
* Use **Vite** for faster dev builds if suitable.

---

# Recommendations & Conclusion

Integrating React code compilation into CI ensures early detection of issues, optimized bundles, and stable production deployments. Use modern tools like Babel, Webpack/Vite, and GitHub Actions for a streamlined, maintainable workflow.

---

# Contact Information

| **Name**    | **Email**                                                                         |
| ----------- | --------------------------------------------------------------------------------- |
| Aditya Tripathi | [aditya.tripathi.snaatak@mygrurukulam.co](aditya.tripathi.snaatak@mygrurukulam.co) |

---

# References

| **Link**                                                                                                 | **Description**     |
| -------------------------------------------------------------------------------------------------------- | ------------------- |
| [create react app.dev getting-started/](https://create-react-app.dev/docs/getting-started/) | Official CRA Docs   |
| [vitejs.dev guide/](https://vitejs.dev/guide/)                                                   | Vite Documentation  |
| [github actions](https://docs.github.com/en/actions)                                 | GitHub Actions Docs |
| [babeljs.io/](https://babeljs.io/)                                                               | Babel Compiler      |
| [webpack.js.org guide](https://webpack.js.org/)                                                       | Webpack Guide       |

---


