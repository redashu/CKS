## SAST tool for k8s object security checking 

### Installation 

```
 wget https://github.com/controlplaneio/kubesec/releases/download/v2.13.0/kubesec_linux_amd64.tar.gz
```

### extract and set in path

```
 tar xvzf kubesec_linux_amd64.tar.gz 
 
 mv kubesec /usr/bin/
```

### verify installation 

```
root@ip-172-31-22-49:~# kubesec  help 

Validate Kubernetes resource security policies

Usage:
  kubesec [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  help        Help about any command
  http        Starts kubesec HTTP server on the specified port
  print-rules Print all the scanning rules with their associated scores
  scan        Scans Kubernetes resource YAML or JSON
  version     Prints kubesec version


```
