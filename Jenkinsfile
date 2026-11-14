
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Akhila1314/petclinic-cicd-project-akhila.git'
            }
        }

        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw clean package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war',
                                 fingerprint: true
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh '''
                    cp target/petclinic-0.0.1-SNAPSHOT.war \
                    /opt/apache-tomcat-9.0.123/webapps/petclinic.war
                '''
            }
        }
    }
}
