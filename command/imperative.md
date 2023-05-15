*******************************************************************************************************************
$ kubectl create namespace ckad
$ kubectl run nginx --image=nginx:1.17.10 --port=80 --namespace=ckad
$ kubectl run busybox --image=busybox --restart=Never --rm -it -n ckad \
  -- wget -O- 10.1.0.66:80
$ kubectl logs nginx --namespace=ckad
$ kubectl exec -it nginx --namespace=ckad  -- /bin/sh
$ kubectl run loop --image=busybox -o yaml --dry-run=client --restart=Never -- /bin/sh -c 'for i in 1 2 3 4 5 6 7 8 9 10; \
  do echo "Welcome $i times"; done' \
  > pod.yaml
$ kubectl create -f pod.yaml --namespace=ckad
$ kubectl get pod loop --namespace=ckad
$ kubectl create secret generic ext-service-secret --from-file=config
$ kubectl exec consumer -it -- /bin/sh
$ kubectl get resourcequota firebird-quota --namespace=project-firebird
$ kubectl get secrets --namespace=project-firebird
$ kubectl create secret generic my-secret --from-literal=test=hello --namespace=project-firebird
$ kubectl set image deployment.v1.apps/nginx-deployment nginx=nginx:1.16.1
$ kubectl create serviceaccount monitoring
$ kubectl run nginx --image=nginx --restart=Never --serviceaccount=monitoring
$ kubectl run pod-1 --image=nginx --restart=Never --labels=tier=frontend,team=artemidis
$ kubectl annotate pod pod-1 pod-3 deployer='Benjamin Muschko'
$ kubectl get pods -l tier=backend,'team in (artemidis,aircontrol)' --show-labels
$ kubectl set image deployment server-deployment grand-server=nginx
$ kubectl create cronjob google-ping --schedule="*/2 * * * *" --image=nginx -- /bin/sh -c 'curl google.com'
$ kubectl run backend --image=nginx --restart=Never --port=80 -l tier=backend,app=nginx
$ kubectl create service clusterip nginx-service --tcp=9000:8081  --dry-run=client -o yaml > nginx-service.yaml
$ kubectl run busybox --image=busybox --restart=Never -it --rm -- /bin/sh
$ kubectl run busybox --image=busybox --restart=Never -it --rm -- /bin/sh
$ kubectl patch service nginx-service -p '{ "spec": {"type": "NodePort"} }'
$ kubectl run alpine --image=alpine:3.12.0 --dry-run=client --restart=Never -o yaml -- /bin/sh -c "while true; do sleep 60; done;" > multi-container-alpine.yaml
kubectl run busybox --image=busybox --command --restart=Never -it --rm -- env
kubectl create quota myrq --hard=cpu=1,memory=1G,pods=2 --dry-run=client -o yaml
kubectl autoscale deploy nginx --min=5 --max=10 --cpu-percent=80
kubectl get hpa nginx

kubectl create job pi  --image=perl:5.34 -- perl -Mbignum=bpi -wle 'print bpi(2000)'
kubectl create cronjob busybox --image=busybox --schedule="*/1 * * * *" -- /bin/sh -c 'date; echo Hello from the Kubernetes cluster'
kubectl get events -o json | jq -r '.items[] | select(.message | contains("failed liveness probe")).involvedObject | .namespace + "/" + .name'
kubectl expose deploy foo --port=6262 --target-port=8080
*******************************************************************************************************************




 
  










  