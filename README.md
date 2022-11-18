# istio-implementation

## install docker

    apt-get install docker.io
    systemctl start docker
    
## install kubectl

    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
    kubectl version --client
    
## install kind

    curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.17.0/kind-linux-amd64
    chmod +x ./kind
    sudo mv ./kind /usr/local/bin/kind
    
 ## create 2 kind cluster
 
    kind create cluster --name cluster1
    kind create cluster --name cluster2 
    kubectl config get-contexts
    
 ## change api server ip
 
    kubectl config set-cluster "kind-cluster${i}" --server="https://${docker_ip}:6443"
    kubectl config rename-context "kind-cluster${i}" "cluster${i}"
    kubectl config use-context cluster1
    
    
   export PATH=$HOME/.istioctl/bin:$PATH
