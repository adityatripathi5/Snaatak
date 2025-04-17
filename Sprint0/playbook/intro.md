![image](https://github.com/user-attachments/assets/adf5b14d-f9c4-4427-93a8-d9895c425360)

| Author          | Created on | Version   | Last updated by | Last edited on | Internal Reviewer | L0  | L1  | L2  |
|-----------------|------------|-----------|------------------|----------------|--------------------|-----|-----|-----|
| Aditya Tripathi | 16-04-25   | version 1 | N/A              | N/A            | Priyanshu         | Khushi | Rishabh | Piyush |

# Introduction to Ansible Playbooks

This document provides an introduction to Ansible Playbooks, a core component of Ansible automation.

## Table of Contents

1. [What is an Ansible Playbook?](#1-what-is-an-ansible-playbook)
2. [Why Use Playbooks?](#2-why-use-playbooks)
3. [Features of Playbooks](#3-features-of-playbooks)
4. [Structure of a Playbook](#4-structure-of-a-playbook)
5. [Modules and Tasks](#5-modules-and-tasks)
6. [Variables and Templates](#6-variables-and-templates)
7. [Handlers and Notifications](#7-handlers-and-notifications)
8. [Conditionals, Loops, and Tags](#8-conditionals-loops-and-tags)
9. [Best Practices & Folder Structure](#9-best-practices--folder-structure)
10. [Conclusion](#10-conclusion)

## 1. What is an Ansible Playbook?

| Feature          | Description                                                                                                                                                                                                                              |
| :--------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Definition       | An Ansible Playbook is a file written in YAML format that defines a series of tasks to be executed on remote hosts.                                                                                                                      |
| Contrast with Ad-hoc Commands | Unlike ad-hoc commands, which are used for one-off tasks, playbooks are used to automate complex, multi-step configurations and deployments. Playbooks are reusable and idempotent.                                                                                                                      |
| YAML Syntax      | Playbooks are written in YAML (YAML Ain't Markup Language), a human-readable data serialization format. YAML uses indentation to define structure, making it easy to understand and write.                                                                                                                      |
| Human-Readable   | YAML's syntax is designed to be easily read and written by humans. This makes playbooks more maintainable and collaborative.                                                                                                                      |

Ansible Playbooks are the primary way to configure and manage systems with Ansible. They allow you to define the desired state of your infrastructure in a declarative way.

## Why Playbooks?

Ansible Playbooks offer several advantages:

* **Automation:** Automate repetitive tasks, reducing manual effort and errors.
* **Configuration Management:** Define the desired state of systems and ensure they remain consistent.
* **Orchestration:** Coordinate complex workflows across multiple systems.
* **Idempotency:** Ensure that running a playbook multiple times has the same result, preventing unintended changes.
* **Version Control:** Store playbooks in version control systems like Git, enabling collaboration and change tracking.
* **Reusability:** Playbooks can be reused across different environments and projects.
* **Simplicity:** YAML syntax makes playbooks easy to write and understand.

## Features of Playbooks

* **Declarative:** Define the desired state, not the steps to achieve it.
* **Idempotent:** Running the same playbook multiple times produces the same outcome.
* **Modular:** Use reusable modules to perform specific tasks.
* **Flexible:** Support variables, conditionals, loops, and handlers for complex workflows.
* **Parallel Execution:** Execute tasks on multiple hosts simultaneously.
* **Orchestration:** Manage multi-tier applications.
* **Reporting:** Provide detailed output of playbook execution.

## 2. Structure of a Playbook

| Component    | Description                                                                                                                                                                                                                                                                                          |
| :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Plays          | A playbook contains one or more plays. A play defines a set of tasks to be executed on a group of hosts.                                                                                                                                                                                           |
| Tasks          | A play consists of a list of tasks. Each task executes a specific Ansible module. Tasks are executed sequentially within a play.                                                                                                                                                                    |
| Hosts          | Specifies the target hosts or groups of hosts on which the tasks will be executed. Hosts are defined in the Ansible inventory.                                                                                                                                                                     |
| Modules        | Ansible modules are pre-built units of code that Ansible uses to manage systems. Tasks in a playbook call these modules to perform actions.                                                                                                                                                        |
| Variables      | Variables can be defined at various levels (playbook, inventory, host/group vars) and are used to parameterize tasks and make playbooks more flexible.                                                                                                                                               |

**Example of a Basic Playbook:**

```yaml
---
- name: Ensure web server is running
  hosts: webservers
  become: true  # Run tasks with elevated privileges

  tasks:
    - name: Install httpd package
      yum:
        name: httpd
        state: present

    - name: Start httpd service
      service:
        name: httpd
        state: started
```

**Indentation and Structure (YAML):**

YAML uses indentation (spaces, not tabs) to define the structure and hierarchy of the playbook. Consistent indentation is crucial for YAML to be parsed correctly. Key-value pairs are common, where a key is followed by a colon and a space, and the value. Lists are indicated by a hyphen and a space.

## 3. Modules and Tasks

| Concept        | Description                                                                                                                                                                                                                                                                                          |
| :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ansible Modules | Modules are the core building blocks of Ansible tasks. They perform specific actions on managed nodes. Ansible has a vast library of built-in modules.                                                                                                                                           |
| Common Modules | `apt`/`yum` (package management), `copy` (file copying), `template` (file templating), `service` (service management), `user` (user management), `file` (file/directory operations), `command`/`shell` (executing arbitrary commands).                                                                 |
| Tasks Execution| Tasks within a play are executed sequentially, one after the other, on the specified hosts. Ansible waits for each task to complete before moving to the next.                                                                                                                                       |

## 4. Variables and Templates

| Concept         | Description                                                                                                                                                                                                                                                                                          |
| :-------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Variables       | Variables allow you to dynamically configure your playbooks. They can be defined in the playbook itself (vars section), in the Ansible inventory, or in separate variable files (group_vars/host_vars).                                                                                             |
| Jinja2 Templating| Ansible uses the Jinja2 templating engine to dynamically generate content in configuration files or commands. Variables can be embedded within template files using Jinja2 syntax (`{{ variable_name }}`).                                                                                             |
| Example         | You can use a template file (`httpd.conf.j2`) to configure an Apache web server. Variables for the server name, port, etc., can be defined in your playbook or inventory and rendered into the final `httpd.conf` file on the target host using the `template` module.                               |

## 5. Handlers and Notifications

| Concept        | Description                                                                                                                                                                                                                                                                                          |
| :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Handlers       | Handlers are special tasks that are only executed when explicitly notified by another task. They are typically used to restart services or perform other actions that should only occur when a configuration change has been made.                                                                    |
| Notifications  | Tasks can notify handlers using the `notify` keyword. If a task that notifies a handler results in a change on the managed host, the handler will be executed at the end of the current play. Multiple notifications to the same handler will only result in the handler being run once.                |
| Use Case       | For example, if you modify the Apache configuration file using the `template` module, you can notify a handler that restarts the `httpd` service. The service will only be restarted if the configuration file was actually changed.                                                                 |

## 6. Conditionals, Loops, and Tags

| Concept        | Description                                                                                                                                                                                                                                                                                          |
| :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Conditionals   | The `when` statement allows you to conditionally execute a task based on the value of a variable or a fact. This enables you to run specific tasks only on certain hosts or under specific conditions.                                                                                               |
| Loops          | Ansible provides several ways to iterate over lists or dictionaries using keywords like `with_items`, `loop`, `with_dict`, etc. This allows you to perform the same task multiple times with different parameters.                                                                                   |
| Tags           | Tags are labels that you can apply to plays and tasks. You can then use the `--tags` or `--skip-tags` command-line options to run only specific parts of a playbook or to skip certain tasks. This is useful for running specific configurations or skipping potentially time-consuming tasks.           |

## 7. Best Practices & Folder Structure

| Practice             | Description                                                                                                                                                                                                                                                                                          |
| :------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Recommended Layout | A common and recommended folder structure includes: `inventory/` (host files), `group_vars/` (group-specific variables), `host_vars/` (host-specific variables), `roles/` (reusable collections of tasks, handlers, and variables), and your playbook files (`*.yml`).                                |
| Version Control    | Always store your playbooks, inventory files, and variable files in a version control system like Git. This allows you to track changes, collaborate effectively, and easily revert to previous versions.                                                                                             |
| Idempotence        | Ensure your playbooks are idempotent. This means that running the same playbook multiple times should result in the same system state without making unnecessary changes. Ansible modules are generally designed to be idempotent.                                                                 |

## 8. Conclusion

Ansible Playbooks are a powerful and flexible way to automate system configuration and management. By understanding their structure, the use of modules, variables, handlers, and best practices, you can effectively leverage Ansible to manage your infrastructure in a consistent and efficient manner.

## Contact Information
| Name         | Email address          |
|--------------|------------------------|
| Aditya Tripathi          | aditya.tripathi.snaatak@mygurukulam.co     |

## Reference Links
| Links        | Descriptions         |
|--------------|------------------------|
|    [Link](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks.html) | Detailed Documentation on Playbook |
[Link](https://medium.com/@sayalishewale12/ansible-playbooks-0bf9336a6e19)     |  Understanding Playbook working   |
