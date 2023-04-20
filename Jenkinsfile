pipeline {
  agent any
  environment{
    img=("${env.JOB_NAME}:${env.BUILD_ID}")
  }
  stages {
    stage('Checkout Code') {
      steps {
        echo "Checkout"
        git branch: 'main', url: 'https://github.com/kss7/SmartFlaskAPP.git'
        sh 'ls -l'
      }
    }
    stage('Build') {
      steps{
        echo "Build Image"
        script{
          dockerimg = docker.build("${img}")

        }
      }
    }
    stage('Run images') {
      steps{
        echo "Run images"
        script{
          dockerimg = docker.image("${img}").run('-d -p 5000:5000')

        }
      }
    }
    stage('Code Coverage') {
      steps{
        echo "Code Coverage"
      }
    }
  }
}
