vi httpd-pod.yaml 
kubectl apply -f httpd-pod.yaml 
vi httpd-pod.yaml 
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: httpd-pod-1
  labels:
    env: prod 
    type: front-end
    app: httpd-ws
spec:
  nodeName: kworker2
  volumes:
  - name: hp-volume
    hostPath:
      path: /data
  containers:
  - name: httpd-container
    image: httpd
    ports:
    - containerPort: 80
    volumeMounts:
    - name: hp-volume
      mountPath: /mnt/docs
```

kubectl apply -f httpd-pod.yaml 
kubectl exec -it httpd-pod-1 -- bash
exit
