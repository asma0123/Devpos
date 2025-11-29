pipeline {
    agent any
    tools { maven 'Default Maven' } // correspond à l'installation Maven dans Jenkins
    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/asma0123/Devpos.git', branch: 'main'
            }
        }
        stage('Maven Clean & Compile') {
            steps {
                dir('DevposApp') {
                    sh 'mvn clean compile'
                }
            }
        }
        stage('SonarQube Analysis') {
            steps {
                dir('DevposApp') {
                    withSonarQubeEnv('sonarqube') { // nom de l'installation SonarQube dans Jenkins
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }
    }
}
