// Jenkinsfile
pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Cloning the Git repository...'
                sh 'ls -la' // Show what's in the workspace after cloning
                // Add some dummy files to your repo later and list them here
            }
        }
        stage('Build Dummy App') {
            steps {
                echo 'Simulating building a dummy application...'
                sh 'echo "This is a dummy build step for my new repo!" > build_output.txt'
            }
        }
        stage('Run Dummy Tests') {
            steps {
                echo 'Simulating running dummy tests...'
                sh 'echo "Dummy tests passed!" >> test_results.txt'
            }
        }
        stage('Archive Artifacts') {
            steps {
                echo 'Archiving dummy artifacts...'
                archiveArtifacts artifacts: 'build_output.txt, test_results.txt', fingerprint: true
            }
        }
    }
    post {
        always {
            echo 'Pipeline run complete!'
        }
        success {
            echo 'All stages completed successfully for your custom repo!'
        }
        failure {
            echo 'Pipeline failed for your custom repo!'
        }
    }
}
