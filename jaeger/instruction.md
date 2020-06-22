#these files are used for deploy jaeger, zipkin and their exposed elasticssearch database.

#set up the config of jaeger

input: kubectl apply -f config.yaml -n kube-system

#deploy the elasticsearch data base and its password and username

input: kubectl create -f es-stateful.yaml 

input: kubectl create -f es-service.yaml

