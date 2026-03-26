 pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw clean package'
            }
        }

        stage('Verify Jar') {
            steps {
                sh 'ls -l target'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh '''
                JAR_FILE=$(ls target/*.jar | head -n 1)
                curl -v -u admin:Ilovejoji18 \
                  --upload-file "$JAR_FILE" \
                  http://nexus:8081/repository/maven-releases/com/example/app/1.0/app-1.0.jar
                '''
            }
        }
    }
}

