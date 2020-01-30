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
   	 
        steps {
             sh 'mvn package sonar:sonar'
         
         
        }
	}
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
