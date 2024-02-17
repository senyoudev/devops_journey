## What is CI/CD?

CI/CD is a method to frequently deliver apps to customers by introducing automation into the stages of app development. The main concepts attributed to CI/CD are continuous integration, continuous delivery, and continuous deployment.

## Example 

Let's say you have a team of developers working on a project. Each developer is working on a different feature of the project. The developers are working on their features in their own branches. Once the developers are done with their features, they push their code to the main branch. Once the code is pushed to the main branch, the CI/CD pipeline is triggered. The CI/CD pipeline will run tests on the code and if the tests pass, the code will be deployed to the production environment. If the tests fail, the code will not be deployed to the production environment.

## We will be using Jenkins for CI/CD

Jenkins is a self-contained, open source automation server which can be used to automate all sorts of tasks related to building, testing, and delivering or deploying software.

Jenkins can be installed through native system packages, Docker, or even run standalone by any machine with a Java Runtime Environment (JRE) installed.


## Why choose Jenkins?

- **Intuitive web inteeface**:
- **Easy installation**:
- **Easy configuration**:
- **Free and open source**:
- **Extensible** : Plugins are available for integrating Jenkins with most version control systems and big databases.
- **Community support**:

## Installing Jenkins through Docker

To install Jenkins through Docker, you need to have Docker installed on your machine. If you don't have Docker installed, you can install it by following the instructions [here](https://docs.docker.com/get-docker/).

Once you have Docker installed, you can install Jenkins by running the following command:

```bash
docker --version

docker pull jenkins/jenkins:lts

docker run --detach --publish 8080:8080 --volume jenkins_home:/var/jenkins_home --name jenkins jenkins/jenkins:lts 

docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword // to get the initial admin password
```

Once you have the initial admin password, you can go to `http://localhost:8080` and enter the initial admin password to unlock Jenkins.

## Jenkins Jobs

# Types of Jenkins Jobs

- **Freestyle Project**:
- **Pipeline**:
- **Multibranch Pipeline**:
- **GitHub Organization**:
- **Folder**:
- **Multi-configuration Project**:

# Creating a Freestyle Project

Freestyle projects are used to create simple Jenkins jobs. For example, you can use a freestyle project to run a shell script, execute a batch command, or run a Maven target.

# Creating a Pipeline

Pipelines are used to create complex Jenkins jobs. Pipelines are defined using a Jenkinsfile. A Jenkinsfile is a text file that contains the definition of a Jenkins Pipeline and is checked into source control.

# Creating a Multibranch Pipeline

Multibranch pipelines are used to create Jenkins jobs that run on multiple branches of a repository. For example, you can use a multibranch pipeline to run a Jenkins job on every branch of a repository.

# Creating a GitHub Organization

GitHub organizations are used to create Jenkins jobs that run on multiple repositories. For example, you can use a GitHub organization to run a Jenkins job on every repository in a GitHub organization.

# Creating a Folder

Folders are used to organize Jenkins jobs. For example, you can use a folder to group related Jenkins jobs together.

# Creating a Multi-configuration Project

Multi-configuration projects are used to create Jenkins jobs that run on multiple configurations. For example, you can use a multi-configuration project to run a Jenkins job on multiple operating systems.

## Jenkins Plugins

Jenkins has a rich ecosystem of plugins that can be used to extend its functionality. There are thousands of plugins available for Jenkins, and they can be used to integrate Jenkins with other tools, such as version control systems, build tools, and testing frameworks.


## Jenkins Pipeline

Jenkins Pipeline is a suite of plugins that supports implementing and integrating continuous delivery pipelines into Jenkins. Jenkins Pipeline provides an extensible set of tools for modeling simple-to-complex delivery pipelines "as code".

## Jenkinsfile

Example of a Jenkinsfile:

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building"'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying"'
            }
        }
    }
}
```


