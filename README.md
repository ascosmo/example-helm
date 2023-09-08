# example-helm
Example Helm

Zabbix Agent / Zabbix Proxy\
https://git.zabbix.com/projects/ZT/repos/kubernetes-helm/browse?at=refs%2Fheads%2Frelease%2F6.4

Clone:\
git clone https://git.zabbix.com/scm/zt/kubernetes-helm.git

Copiar a pasta kubernetes-helm para server destino.

Entrar na pasta, ajustar o arquivo values.yaml
- images
- tolerations
- requests/limits

Validar o chart:
```
helm lint kubernetes-helm/
```

Validar template:
```
helm template Documents/zabbix/kubernetes-helm/
```

Pegar o nome do chart para instalação no Chart.yaml no campo **name**, que no exemplo é ***zabbix-helm-chrt***

Criar namespace **monitoring**

```
kubectl create namespace monitoring
```

Para instalar: 
```
helm install zabbix-helm-chrt Documents/zabbix/kubernetes-helm -f values.yaml -n monitoring
```
- zabbix-helm-chrt -> nome do chart
- kubernetes-helm -> path dos arquivos do pacote

Se der erro de dependences, comentar dependencias no arquivo Chart.yaml. Erro pode ser do metrics do kubernetes.


Para desistalar:
```
helm uninstall zabbix-helm-chrt Documents/zabbix/kubernetes-helm -n monitoring
```
Para upgrade:
```
helm upgrade zabbix-helm-chrt Documents/zabbix/kubernetes-helm -f values.yaml -n monitoring
```
Outros comandos:
- helm list
- helm list -n monitoring
- helm upgrade zabbix-helm-chrt 
- helm history zabbix-helm-chrt 
- helm rollback zabbix-helm-chrt 2

Remover o warning:\
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /Users/andre/.kube/config\
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /Users/andre/.kube/config

chmod g-r ~/.kube/config\
chmod 600 ~/.kube/config

Tutorial para configuração no zabbix.\
https://www.youtube.com/watch?v=Et2O2iyoCzI&t=600s

Espose da secret serviceaccount:
```
kubectl get secret zabbix-service-account -o jsonpath={.data.token} | base64 -d
```