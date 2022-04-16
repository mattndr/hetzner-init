## kubeadm init

``` sudo kubeadm init --config init-config.yaml ```

Configuration example:
```
apiVersion: kubeadm.k8s.io/v1beta3
kind: InitConfiguration
localAPIEndpoint:
  advertiseAddress: 10.0.0.2
nodeRegistration:
  kubeletExtraArgs:
    node-ip: 10.0.0.2
---
apiVersion: kubeadm.k8s.io/v1beta3
kind: ClusterConfiguration
networking:
  podSubnet: 10.244.0.0/16
# This is required when k8s nodes communicate through a
# private network (like 10.0.0.0/16) and you want to
# connect to the cluster from outside (public network).
# The tcp Load Balancer exposes its own IP/DNS and
# redirect requests to the private network.
# apiServer:
#   certSANs:
#   - "static.14.10.233.167.clients.your-server.de"
  
```
```
apiserver serving cert is signed for DNS names [kubernetes kubernetes.default kubernetes.default.svc kubernetes.default.svc.cluster.local node-1 static.14.10.233.167.clients.your-server.de] and IPs [10.96.0.1 10.0.0.2]
```

## kubeadm join

``` sudo kubeadm join --config join-config.yaml ```

Configuration example:
```
apiVersion: kubeadm.k8s.io/v1beta3
kind: JoinConfiguration
nodeRegistration:
  kubeletExtraArgs:
    node-ip: 10.0.0.3
discovery:
  bootstrapToken:
    apiServerEndpoint: 10.0.0.2:6443
    token: <token>
    caCertHashes:
    - <sha> 
    unsafeSkipCAVerification: false
```

## Get internal IP
CIDR: 10.0.0.0/16

``` ip route get 10.0.0.0 | sed -n '/src/{s/.*src *\([^ ]*\).*/\1/p;q}' ```
