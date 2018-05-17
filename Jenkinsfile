pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('build'){
            steps{
                sh 'docker image buid --tag readytogo .'
            }
        }
    }
}