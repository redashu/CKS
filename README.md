# CKS

## Kubernetes security category 

<ol>
  <li>Host Os level </li>
  <li>Kubernetes cluster Level </li>
  <li>Application Level </li>

</ol>

### Host OS level security 

<ol>
  <li>Minion nodes should do only kubernetes things </li>
  <li>Reduce attack surface : By reducing unnecessary application , keep things up to date </li>
  <li>Runtime security tools </li>
  <li>Restrict access to Minion Host : IAM or SSH </li>
</ol>


## Cloud Native Security 

<ol>
  <li>Cloud</li>
  <li>Container</li>
  <li>Cluster</li>
  <li>Code</li>
</ol>


## Cluster Hardening points

<ol>
  <li>CIS Benchmark </li>
  <li>Node Metadata and Endpoints protection </li>
  <li>DashBoard Security </li>
  <li>UPgrading Cluster</li>
  <li>Securing Images</li>
  <li>Network Policies </li>
</ol>

##  CIS {Center for InterNet Security} Benchmarking 

### Security Benchmark by CIS 

<img src="cis1.png">

### SErvice account with CLusterorle and clusterrolebinding --

```
 10  kubectl create clusterrolebinding  ns1bind  --clusterrole=view  --serviceaccount=ns1:pipeline 
   11  kubectl create clusterrolebinding  ns2bind  --clusterrole=view  --serviceaccount=ns2:pipeline 
   12  kubectl get roles -n ns1
   13  k get clusterrole view 
   14  k create clusterrole  pipe-deploy  --verb create,delete --resource deployment 
   15  kubectl create clusterrolebinding  ns1binddep  --clusterrole=pipe-deploy   --serviceaccount=ns1:pipeline 
   16  kubectl create clusterrolebinding  ns2binddep  --clusterrole=pipe-deploy   --serviceaccount=ns2:pipeline 
```

## k8s users with roles and rolebinding --

### create role with permission and bind it with k8s user 

```
  4  k -n applications  create role smokerole --verb create,delete --resource  pod,deployment,sts 
    5  k -n applications  create rolebinding  smokebind  --user smoke --role smokerole 
```

### clusterrole with rolebinding for k8s users --

```
 7  k -n applications  create rolebinding smoke-view --clusterrole  view --uesr smoke
    8  k -n applications  create rolebinding smoke-view --clusterrole  view --user  smoke
    9  k -n default  create rolebinding smoke-view --clusterrole  view --user  smoke
   10  k -n kube-public   create rolebinding smoke-view --clusterrole  view --user  smoke
   11  k -n kube-node-lease    create rolebinding smoke-view --clusterrole  view --user  smoke
```


