pipeline{
    agent any
    stages{
        stage('Code_Checkout'){
          steps{
            checkout([$class: 'GitSCM', branches: [], extensions: [], userRemoteConfigs: [[credentialsId: 'git_cred', url: 'https://github.com/Raja775/angular-realworld-example-app.git']]])  
          }
        }
        stage('npm_build'){
            tools {
             nodejs "nodeJS14"
            }
            steps{
                sh 'npm install'
                sh 'npm run build'
            }
        }
		stage('SonarQube Code Analysis'){
		    tools {
             jdk "JAVA11" 
             nodejs "nodeJS14"
            }
			environment {
				scannerHome = tool 'SonarScanner'
					}
			steps {
				withSonarQubeEnv('SonarCloud')
					{
					sh "${scannerHome}/bin/sonar-scanner -X -Dsonar.projectKey=sonarqube-tesing1 -Dsonar.login=f470d5786118c2bd0edf99f9af610aec3d331eaf -Dsonar.projectName=sonarqube-tesing1 -Dsonar.host.url=https://sonarcloud.io/ -Dsonar.sourceEncoding=UTF-8 -Dsonar.organization=sonarqube-test1 -Dsonar.sources=src/"
				}
			}
		}
		//stage('JUnit Test Cases'){
      //      tools {
        //    }
          //  steps{
                
            //}
        //}
    }
}
