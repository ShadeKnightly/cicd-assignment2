pipeline{
    agent any

    tools{
        nodejs 'Node20'
    }

    environment{
        NETLIFY_SITE_ID = credentials('NETLIFY_SITE_ID')
        NETLIFY_TOKEN = credentials('NETLIFY_TOKEN')
    }
    stages{
        stage('Build'){
            steps{
                echo 'Building the application...'
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Test'){
            steps{
                echo 'Running tests...'
                sh 'npm test -- --watchAll=false'
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