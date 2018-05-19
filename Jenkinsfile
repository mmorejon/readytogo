pipeline {
    agent {
        label 'master'
    }
    parameters {
        booleanParam(name: 'Mi-Variable', defaultValue: false, description: 'Dime que pongo aqui.')
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
            echo 'Success'
        }
        
        failure{
            slackSend baseUrl: 'https://gentalia-cujae.slack.com/services/hooks/jenkins-ci/', 
                channel: 'notifications', 
                color: 'danger', 
                message: "Website: Deploy failed on production (<${env.BUILD_URL}|View Build ${env.BUILD_DISPLAY_NAME}>)", 
                tokenCredentialId: 'slack_token'
        }
    }
}