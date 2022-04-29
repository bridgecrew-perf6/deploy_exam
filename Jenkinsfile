pipeline {
  agent any



  stages {
    stage('Copy artifact') {
      steps {
        copyArtifacts filter: 'main.rb', fingerprintArtifacts: true
      }
    }
    stage('Deliver') {
      steps {
        sshagent(['cloud']) {
          sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i cloud.ini playbook.yml'
        }
 
      }
    }
   
  }
}
