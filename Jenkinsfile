pipeline {
    agent any

    tools {
        maven 'Default' // Nom de ton installation Maven dans Jenkins
    }

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/asma0123/Devpos.git'
            }
        }

        stage('Maven Clean & Compile') {
            steps {
                dir('DevposApp') { // <-- pointez vers le dossier avec pom.xml
                    sh 'mvn clean compile'
                }
            }
        }

        stage('SonarQube Analysis') {
            environment {
                SONAR_TOKEN = credentials('token') // ton ID des credentials secrets
            }
            steps {
                dir('DevposApp') {
                    sh "mvn sonar:sonar -Dsonar.projectKey=DevposApp -Dsonar.host.url=http://localhost:9000 -Dsonar.login=$SONAR_TOKEN"
                }
            }
        }
    }
}
