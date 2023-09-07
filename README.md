# example-helm
Example Helm

#Zabbix
https://git.zabbix.com/projects/ZT/repos/kubernetes-helm/browse?at=refs%2Fheads%2Frelease%2F6.4

clone:
git clone https://git.zabbix.com/scm/zt/kubernetes-helm.git

Copiar a pasta kubernetes-helm para server destino

Entrar na pasta, ajustar o arquivo values.yaml
- images
- tolerations
- requests/limits

validar o chart
helm lint kubernetes-helm

Pegar o nome do chart para instalação no Chart.yaml no campo name

Rodar instalacao 

helm install zabbix-helm-chrt kubernetes-helm -n monitoring

Erro de dependences, comentar dependencias no arquivo Chart.yaml

Unistall:
helm uninstall zabbix-helm-chrt kubernetes-helm -n monitoring




