pipeline {
    agent any
    environment {
        ANSIBLE_SERVER = "172.31.1.94"
    }
    stages {
        stage("Deploy") {
            steps {
                sshagent(['ansible-server']) {
                    sh "ssh -o StrictHostKeyChecking=no ubuntu@${ANSIBLE_SERVER} 'ansible-playbook /home/ubuntu/playbook.yml'"
                }
            }
        }
    }
}
