// pipeline {
//   agent any
//   stages {
//     stage('git scm update') {
//       steps {
//         git url: 'https://github.com/PSH989898/jenkintest.git', branch: 'master'
//       }
//     }
//     stage('docker build and push') {
//       steps {
//         sh '''
//         sudo docker build -t pshhhhh98/keduitlab:yello .
//         sudo docker push pshhhhh98/keduitlab:yello
//         '''
//       }
//     }
//     stage('deploy and service') {
//       steps {
//         sh '''
//         sudo kubectl apply -f testpod.yml
//         '''
//       }
//     }
//   }
// }
pipeline {
  agent any
  stages {
    stage('Deploy Docker Image on Master') {
      environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
        ANSIBLE_PRIVATE_KEY_FILE = '/var/lib/jenkins/.ssh/ansible_key'
      }
      steps {
        sh '''
        ansible-playbook -i /etc/ansible/hosts /var/lib/jenkins/workspace/ansible/playbook.yml
        '''
      }
    }
  }
}
