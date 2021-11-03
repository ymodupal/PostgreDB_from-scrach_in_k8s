#### kubectl config get-contexts
#### kubectl get current-context

#### kubectl create -f postgres-storage.yaml
#### kubectl create -f postgres-configmap.yaml
#### kubectl create configmap dbscripts --from-file librarydbschema.sql
#### kubectl create -f postgres-deployment.yaml
#### kubectl create -f postgres-service.yaml

#### kubectl get pvc

#### kubectl get pods -o wide 

#### kubectl logs pod/postgres-86d79fbd5d-lg54l -f

#### kubectl exec -it postgres-7d8846dcf-65jh4  --  psql -h localhost -U admin --password -p 5432 library_db
\i '/mnt/librarydbschema.sql'    ### (run the .sql file manually using this command)

test_db=# CREATE USER postgresadmin WITH PASSWORD 'admin123';

delete from public.holds;
delete from public.checkouts;
delete from public.checkout_histories;
update public.assets set "AvailabilityStatusId" = 2 where "AvailabilityStatusId" = 4;
### if the database is not created using the command from readiness probe, then login the postgre pod via above command and load the .sql file from volume mount

## This command is login to pod and see the list of files and folders using 'ls' and other commands
kubectl exec --stdin --tty postgres-6ffc84f8f6-hxt5c -- /bin/bash

#### To Debug the Webapp container ( we should chose the namespace of the container)
kubectl exec --stdin --tty -n openfaas-fn lightlibweb-78f97f77b4-5frrd -- /bin/bash
ls
#### log files are available in 'c:\temp\nlog-all-2021-10-25.log' and 'c:\temp\nlog-own-2021-10-25.log' locations
### if vim is not available install it
apt-get update
apt-get install vim
vim 'c:\temp\nlog-all-2021-10-25.log' #### to see the log file content
:q

(or you can simply cat the contents of the file without opening the file via vim)
cat 'c:\temp\nlog-all-2021-10-29.log'

apt-get update
apt-get install -y postgresql-client
psql -h postgres.default.svc.cluster.local -U admin --password -p 5432 postgresdb
psql -h postgres.default.svc.cluster.local -U postgresadmin --password -p 5432 library_db
#### psql -h localhost -d test_db -U root -f infile

#### kubectl describe pod postgres-67ccf65ffd-wxnzv

#### \l
#### drop database sample_db;
#### \c test_db
#### \dt
#### select * from assets;           

#### kubectl create -f postgres-configmap.yaml
#### kubectl create configmap dbscripts --from-file testdbschema.sql
#### kubectl create -f postgres-deployment.yaml

#### kubectl delete -f postgres-deployment.yaml 
#### kubectl delete configmap dbscripts
#### kubectl delete -f postgres-configmap.yaml
#### kubectl delete -f postgres-service.yaml
#### kubectl delete -f postgres-storage.yaml