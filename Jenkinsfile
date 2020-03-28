pipeline {
    agent any

 stages{

   stage('preperation'){

     steps {
       cleanWs()
       git credentialsId: 'github', url: "https://github.com/myfinance/k8ntools.git"
     }
   }

   stage('kubectl'){

     steps {
       sh 'kubectl apply -f .'
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
 }
}


