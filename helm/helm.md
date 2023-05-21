```
$helm list
```
$helm repo add bitnami https://charts.bitnami.com/bitnami
```
kubectl create namespace today
```
$helm  install devsite bitnami/drupal -n today
```
$helm search repo drupal --version
```
$helm repo update              # Make sure we get the latest list of charts
```
$helm install bitnami/mysql --generate-name
```
$helm uninstall mysql-1684645602
```
$helm status mysql-1684645602
```
$helm get -h
```
