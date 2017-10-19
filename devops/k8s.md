1. Why we need k8s
- Zero downtime deployments
- Monitor resource
- Auto scale
- Load balacing

2. Concept
 - Running Kubernetes cluster: `minikube start`
Minikube started a virtual machine for you, and a Kubernetes cluster is now running in that VM
- Pods: a group of one or more application containers and includes shared storage(volumes),
IP address and information about how to run them
When you created a `Deployment`, K8s created a Pod to host your application instance
- Node: A pod always run on a Node. A node can have multiple Pods
- Scale an app using `kubectl`
- KBC Deployment: check on the health of Pod and restart Pod's Container if it terminates.

3. Tools
 - Local: `Minikube`
 - Production: `Kops`, `kubeadm`, `kubespray`
 To choose a tool which best fits your use case, read this [comparison](https://github.com/kubernetes-incubator/kubespray/blob/master/docs/comparisons.md)

4. Install tool
  - kubectl: `brew install kubectl`
  - Hypervisor:  VirtualBox
  - Minikube: `brew cask install minikube`
  - [Kops] (https://github.com/kubernetes/kops/blob/master/docs/install.md)

5. Step by step
  - First step: always run `minikube start`
  - Reusing the Docker daemon: `eval $(minikube docker-env)`
  - Create deployment: `kubectl run hello-node --image=hello-node:v1 --port=8080`
  - Create service: `kubectl expose deployment hello-node --type=LoadBalancer`
    Type of service:
      - LoadBalancer
      - NodePort
      - ClusterIP
  - Show logs: `kubectl logs --tail=-1 backend`
  - Open service on browser: `minikube service nginx`

  - Kubernetes configmap:
    - Create: 
      `kubectl create configmap masterclass-backend-config \
      --from-literal=postgres_user=geeker \
      --from-literal=postgres_host=$(minikube ip) \
      --from-literal=rails_log_to_stdout=true`
    - Edit 
      `kubectl edit configmap masterclass-backend-config`

  - Rake database
    `kubectl exec backend-a12 rake db:setup`

