pipeline{
  agent any
  stages{
    stage('checkout'){
      steps{
        git url:'https://https://github.com/Srinidhi-Padmanabhan-1/DevOps_course.git',branch:'main'
      }
    }

    stage('Build Image'){
      steps{
        bat 'docker build -t mywebsite .'
      }
  }

    stage('Stop Old Containers'){
      steps{
        bat 'docker stop mycont || exit 0'
        bat 'docker rm mycont || exit 0'
      }
    }

    stage('Run Image - Containerize'){
      steps{
        bat 'docker run -d -p 7000:80 --name mycont mywebsite'
      }
    }
}
}
