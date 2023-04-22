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

```
    kind create cluster
```
ou
```
    kind create cluster --name kind-multinodes --config kind-3nodes.yaml
```

   - Criar um pod com o Kubectl
```
    kubectl run --image nginx --port 80 reverse-proxy
```

   - Criar um YAML de configuração de um pod
```
    kubectl run --image nginx --port 80 reverse-proxy --dry-run=client -o yaml > pod.yaml
```


## Day 02

  - Aplicar modificações do YAML no pod

```
    kubectl delete -f pod.yaml
    kubectl apply -f pod.yaml
```

  - Obter logs de um container dentro de um pod
```
    k logs pods/my-pod my-pod-nginx
```

  - Impor limites aos pods
```
    
```