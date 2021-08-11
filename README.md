## steps to achieve the lab

## 1. run two ec2 instances (one as master node and the second as the worker node)

## 2. run the following command on the both instances you created above
```
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl
sudo apt install docker.io
```

## 3. initialization of the master node run the command below (run this command only on the master node)
```
sudo kubeadm init --pod-network-cidr=10.244.0.0/16
```

## 4. install the network plugin on the control plane (master node in our case)
```
sudo kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
```
