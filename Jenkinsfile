pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/wooseulk1/cicdtest1.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t wooseulki/testweb:newnewmain .
        sudo docker push wooseulki/testweb:newnewmain
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth
        sudo kubectl set image deployment deploy-main ctn-main=wooseulki/testweb:newnewmain
        '''
      }
    }
  }
}
