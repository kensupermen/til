1. Why we need k8s
- Zero downtime deployments
- Monitor resource
- Auto scale
- Load balacing

2. Concepts
 - Running Kubernetes cluster: `minikube start`
Minikube started a virtual machine for you, and a Kubernetes cluster is now running in that VM
- Pods: a group of one or more application containers and includes shared storage(volumes),
IP address and information about how to run them
When you created a `Deployment`, K8s created a Pod to host your application instance
- Node: A pod always run on a Node. A node can have multiple Pods. A Node maybe a VM or physical machine
- Scale an app using `kubectl`
- KBC Deployment: check on the health of Pod and restart Pod's Container if it terminates.

3. Tools
  - Install cluster
    - Local: `Minikube`
    - Production: `Kops`, `kubeadm`, `kubespray`, `conjure-up`
    Note:
      - `kubeadm` in beta, so not recommend for production.
      - `Kops` recommend for AWS
      - To choose a tool which best fits your use case, read this [comparison](https://github.com/kubernetes-incubator/kubespray/blob/master/docs/comparisons.md)

4. Install tools
  - kubectl: `brew install kubectl`
  - Hypervisor:  VirtualBox
  - Minikube: `brew cask install minikube`
  - [Kops] (https://github.com/kubernetes/kops/blob/master/docs/install.md)

5. Step by step
  - First step we need to create cluster. Ex: `minikube start`
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

6. Note
 - By default, pods and services not run on node master, they only run on node minion. If you want to run on node master, you must to run the command bellow:
 ```bash
  kubectl taint nodes --all node-role.kubernetes.io/master-
 ```
 - We need to install network on node master and then the pods can comunicate. 
 Use Weave Net
```bash
  kubectl apply -f https://git.io/weave-kube-1.6
``` 
- Run dashboard:
```bash
  kubectl proxy --address='0.0.0.0' --accept-hosts='^*$'
```

7. References
- https://github.com/hocchudong/ghichep-kubernetes
- https://crondev.com/kubernetes-installation-kubeadm/
- http://kubernetesbyexample.com/nodes/
