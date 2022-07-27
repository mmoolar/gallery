pipeline { 
  agent any 
  tools{

  nodejs 'NodeJS-18.7.0'

  }

  stages { 
    stage('clone repository') {
      steps { 
        
         // Get some code from a GitHub repository
                git 'https://github.com/mmoolar/gallery.git'
      }
    }
     stage('Build the project') {
      steps { 
        sh 'echo "here we will Build" '
      }
    }
stage('Install Dependencies') {
      steps { 
        sh 'npm install'
      }
    }
    stage('Tests') {
      steps { 
        sh 'npm test'
      }
    }
    stage('Deploy Application') {
      steps {
               withCredentials([usernameColonPassword(credentialsId: 'Jenkins-Heroku-Conn', variable: 'HEROKU_CREDENTIALS' )]){

                    sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/app001-251.git master'
              }
    }
  }
}
}