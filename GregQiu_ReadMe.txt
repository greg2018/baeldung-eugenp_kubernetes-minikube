https://www.baeldung.com/spring-boot-minikube

from (https://github.com/eugenp/tutorials.git):

tutorials\spring-cloud\spring-cloud-kubernetes\kubernetes-minikube

	This tutorials is exercised in git bash

	mvn package -DskipTests

#1) Use minikube's Own Local Docker Images With Minikube
	eval $(minikube -p minikube docker-env)
	
	Reference: 
	How to Use Own Local Docker Images With Minikube
	https://medium.com/bb-tutorials-and-thoughts/how-to-use-own-local-doker-images-with-minikube-2c1ed0b0968
	eval $(minikube docker-env)

#2) Build Backend application/image
	cd /C/UserApps3/kubernetesWorkspaces/baeldung-eugenp_kubernetes-minikube/demo-backend
	
	mvn package -DskipTests
	
	docker build --file=Dockerfile --tag=demo-backend:latest --rm=true .

	kubectl run demo-backend --image=demo-backend:latest --port=8080 --image-pull-policy Never
	  
	kubectl logs demo-backend

	kubectl expose deployment demo-backend --type=NodePort
 
	minikube service demo-backend
 
	kubectl delete service demo-backend
	
	cd /C/UserAppsFive/kubernetes-minikube/object-configurations
 
	kubectl create -f backend-deployment.yaml
  
	kubectl get deployments

#3) Build Frontend application/image

	cd /C/UserApps3/kubernetesWorkspaces/baeldung-eugenp_kubernetes-minikube/demo-frontend
	
	mvn package -DskipTests

	docker build --file=Dockerfile --tag=demo-frontend:latest --rm=true .

	cd /C/UserAppsFive/kubernetes-minikube/object-configurations

	kubectl create -f frontend-deployment.yaml

