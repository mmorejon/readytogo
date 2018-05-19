pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('build'){
            steps{
                sh 'docker image build --tag=readytogo .'
            }
        }
    }
    post{        
        success{
            slackSend baseUrl: 'https://gentalia-cujae.slack.com/services/hooks/jenkins-ci/', 
                channel: 'general', 
                color: 'danger', 
                message: "Website: Deploy failed on production (<${env.BUILD_URL}|View Build ${env.BUILD_DISPLAY_NAME}>)", 
                tokenCredentialId: 'slack_token'
        }
    }
}