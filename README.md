# example-helm
Example Helm

Zabbix
https://git.zabbix.com/projects/ZT/repos/kubernetes-helm/browse?at=refs%2Fheads%2Frelease%2F6.4

Clone:
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
Pegar o nome do chart para instalação no Chart.yaml no campo **name**

Criar namespace **monitoring**

Rodar instalacao: 
```
helm install zabbix-helm-chrt kubernetes-helm -n monitoring
```
Se der erro de dependences, comentar dependencias no arquivo Chart.yaml. Erro pode ser do metrics do kubernetes.


Para desistalar:
```
helm uninstall zabbix-helm-chrt kubernetes-helm -n monitoring
```

Outros comandos:
- helm list
- helm list -n monitoring
- helm upgrade zabbix-helm-chrt 
- helm history zabbix-helm-chrt 
- helm rollback zabbix-helm-chrt 2

Tutorial para configuração no zabbix.
https://www.youtube.com/watch?v=Et2O2iyoCzI&t=600s
