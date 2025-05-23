pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository (abc)
                echo "Cloning repository jenkins..."
                sh '''
                      mkdir -p /var/lib/jenkins/.ssh
                      ssh-keyscan github.com >> /var/lib/jenkins/.ssh/known_hosts
                      chmod 644 /var/lib/jenkins/.ssh/known_hosts
                    '''
                git branch: 'main', url: 'git@github.com:lizmariababy11/jenkins.git'
            }
        }

        stage('Modify File') {
            steps {
                // Append content to helloworld.sh file
                echo "Copying helloworld.sh to helloworld_modified.sh..."
                sh 'echo "HeyABC" >> helloworld_modified.sh'
            }
        }

        stage('Commit Changes') {
            steps {
                // Set Git user credentials and commit changes
                echo "Committing changes..."
                sh '''
                git config user.name "lizmariababy11"
                git config user.email "lizmariababyj@gmail.com"
                git add helloworld_modified.sh
                git commit -m "Modified helloworld.sh by appending text"
                git push origin main
                '''
            }
        }

        stage('Test') {
            steps {
                // Placeholder for tests
                echo "Running tests..."
                sh 'echo Tests are successful'
            }
        }

        stage('Deploy') {
            steps {
                // Placeholder for deployment
                echo "Deploying..."
            }
        }
    }

    post {
        always {
            echo "Pipeline completed"
        }
    }
}
