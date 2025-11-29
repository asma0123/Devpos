node {
    stage('SCM') {
        checkout scm
    }

    stage('Maven Clean') {
        def mvn = tool 'Default Maven'
        dir('DevposApp') { // On se place dans le sous-dossier du projet Maven
            sh "${mvn}/bin/mvn clean"
        }
    }

    stage('Maven Compile') {
        def mvn = tool 'Default Maven'
        dir('DevposApp') {
            sh "${mvn}/bin/mvn compile"
        }
    }

    stage('SonarQube Analysis') {
        def mvn = tool 'Default Maven'
        dir('DevposApp') {
            withSonarQubeEnv('sonarqube') {
                sh "${mvn}/bin/mvn verify sonar:sonar -Dsonar.projectKey=Devpos -Dsonar.projectName='Devpos'"
            }
        }
    }
}
