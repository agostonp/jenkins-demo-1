pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
//         stage('Security Scan') {
//              steps { 
//                 aquaMicroscanner imageName: 'alpine:latest', notCompleted: 'exit 1', onDisallowed: 'fail'
//              }
//         }         
         stage('Deliver for development') {
            when {
                branch 'development'
            }
            steps {
                 sh 'echo "Delivery to development steps come here"'
            }
         }
         stage('Deliver for testing to staging') {
            when {
                branch 'staging'
            }
            steps {
                 sh 'echo "Deliver for testing to staging steps come here"'
            }
         }
         stage('Deploy for production') {
            when {
                branch 'deployment'
            }
            steps {
                 sh 'echo "Deploy for production steps come here"'
            }
         }
        //  stage('Upload to AWS') {
        //       steps {
        //           withAWS(region:'us-east-2',credentials:'aws-static') {
        //           sh 'echo "Uploading content with AWS creds"'
        //               s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-jenkins-pipeline')
        //           }
        //           sh 'echo "Why is this step here? Upload to AWS"'
        //       }
         }
     }
}
