pipeline {
    agent any
 
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven"
    }
    stages {
        stage('Gitcheckout') {
            steps {
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Tokencredentials', url: 'https://github.com/Vijay4535515/first.git']])
        }
        }
       stage('build') {
            steps {
             bat 'mvn -f pom.xml clean install -DskipTests'
        }
        }
        stage('deploy') {
            steps {
             deploy adapters: [tomcat8(credentialsId: 'TomcatCredentials', path: '', url: 'http://localhost:8000/')], contextPath: 'first', war: '**/*.war'
        }
        }

}
}



