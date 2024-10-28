pipeline {
    agent any
    tools{
        git 'Default'
    }
    stages {
        stage ('GetProject') {
            steps {
                git branch:'main', url:'https://github.com/Chadlikouider/demo_springboot.git'
            }
        }
        stage ('build') {
            steps {
                sh 'mvn clean:clean'
                sh 'mvn dependency:copy-dependencies'
                sh 'mvn compiler:compile'
            }
        }
        stage ('Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage ('Exec') {
            steps {
                sh 'mvn exec:java'
            }
        }
    }
    post{
     success{
         archiveArtifacts allowEmptyArchive: true,
             artifacts:'**/demo_springboot*.jar'
     }   
    }
}
