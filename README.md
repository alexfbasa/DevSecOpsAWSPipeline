# DevSecOps AWS Pipeline - Continuation

## Overview

Welcome to the DevSecOps AWS Pipeline repository! This project is a continuation of the DevSecOps AWS Terraform
repository ([DevSecOpsAWSTerraform](https://github.com/alexfbasa/DevSecOpsAWSTerraform.git)), focusing on the second
step in our journey to enhance software security and address vulnerabilities.

## Purpose

This repository extends the infrastructure established in the previous Terraform-based DevSecOps setup. Now, we shift
our focus to implementing a robust CI/CD pipeline using AWS CodePipeline, CodeBuild, and other DevSecOps tools. The
pipeline aims to automate security processes, conduct vulnerability scans, and ensure secure deployments.

![DevSecOps scope](./images/devsecops_scope.png)

## Java Reachability Playground - Modified for AWS DevSecOps

This is an intentionally vulnerable application, modified by ASecurityGuru for AWS DevSecOps. The application is
designed to demonstrate the capabilities of Snyk's Reachable Vulnerabilities feature, showcasing both "Reachable" and "
Potentially Reachable" vulnerabilities.

### Included Vulnerabilities

1. **Arbitrary File Write via Archive Extraction:**
 - Exploits the ZipSlip vulnerability, resulting in remote command execution. The application creates both good.txt
   and evil.txt during extraction, demonstrating the potential risk.

2. **Deserialization of Untrusted Data:**
 - Demonstrates potentially vulnerable code without actual exploitation. Data about vulnerable functions is not
   available.

### How to Run the Demo (Maven)

1. Checkout this repository:
```bash
git clone git@github.com:snyk/java-reachability-playground.git
```

2. Install dependencies:
```bash
mvn install
```

3. Compile the project:
```bash
mvn compile
```

4. Run the main class:
```bash
mvn exec:java -Dexec.mainClass=Unzipper
```

5. Run Snyk command with Reachable Vulnerabilities flag:
```bash
snyk test --reachable
```
or
```bash
snyk monitor --reachable
```

6. View the vulnerability SNYK-JAVA-ORGND4J-72550 marked as reachable along with the function call path to the
vulnerability.

### For Gradle

1. Build the artifacts:
```bash
./gradlew build
```

2. See test results:
```bash
snyk test --file=build.gradle --reachable
```
or
```bash
snyk monitor --file=build.gradle --reachable
```

**Note:** Once the Java application is run, malicious_file.zip will be deleted. To run it again, run `git checkout .`
prior to the next Java run.

### Screenshots

#### CLI

![Snyk CLI Reachable Vulnerabilities](./images/CLI_reachable.png)

#### Snyk UI

![Snyk UI Reachable Vulnerabilities](./images/UI_reachable.png)

## Contributions and Issues

Feel free to contribute to the project by submitting pull requests or reporting any issues you encounter. Let's
collaboratively build a secure and efficient DevSecOps pipeline.

## License

This project is licensed under the [MIT License](LICENSE), allowing you to freely use and modify the codebase for your
needs.

Happy Coding!
