pipeline {
    agent any

    stages{
        stage('deploy to S3'){
            steps{
               sh "aws configure set region $AWS_DEFAULT_REGION" 
               sh "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"  
               sh "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
               sh 'aws s3 cp public s3://pawan-web --recursive'
               sh 'aws s3api put-bucket-policy --bucket pawan-web --policy file://policy.json'
               sh 'aws s3 website s3://pawan-web/ --index-document index.html --error-document error.html'
             
            }
        }
    }
    
}
