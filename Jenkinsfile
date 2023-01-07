pipeline{
    agent any

    stages{
        stage('git checkout'){
            steps{
                git branch: 'devops', url: 'https://github.com/chiomambu/Pipeline-01.git'
            }
        }

        stage('sonar analysis'){
            agent{
                docker{
                    image 'maven'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsID: 'sonar-token'){
                        sh 'mvn clean package sonar:sonar'

                    }
                    

                }
            }
        }

        stage('quality gates'){
            steps{
                script{
                    waitForQualityGate(abortPipeline: false, credentialsId: 'sonar-token')
                }
            }
        }
    }
}