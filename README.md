# artyom-markov_platform
artyom-markov Platform repository

HW8

ubuntu@markov-minikube:~/k8s/kubernetes-operators/deploy$ kubectl get jobs
NAME                         COMPLETIONS   DURATION   AGE
backup-mysql-instance-job    1/1           2s         6m53s
restore-mysql-instance-job   1/1           41s        5m22s

ubuntu@markov-minikube:~/k8s/kubernetes-operators/deploy$ export MYSQLPOD=$(kubectl get pods -l app=mysql-instance -o jsonpath="{.items[*].metadata.name}")
ubuntu@markov-minikube:~/k8s/kubernetes-operators/deploy$ kubectl exec -it $MYSQLPOD -- mysql -potuspassword -e "select * from test;" otus-database
mysql: [Warning] Using a password on the command line interface can be insecure.
+----+-------------+
| id | name        |
+----+-------------+
|  1 | some data   |
|  2 | some data-2 |
+----+-------------+
