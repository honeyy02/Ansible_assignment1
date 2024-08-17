pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
    }

    stages {
        stage('Checkout Code') {
            steps {
              checkout scm
            }
        }
      
        stage('Run Ansible Playbook') {
            steps {
                // Run your Ansible playbook
                sh '''
                ansible-playbook -i localhost, copy_JarToS3.yml
                '''
            }
        }
    }

    post {
        always {
            // Archive the logs
            archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true
        }
    }
}
