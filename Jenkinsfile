pipeline {
  agent any

 environment{
   //Snapshot Version
   VERSION = "0.13.0-alpha.${BUILD_ID}"
   //Release Version
   //VERSION = "0.13.0"
   K8N_IP = "192.168.100.73"
   NEXUS_URL = "${K8N_IP}:31001"
   TARGET_HELM_REPO = "http://${NEXUS_URL}/repository/myhelmrepo/"
 }    

 stages{

   stage('preperation'){
     steps {
       cleanWs()
       git credentialsId: 'github', url: "https://github.com/myfinance/k8ntools.git"
     }
   }

   stage('deploy to cluster'){
     steps {
       sh 'envsubst < ./Chart_template.yaml > ./helm/myk8ntools/Chart.yaml'
       sh 'less ./helm/myk8ntools/Chart.yaml' 
       sh 'helm dependency update ./helm/myk8ntools'
       sh 'helm upgrade -i --cleanup-on-fail myk8ntools ./helm/myk8ntools'
       sh 'helm package helm/myk8ntools -u -d helmcharts/'
       sh 'curl -u admin:vulkan ${TARGET_HELM_REPO} --upload-file myk8ntools-${VERSION}.tgz -v'
     }
   }  
 }
}
 
   

