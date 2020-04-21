pipeline {
  agent any

 environment{
   //Snapshot Version
   VERSION = "0.13.0.${BUILD_ID}-RC"
   //Release Version
   //VERSION = "0.13.1.${BUILD_ID}"
 }    

 stages{

   stage('preperation'){

     steps {
       cleanWs()
       git credentialsId: 'github', url: "https://github.com/myfinance/k8ntools.git"
     }
   }

   stage('deploy to cluster'){
     agent any
     steps {
       sh 'envsubst < ./helm/myk8ntools/Chart.yaml | helm upgrade -i --cleanup-on-fail myk8ntools -'
       helm dependency update
       helm upgrade mfbackend .
     }
   }  
 }
}


