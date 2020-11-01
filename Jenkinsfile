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
                sh "curl -o terraform.zip https://releases.hashicorp.com/terraform/0.12.19/terraform_0.12.19_linux_amd64.zip"
                sh "unzip -o terraform.zip"
                sh "pwd && ls -al"
                sh "rm -rf terraform.zip"
                sh "curl -sL https://aka.ms/InstallAzureCLIDeb | bash"
            }
        }
        stage('init and plan') {
            steps {
                sh "terraform init"
                sh "terraform plan"
            }
        }
    }
}
