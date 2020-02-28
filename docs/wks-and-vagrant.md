# WKS and Vagrant

```console
$ cd examples/vagrant
$ vagrant up
$ wksctl apply --ssh-key=$HOME/.vagrant.d/insecure_private_key
INFO[0000] installing CRI implementation
INFO[0054] installing Kubernetes
INFO[0079] initializing Kubernetes cluster with kubeadm
INFO[0164] installing CNI implementation
INFO[0165] applying cluster API's custom resource definitions
INFO[0166] applying cluster's manifest
INFO[0166] applying machines' manifest
INFO[0166] applying WKS controller's manifests
INFO[0167] adding SSH key to WKS secret and applying its manifest
$ vagrant ssh kube-01
$ sudo -i
# It takes a few minutes for the controller to create the second node.
# kubectl get nodes
NAME      STATUS   ROLES    AGE     VERSION
kube-01   Ready    master   8m8s    v1.13.3
kube-02   Ready    <none>   4m53s   v1.13.3

At any time, one can look at what the controller is doing:
# kubectl logs --tail 100 -f -n weavek8sops -l name=wks-controller
```
