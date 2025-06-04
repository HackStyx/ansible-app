pipeline{
	agent any
	tools{
		maven 'Maven'
	}
	stages{
		stage('checkout'){
			steps{
				git 'https://github.com/HackStyx/ansible-app.git'
			}
		}
		stage('build'){
			steps{
				sh 'mvn clean install'
			}
		}
		stage('archive'){
			steps{
				archiveArtifacts artifacts: 'target/*.war',fingerprint:true
			}
		}
		stage('deploy'){
			steps{
				ansiblePlaybook playbook:'ansible/deploy.yml', inventory:'ansible/hosts.ini'
			}
		}
	}
}
