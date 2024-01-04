pipeline {
    agent any

    stages {
        stage('Clone Terraform Repo') {
            steps {
                echo 'Hello World'
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/aws-ia/terraform-aws-eks-blueprints.git']]])
                        }}
        stage('Terraform provision') {
            steps {
                sh """
                    cd patterns/multi-tenancy-with-teams/
                    terraform init
                    export AWS_REGION=us-east-1
                    terraform plan
                    terraform apply --auto-approve
                """
            }
        }
        
        
    }
}
