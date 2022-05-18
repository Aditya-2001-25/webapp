pipeline {
    agent {
        label 'videopro'
    }
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                bat 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
        stage('Sonar-Report') {
             steps {
                    sh 'mvn clean install sonar:sonar -Dsonar.host.url=http://lpcalhost:9000 -Dsonar.analysis.mode=publish'
                    }
                }
    }
}
