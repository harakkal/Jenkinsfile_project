pipeline{
    // need to add agents
    agent any
    tools{
        // here mymaven is tool configured under global tool configuration
        // new tools added
        maven 'local_maven'
    }
    stages{ 
        stage('Clone repo') {
            steps{            
              //  git 'https://github.com/abhijithvg/simple-java-maven-app.git'
                git 'https://github.com/harakkal/simple-java-maven-app.git'
            }
        }
        stage('Compile Code') {
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test Code') {
            steps{
                sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package Code') {
            steps{
                sh 'mvn package'
            }
        }
    }
    post{
        success{
            //This will be executed if the pipeline execution is successful
            slackSend channel: 'devops-learning', message: 'Pipeline executed successfully (msg from [9 - SCMPipelineDemo])!'
            echo 'Pipeline executed successfully!'
        }
        failure{
            //This will be executed if the pipeline execution fails
            slackSend channel: 'devops-learning', message: 'Pipeline failed!'
            echo 'Pipeline failed!'
        }
    }
}
