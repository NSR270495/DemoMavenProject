pipeline{
  agent any
}
  stages{
    stage('Get Code'){
      steps{
        git url:"https://github.com/NSR270495/DemoMavenProject.git"
      }
    }
    stage{
      steps('Build'){
        sh "docker build -t naveen047/DemoMavenProject"
      }
    }
    stage{
      steps{
        script{
          withCredentials([usernameColonPassword(credentialsId: 'Docker-Credential-latest', variable: 'Docker-Credential')]) {
            sh "docker login -u naveen047 -p ${Docker-Credential}"
          }
            sh "docker push naveen047/DemoMavenProject"
        }
      }
    }
  }
