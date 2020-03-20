# KUBECTL

## Installing
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



