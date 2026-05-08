pipeline {
    agent any

    tools {
        jdk 'JDK11'
        gradle 'Gradle'
    }

    stages {

        stage('Checkout SCM') {
            steps {
                git branch: 'master',
                url: 'https://github.com/karthikvishwanath21-dev/MyGradleApp.git'
            }
        }

        stage('Verify Files') {
            steps {
                sh 'echo "Current Directory:"'
                sh 'pwd'

                sh 'echo "Project Files:"'
                sh 'ls -la'

                sh 'echo "settings.gradle content:"'
                sh 'cat settings.gradle'

                sh 'echo "build.gradle content:"'
                sh 'cat build.gradle'
            }
        }

        stage('Build') {
            steps {
                sh 'gradle clean build'
            }
        }

        stage('Test') {
            steps {
                sh 'gradle test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'gradle run'
            }
        }
    }

    post {
        always {
            echo 'Pipeline Execution Completed'
        }

        success {
            echo 'Build Successful'
        }

        failure {
            echo 'Build Failed'
        }
    }
}
