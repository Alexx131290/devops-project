pipeline {
    agent any
    environment {
        ANSIBLE_SERVER = "172.31.1.94"
    }
    stages {
        stage("Deploy") {
            steps {
                sshagent(['ansible-server']) {
                    // 1. PRIMERO: Copiamos los archivos de Jenkins hacia la maquina Ansible
                    sh "scp -o StrictHostKeyChecking=no playbook.yml Deployment.yml Service.yml ubuntu@${ANSIBLE_SERVER}:/home/ubuntu/"
                    
                    // 2. LUEGO: Ahora si ejecutamos el playbook (que ya existe alla)
                    sh "ssh -o StrictHostKeyChecking=no ubuntu@${ANSIBLE_SERVER} 'ansible-playbook /home/ubuntu/playbook.yml'"
                }
            }
        }
    }
}
