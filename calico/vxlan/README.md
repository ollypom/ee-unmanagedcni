# Calico VXLAN

> Note you will need to generate your own `vxlansecrets.yaml` file by taking a
> base64 of the ca.pem, cert.pem and key.pem files in
> `/var/lib/docker/volumes/ucp-node-certs/_data`

Install UCP with the unmanaged CNI flag.
https://docs.docker.com/ee/ucp/kubernetes/install-cni-plugin/

Navigate to this directory and the `$ kubectl apply -f .` away.
