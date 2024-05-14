# Jenkins CI/CD Pipeline for React Application

This Jenkins pipeline automates the Continuous Integration and Continuous Deployment (CI/CD) process for a React application hosted on GitHub. The pipeline performs the following steps:

1. **Checkout Code:** The pipeline checks out the code from the GitHub repository.

2. **Run Unit Tests:** It executes npm unit tests using a Gradle script and stores the test reports as artifacts.

3. **SonarQube Analysis:** The pipeline performs a SonarCloud analysis on the unit test reports generated in the previous step to analyze code quality.

4. **Build NPM Code:** It builds the React application using npm with the help of a Gradle script.

5. **Deployment:** Finally, the built code is deployed using Nginx.

## Prerequisites

- Jenkins installed and configured.
- Nodejs and npm installed and configured.
- SonarCloud account and project set up.
- Gradle installed and Configured
- Nginx server for deployment.

## Setup

1. **Configure Jenkins:**
   - Install necessary plugins (Git plugin, Gradle plugin, SonarQube Scanner plugin).
   - Configure Jenkins credentials for GitHub and SonarQube token.

2. **Install Nodejs and Npm:**
   - Install and configure nodejs and npm on the build server.

2. **Set Up SonarCloud:**
   - Set up a project in SonarCloud and obtain a token for authentication.

3. **Set Up Gradle:**
   - Install and configure Gradle on the build server.

4. **Set Up Nginx:**
   - Install and configure Nginx on the deployment server.

5. **Update Jenkinsfile:**
   - Replace placeholders in the Jenkinsfile with actual values

6. **Update sonar-project.properties:**
   - Replace placeholders in the sonar-project.properties with actual values

## Usage

1. **Run Pipeline:**
   - Trigger the pipeline manually or configure it to run automatically on code changes.

## Jenkins Pipeline

The Jenkins pipeline is defined in the `Jenkinsfile`. It orchestrates the entire CI/CD process, including code checkout, testing, analysis, building, and deployment.

## Files

- `Jenkinsfile`: Defines the Jenkins pipeline stages and steps.
- `build.gradle`: Contains Gradle steps.
- `sonar-project.propertis`: Sonarcloud configuration file for sonar scan.

## References

- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [NodeJs Documentation](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)
- [SonarCloud Documentation](https://sonarcloud.io/documentation)
- [Gradle Documentation](https://docs.gradle.org/current/userguide/userguide.html)
- [Nginx Documentation](https://nginx.org/en/docs/)
