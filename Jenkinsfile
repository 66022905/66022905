pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
                sh "scp -r /var/lib/jenkins/workspace/66022905/* root@43.208.146.8:~/66022905/"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022905/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66022905/playbooks/deploy.yaml'
            }    
        } 
    }
}
