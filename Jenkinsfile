pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-creds',
                    url: 'https://github.com/shivasaidhattareddykthestackly/uploads.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh '''
                    pwd
                    ls -la
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application to Apache web server...'
                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp -r *.html /var/www/html/
                    sudo ls -la /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the logs.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
