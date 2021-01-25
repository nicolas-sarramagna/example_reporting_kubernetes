# Example of usages of Kubernetes : deployment, service, expose with Ingress, secret, Pod

Example of usages of kubernetes with the reporting projects 
[reporting_web_services](https://github.com/nicolas-sarramagna/example_reporting_web_services) and 
[reporting_main](https://github.com/nicolas-sarramagna/example_reporting_main).

# Test with minikube
Open a terminal, install minikube if not -> [link minikube installation guide](https://kubernetes.io/fr/docs/tasks/tools/install-minikube/)

# Start the cluster
To avoid issue with the pulling of images from Docker, a (speed) workaround is to start with a fresh minikube cluster with the insecure-registry option.

So, type **minikube delete --all** then **minikube start --insecure-registry="registry-1.docker.io"**

# Enable Ingress controller
To check the deployment of the web services, we will expose it outside of the cluster. 

So, type **minikube addons enable ingress** to enable the nginx Ingress controller.

Wait a little, then chek with the command **kubectl get pods -n kube-system**, we will see that the Pod *ingress-nginx-controller* is Running.

to add screenshot

# Deploy the reporting web sevices
This web service comes from the projet [reporting_web_services](https://github.com/nicolas-sarramagna/example_reporting_web_services).

## Create the deployment
Type **kubectl  apply -f backend-deployment.yaml** then check with **kubectl get pods**

Wait for the Running status.

o add screenshot

## Create the service
Type **kubectl  apply -f backend-service.yaml**, check with **kubectl get services**

# Expose the web services
We need an url to expose the web service, we choose *web-services.k8s.com*.

## Map the url 
Type **minikube ip** to know ip of your minikube cluster.

Then, edit the file */etc/hosts* and add the line 
192.168.49.2 web-services.k8s.com

In my case, 192.168.49.2 is the ip of my cluster.

## Expose the url
Type **kubectl  apply -f backend-ingress.yaml**, check with **kubectl get ingress**

## Test the url
For example, type **curl http://web-services.k8s.com/api/v1/trend/indicator/tradingview** or copy url in a browser.

The endpoints of this web service are described [here](https://github.com/nicolas-sarramagna/example_reporting_web_services).

The web services is now ON !

11. Fill fieds on main-pod.yaml

12. kubectl apply -f main-pod.yaml

13. check kubectl get pods

14. kubectl logs main-app

15. checl mail box 
