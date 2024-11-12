# stack

## Quickstart

Start the cluster.

```
task up
```

```
task: [up] k3d cluster create --config ./k3d-config.yaml
INFO[0000] Using config file ./k3d-config.yaml (k3d.io/v1alpha5#simple) 
INFO[0000] portmapping '80:80' targets the loadbalancer: defaulting to [servers:*:proxy agents:*:proxy] 
INFO[0000] portmapping '443:443' targets the loadbalancer: defaulting to [servers:*:proxy agents:*:proxy] 
INFO[0000] Created named volume 'k3d-server-0-var-lib-rancher-k3s-agent-containerd' 
INFO[0000] Prep: Network                                
INFO[0000] Created network 'k3d-k3s-default'            
INFO[0000] Created image volume k3d-k3s-default-images  
INFO[0000] Starting new tools node...                   
INFO[0000] Starting node 'k3d-k3s-default-tools'        
INFO[0001] Creating node 'k3d-k3s-default-server-0'     
INFO[0001] Creating LoadBalancer 'k3d-k3s-default-serverlb' 
INFO[0001] Using the k3d-tools node to gather environment information 
INFO[0001] HostIP: using network gateway 172.18.0.1 address 
INFO[0001] Starting cluster 'k3s-default'               
INFO[0001] Starting servers...                          
INFO[0001] Starting node 'k3d-k3s-default-server-0'     
INFO[0005] All agents already running.                  
INFO[0005] Starting helpers...                          
INFO[0005] Starting node 'k3d-k3s-default-serverlb'     
INFO[0012] Injecting records for hostAliases (incl. host.k3d.internal) and for 2 network members into CoreDNS configmap... 
INFO[0014] Cluster 'k3s-default' created successfully!  
INFO[0014] You can now use it like this:                
kubectl cluster-info
task: [up] kubectl wait --for condition=available -n kube-system deployment/coredns
deployment.apps/coredns condition met
```

You should now have access to it using kubectl or k9s.

```
kubectl get nodes -o wide
```
```
NAME                       STATUS   ROLES                  AGE   VERSION        INTERNAL-IP   EXTERNAL-IP   OS-IMAGE           KERNEL-VERSION     CONTAINER-RUNTIME
k3d-k3s-default-server-0   Ready    control-plane,master   76s   v1.31.1+k3s1   172.18.0.2    <none>        K3s v1.31.1+k3s1   6.5.0-1025-azure   containerd://1.7.21-k3s2
```

To delete the cluster.

```
task down
```
```
task: [down] k3d cluster delete
INFO[0000] Deleting cluster 'k3s-default'               
INFO[0000] Deleting cluster network 'k3d-k3s-default'   
INFO[0001] Deleting 2 attached volumes...               
INFO[0001] Removing cluster details from default kubeconfig... 
INFO[0001] Removing standalone kubeconfig file (if there is one)... 
INFO[0001] Successfully deleted cluster k3s-default! 
```