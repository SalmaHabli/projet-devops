pipeline {
    agent any

    environment {
        DOCKER_HOST = "unix:///var/run/docker.sock"
        ANSIBLE_CONFIG = "${WORKSPACE}/ansible/ansible.cfg"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SalmaHabli/projet-devops.git'
            }
        }

        stage('Test Ansible') {
            steps {
                sh '/bin/ansible-playbook --version'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh '''
                    echo "🔹 Lancement du playbook..."
                    /bin/ansible-playbook ansible/deploy-containers.yml -i ansible/hosts
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Déploiement terminé avec succès !'
        }
        failure {
            echo '❌ Échec du déploiement. Vérifiez les logs.'
        }
    }
}

