Following https://docs.docker.com/ee/ucp/kubernetes/install-cni-plugin/.

Additional Firewall ports that need to be opened for Weave between nodes 6783 TCP, 6783 UDP, 6784 UDP.

1) Install UCP

```
$ docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock docker/ucp:3.1.7 install \
  --san 35.176.141.176 \
  --admin-password docker123 \
  --unmanaged-cni
```

2) Install the CNI binaries for CNI v0.3.0 including a portmap binary hosted by Calico.
This needs to be done on all nodes!

```
# Make sure its a fresh node
$ rm -fr /opt/cni/bin
$ rm -fr /etc/cni/net.d

$ mkdir /opt/cni/bin
$ cd /opt/cni/bin
$ wget https://github.com/containernetworking/cni/releases/download/v0.3.0/cni-v0.3.0.tgz
$ tar xvzf cni-v0.3.0.tgz
$ rm cni-v0.3.0.tgz
$ wget https://github.com/projectcalico/cni-plugin/releases/download/v1.9.0/portmap
$ chmod +x portmap
```

3) Install the Weave Yaml using kubectl connected to UCP via a client bundle.

```
$ wget -O net.yaml "https://cloud.weave.works/k8s/net?k8s-version=1.11.19"
$ kubectl apply -f net.yaml
```

4) Add additional nodes to the cluster
