# KUBECTL

## Install
Full instructions can be found https://kubernetes.io/docs/tasks/tools/install-kubectl/

### Ubuntu/Debian

```
sudo apt-get update && sudo apt-get install -y apt-transport-https
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

or through snap 

```
snap install kubectl --classic
```

### Mac OSX 
use homebrew for easiest install

```
brew install kubectl 
```
or 
```
brew install kubernetes-cli
```

### Windows
Identify the latest stable version (for example, for scripting), take a look at https://storage.googleapis.com/kubernetes-release/release/stable.txt. Currently 1.17

Then use curl to download the binry or download it directly
```
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.17.0/bin/windows/amd64/kubectl.exe
```
Add the binary in to your PATH. "C:\Windows\System32"

---
## Configure
In order for kubectl to find and access a Kubernetes cluster, it needs a kubeconfig file. By default, kubectl configuration is located at ```~/.kube/config```. 

Inside the config file it should look similar to this:

<b>NOTE:</b> 10.0.0.15 is the VIP for our kubernetes cluster we definied in our konvoy config
```
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: HashedCertGoesHere=
    server: https://10.0.0.15:6443
  name: vanillasystem
contexts:
- context:
    cluster: vanillasystem
    user: kubernetes-admin
  name: kubernetes-admin@vanillasystem
current-context: kubernetes-admin@vanillasystem
kind: Config
preferences: {}
users:
- name: kubernetes-admin
  user:
    client-certificate-data: ClientCertGoesHere@@@      
```

If you have a seprate config file you will need to specify the fule everytime you run kubectl
```
kubectl --kubeconfig admin.conf
```
If you write your config file to  ```~/.kube/config``` then you will not be required to specify it
```
kubectl
```

---
## Kubectl cp

To copy a directory ```/home/yabbo/html/*``` from the local system to the container to run from ```/usr/share/nginx/html/*```
```
kubectl cp /home/yabbo/html my-nginx-dep-768b657d56-x66mb:/usr/share/nginx/
```
Notice there is no html trailing on the destination. it will copy the folder and place it in the path... not just the contents of the folder!
