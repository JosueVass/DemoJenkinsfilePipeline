pipeline {
	agent any
	
	stages {
		stage ('Build') {
			steps {
				git 'https://github.com/JosueVass/DemoPipeline.git'
			    
			    bat 'mvn clean'
				bat 'mvn -B compile'
			}
		}
		stage ('Test') {
			steps {
				bat 'mvn test'
			}
			post {
				success {
				    echo "Terminó exitosamente"
				}
				failure {
				    echo "Terminó con error"
				}
				always {
				    junit 'target/surefire-reports/*.xml'
				}
			}
		}
		stage ('Package') {
			steps {
			    echo "Se ha empaquetado la aplicación"
				bat 'mvn package'
			
				archiveArtifacts 'target/*.jar'
			}
		}
	}
}
