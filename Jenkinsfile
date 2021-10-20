pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('clone scm'){
            steps{
                git 'https://github.com/narendrakumar998931/pipeline-ansible-httpd.git'
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean install -DskipUnitTest'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('test useing checkstyle'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('ansible playbook excute'){
            steps{
                script{
                    ansiblePlaybook credentialsId: 'ansible-node-10.1.2.120', disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'httpd.yml'
                }
            }
        }
    }
}
