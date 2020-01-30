pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		sh 'mvn package'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
	stage('Sonarqube') {
   	 environment {
                scannerHome = tool 'SonarqubeScanner'
          }
        steps {
          withSonarQubeEnv('sonarqube') {
            sh 'mvn sonar:sonar'
          }
          timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
          }
        }
	}
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
