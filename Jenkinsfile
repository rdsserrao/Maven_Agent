pipeline {
    agent {
            label "mvn"
    }
    
        stages {
                stage ('Sonar') {
                    steps {
                        withSonarQubeEnv('Sonarqube') {
                            sh 'mvn clean package sonar:sonar'
                        }
                    }
                }
                stage ('Qualidade Código') {
                    steps {
                    waitForQualityGate abortPipeline: true
                    }
                }
                stage('Clean') {
                    steps {
                        cleanWs()
                    }
                }
       }
}
