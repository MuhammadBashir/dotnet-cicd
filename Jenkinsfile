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
				bat "dotnet restore \"C:\\Muhammad Bashir\\Projects\\Jenkins\\dotnet-cicd\\CICD Test.sln\""
			}
		}
		
		stage('Build') {
			steps {
				bat "dotnet build \"C:\\Muhammad Bashir\\Projects\\Jenkins\\dotnet-cicd\\CICD Test.sln\" --configuration Release"
			}
		}
		
		stage('Publish') {
			steps {
				bat "dotnet publish \"C:\\Muhammad Bashir\\Projects\\Jenkins\\dotnet-cicd\\CICD Test.sln\" --configuration Release"
			}
		}
		
		stage('Zip') {
			steps {
				bat "tar.exe -a -c -f \"C:\\Muhammad Bashir\\Projects\\Published Sites\\CICD Web.zip\" -C \"C:\\Muhammad Bashir\\Projects\\Jenkins\\dotnet-cicd\\CICD Test\\bin\\Release\\netcoreapp3.1\\publish\" *.*"
			}
		}
		
		stage('Deploy') {
			steps {
				bat "\"C:\\Program Files (x86)\\IIS\Microsoft Web Deploy V3\\msdeploy.exe\" -source:package=\"C:\\Muhammad Bashir\\Projects\\Published Sites\\CICD Web.zip\" -dest:contentPath='CICD' -verb:sync -allowUntrusted"
			}
		}
				
    }
}