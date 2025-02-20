pipeline {
    agent any
    triggers {
        cron('H/3 * * * 4') // Trigger every 3 minutes on Thursdays
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Clean and build the project using Windows command
                    bat '.\\mvnw.cmd package'
                }
            }
        }
        stage('Code Coverage') {
            steps {
                script {
                    // Generate Jacoco code coverage report
                    bat '.\\mvnw.cmd jacoco:report'
                }
            }
        }
    }
    post {
        always {
            // Archive Jacoco coverage report
            archiveArtifacts artifacts: '**/target/site/jacoco/index.html', allowEmptyArchive: true
        }
    }
}
