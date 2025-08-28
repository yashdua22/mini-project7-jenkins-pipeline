pipeline {
    agent any

    stages {
        stage('Pull & Run Nginx') {
            steps {
                sh '''
                docker pull nginx:latest
                docker run -d --name nginx-container -p 80:80 nginx:latest
                '''
            }
        }

        stage('Pull & Run Tomcat') {
            steps {
                sh '''
                docker pull tomcat:latest
                docker run -d --name tomcat-container -p 8081:8080 tomcat:latest
                '''
            }
        }

        stage('Pull & Run RabbitMQ') {
            steps {
                sh '''
                docker pull rabbitmq:latest
                docker run -d --name rabbitmq-container -p 5672:5672 -p 15672:15672 rabbitmq:latest
                '''
            }
        }

        stage('Pull & Run Memcached') {
            steps {
                sh '''
                docker pull memcached:latest
                docker run -d --name memcached-container -p 11211:11211 memcached:latest
                '''
            }
        }

        stage('Pull & Run MySQL 8.0') {
            steps {
                sh '''
                docker pull mysql:8.0
                docker run -d --name mysql-container -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 mysql:8.0
                '''
            }
        }

        stage('Update OS') {
            steps {
                sh '''
                sudo apt-get update -y
                '''
            }
        }
        stage('Pull & Run Hello World') {
            steps {
                sh '''
                docker pull hello-world:latest
                docker run --name hello-container hello-world:latest || true
                '''
            }
        }

        stage('Send Slack Notification') {
            steps {
                slackSend (
                    channel: '#jenkins-channel',
                    color: '#0000FF',  // Blue
                    message: '✅ All containers deployed and OS updated successfully!'
                )
            }
        }
    }
}
