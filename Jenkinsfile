pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "C/ProgramData/Jenkins/.jenkins/workspace/Jenkinsfile"
        TESTING_ENVIRONMENT = "Testing Environment"
        PRODUCTION_ENVIRONMENT = "Regina Production Environment"
    }
    
    stages {
        stage('Build') {
            steps {
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
        post{
            //if success, send success email
            success{
                mail to: "regina.arissaputri@gmail.com",
                subject: "Test Status Email",
                body: "Test was successful",
                attachLog: true
            }
            // //if failure, send failure email
            // failure{
            //     mail to: "regina.arissaputri@gmail.com",
            //     subject: "Test Status Email",
            //     body: "Test has failed",
            //     //attach log file
            //     // attachLog: true
            // }
        }
        }
        stage('Code Analysis') {
            steps {
                echo "Check the Quality of the Code"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Security scanning"
            }
            
        // post{
        //     //if success, send success email
        //     success{
        //         mail to: "regina.arissaputri@gmail.com",
        //         subject: "Test Status Email",
        //         body: "Security Scan was successful",
        //         //attach log file
        //         attachLog: true
        //     }
        //     //if failure, send failure email
        //     failure{
        //         mail to: "regina.arissaputri@gmail.com",
        //         subject: "Test Status Email",
        //         body: "Security Scan has failed",
        //         //attach log file
        //         attachLog: true
        //     }
        // }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploy the application to the ${env.TESTING_ENVIRONMENT} environment specified by the environment variable"
            }
        }
        stage('Integration Test on Staging') {
            steps {
                sleep time: 10, unit: 'SECONDS'
                echo 'Manual approval received'
            }
        
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the ${env.PRODUCTION_ENVIRONMENT} environment"
            }
        }
    
                
            
            
        
        
    }
}
