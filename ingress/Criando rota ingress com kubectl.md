# Criando rota ingress com kubectl


## Primeiro, consulte a classe de ingress instalado

```bash
$ kubectl get ingressclass
NAME    CONTROLLER             PARAMETERS   AGE
nginx   k8s.io/ingress-nginx   <none>       43m
```

Obs.: Conseguimos ver que o nome da classe é nginx


## Agora, vamos criar a rota

```bash
$ kubectl -n world create ingress world --class=nginx --rule="world.universe.mine/europe/*=europe:80"  --rule="world.universe.mine/asia/*=asia:80" --dry-run=client -o yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  creationTimestamp: null
  name: world
  namespace: world
spec:
  ingressClassName: nginx
  rules:
  - host: world.universe.mine
    http:
      paths:
      - backend:
          service:
            name: europe
            port:
              number: 80
        path: /europe/
        pathType: Prefix
      - backend:
          service:
            name: asia
            port:
              number: 80
        path: /asia/
        pathType: Prefix
status:
  loadBalancer: {}
controlplane $ 
```

Obs.: Notar que quando inseri /* foi gerado pathType com Prefix. Se remover * será Exact.