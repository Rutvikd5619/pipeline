pipeline{
    agent{
        node{
            label "slave-1"
            customWorkspace "/mnt/jenkins-slave/project"
        }

    }

    stages{
        stage('httpd-install'){
            steps{
                sh "sudo dnf install httpd -y"
                sh "sudo dnf install git -y"
            }
        }
        stage('clone-repo'){
            steps{
                git branch: 'main', poll: false, url: 'https://github.com/Rutvikd5619/pipeline.git'
            }
        }
        stage('deploy'){
            steps{
                sh "sudo cp /mnt/jenkins-slave/project/index.html /var/www/html/" 

            }
        }
        stage('start-server'){
            steps{
                sh "sudo systemctl start httpd"
                sh "sudo systemctl enable httpd"
            }
        }
    }
}
