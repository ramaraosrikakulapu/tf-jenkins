pipeline {
    agent any
    stages {
        stage('git clone') {
            steps {
                git branch: 'ft-automation-update', url: 'https://github.com/EC-Release/solutions.git'
            }
        }
        stage('prerequisites') {
            steps {
                sh '''
                    pwd && ls -al
                    cd ft/aws2azure
                    pwd && ls -al
                    curl -o terraform.zip https://releases.hashicorp.com/terraform/0.12.19/terraform_0.12.19_linux_amd64.zip
                    unzip -o terraform.zip
                    pwd && ls -al
                    rm -rf terraform.zip
                '''
            }
        }
        stage('init and plan') {
            steps {
                sh '''
                    pwd && ls -al
                    cd ft/aws2azure
                    ./terraform init
                    ./terraform plan
                '''
            }
        }
    }
}
