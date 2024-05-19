pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "C/ProgramData/Jenkins/.jenkins/workspace/Jenkinsfile"
        TESTING_ENVIRONMENT = "AWS EC2 Instance"
        PRODUCTION_ENVIRONMENT = "Regina Production Environment"
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Adding short delay for the changes to stabilize"
                sleep time: 60, unit: 'SECONDS'

                echo "Fetch the source code from the directory path"
                echo "compile the code and generate any necessary artifacts"
                echo "Run Maven clean package"
                //Build step is to compile and assemble source code to deployable format
                // ex: exe file, or installer
                // the tools used depends on programming language
                // for Java, the tools used is usually Maven or Gradle
                //Let's say we are developing an Android mobile app, we can use Gradle
            }
        }
        stage('Unit and Integration Test') {
            steps {
                echo "Running unit tests on each component in JUnit"
                echo "Running integration tests on the whole system to test intraction with Katalon Studio"
                //Testing is crucial step to ensure that the product delivered acts as expected
                //Unit tests is the first layer, testing the smallest unit in the code.
                //Integration tests is the second layer, it tests the interation between the units
                //thus ensuring that the product runs smoothly as a whole (ready to be deployed)
                //Unit test is executed within the development environment using the tool that is specific for the language
                //we can use JUnit for unit testing in  Java
                //Integration test can be done using Katalon Studio that can simulate user interaction with the system
            }

            post {
                //if success, send success email
                success {
                    script {
                        emailext(
                            to: 'regina.arissaputri@gmail.com',
                            subject: 'Unit and Integration Test Status: SUCCESS',
                            body: 'Unit and Integration tests were successful, the log is attached below',
                            attachLog: true,
                            compressLog: true,
                        )
                    }
                }
                //if failure, send failure email
                failure {
                    script {
                        emailext(
                            to: 'regina.arissaputri@gmail.com',
                            subject: 'Unit and Integration Test Status: FAILURE',
                            body: 'Unit and Integration tests have failed, the log is attached below',
                            attachLog: true,
                            compressLog: true,
                        )
                    }
                }

            }
        }
        
        stage('Code Analysis') {
            steps {
                echo " analysing the quality of the code to ensure it meets industry standards"
                echo "Running SonarQube Scanner to check the quality of the code"
                // code analysis is very important to ensure that the code always adhere to the best practice. 
                // If the code is high quality, it wil be easier to understand and maintain
                // it can also detects common bugs and security issues.
                // SonarQube is such tool that can automate the analysis process, and it is compatible with multiple languages
            }
        }
        stage('Security Scan') {
            steps {
                echo "Security Scanning... checking for vulnerabilities"
                echo "Running SonarQube with security plugins to check for vulnerabilities in the code"
                //security scanning is important to ensure that the code is free from vulnerabilities
                //it catches security issues early in the development stage.
                // thus it can prevent potential security breaches, data loss, or other security threats
                // There are various tools to automate security scan, ex: OWASP ZAP, SonarQube, Synk etc
                // Since we already use SonarQube for Code Analsis, we can use this tool again with security plugins
    
            }
            post {
                //if success, send success email
                success {
                    script {
                        emailext(
                            to: 'regina.arissaputri@gmail.com',
                            subject: 'Security Scan Status: SUCCESS',
                            body: 'Security Scan were successful, the log is attached below',
                            attachLog: true,
                            compressLog: true,
                        )
                    }
                }
                //if failure, send failure email
                failure {
                    script {
                        emailext(
                            to: 'regina.arissaputri@gmail.com',
                            subject: 'Security San Status: FAILURE',
                            body: 'Security Scan has failed, the log is attached below',
                            attachLog: true,
                            compressLog: true,
                        )
                    }
                }

            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Setting up the Staging Environment"
                echo "Provisioning the EC2 instance on AWS"
                echo "Use AWS CLI to copy artifacts to AWS EC2 instance and run deployment command"
                echo "Deploy the application to the ${env.TESTING_ENVIRONMENT} testing environment specified"
                //This stage deploys the code to staging, which is a replica of the production environment,
                // this is to test the code for the final time before releasing it to production
                //there a a few tests, such as user acceptance testing (UAT), performance testing, and integration testing with other systems.
                // AWS EC2 or Amazon Web Services Elastic Compute Cloud can be used as server to host the staging environment

            }
        }
        stage('Integration Test on Staging') {
            steps {
                echo "Preparing the staging environment for integration stage"
                echo "executing integration test on staging environment"
                echo "executing end-to-end test with Katalon Studio"
                echo "executing API test using Newman (Postman command line tool)"
                //this test does testing for the code in the staging environment (which is a replica of the production environment)
                //this test is to ensure that the code behaves as expected even in the production environment
                // end to end tests the complete workflow of the code from start to finish to simulate real user scenarios to verify the system as a whole
                // Katalon Studio can be used again for End-to-end testing
                // API testing tests the application programming interfaces (APIs) directly, tests the back-end functionality, reliability, performance, and security
                // Postman is a common tool to test API, especially for debugging API


            }
        
        }
        stage('Deploy to Production') {
            steps {
                echo "Hosting server for production with AWS EC2"
                echo "Deploying the code to the ${env.PRODUCTION_ENVIRONMENT} live environment"
                // after all the testing is done and the code behaves as expected in both controlled environment and production environment
                // it is time to deploy the final code to the production stage to be accessible to end-user.
                // it involves making the application available for actual use by customers or stakeholders.
                // thus, this means the code is now in live environment, accessible for public or end-users.
            }
        }
    
                
            
            
        
        
    }
}
