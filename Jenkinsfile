pipeline{
    agent any

    stages{
        stage('git checkout'){
            steps{
                git branch: 'devops', url: 'https://github.com/chiomambu/Pipeline-01.git'
            }
        }
    }
}