# k8ntools

## prequesit

kubernetes server is installed see repository mfinfra and jenkins runs on kubernetes see repo myjenkins

## setup

go to http://{kuberneteshost}:31000/ and run the job for this repo 
or run the commands described in the Jenkinsfile on the kuberneteshost
or install the helm chart directly from nexus: helm upgrade -i --cleanup-on-fail myk8ntools local/myk8ntools --set stage=prod --devel


add all the localdomains from the ingress file to your dns-server (e.G. /etc/hosts or Sophos/network/dns)

