pipeline {
    agent {
        label "ansible_docker"
    }

    stages {
        stage('prepare_node') {
            steps {
                git 'https://github.com/Bora2k3/example-playbook.git'
                sh 'ansible-vault decrypt secret --vault-password-file vault_pass'
                sh 'mkdir ~/.ssh/ && mv ./secret ~/.ssh/id_rsa && chmod 400 ~/.ssh/id_rsa'
                sh 'ansible-galaxy install -r requirements.yml -p roles'
                sh 'ansible-playbook site.yml -i inventory/prod.yml'
            }
        }
    }
}
