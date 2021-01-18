pipeline {

  agent {
    label 'manager'
  }

  stages {
    stage ('Test Pipeline 3') {
      steps {
        echo "Show Docker"
        sh '''
          docker --version
          docker image ls

          echo "You can do docker-compose, and other command here!!"
        '''
        }
      }
       stage ('Docker Stack Deploy') {
        steps {
          echo "Deploying Services"
          script{
            def files = findFiles(glob: '**.yml')
            def command = "docker stack deploy "
            files.each {
              echo "${files}"
              command += "-c ${files} "
            }
            command += "future"
            echo "${command}"
            sh (script: "${command}", returnStdout: true)
        }
      }
    }
  }
}
