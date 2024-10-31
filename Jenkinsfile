pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/PSH989898/jenkintest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t pshhhhh98/keduitlab:green .
        sudo docker push pshhhhh98/keduitlab:green
        '''
      }
    }
    stage('deploy and service') {
      steps {
        sh '''
        sudo kubectl apply -f testpod.yml
        '''
      }
    }
  }
}
