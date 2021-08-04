pipeline{
    agent any
    tools{
        gradle 'GradleTool'
    }
    stages{
        stage('clone'){
            steps{
                git branch: 'Haribranch', url:'https://github.com/Harini2196/gradle-build-scan-quickstart.git'
            }
        }
        stage('build'){
            steps{
                sh 'gradle build'
            }
        }
        stage('test'){
            steps{
                sh 'gradle wrapper'
                sh './gradlew test'
                
            }
        }
        stage('Code analysis')
        {
            steps{
               withSonarQubeEnv(installationName: 'sonar-server', credentialsId: 'sonar-creds') {
                   sh './gradlew sonarqube -Dsonar.tests=./build/test-results/test/TEST-example.ExampleTest.xml'
                }
            }
        }
    }
}
