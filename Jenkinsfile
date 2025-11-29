node {
    stage('SCM') {
        checkout scm
    }

    stage('Maven Clean') {
        def mvn = tool 'Default Maven'
        sh "${mvn}/bin/mvn clean"
    }

    stage('Maven Compile') {
        def mvn = tool 'Default Maven'
        sh "${mvn}/bin/mvn compile"
    }

    stage('SonarQube Analysis') {
        def mvn = tool 'Default Maven'
        withSonarQubeEnv('sonarqube') {
            sh "${mvn}/bin/mvn verify sonar:sonar -Dsonar.projectKey=Devpos -Dsonar.projectName='Devpos'"
        }
    }
}
