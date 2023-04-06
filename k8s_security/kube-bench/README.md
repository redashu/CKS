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
### running the bench marking 

```
kube-bench run --config-dir   /opt/cfg/  --config /opt/cfg/config.yaml
```

## Deploy kube-bench in k8s cluster 

```
kubectl apply -f https://raw.githubusercontent.com/aquasecurity/kube-bench/main/job.yaml

```

### lets verify that 

```
root@ip-172-31-22-49:~# kubectl get jobs.batch 
NAME         COMPLETIONS   DURATION   AGE
kube-bench   1/1           5s         36s

========
root@ip-172-31-22-49:~# kubectl get po 
NAME               READY   STATUS      RESTARTS   AGE
kube-bench-w5djx   0/1     Completed   0          57s


```

### checking the report 

```
root@ip-172-31-22-49:~# kubectl logs kube-bench-w5djx 
[INFO] 4 Worker Node Security Configuration
[INFO] 4.1 Worker Node Configuration Files
[FAIL] 4.1.1 Ensure that the kubelet service file permissions are set to 600 or more restrictive (Automated)
[PASS] 4.1.2 Ensure that the kubelet service file ownership is set to root:root (Automated)
[PASS] 4.1.3 If proxy kubeconfig file exists ensure permissions are set to 600 or more restrictive (Manual)
```


