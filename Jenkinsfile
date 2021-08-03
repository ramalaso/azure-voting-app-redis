pipeline {
   agent any
   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Docker Build') {
         steps {
            script {
               def branch = readFile('branch').trim()
               if (branch == master) {
                  sh(script: 'docker images -a')
                  sh(script: """
                  cd azure-vote/
                  docker images -a
                  docker build -t jenkins-pipeline .
                  docker images -a
                  cd ..
               """)
            }
            }
         }
      }
   }
}
