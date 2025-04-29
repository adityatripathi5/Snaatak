| Author          | Created on | Version   | Last updated by |  Internal Reviewer | L0  | L1  | L2  |
|-----------------|------------|-----------|------------------|--------------------|-----|-----|-----|
| Aditya Tripathi | 28-04-25   | version 1 | N/A              | Priyanshu        | Khushi | Rishabh | Piyush |

## Table of Contents

1.  [Introduction](#introduction)
2.  [What is GitOps?](#what-is-gitops)
3.  [Why GitOps? (Benefits)](#why-gitops-benefits)
4.  [Types of GitOps Workflows](#types-of-gitops-workflows)
    *   [Push-based Workflow (CI-driven)](#push-based-workflow-ci-driven)
    *   [Pull-based Workflow (Operator-driven)](#pull-based-workflow-operator-driven)
    *   [Hybrid Workflow (Combined Approach)](#hybrid-workflow-combined-approach)
5.  [Comparison: Push vs. Pull vs. Hybrid Workflows](#comparison-push-vs-pull-vs-hybrid-workflows)
6.  [Conclusion](#conclusion)
7.  [Contact Information](#contact-information)
8.  [References](#references)

## Introduction

GitOps is a way to manage infrastructure and application deployments using Git. It treats Git as the main source of truth, making it easier to automate changes, work together as a team, and keep everything consistent and trackable.

## What is GitOps?

GitOps is a way to manage your infrastructure and app deployments using Git. It works by:

- Keeping all your configuration files in Git.
- Using automation (like CI/CD pipelines) to handle deployments.
- Continuously checking that what's running matches what’s defined in Git—and fixing it if it doesn’t.

## Why GitOps? (Benefits)

Adopting GitOps offers numerous advantages for development and operations teams:

| **Factors**                       | **Description**                                                                                                                                                                   |
|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Improved Developer Experience** | Developers can use familiar Git workflows to manage infrastructure and application deployments, reducing the need to learn complex orchestration tools directly.                 |
| **Enhanced Stability & Reliability** | Git provides a full audit trail (who changed what, when, and why). Rollbacks are as simple as reverting a Git commit. The declarative nature ensures predictability.            |
| **Increased Security**           | Git provides strong correctness guarantees through commit history and PR reviews. Pull-based and well-designed hybrid models limit credential exposure by keeping environment credentials within the target system boundary. |
| **Faster Deployment Velocity**   | Automation triggered by Git commits significantly speeds up the deployment process.                                                                                               |

## Types of GitOps Workflows

There are three primary approaches to implementing the GitOps synchronization loop:

### Push-based Workflow (CI-driven)

- Changes are pushed to the target environment using CI/CD pipelines.
- CI/CD tools like Jenkins or GitHub Actions trigger deployments after code changes.
- Suitable for teams already using CI/CD workflows for deployments.
*   **Pros:** Can be simpler to set up initially if you already have a robust CI system; direct feedback within the pipeline run.
*   **Cons:** CI system needs potentially high-privilege access to the cluster (security concern); less separation between build and deployment concerns; no inherent continuous drift detection outside of pipeline runs.
![Push based workflow](https://github.com/user-attachments/assets/002806b0-87ab-4673-9357-a1489756ce5d)

### Pull-based Workflow (Operator-driven)

- A GitOps operator (e.g., Flux or ArgoCD) pulls changes from Git and applies them to the target environment.
- Provides a more secure approach by removing the need to expose the cluster to external CI/CD tools.
*   **Pros:** More secure (environment credentials stay contained); strong separation of concerns; continuous reconciliation detects and corrects drift; aligns closely with the Kubernetes controller pattern.
*   **Cons:** Requires running and managing an additional agent in the cluster; feedback loop might feel less direct than a push-based pipeline (though tools provide UIs/notifications).
![Pull based workflow](https://github.com/user-attachments/assets/b8f5436d-a69e-4b36-8fcd-3848037396e9)

### Hybrid Workflow (Combined Approach)

*   **How it works:** This model combines elements of both push and pull mechanisms. A common pattern:
    1.  CI pipeline builds an image, pushes it to a registry.
    2.  CI pipeline **pushes** a configuration change (e.g., updating an image tag in a `values.yaml` or Kustomization file) **to the Git repository**.
    3.  A pull-based operator (like Argo CD or Flux) running in the cluster detects the change **in the Git repository** and *pulls*/applies the update to the environment.
*   **Characteristics:**
    *   Leverages strengths of both: CI handles build/artifact promotion and updates Git; the Pull agent handles secure deployment and reconciliation from Git.
    *   Maintains good separation of concerns while integrating with CI.
    *   Often a pragmatic choice in complex environments.
*   **Pros:** Balances CI integration with the security/reconciliation benefits of the pull model; flexible; keeps environment credentials secure within the cluster (managed by the Pull agent).
*   **Cons:** Can be more complex to set up and orchestrate due to the interaction between CI and the pull agent; requires careful design.
![image](https://github.com/user-attachments/assets/ec2d64f4-08d3-490e-b1f4-f501b9ad522c)


**The Pull-based workflow is often considered the most aligned with core GitOps principles. However, the Hybrid model is a very common and practical approach.**

## Comparison: Push vs. Pull vs. Hybrid Workflows

| Feature               | Push-based (CI-driven)                      | Pull-based (Operator-driven)                  | Hybrid (Combined)                                    |
| :-------------------- | :----------------------------------------- | :-------------------------------------------- | :--------------------------------------------------- |
| **Security**          | Lower (Environment credentials exposed externally) | Higher (Environment credentials contained)    | Moderate to High (Env creds contained, relies on Git security & Agent) |
| **Drift Detection**   | Limited (Only during pipeline execution)   | Continuous (via Pull Agent)                   | Continuous (via Pull Agent component)                |
| **Reconciliation**   | Manual or triggered by pipeline            | Automatic & Continuous                        | Automatic & Continuous (via Pull Agent component)    |
| **Separation (CI/CD)**| Often tightly coupled (CI does deployment) | Clearly separated (Agent does deployment)     | Clearly separated (CI builds/updates Git, Agent deploys) |

## Conclusion

GitOps is a modern way to manage infrastructure and applications using Git as the single source of truth. It boosts developer productivity, strengthens security, and makes deployments more reliable and consistent. Pull-based and hybrid models, powered by tools like Argo CD or Flux, are often preferred for their security and continuous sync features.

## Contact Information

| Name         | Email address          |
|--------------|------------------------|
| Aditya Tripathi          | aditya.tripathi.snaatak@mygurukulam.co     |

## References

| Links                                                                                     | Description                                        |
|-------------------------------------------------------------------------------------------|----------------------------------------------------|
| [GitOps Principles](https://medium.com/@ezinneanne/what-is-gitops-principles-tools-and-benefits-3d9760430335) | It outlines some important Principles of GitOps |                                
| [Guide To GitOps](https://www.weave.works/technologies/gitops/)                           | Introduction to GitOps by Weaveworks               |
| [Argo CD Documentation](https://argo-cd.readthedocs.io/)                                  | Official documentation for Argo CD                 |
| [Flux CD Documentation](https://fluxcd.io/)                                               | Official documentation for Flux CD                 |
| [OpenGitOps Project](https://opengitops.dev/)                                             | Open source GitOps standards and best practices    |
