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

In the era of cloud-native technologies, microservices, and container orchestration (like Kubernetes), managing infrastructure and application deployments efficiently, reliably, and securely is paramount. Traditional methods often involve manual steps, imperative scripts, or complex tooling that can lead to inconsistencies and operational overhead.

GitOps emerges as a modern operational paradigm that leverages Git as the **single source of truth** for declarative infrastructure and applications. By using familiar Git workflows (like pull requests and version control), teams can automate, manage, and audit system changes more effectively. This document provides an overview of GitOps, its core concepts, common workflows (push, pull, and hybrid), and benefits.

## What is GitOps?

GitOps is an operational framework that takes DevOps best practices used for application development (such as version control, collaboration, compliance, and CI/CD) and applies them to infrastructure automation.

**At its core, GitOps is:**

1.  **Declarative:** The desired state of the entire system (infrastructure, applications) is described declaratively in configuration files (e.g., `YAML` for Kubernetes, Terraform `HCL`).
2.  **Version Controlled:** These declarative configuration files are stored and versioned in a Git repository, which acts as the **single source of truth**.
3.  **Automated:** Approved changes to the Git repository automatically trigger processes to apply or make the desired state available to the target environment(s).
4.  **Continuously Reconciled:** Software agents (often called operators or controllers) continuously ensure that the actual state matches the desired state defined in Git. They alert on and/or correct any divergence (this is strongest in Pull-based and Hybrid models).

The term "GitOps" was originally coined by [Weaveworks](https://www.weave.works/technologies/gitops/).

## Why GitOps? (Benefits)

Adopting GitOps offers numerous advantages for development and operations teams:

*   **Improved Developer Experience:** Developers can use familiar Git workflows to manage infrastructure and application deployments, reducing the need to learn complex orchestration tools directly.
*   **Enhanced Stability & Reliability:** Git provides a full audit trail (who changed what, when, and why). Rollbacks are as simple as reverting a Git commit. The declarative nature ensures predictability.
*   **Increased Security:** Git provides strong correctness guarantees through commit history and PR reviews. Pull-based and well-designed hybrid models limit credential exposure by keeping environment credentials within the target system boundary.
*   **Faster Deployment Velocity:** Automation triggered by Git commits significantly speeds up the deployment process.
*   **Consistency & Standardization:** Git ensures that the configuration repository is the single source of truth, leading to consistent environments (dev, staging, prod).
*   **Easier Auditing & Compliance:** The Git history provides a clear, immutable record of all changes, simplifying audits and compliance checks.
*   **Disaster Recovery:** Re-creating infrastructure and applications becomes straightforward by pointing a new environment to the Git repository defining its desired state.

## Types of GitOps Workflows

There are three primary approaches to implementing the GitOps synchronization loop:

### Push-based Workflow (CI-driven)

*   **How it works:** The CI/CD pipeline (e.g., Jenkins, GitLab CI, GitHub Actions) builds artifacts and updates deployment configurations. The pipeline then *pushes* these changes **directly to the target environment** (e.g., by running `kubectl apply`, `helm upgrade`).
*   **Characteristics:**
    *   Deployment logic resides within the CI/CD pipeline.
    *   The pipeline requires direct credentials to access the target environment.
    *   Often an extension of traditional CI/CD practices.
*   **Pros:** Can be simpler to set up initially if you already have a robust CI system; direct feedback within the pipeline run.
*   **Cons:** CI system needs potentially high-privilege access to the cluster (security concern); less separation between build and deployment concerns; no inherent continuous drift detection outside of pipeline runs.

### Pull-based Workflow (Operator-driven)

*   **How it works:** A dedicated software agent (operator) runs *inside* the target environment (e.g., Kubernetes cluster). This agent continuously monitors a specified Git repository. When it detects a change (a divergence between Git and the live state), it *pulls* the manifests **from Git** and applies them locally within the environment.
*   **Popular Tools:** [Argo CD](https://argo-cd.readthedocs.io/), [Flux CD](https://fluxcd.io/)
*   **Characteristics:**
    *   The agent within the environment initiates the synchronization.
    *   Environment credentials remain within the environment boundary, enhancing security.
    *   Provides continuous reconciliation and drift detection.
    *   Strong separation of concerns: CI builds artifacts, the agent deploys/reconciles state defined in Git.
*   **Pros:** More secure (environment credentials stay contained); strong separation of concerns; continuous reconciliation detects and corrects drift; aligns closely with the Kubernetes controller pattern.
*   **Cons:** Requires running and managing an additional agent in the cluster; feedback loop might feel less direct than a push-based pipeline (though tools provide UIs/notifications).

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

**The Pull-based workflow is often considered the most aligned with core GitOps principles. However, the Hybrid model is a very common and practical approach.**

## Comparison: Push vs. Pull vs. Hybrid Workflows

| Feature               | Push-based (CI-driven)                      | Pull-based (Operator-driven)                  | Hybrid (Combined)                                    |
| :-------------------- | :----------------------------------------- | :-------------------------------------------- | :--------------------------------------------------- |
| **Mechanism**         | CI pipeline pushes changes **directly to environment** | Agent inside environment pulls changes **from Git** | Mix: CI pushes config changes **to Git**, Agent pulls changes **from Git** |
| **Agent Location**    | External (CI/CD Server)                    | Internal (Within the target environment)        | Both (External CI, Internal Pull Agent)              |
| **Credentials**       | CI server needs **environment** credentials    | **Environment** credentials stay within its boundary | CI needs **Git write** access; Agent needs **Git read & env** access (env creds internal) |
| **Security**          | Lower (Environment credentials exposed externally) | Higher (Environment credentials contained)    | Moderate to High (Env creds contained, relies on Git security & Agent) |
| **Drift Detection**   | Limited (Only during pipeline execution)   | Continuous (via Pull Agent)                   | Continuous (via Pull Agent component)                |
| **Reconciliation**   | Manual or triggered by pipeline            | Automatic & Continuous                        | Automatic & Continuous (via Pull Agent component)    |
| **Separation (CI/CD)**| Often tightly coupled (CI does deployment) | Clearly separated (Agent does deployment)     | Clearly separated (CI builds/updates Git, Agent deploys) |
| **Complexity**        | Potentially simpler initial setup          | Requires deploying/managing an agent          | Higher (Coordination between push & pull parts)      |
| **Typical Trigger**   | CI pipeline completion                     | Git commit detection by Agent                 | Git commit detection by Agent (often after CI pushes commit) |

## Conclusion

GitOps provides a powerful, auditable, and automated framework for managing modern infrastructure and applications declaratively using Git as the source of truth. It enhances developer productivity, improves system reliability and security, and standardizes deployment practices. While different workflows exist – Push, Pull, and Hybrid – the Pull-based and Hybrid models are often preferred for their enhanced security posture and continuous reconciliation capabilities provided by in-cluster agents like Argo CD or Flux. Choosing the right workflow depends on specific organizational needs, security requirements, and existing tooling landscape. Adopting GitOps principles represents a significant step forward in streamlining cloud-native operations.

## Contact Information

| Name         | Email address          |
|--------------|------------------------|
| Aditya Tripathi          | aditya.tripathi.snaatak@mygurukulam.co     |

## References

| Links                                                                                     | Description                                        |
|-------------------------------------------------------------------------------------------|----------------------------------------------------|
| [Guide To GitOps](https://www.weave.works/technologies/gitops/)              | Introduction to GitOps by Weaveworks               |
| [Argo CD Documentation](https://argo-cd.readthedocs.io/)                                  | Official documentation for Argo CD                 |
| [Flux CD Documentation](https://fluxcd.io/)                                               | Official documentation for Flux CD                 |
| [OpenGitOps Project](https://opengitops.dev/)                                             | Open source GitOps standards and best practices    |
| [CNCF App Delivery SIG](https://github.com/cncf/sig-app-delivery)                         | CNCF Special Interest Group for app delivery       |
