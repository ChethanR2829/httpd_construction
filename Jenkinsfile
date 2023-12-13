pipeline {
    agent { label "slave_2"}
    
    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('clone') {
            steps {
                echo 'clone project'
                git branch: 'main', url: 'https://github.com/ChethanR2829/httpd_construction.git'
            }
        }
        stage('verify') {
            steps {
                echo 'verifying files'
                sh 'pwd'
                sh 'ls'
            }
        }
        stage('copy') {
            steps {
                echo 'copying files'
                sh 'scp -i /home/ec2-user/key.pem -r /var/jenkins/workspace/httpd_construction_normal_method/* ec2-user@172.31.41.51:/var/www/html'
            }
        }
        stage('check deploy') {
            steps {
                echo 'check deploy'
            }
        }
    }
}
