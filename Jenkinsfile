node {
    stage('SCM') {
        checkout scm
    }
    stage('SonarQube Analysis') {
        def mvn = tool 'Default Maven';
        withSonarQubeEnv() {
            sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=Devpos -Dsonar.projectName='Devpos' -Dsonar.login=squ_648ff9da2f9b2824d303395294c10a4aff843797"
        }
    }
}
