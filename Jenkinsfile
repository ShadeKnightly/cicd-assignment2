pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo 'Building the application...'
                sh 'npm install'
            }
        }
        stage('Test'){
            steps{
                echo 'Running tests...'
                sh 'npm test'
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploying the application...'
                
                // Deployment steps
                sh 'npx netlify-cli deploy --prod --dir=build --site=$NETLIFY_SITE_ID --auth=$NETLIFY_TOKEN'
            }
        }
    }
}