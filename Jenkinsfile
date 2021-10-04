pipeline {
    agent any

    stages {
        
		stage ('Clean workspace') {
			steps {
				cleanWs()
			}
		}
		
        
		stage ('Git Checkout') {
			steps {
			  git branch: 'main', url: 'https://github.com/MuhammadBashir/dotnet-cicd.git'
			}
		  }
		
        stage('Restore packages') {
			steps {
				sh "dotnetRestore \"C:\\Muhammad Bashir\\Projects\\Jenkins\\dotnet-cicd\\CICD Test.sln\""
			}
		}
				
    }
}