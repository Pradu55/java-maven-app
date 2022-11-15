pipeline {
	agent any
	tools {
		maven 'maven-3.8.6'
	}
	stages {
		stage('build') {
			steps {
				sh 'mvn -B -DskipTests clean install'
			}
		}
		stage('test') {
			steps {
				sh 'mvn test'
			}
			post {
				always {
					junit 'target/surefire-reports/*.xml'
				}
				success {
					sh 'echo "This is a success block"'
				}
				Failure {
					sh 'echo "build failed"'
				}
			}
		}
	}
}
