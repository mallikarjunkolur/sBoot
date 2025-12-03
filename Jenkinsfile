pipeline {
    agent any
 triggers {
    pollSCM('*/2 * * * *')   // every 2 minutes
  }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/mallikarjunkolur/sBoot.git'
            }
        }
stage('clean') {
steps {
sh 'mvn clean'
}
}
stage('compile') {
steps {
sh 'mvn compile'
}
}
stage('test') {
steps {
sh 'mvn test'
}
}
stage('build') {
steps {
sh 'mvn clean install'
}
}
stage('package') {
steps {
sh 'mvn package'
}
}
}
post {
success {
archiveArtifacts artifacts: 'target/*.jar, target/*.war', fingerprint: true
}
failure {
echo "build failed"
}
}
}

