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
    stage('git scm update') {
      steps {
        git url: 'https://github.com/beomtaek78/jenkinstest.git', branch: 'main'
      }
    }
    stage('delivery and deployment') {
      steps {
        sh '''
        ansible master -m copy -a "src=testpod.yml dest=/root/testpod.yml" --become
        now=$(date +%y%m%d%H%M)
        sudo docker build -t pshhhhh98/keduitlab:${now} .
        sudo docker push pshhhhh98/keduitlab:${now}
        ansible node -m shell -a "sudo docker pull pshhhhh98/keduitlab:${now}"
        ansible master -m shell -a "sudo kubectl create deploy web-${now} --replicas=3 --port=80 --image=pshhhhh98/keduitlab:${now}"
        ansible master -m shell -a "sudo kubectl expose deploy web-${now} --type=LoadBalancer --port=80 --target-port=80 --name=web-${now}-svc"
        '''
      }
    }
  }
}
