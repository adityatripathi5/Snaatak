
#    **Java Unit Testing**

| **Author**  | **Created on** | **Version** | **Last updated by** | **Internal Reviewer** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer** |
| ----------- | -------------- | ----------- | ------------------- | ------------------ | --------------- | --------------- | --------------- |
| Aditya Tripathi | 13-05-25       |       1      | Aditya Tripathi        | Priyansh    | Priyanka           | Rishabh        | Piyush        |



**Table of Contents**

1. [**Introduction**](#introduction)
2. [**What is Unit Testing?**](#what-is-unit-testing?)
3. [**Why Unit Testing?**](#why-unit-testing?)
4. [**Different Tools used in Unit Testing**](#different-tools-used-in-unit-testing)
5. [**POC - Java Unit Testing**](#poc--java-unit-testing)
6. [**Conclusion**](#conclusion)
7. [**Contact Information**](#contact-information)
8. [**References**](#references)



## Introduction
Unit testing is like checking each piece to make sure it fits correctly and works as it should. By testing each piece individually, we can catch any mistakes early on and build a stronger, more stable castle. fixing errors in small parts of our code, so the whole program works correctly.

## What is Unit Testing?

Unit testing is a way to test small pieces of code to make sure they work correctly. It's like testing each brick in a wall to make sure it's strong and fits properly.

## Why Unit Testing?

| **Reasons**               | **Description**                                                                                      |
|---------------------------|------------------------------------------------------------------------------------------------------|
| **Early Bug Detection**    | It helps find and fix errors early in the development process, before they become bigger problems.    |
| **Improved Code Quality**  | It encourages writing clean, well-structured, and maintainable code.                                 |
| **Increased Confidence**   | By testing small parts of your code, you can be more confident that your software will work as expected. |
| **Facilitates Refactoring**| It allows you to make changes to your code without fear of breaking things, as unit tests can quickly identify any unintended consequences. |
| **Documentation**          | Unit tests serve as living documentation, showing how code is intended to be used.                   |


## Different Tools used in Unit Testing
The list of several relevant testing frameworks for Java is mentioned below





| Tool | What It Does | Key Features | Pros | Cons |
|---|---|---|---|---|
| **JUnit** | Used for testing small parts of Java programs. | Simple test annotations like @Test, @Before. Works well with IDEs like IntelliJ and Eclipse. | Easy to learn and use. Lots of community help available. | Can't run tests in parallel. Not great for very complex test setups. |
| **TestNG** | A testing tool for all types of tests (unit, integration, etc.). | Extra features like @BeforeSuite, @DataProvider. Runs tests in parallel. Test configuration using XML. | Great for managing big test suites. Runs tests faster with parallel execution. | Harder to learn than JUnit. XML setup can be tricky. |
| **Mockito** | Creates fake objects to test code. | Makes fake objects to replace real ones. Checks if fake objects are used correctly. Works with JUnit and TestNG. | Helps test without needing actual dependencies. Easy to use with clear syntax. | Doesn't support static methods without extra tools. Overuse can create bad test setups. |
| **Selenium** | Automates browsers to test websites. | Works with Chrome, Firefox, Safari, and more. Can be used with JUnit and TestNG. | Tests work across browsers. Supports many languages like Java, Python. | Tests can be slow. Needs extra tools for advanced features. |
| **Maven**     | Automates builds and manages dependencies. | Manages dependencies (e.g., JUnit, TestNG) using `pom.xml`. Plugins for testing (e.g., Surefire). Generates reports. | Simplifies dependency management. Automates test execution. Integrates easily with CI/CD tools. | Requires proper configuration to work effectively. Not a standalone testing tool.          |



## POC - Java Unit Testing 

- Please Refer Here for Unit Test [POC](https://github.com/adityatripathi5/Snaatak/blob/main/sprint2/Application%20CI%20Design/React%20CI%20Checks%20/Code%20compilation/POC.md)



## Conclusion

The goal of unit testing is to make sure that any new functionality does not break the existing functionality. It also helps identify any issues or bugs earlier in the development process and helps ensure that code meets quality standards set by the organisation.

##  Contact Information


| **Name**    | **Email address**         |
|-------------|---------------------------|
| Aditya Tripathi | aditya.tripathi.snaatak@mygurukulam.co |


## References

| **Link** | **Description** |
|------------------------------------------------------|------------------|
|[Testing Framework for Java](https://www.geeksforgeeks.org/7-best-testing-frameworks-for-java-developers/)| Unit Testing |
| [Java Unit Testing](https://www.freecodecamp.org/news/java-unit-testing/)| Unit Testing tool |
