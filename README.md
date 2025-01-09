# E-commerce-k8 Deployment
------------------------------------------------------------------------------------------------------

## Project Overview
This project demonstrates a Kubernetes-based deployment for an e-commerce website, providing scalable and reliable infrastructure.

## Prerequisites
- Kubernetes Cluster
- Docker
- kubectl
- Docker Hub Account

## Project Structure


E-commerce-k8/
 
 ├── deployment.yaml
 ├── service.yaml
 ├── Dockerfile

###
     docker build -t Suresh202/E-commerce-k8:v1 .
     docker push Suresh202/E-commerce-k8:v1


###  Kubernetes Deployment

     kubectl apply -f k8s/deployment.yaml
     kubectl apply -f k8s/service.yaml
     kubectl apply -f k8s/ingress.yaml

### sudo nano ingress.yaml

     apiVersion: networking.k8s.io/v1
     kind: Ingress
     metadata:
          name: ecommerce-ingress
     annotations:
         kubernetes.io/ingress.class: nginx
         nginx.ingress.kubernetes.io/rewrite-target: /
     spec:
       rules:
       - host: "e-commerce.chickenkiller.com"                       --------ip of minikube (check with minikube ip) point to dns (on website free dns write on web browser)
       http:
       paths:
      - pathType: Prefix
        path: "/"                                               --------------- this is root path of website like:index.html
        backend:
          service:
            name: ecommerce-service                              ---------check service (minikube service list) & name of service put here
            port:
              number: 80




     



## Features
- Scalable Kubernetes Deployment
- 3 Replica Pods
- LoadBalancer Service
- Resource-managed Containers

## Monitoring

     kubectl get deployments
     kubectl get pods
     kubectl get services

     
## Scaling

    kubectl scale deployment ecommerce-deployment --replicas=5



## Troubleshooting
- Check pod logs: `kubectl logs <pod-name>`
- Verify service status: `kubectl describe service ecommerce-service`

## Environment Variables
Configure in `deployment.yaml`:

env:

    name: DATABASE_URL
    value: "your-database-connection-string"

## Security Recommendations
- Use Kubernetes Secrets
- Implement Network Policies
- Regular image scanning

## Performance Tuning
- Adjust resource limits
- Implement horizontal pod autoscaler
- Use persistent volumes for stateful components

## Contributing
1. Fork Repository
2. Create Feature Branch
3. Commit Changes
4. Push to Branch
5. Create Pull Request

## License
MIT License

## Contact
Suresh beniwal
beniwalsuresh117@gmail.com

    
