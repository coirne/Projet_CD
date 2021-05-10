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
                sh 'cat /root/.ssh/id_rsa.pub'
                sh 'echo "172.17.0.2 ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBMS6WL8HlSrRXcjgLnT6dhDhms367+pqNTvr7NJmfpgtt3vLoCkmJ16MbRKc0+jM4jlGJRfuhGJ3jGwSd4YGDN8=" > /root/.ssh/known_hosts'
                sh 'ansible-playbook -vvvv -i /var/jenkins_home/workspace/Projet_CD/hosts  /var/jenkins_home/workspace/Projet_CD/playbook.yml'
          }
    }
}  
}
