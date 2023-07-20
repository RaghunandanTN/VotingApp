# VotingApp
kubectl delete all --all;
pod "db-b54cd94f4-c5tkf" deleted
pod "redis-868d64d78-v8t2s" deleted
pod "result-5d57b59f4b-qlqpk" deleted
pod "vote-94849dc97-9jswn" deleted
pod "worker-dd46d7584-fbfvp" deleted
service "db" deleted
service "kubernetes" deleted
service "redis" deleted
service "result" deleted
service "vote" deleted
deployment.apps "db" deleted
deployment.apps "redis" deleted
deployment.apps "result" deleted
deployment.apps "vote" deleted
deployment.apps "worker" deleted

yum install git -y
Loaded plugins: extras_suggestions, langpacks, priorities, update-motd
amzn2-core                                                                                                                                                  | 3.7 kB  00:00:00     
amzn2extra-docker                                                                                                                                           | 3.0 kB  00:00:00     
amzn2extra-kernel-5.10                                                                                                                                      | 3.0 kB  00:00:00     
kubernetes                                                                                                                                                  | 1.4 kB  00:00:00     
11 packages excluded due to repository priority protections
Package git-2.40.1-1.amzn2.0.1.x86_64 already installed and latest version
Nothing to do

 git clone  https://github.com/ashishrpandey/example-voting-app
fatal: destination path 'example-voting-app' already exists and is not an empty directory.

cd k8s-specifications/
[root@ip-172-31-39-73 k8s-specifications]# ll
total 36
-rw-r--r-- 1 root root 401 Jul 18 08:28 db-deployment.yaml
-rw-r--r-- 1 root root 146 Jul 18 08:28 db-service.yaml
-rw-r--r-- 1 root root 402 Jul 18 08:28 redis-deployment.yaml
-rw-r--r-- 1 root root 152 Jul 18 08:28 redis-service.yaml
-rw-r--r-- 1 root root 299 Jul 18 08:28 result-deployment.yaml
-rw-r--r-- 1 root root 195 Jul 18 08:28 result-service.yaml
-rw-r--r-- 1 root root 289 Jul 18 08:28 vote-deployment.yaml
-rw-r--r-- 1 root root 192 Jul 18 08:28 vote-service.yaml
-rw-r--r-- 1 root root 292 Jul 18 08:28 worker-deployment.yaml
[root@ip-172-31-39-73 k8s-specifications]# vim result-service.yaml

[root@ip-172-31-39-73 k8s-specifications]# vim vote-service.yaml

kubectl apply -f .
deployment.apps/db created
service/db created
deployment.apps/redis created
service/redis created
deployment.apps/result created
service/result created
deployment.apps/vote created
service/vote created
deployment.apps/worker created


kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/db-b54cd94f4-cc89v        1/1     Running   0          61s
pod/redis-868d64d78-sxxg7     1/1     Running   0          61s
pod/result-5d57b59f4b-5w65m   1/1     Running   0          61s
pod/vote-94849dc97-jm2ms      1/1     Running   0          61s
pod/worker-dd46d7584-xskkd    1/1     Running   0          61s

NAME                 TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
service/db           ClusterIP   10.111.151.197   <none>        5432/TCP         61s
service/kubernetes   ClusterIP   10.96.0.1        <none>        443/TCP          9m29s
service/redis        ClusterIP   10.100.72.34     <none>        6379/TCP         61s
service/result       NodePort    10.103.107.71    <none>        5001:31001/TCP   61s
service/vote         NodePort    10.99.40.243     <none>        5000:31000/TCP   61s

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/db       1/1     1            1           61s
deployment.apps/redis    1/1     1            1           61s
deployment.apps/result   1/1     1            1           61s
deployment.apps/vote     1/1     1            1           61s
deployment.apps/worker   1/1     1            1           61s

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/db-b54cd94f4        1         1         1       61s
replicaset.apps/redis-868d64d78     1         1         1       61s
replicaset.apps/result-5d57b59f4b   1         1         1       61s
replicaset.apps/vote-94849dc97      1         1         1       61s
replicaset.apps/worker-dd46d7584    1         1         1       61s


kubectl get po --show-labels
NAME                      READY   STATUS    RESTARTS   AGE   LABELS
db-b54cd94f4-cc89v        1/1     Running   0          97s   app=db,pod-template-hash=b54cd94f4
redis-868d64d78-sxxg7     1/1     Running   0          97s   app=redis,pod-template-hash=868d64d78
result-5d57b59f4b-5w65m   1/1     Running   0          97s   app=result,pod-template-hash=5d57b59f4b
vote-94849dc97-jm2ms      1/1     Running   0          97s   app=vote,pod-template-hash=94849dc97
worker-dd46d7584-xskkd    1/1     Running   0          97s   app=worker,pod-template-hash=dd46d7584


kubectl get po -o wide
NAME                      READY   STATUS    RESTARTS   AGE   IP              NODE                                              NOMINATED NODE   READINESS GATES
db-b54cd94f4-cc89v        1/1     Running   0          13m   192.168.77.12   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
redis-868d64d78-sxxg7     1/1     Running   0          13m   192.168.77.13   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-5w65m   1/1     Running   0          13m   192.168.77.14   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-jm2ms      1/1     Running   0          13m   192.168.77.15   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-xskkd    1/1     Running   0          13m   192.168.77.16   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>

kubectl delete po vote-94849dc97-jm2ms
pod "vote-94849dc97-jm2ms" deleted

kubectl get po -o wide
NAME                      READY   STATUS    RESTARTS   AGE   IP              NODE                                              NOMINATED NODE   READINESS GATES
db-b54cd94f4-cc89v        1/1     Running   0          20m   192.168.77.12   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
redis-868d64d78-sxxg7     1/1     Running   0          20m   192.168.77.13   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-5w65m   1/1     Running   0          20m   192.168.77.14   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-jdxhj      1/1     Running   0          5s    192.168.77.17   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-xskkd    1/1     Running   0          20m   192.168.77.16   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>

After deleting the VOTE POD ,automatically new VOTE POD is created with new container ID & IP address from pool, also can observe age of New pod which is created newly.

kubectl delete po worker-dd46d7584-xskkd
pod "worker-dd46d7584-xskkd" deleted
[root@ip-172-31-39-73 k8s-specifications]# kubectl get po -o wide
NAME                      READY   STATUS    RESTARTS   AGE   IP              NODE                                              NOMINATED NODE   READINESS GATES
db-b54cd94f4-cc89v        1/1     Running   0          21m   192.168.77.12   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
redis-868d64d78-sxxg7     1/1     Running   0          21m   192.168.77.13   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-5w65m   1/1     Running   0          21m   192.168.77.14   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-jdxhj      1/1     Running   0          93s   192.168.77.17   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-z5dxv    1/1     Running   0          4s    192.168.77.18   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>

After deleting the Worker POD ,automatically new VOTE POD is created with new container ID & IP address from pool, also can observe age of New pod which is created newly. Same observation as Vote POD.


kubectl delete po db-b54cd94f4-cc89v
pod "db-b54cd94f4-cc89v" deleted

[root@ip-172-31-39-73 k8s-specifications]# 
[root@ip-172-31-39-73 k8s-specifications]# kubectl get po -o wide
NAME                      READY   STATUS    RESTARTS   AGE    IP              NODE                                              NOMINATED NODE   READINESS GATES
db-b54cd94f4-vvkdc        1/1     Running   0          35s    192.168.77.19   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
redis-868d64d78-sxxg7     1/1     Running   0          23m    192.168.77.13   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
result-5d57b59f4b-5w65m   1/1     Running   1          23m    192.168.77.14   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
vote-94849dc97-jdxhj      1/1     Running   0          3m4s   192.168.77.17   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>
worker-dd46d7584-z5dxv    1/1     Running   1          95s    192.168.77.18   ip-172-31-42-42.ap-southeast-1.compute.internal   <none>           <none>

It takes a longer time while deleting the DB POD and also can see VOTING RESULTS set to default and actomatically new DB pod is created with new containder ID & IP Address. During this process Worker and Result Pods are not able to communicate with DB pod, ehnce we cannot able to Vote. After Creating DB pod we can observe Worker and result pods are restarted and connected again & able to VOTE now & can see the results aswel.



1. Commands that you used during the assignment.
kubectl delete all --all;
yum install git -y
git clone  https://github.com/ashishrpandey/example-voting-app
kubectl apply -f .
kubectl get all
kubectl get po -o wide
pod "vote-94849dc97-jm2ms" deleted

Above are the basic commands used during assignment, Logs/Snapshot as above.

2. snapshot of logs

Logs of command outputs are as above.


3. your comment on WHY result app STOPPED working after db pod stop
As the DB Pod having Data Stored whcih is received from Vote --> Korker --> DB & Result Pod will fetch the data saved in DB Pod and project the results. In order to Work, result pod depends on DB Pod. Hence resutl pod stopped working during un availablilty of DB Pod.

4. your answer to HOW YOU MADE THE RESULT POD work.
After DB pod recreates, result pod got automatic restart and with successful connectivity with DB Pod .. restult Pod started working Normal.


5. Some jargons (just names are enough- dont need sentences) that you learnt from the Training session

Able to understand working of Pods, services and deployment process, we are able to see the changes in each pod when they deleted & recreated by RS or RC. Overall it was a good understanding above kubernetes and commands.


