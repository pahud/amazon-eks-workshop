## Installing Helm



### Install the Helm CLI 

check https://github.com/kubernetes/helm/blob/master/docs/install.md for installation

or just

```
curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
```



### Create tiller ServiceAccount and ClusterRoleBinding

```
$ kubectl apply -f https://gist.githubusercontent.com/pahud/14e6cc08f3a7e65cd9b0e8bed454a901/raw/954d71614dda911c4f7960f0d18687fa1ea093fa/helm-sa-rolebinding.yaml
```



### Initialize the Helm

```
$ helm init --service-account tiller --upgrade
$HELM_HOME has been configured at /Users/hunhsieh/.helm.

Tiller (the Helm server-side component) has been upgraded to the current version.
Happy Helming!

```



### Helm Search

```
$ helm search mysql
NAME                            	CHART VERSION	APP VERSION	DESCRIPTION
stable/mysql                    	0.8.2        	5.7.14     	Fast, reliable, scalable, and easy to use open-...
stable/prometheus-mysql-exporter	0.1.0        	v0.10.0    	A Helm chart for prometheus mysql exporter with...
stable/percona                  	0.3.2        	5.7.17     	free, fully compatible, enhanced, open source d...
stable/percona-xtradb-cluster   	0.1.5        	5.7.19     	free, fully compatible, enhanced, open source d...
stable/phpmyadmin               	0.1.7        	4.8.2      	phpMyAdmin is an mysql administration frontend
stable/gcloud-sqlproxy          	0.3.6        	1.11       	Google Cloud SQL Proxy
stable/mariadb                  	4.2.7        	10.1.34    	Fast, reliable, scalable, and easy to use open-...
```

