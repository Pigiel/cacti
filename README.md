# Cacti
Repository of Cacti kubernetes deployment

## Application Deployment

To deploy application run the following commands
```sh
kubectl apply -f cacti.yml       
kubectl apply -f cacti-svc.yml 
kubectl apply -f cacti-ingress.yml
```

Check if the applicaiton is running
```sh
kubectl get all -l app==cacti
```
```sh
NAME                         READY     STATUS    RESTARTS   AGE
pod/cacti-846855bf7d-n2k5z   1/1       Running   0          15m

NAME                    DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/cacti   1         1         1            1           15m

NAME                               DESIRED   CURRENT   READY     AGE
replicaset.apps/cacti-846855bf7d   1         1         1         15m
```

## Backup & Restore Cacti Database

To backup use the command below

```sh
kubectl exec -it <CONTAINER_NAME> /sbin/backup
```

> Then backup data was created `/var/backups/alldb_backup.sql`

To restore use the command below
```sh
kubectl exec -it <CONTAINER_NAME> /sbin/restore
```