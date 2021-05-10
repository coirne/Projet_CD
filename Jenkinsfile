pipeline {
    agent any
    stages {
        stage('SCM') {
        steps {
            git branch: 'main', url: 'https://github.com/coirne/PROJET_CD.git'
            sh 'ls'
              }
        }
        
        stage('Start manager'){
          agent {
              docker { 
                  args '-u 0:0'
                  image 'ahmed24khaled/ansible-management'
                  reuseNode true
              }
              
          }
          steps {
                sh 'echo "172.17.0.2 ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBDmqkTYoZkaSWo/mjuQgkiAwXCpfT6FYUOypwBxZ5Id8E9p0vsUxn57Skk+2ce2ujWQLLMZ+LOaMoBdgbMADOAs=" > /root/.ssh/known_hosts'
                sh 'ansible-playbook -vvvv -i /var/jenkins_home/workspace/Projet_CD/hosts  /var/jenkins_home/workspace/Projet_CD/playbook.yml'
          }
    }
}  
}
