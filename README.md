# Installing Unmanaged CNIs on Docker Enterprise

My default Universal Control Plane installs the [Calico
CNI](https://www.projectcalico.org/). By default Calico will enable a POD IP
Pool, as well as use IP in IP tunnelling as an overlay. For lots of little
reasons you may want to install an alternative CNI on Docker Enterprise. This
is called an "unmanaged" CNI. It is called unmanaged because the lifecycle of
the CNI components themselves are not managed by the Universal Control Plane
(Installation / Upgrade etc), therefore these CNI components are not actually
supported by Docker Inc. This Repo contains some example YAMLs when deploying
alternative CNIs on to Docker Enterprise.

For full instructions on installing Docker Enterprise without installing /
managing a CNI, see the [official
docs](https://docs.docker.com/ee/ucp/kubernetes/install-cni-plugin/).

Unmanaged CNIs:

- WeaveNet
- Calico using VXLAN tunneling
