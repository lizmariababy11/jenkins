pipeline {
    agent any

    stages {
        stage('Stage 1 - Build') {
            steps {
                script {
                    try {
                        echo "Running build step..."
                        sh 'exit 1' 
                    } catch (e) {
                        echo "Stage 1 failed: ${e}"
                        currentBuild.result = 'UNSTABLE'
                    }
                }
            }
        }

        stage('Stage 2 - Test') {
            steps {
                script {
                    try {
                        echo "Running tests..."
                        sh 'echo Tests are successful'
                    } catch (e) {
                        echo "Stage 2 failed: ${e}"
                    }
                }
            }
        }

        stage('Stage 3 - Deploy') {
            steps {
                script {
                    try {
                        echo "Deploying..."
                        sh 'exit 2'
                    } catch (e) {
                        echo "Stage 3 failed: ${e}"
                    }
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline completed (some stages may have failed.refer logs)."
        }
    }
}
