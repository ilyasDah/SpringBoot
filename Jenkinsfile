pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    environment {
            DEPLOY_DIR = 'D:\\SupMTI\\TP\\Jenkins\\deploy'   // Le répertoire de destination pour le JAR
            TARGET_DIR = 'C:\\Users\\IlyasDahhane\\.jenkins\\workspace\\SpringBoot\\target'   // Le répertoire de destination pour le JAR
    }

    stages {
		stage('Checkout from git') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/ilyasDah/SpringBoot.git'
            }

        }
        stage('Compile code') {
            steps {
                bat 'mvn compile'
            }
		
        }
		stage('build code') {
            steps {
                bat 'mvn clean install'
            }
		
        }
		
		stage('Construire package') {
            steps {
                bat 'mvn clean package'
            }
		
        }

		stage ('Démarrer projet'){
			steps {
			        bat 'copy "${TARGET_DIR}\\Springboot-0.0.1-SNAPSHOT.jar" "${DEPLOY_DIR}\\Springboot-0.0.1-SNAPSHOT.jar"'
                    bat 'start java -jar "${DEPLOY_DIR}\\Springboot-0.0.1-SNAPSHOT.jar"'
			}
		}
    }
	post {
		failure {
			echo "le build n'a pas bien passé :( "
		}
	}
	
}
