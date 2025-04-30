![image](https://github.com/user-attachments/assets/7a3460d3-281d-475b-b65b-21670301cca8)

| Author          | Created on | Version   | Last updated by |  Internal Reviewer | L0  | L1  | L2  |
|-----------------|------------|-----------|------------------|--------------------|-----|-----|-----|
| Aditya Tripathi | 28-04-25   | version 1 | N/A              | Priyanshu        | Khushi | Rishabh | Piyush |

This repository contains the documentation for **Monorepo** strategy for version control.
---

## Table of Contents

*   [Introduction](#introduction)
*   [Why](#why)
*   [Monorepo Key Features](#monorepo-key-features)
*   [Advantages of Monorepo](#advantages-of-monorepo)
*   [Challenges / Disadvantages of Monorepo](#challenges--disadvantages-of-monorepo)
*   [Typical Monorepo Workflow](#typical-monorepo-workflow)
*   [Best Practices for Monorepo Management](#best-practices-for-monorepo-management)
*   [Conclusion](#conclusion)
*   [Contact Information](#contact-information)
*   [References](#references)

---

## Introduction

A Monorepo ("mono" meaning single, "repo" meaning repository) is a version control strategy where source code for many distinct projects or components is stored in the same repository. This contrasts with the Multi-repo (often associated with microservices) approach where each project/service/component has its own dedicated repository. This documnent evaluates the Monorepo strategy's suitability for our specific context.

![image](https://github.com/user-attachments/assets/248febb5-e100-4c83-a2f0-11348a32142a)


## Why

| Evaluation Focus                                 | Description                                                                                   |
|--------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Developer Experience (DX)                        | Improve ease of development, onboarding, and day-to-day workflows.                            |
| Code Sharing and Reuse                           | Promote reuse of components/libraries across projects.                                        |
| Dependency Management Consistency                | Ensure consistency in how dependencies are managed across teams and services.                 |
| Build and Deployment Pipeline Efficiency         | Streamline and standardize CI/CD processes.                                                   |
| Cross-team Collaboration and Visibility          | Increase code discoverability and enable better collaboration between teams.                  |

## Monorepo Key Features

| Feature                            | Description                                                                                   |
|------------------------------------|-----------------------------------------------------------------------------------------------|
| Single Source of Truth             | All code resides in one repository, simplifying navigation and discovery.                     |
| Atomic Commits                     | Enables cross-project changes to be committed together as a single unit.                      |
| Simplified Dependency Management   | Easier handling of internal dependencies using workspace tools or direct linking.             |
| Unified Tooling                    | Consistent linting, testing, building, and deployment processes across all projects.          |
| Code Visibility & Discovery        | Developers can search and browse all projects easily within a centralized repo.               |
| Large-Scale Refactoring            | Facilitates updating shared code and applying changes across all consumers in one go.         |

## Advantages of Monorepo

| Advantage                  | Description                                                                                  |
|---------------------------|----------------------------------------------------------------------------------------------|
| Simplified Code Sharing   | Reduced friction in sharing code between projects and teams.                                |
| Improved Collaboration    | Easier for developers to contribute to different parts of the system.                       |
| Consistency               | Easier enforcement of code standards, linting rules, and unified build processes.           |
| Atomic Refactoring        | Ability to update APIs and their consumers in a single, system-wide change.                 |


## Challenges / Disadvantages of Monorepo

| Challenge                  | Description                                                                                          |
|---------------------------|------------------------------------------------------------------------------------------------------|
| Tooling Complexity         | Requires investment in and maintenance of specialized tools to manage the scale of a monorepo.      |
| Build/Test Performance     | Without optimizations like caching and affected-logic detection, performance can degrade quickly.   |
| Scalability Concerns       | As the repo grows, Git operations (e.g., clone, pull) can become slower and more resource-intensive. |
| CI/CD Complexity           | Pipelines must be intelligently scoped to avoid unnecessary builds and deployments.                 |

## Typical Monorepo Workflow

| Step         | Action                                                                                             |
|--------------|----------------------------------------------------------------------------------------------------|
| 1. Clone     | Developers clone the single repository.                                                            |
| 2. Branch    | Create a feature branch from the main branch (e.g., `main` or `master`).                           |
| 3. Develop   | Make changes across one or more projects/packages.                                                 |
| 4. Build/Test| Run affected builds/tests using monorepo tooling (e.g., `nx affected:build`).                      |
| 5. Commit    | Commit changes, ideally using conventional commit messages.                                        |
| 6. Push & PR | Push your branch and open a Pull Request. CI triggers on affected projects.                        |
| 7. Review    | Relevant code owners review changes across affected projects.                                      |
| 8. Merge     | Merge the PR into the main branch once approved and passing CI.                                    |
| 9. Deploy    | CI/CD deploys only the changed apps/services.                                                      |

## Best Practices for Monorepo Management

| Best Practice                | Description                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------|
| Adopt Specialized Tooling   | Use tools like Nx, Turborepo, Bazel, or Lerna for advanced task orchestration and caching.    |
| Optimize CI/CD              | Configure pipelines to run only on affected paths using monorepo-aware tooling.              |
| Implement Build Caching     | Enable local and remote caching to drastically reduce build and test times.                  |
| Enforce Code Ownership      | Use `CODEOWNERS` to assign responsibility and streamline pull request reviews.               |

## Conclusion

This POC confirms that a Monorepo can significantly enhance code sharing, consistency, and cross-team collaboration.  
However, it also introduces challenges around tooling complexity and build performance that must be carefully managed.  
We recommend proceeding with a pilot implementation using specialized tooling and adhering to established best practices.

## Contact Information

| Name         | Email address          |
|--------------|------------------------|
| Aditya Tripathi          | aditya.tripathi.snaatak@mygurukulam.co     |

## References

| Links        | Descriptions         |
|--------------|------------------------|
|   [Why MonoRepo](https://medium.com/@avicsebooks/monorepo-2edb5a67517d) | Reasons For MonoRepo. |
[Understanding MonoRepo](https://medium.com/@r.sipchenko/understanding-monorepos-ad9c4ac7b504)     |   A detailed guide on MonoRepo.   |
