pipeline{
 agent any
 tool {
     maven 'maven'
 }
stages {
    stage ('Build') {
        steps{
            sh 'mvn clean package'
        }
    post{
        success {
            ech0 "Archiving the Artifacts"
            ArchiveArtifacts Artifacts: '**/target/*.war'
         }
        }     
    }
}
stage ('Deploy to tomcat server') {
    steps {
        deploy adapters: [tomcat9(credentialsId: 'apache-tomcat', path: '', url: 'http://35.154.254.156:8080/')], contextPath: null, war: '**/*.war'
    }
}
}