##  Kube-bench 

<ul>
    <li> Security tool under apache license  </li>
    <li> Use to check that k8s deployment is running by CIS standard   </li>
    <li>  Give you result to k8s security standard  </li>
</ul>


### Installing kube-bench 

```
cd /opt
curl -L https://github.com/aquasecurity/kube-bench/releases/download/v0.6.2/kube-bench_0.6.2_linux_amd64.tar.gz -o kube-bench_0.6.2_linux_amd64.tar.gz

=== listing 
 ls
cni  containerd  kube-bench_0.6.2_linux_amd64.tar.gz
```

### extracting it 

```
root@ip-172-31-22-49:/opt# ls
cni  containerd  kube-bench_0.6.2_linux_amd64.tar.gz
root@ip-172-31-22-49:/opt# tar xvzf kube-bench_0.6.2_linux_amd64.tar.gz 
cfg/ack-1.0/config.yaml
cfg/ack-1.0/controlplane.yaml
cfg/ack-1.0/etcd.yaml
cfg/ack-1.0/managedservices.yaml
cfg/ack-1.0/master.yaml
cfg/ack-1.0/node.yaml
cfg/ack-1.0/policies.yaml

```

### listing 

```
root@ip-172-31-22-49:/opt# ls
cfg  cni  containerd  kube-bench  kube-bench_0.6.2_linux_amd64.tar.gz
root@ip-172-31-22-49:/opt# ls cfg/
ack-1.0  aks-1.0  cis-1.5  cis-1.6  config.yaml  eks-1.0  gke-1.0  rh-0.7  rh-1.0
root@ip-172-31-22-49:/opt# 

```

### add to Path variable 

```
root@ip-172-31-22-49:/opt# cp kube-bench /usr/bin/
```

### checking version 

```
root@ip-172-31-22-49:/opt# kube-bench version 
0.6.2
```

    
