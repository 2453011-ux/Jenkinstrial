
pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR_USERNAME/portfolio-jenkins.git'
            }
        }

        stage('Build') {
            steps {
                bat '''
                    echo Building Portfolio Website...
                    echo HTML and CSS files are ready.
                '''
            }
        }

        stage('Validate Files') {
            steps {
                bat '''
                    if not exist index.html (
                        echo ERROR: index.html not found
                        exit /b 1
                    )

                    if not exist style.css (
                        echo ERROR: style.css not found
                        exit /b 1
                    )

                    echo Portfolio files validated successfully.
                '''
            }
        }

        stage('Archive Website') {
            steps {
                archiveArtifacts artifacts: 'index.html,style.css',
                    fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Portfolio Pipeline Executed Successfully!'
        }

        failure {
            echo 'Portfolio Pipeline Failed!'
        }
    }
}
