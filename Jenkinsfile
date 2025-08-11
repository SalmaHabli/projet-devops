pipeline {
    agent any

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
                sh '/bin/ansible-playbook ansible/deploy-containers.yml -i ansible/hosts'
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

