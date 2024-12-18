pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    environment {
            TARGET_DIR = 'D:\\SupMTI\\TP\\Jenkins\\deploy'   // Le répertoire de destination pour le JAR
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

		stage('Construire package') {
            steps {
                bat 'mvn clean install package'
            }

        }

		stage ('Déployer projet'){
			steps {
			        bat 'copy target\\Springboot-0.0.1-SNAPSHOT.jar D:\\SupMTI\\TP\\Jenkins\\deploy\\Springboot-0.0.1-SNAPSHOT.jar'
			}
		}
		stage ('Démarrer projet'){
            steps {
                bat 'cmd /c "D:\\SupMTI\\TP\\Jenkins\\deploy\\run-springboot.bat"'            }
        }
    }
	post {
		failure {
			echo "le build n'a pas bien passé :( "
		}
	}

}
