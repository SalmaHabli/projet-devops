pipeline {
    agent any

    stages {
        stage('Déployer avec Ansible') {
            steps {
                echo 'Exécution du playbook Ansible depuis l’hôte...'
                sh 'bash /home/salma/projet-devops/run-ansible.sh'
            }
        }
    }
}
