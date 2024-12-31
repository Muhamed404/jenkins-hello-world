pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M398"
    }

    stages {
        stage('Echo Version') {
            steps {
                sh 'echo Print mn Version'
                sh 'mvn -version'
            }
        }
        stage('Build') {
            steps {
               
                sh 'mvn clean package -DskipTests=true'
                archiveArtifacts 'target/hello-demo-*.jar'
            }
        }
        stage('Unit TEST') {
            steps {

                sh 'mvn test'
                junit(testResults:  'target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
            }
            
        }

    }
}
