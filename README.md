# tool

pipeline {
    agent any
    environment {
        ANSIBLE_SSH_ARGS = '-o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null'
    }
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/DipanshuRawat/tool.git'
            }
        }
        stage('Install MongoDB') {
            steps {
                ansiblePlaybook credentialsId: '1dfb88aa-b117-42bf-a70a-12e98a81d7d1', disableHostKeyChecking: true, installation: 'ansible', inventory: 'assignment6/aws_ec2.yml', playbook: 'assignment6/installmongo.yml', vaultTmpPath: ''
            }
        }
    }
}

#using pipeline

#
