pipeline {
     agent any
     stages {
         stage('Echo Hello World') {
              steps {
                  echo "Hello World!"
              }
         }
         stage('Upload to AWS') {
             steps {
                 sh 'echo "Hello AWS"'
                 sh '''
                     echo "Here is multiline shell steps"
                     ls -lah
                 '''
                  withAWS(region:'us-east-2',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-jenkins-pipeline')
                  }
             }
         }
     }
}