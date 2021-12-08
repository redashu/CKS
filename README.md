# CKS

## Kubernetes security category 

## Namespace :

### Running two container in same Pid namespace 

### containers running 

```
docker run --name c11 -d ubuntu sh -c 'sleep 1d'
 docker run --name c22 --pid=container:c11  -d ubuntu sh -c 'sleep 100d'
 
```
### checking containers with namespace 

```
 docker exec c11 ps aux 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2612   608 ?        Ss   13:06   0:00 sh -c sleep 1d
root         8  0.0  0.0   2512   588 ?        S    13:06   0:00 sleep 1d
root        15  0.0  0.0   2612   608 ?        Ss   13:08   0:00 sh -c sleep 100d
root        24  0.0  0.0   2512   588 ?        S    13:08   0:00 sleep 100d
root        31  0.0  0.0   5900  2888 ?        Rs   13:19   0:00 ps aux

```
 
 
 


