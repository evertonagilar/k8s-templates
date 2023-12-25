# Deploy + volumes + configmap

```bash
controlplane $ k -n world  get deploy/asia -oyaml
apiVersion: apps/v1
kind: Deployment
metadata:
  annotations:
    deployment.kubernetes.io/revision: "1"
  creationTimestamp: "2023-12-25T13:22:43Z"
  generation: 1
  labels:
    app: asia
  name: asia
  namespace: world
  resourceVersion: "2975"
  uid: fb5d68bc-118b-408b-aafd-4aefa9949c67
spec:
  progressDeadlineSeconds: 600
  replicas: 2
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: asia
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: asia
    spec:
      containers:
      - image: nginx:1.21.5-alpine
        imagePullPolicy: IfNotPresent
        name: c
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
        volumeMounts:
        - mountPath: /usr/share/nginx/html
          name: html
        - mountPath: /etc/nginx
          name: nginx-conf
          readOnly: true
      dnsPolicy: ClusterFirst
      initContainers:
      - command:
        - sh
        - -c
        - echo 'hello, you reached ASIA' > /html/index.html
        image: busybox:1.28
        imagePullPolicy: IfNotPresent
        name: init-container
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
        volumeMounts:
        - mountPath: /html
          name: html
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext: {}
      terminationGracePeriodSeconds: 30
      volumes:
      - emptyDir: {}
        name: html
      - configMap:
          defaultMode: 420
          items:
          - key: nginx.conf
            path: nginx.conf
          name: nginx-conf
        name: nginx-conf
status:
  availableReplicas: 2
  conditions:
  - lastTransitionTime: "2023-12-25T13:22:52Z"
    lastUpdateTime: "2023-12-25T13:22:52Z"
    message: Deployment has minimum availability.
    reason: MinimumReplicasAvailable
    status: "True"
    type: Available
  - lastTransitionTime: "2023-12-25T13:22:43Z"
    lastUpdateTime: "2023-12-25T13:22:52Z"
    message: ReplicaSet "asia-5b7655fc9d" has successfully progressed.
    reason: NewReplicaSetAvailable
    status: "True"
    type: Progressing
  observedGeneration: 1
  readyReplicas: 2
  replicas: 2
  updatedReplicas: 2
```


```bash
controlplane $ k -n world get cm
NAME               DATA   AGE
kube-root-ca.crt   1      10m
nginx-conf         1      10m
controlplane $ k -n world get cm/nginx-conf -o yaml
apiVersion: v1
data:
  nginx.conf: |
    user nginx;
    worker_processes  3;
    error_log  /var/log/nginx/error.log;
    events {
      worker_connections  10240;
    }
    http {
      server {
          listen       80;
          server_name  _;
          root   /usr/share/nginx/html;
          index  index.html index.htm;

          location /europe {
              alias /usr/share/nginx/html/;
              index  index.html index.html;
          }
          location /asia {
              alias /usr/share/nginx/html/;
              index  index.html index.html;
          }
          location / {
              root   /usr/share/nginx/html;
              index  index.html index.htm;
          }
      }
    }
kind: ConfigMap
metadata:
  creationTimestamp: "2023-12-25T13:22:43Z"
  name: nginx-conf
  namespace: world
  resourceVersion: "2802"
  uid: 2d30c36d-8f96-4cb5-b09a-5af51b5fb4d3
```  