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
    agent {
        docker {
            image 'lachlanevenson/k8s-helm:latest' 
        }
     }
     steps {
       sh 'helm dependency update ./helm/myk8ntools'
       sh 'envsubst < ./helm/myk8ntools/Chart.yaml | helm upgrade -i --cleanup-on-fail myk8ntools -'
     }
   }  
 }
}
 
   //stage('kubectl'){
   // agent {
   //     docker {
   //         image 'lachlanevenson/k8s-kubectl:v1.8.8' 
    //        args '-p 3000:3000' 
    //    }
    //}
   //  steps {
  //     sh 'kubectl apply -f .'
   //  }
  // } 
  // stage('helm'){
  //  agent {
  //      docker {
  //          image 'lachlanevenson/k8s-helm:latest' 
  //          args '-p 3000:3000' 
  //      }
  //  }
  //   steps {
  //     sh 'helm install monitoring stable/prometheus-operator --namespace default --set grafana.adminPassword=vulkan'
  //   }
  // }      

