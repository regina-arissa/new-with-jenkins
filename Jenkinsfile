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
            echo "Fetch the source code from the directory path: ${env.DIRECTORY_PATH}"
            echo "compile the code and generate any necessary artifacts"
        }
        post{
            success{
                mail to: "regina.arissaputri@gmail.com",
                subject: "Build Status Email",
                body: "Build was successful"
            }
        }
        }
        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }
        stage('Code Qualtiy Check') {
            steps {
                echo "Check the Quality of the Code"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy the application to the ${env.TESTING_ENVIRONMENT} environment specified by the environment variable"
            }
        }
        stage('Approval') {
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