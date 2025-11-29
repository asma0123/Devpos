node {
    stage('SCM') {
        // Récupère le code depuis Git
        checkout scm
    }

    stage('Maven Clean') {
        // Utilise Maven installé sur Jenkins
        def mvn = tool 'Default Maven'
        sh "${mvn}/bin/mvn clean"
    }

    stage('Maven Compile') {
        def mvn = tool 'Default Maven'
        sh "${mvn}/bin/mvn compile"
    }

    stage('SonarQube Analysis') {
        def mvn = tool 'Default Maven'
        // Remplace 'sonarqube' par le même nom que dans Jenkins Configure System
        withSonarQubeEnv('sonarqube') {
            // Utilise ton token pour l'authentification
            sh "${mvn}/bin/mvn verify sonar:sonar -Dsonar.projectKey=Devpos -Dsonar.projectName='Devpos' -Dsonar.login=squ_648ff9da2f9b2824d303395294c10a4aff843797"
        }
    }
}
