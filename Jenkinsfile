pipeline
{
  agent
  {
    label 'worker'
    customWorkspace '/home/ubuntu'
  }
  stages
  {
    stage ('Testing connection')
    {
      steps
      {
        sh "echo Testing connection"
      }
    }
    stage ('build and run docker container')
    {
      steps
      {
        sh '''
        echo "starting code"
        ls
        cd code
        aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 137756358866.dkr.ecr.us-east-1.amazonaws.com
        docker build -t assign-6 .
        docker tag assign-6:latest 137756358866.dkr.ecr.us-east-1.amazonaws.com/assign-6:latest
        docker push 137756358866.dkr.ecr.us-east-1.amazonaws.com/assign-6:latest
        docker run -itd -p 8081:8081 137756358866.dkr.ecr.us-east-1.amazonaws.com/assign-6:latest
        '''
      }
    }
  }
}
