# Descomplicando_Kubernetes
Repositório com atividades do curso Descomplicando Kubernetes da LinuxTips

## Day 01
Arquivos criados durante as atividades do [Day-1](https://github.com/badtuxx/CertifiedContainersExpert/tree/main/DescomplicandoKubernetes/day-1) do curso.

O que foi aprendido:
 - Conceitos
   - Container, Cluster, Node, Pod, Kubernetes, etc
 - Prática
   - Instalar o Kubectl
   - Instalar o Docker
   - Instalar o Kind
   - Criar um Cluster com o Kind

```sh
    kind create cluster
```
ou
```sh
    kind create cluster --name kind-multinodes --config kind-3nodes.yaml
```

   - Criar um pod com o Kubectl
```sh
    kubectl run --image nginx --port 80 reverse-proxy
```

   - Criar um YAML de configuração de um pod
```sh
    kubectl run --image nginx --port 80 reverse-proxy --dry-run=client -o yaml > pod.yaml
```


## Day 02

  - Aplicar modificações do YAML no pod

```sh
    kubectl delete -f pod.yaml
    kubectl apply -f pod.yaml
```

  - Obter logs de um container dentro de um pod
```sh
    k logs pods/my-pod my-pod-nginx
```

  - Impor limites aos pods
```yaml
    resources:
      limits:
        cpu: "1"
        memory: "128Mi"
      requests:
        cpu: "0.5"
        memory: "64Mi"
```
  - Criar um pod com um diretório vazio
```yaml
    volumeMounts:
    - mountPath: /giropops
      name: primeiro-emptydir
    
    ...
    
  volumes:
  - name: primeiro-emptydir
    emptyDir:
      sizeLimit: 256Mi
```


## Day 03

  - Deployment strategies
    - RollingUpdate
    - Recreate
  - replicas
  - namespace
  
  - Resultado Final
  
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: nginx-deployment
  name: nginx-deployment
  namespace: my-namespace
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx-deployment
  strategy:
    type: Recreate
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: nginx-deployment
    spec:
      containers:
      - image: nginx:1.16
        name: nginx
        resources: {}
status: {}
```
  
