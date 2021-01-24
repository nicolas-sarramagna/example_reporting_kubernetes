# example_reporting_kubernetes
example of usages of kubernetes of the reporting projects

## test with minikube
*formatting in progress to add screenshots and addtional details*

1. minikube delete --all
2. minikube start --insecure-registry="registry-1.docker.io"

3. enable the nginx Ingress controller
minikube addons enable ingress

4. wait some minutes, check with the command
kubectl get pods -n kube-system

5. kubectl  apply -f backend-deployment.yaml 

6. check kubectl get pods

7. kubectl  apply -f backend-service.yaml

8. kubectl get services

9. sudo emacs /etc/hosts
add minilube ip 
ex : 192.168.49.2 web-services.k8s.com

10. kubectl  apply -f backend-ingress.yaml
check kubectl get ingress

11. browser http://web-services.k8s.com/api/v1/trend/indicator/tradingview
project web services deployement ok

11. Fill fieds on main-pod.yaml

12. kubectl apply -f main-pod.yaml

13. check kubectl get pods

14. kubectl logs main-app

15. checl mail box 
