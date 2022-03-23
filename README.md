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

# OCI [open container initiative]

## a project by LF to set standards and specifications for container and images 

<img src="oci1.png">

## any runtime engine sending instruction to RUNC

<img src="runc.png">

## early days how k8s --kubelet was creating container 

<img src="k8s1.png">

### CRI (container runtime interface ) how kubelet using CRI to create container 

<img src="cri.png">

## COntainer sandbox using kata containers 

<img src="kata.png">

### container sanboxing using gVisor 

<img src="gvisor.png">

### more info 

<img src="gvisor2.png">


