pipeline {
  environment {
    dockerImage = ''
  }
  agent any
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build frontend
        }
      }
    }
    stage('Deploy to ECR') {
      steps{
        script {
          docker.withRegistry( 
            'https://<aws-account-number>.dkr.ecr.<ecr-repository-server>.amazonaws.com', 
            'ecr:<ecr-repository-server>:<jenkins-aws-ID>') {
            def myImage = docker.build('<ecr-repository-name>')
            myImage.push('<tag>')

          }
        }
      }
    }
  
      }
    }
  }
}
