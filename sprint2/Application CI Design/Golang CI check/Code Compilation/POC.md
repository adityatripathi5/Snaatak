

---

# **POC - Golang Code Compilation via CI**

---

## Table of Contents

1. [Objective](#objective)
2. [Pre-requisites](#pre-requisites)
3. [Step-by-Step Guide](#step-by-step-guide)
4. [Contact Information](#contact-information)
5. [References](#references)

---

## Objective: Compile and verify a Golang application

The objective of this POC is to demonstrate how to compile a basic **Golang** microservice into an executable binary and verify its correctness via CI. This process ensures that the Go application is free of syntax errors, compiles successfully, and can be packaged for deployment.

---

## Pre-requisites:

| **Specification**  | **Details**                         |
| ------------------ | ----------------------------------- |
| OS                 | Ubuntu 22.04                        |
| Go Version         | >= 1.20                             |
| Project Structure  | Standard Go module (`go.mod`) setup |
| Dependency Manager | `go mod`                            |

---

## Step-by-Step Guide:

**Step 1**: Clone the Go microservice repository

```bash
git clone https://github.com/your-org/go-ci-demo.git
cd go-ci-demo
```

![Screenshot 2025-05-18 151359](https://github.com/user-attachments/assets/f558c01c-ead3-4467-a149-70aadb47dc99)


---

**Step 2**: Verify dependencies

```bash
go mod tidy
```

This command ensures that all required modules are listed and unnecessary ones are removed.

![Screenshot 2025-05-18 151319](https://github.com/user-attachments/assets/bad30208-db0a-49e7-a97e-c1cc207c821c)


---

**Step 3**: Compile the code manually

```bash
go build -o output-binary-name main.go
```

This will generate a binary (`output-binary-name`) in the current directory if the code compiles successfully.

![Screenshot 2025-05-18 151928](https://github.com/user-attachments/assets/e12e4cdd-44fd-44c9-908d-8ac782d4d972)




---

## Contact Information

| **Name**        | **Email**                                                                                 |
| --------------- | ----------------------------------------------------------------------------------------- |
| Aditya Tripathi | [aditya.tripathi.snaatak@mygrurukulam.co](mailto:aditya.tripathi.snaatak@mygrurukulam.co) |

---

## References

| **Link**                                                                                   | **Description**         |
| ------------------------------------------------------------------------------------------ | ----------------------- |
| [golang.org](https://golang.org/doc/)                                                      | Official Go Docs        |
| [Go Build Command](https://pkg.go.dev/cmd/go#hdr-Compile_packages_and_dependencies)        | Go Build Reference      |
| [GitHub Actions for Go](https://docs.github.com/en/actions/guides/building-and-testing-go) | Go CI in GitHub Actions |
| [Go Modules](https://blog.golang.org/using-go-modules)                                     | Go Module Guide         |

---

