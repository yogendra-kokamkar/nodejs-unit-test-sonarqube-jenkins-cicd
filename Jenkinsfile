pipeline {
    agent any
    
    stages {
        stage('Unit Tests') {
            steps {
                // Run npm build to build the React application
                sh '${GRADLE_HOME}/bin/gradle npmTest'
            }
            post {
                always {
                    // Archive test report in HTML format
                    archiveArtifacts 'coverage/lcov-report/**'
                }
            }
        }
        stage('Sonarqube scan'){
            steps{
                //Run Sonar Scan
                sh 'npx sonar-scanner'
            }
        }
        stage('Build'){
            steps {
                // Run npm build to build the React application
                sh '${GRADLE_HOME}/bin/gradle npmBuild'
            }
        }
        stage('Deploy'){
            steps {
                script{
                    def pipelineName = env.JOB_NAME.tokenize('/').last()
                    echo "Running pipeline: ${pipelineName}"
                    // Run npm build to build the React application
                    sh """
                    sed -i "s|root /var.*;|root /var/lib/jenkins/workspace/${pipelineName}/build;|" /etc/nginx/sites-available/default
                    sudo systemctl restart nginx
                    """
                }
            }
        }
    }
}