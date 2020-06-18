  #The prometheus file is from a integrated project built by coreos.
  #So the first step is to clone the project through github.
  input: git clone https://github.com/coreos/kube-prometheus.git
  
  #For the difficulty to change the orgin codes in the project, we have to delete all the file about grafana in that project(The grafana of that project can't expose its own database.).
  
  #After that, we can deploy this project to our kubernetes group by the orders in the following.
  
  input: kubectl create -f manifests/setup    #deploy the crd and namespace of prometheus
  input: kubectl create -f manifests/         #deploy all the other components like alertmanager, adapter and so on.
  
  
  #However, the prometheus still havs no authority to gain data from istio or access istio.
  
 input: kubectl create -f rbac.yaml # add endpoint
 input: kubectl create -f serviceMonitoring.yaml # set up monitoring settings
 
 #The two orders above should be done after istio deployment.
  
