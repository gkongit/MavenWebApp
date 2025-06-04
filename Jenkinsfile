pipeline {
	agent any
	
	tools {
		maven 'Maven'
	}
	
	stages {
		stage('Checkout') {
			steps {
				git branch: 'main', url: 'https://github.com/gkongit/MavenWebApp.git'
			}
		}
		
		stage('Build') {
			steps {
				sh 'mvn clean install'
			}
		}
		
		stage('Archive') {
			steps {
				archiveArtifacts artifacts: 'target/*.war', fingerprint: true 
			}
		}
		
		stage('Deploy') {
			steps {
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
			}
		}
	}
}
