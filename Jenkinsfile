pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Restore packages'){
           steps{
               sh 'dotnet restore net6-test.sln'
            }
         }
        stage('Clean'){
           steps{
               sh 'dotnet clean net6-test.sln --configuration Release'
            }
         }
        stage('Build'){
           steps{
               sh 'dotnet build net6-test.sln --configuration Release --no-restore'
            }
         }
        stage('Publish'){
             steps{
               sh 'dotnet publish net6-test/net6-test.csproj --configuration Release --no-restore --output /builds/net6-test'
             }
        }
    }
}