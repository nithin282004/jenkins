pipeline {
    agent any
    triggers{
        cron('H/15 * * * *')
    }
    stages{
        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t my-portfolio-site .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    bat 'docker rm -f portfolio || true'
                    bat 'docker run -d -p 8081:80 --name portfolio my-portfolio-site'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete.'
        }
    }
}
