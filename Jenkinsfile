pipeline {
    agent any
    
    tools{
        maven 'mvn_3.1'
        jdk 'localjdk'
    }
    
    stages {
        
        stage('Checkout'){
            steps {
                cleanWs()
                git 'https://github.com/zielotechgroup/maven-standalone-app.git'
            }
        }
        
        stage('Build'){
            steps {
                sh 'mvn -DskipTests clean package'
            }
            post {
                failure {
                    archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
                }
            }
        }
        
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        
        
    }
}
