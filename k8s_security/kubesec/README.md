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

## Usage

### scaning a YAML for best standard practise 

```
kubesec scan test.yaml 

  {
    "object": "Pod/apod.default",
    "valid": true,
    "fileName": "test.yaml",
    "message": "Passed with a score of 0 points",
    "score": 0,
    "scoring": {
      "advise": [
        {
          "id": "ApparmorAny",
          "selector": ".metadata .annotations .\"container.apparmor.security.beta.kubernetes.io/nginx\"",
          "reason": "Well defined AppArmor policies may provide greater protection from unknown threats. WARNING: NOT PRODUCTION READY",
          "points": 3
        },

```

### you can use docker image also for scaning 

```
root@ip-172-31-22-49:~# docker run -i kubesec/kubesec:512c5e0 scan /dev/stdin < test.yaml 
Unable to find image 'kubesec/kubesec:512c5e0' locally
512c5e0: Pulling from kubesec/kubesec
c87736221ed0: Pull complete 
5dfbfe40753f: Pull complete 
0ab7f5410346: Pull complete 
b91424b4f19c: Pull complete 
0cff159cca1a: Pull complete 
32836ab12770: Pull complete 
Digest: sha256:8b1e0856fc64cabb1cf91fea6609748d3b3ef204a42e98d0e20ebadb9131bcb7
Status: Downloaded newer image for kubesec/kubesec:512c5e0
[
  {
    "object": "Pod/apod.default",
    "valid": true,
    "message": "Passed with a score of 0 points",
    "score": 0,
    "scoring": {
      "advise": [
        {
          "selector": "containers[] .securityContext .runAsUser -gt 10000",
          "reason": "Run as a high-UID user to avoid conflicts with the host's user table"
        },

```


