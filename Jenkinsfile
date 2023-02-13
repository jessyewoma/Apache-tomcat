pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		sh '/usr/share/maven/bin/mvn clean package'
            }
        }
        stage('test') {
            steps {
                echo 'Building..'
		sh '/usr/share/maven/bin/mvn test'
            }
        }
        stage('delopy') {
            steps {
                echo 'Deploying....'
		sshagent(['Deploy-jenkins'])  {
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Apche-tomcat/target/webapp-0.2.war ec2-user@18.212.178.161:/home/ec2-user/apache-tomcat-10.0.27/webapps"
		 }
            }
        }
    }
}
