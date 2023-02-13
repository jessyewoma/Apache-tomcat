pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		sh 'mvn clean package'
            }
        }
        stage('test') {
            steps {
                echo 'Building..'
		sh 'mvn test'
            }
        }
        stage('starting Ansible deployment') {
            steps {
                echo 'Deploying....'
		ansiblePlaybook become: true, credentialsId: 'Ansible', disableHostKeyChecking: true, installation: 'ansible', inventory: 'host.inv', playbook: 'javas.yml'
            }
        }
    }
}
