# GuestBook-k8s

Please find the steps taken
1. Create the Redis master pod. File used- redis-master-controller.yml
2. Create the Redis master service. File used- redis-master-service.yml
3. Create the Redis slave pods. File used- redis-slave-controller.yml
4. Create the Redis slave service. File used- redis-slave-service.yml
5. Create the GuestBook pods. File used- guestbook-controller.yml
6. Create the GuestBook service with type LoadBalancer as need to access the application from outside using External IP. File used- guestbook-service.yml

After creating all the objects below is the output:
vanijain06@cloudshell:~ (flowing-goods-226717)$ kubectl get all
NAME                     READY   STATUS    RESTARTS   AGE
pod/guestbook-dtf7w      1/1     Running   0          3h19m
pod/guestbook-h467l      1/1     Running   0          3h19m
pod/guestbook-qjj7l      1/1     Running   0          3h19m
pod/redis-master-2k2wn   1/1     Running   0          4h50m
pod/redis-slave-6pd26    1/1     Running   0          3h22m
pod/redis-slave-sxhfp    1/1     Running   0          3h22m

NAME                                 DESIRED   CURRENT   READY   AGE
replicationcontroller/guestbook      3         3         3       3h19m
replicationcontroller/redis-master   1         1         1       4h50m
replicationcontroller/redis-slave    2         2         2       3h22m

NAME                   TYPE           CLUSTER-IP   EXTERNAL-IP      PORT(S)        AGE
service/guestbook      LoadBalancer   10.0.9.9     104.197.147.92   80:32275/TCP   3h22m
service/kubernetes     ClusterIP      10.0.0.1     <none>           443/TCP        4h52m
service/redis-master   ClusterIP      10.0.6.137   <none>           6379/TCP       3h40m
service/redis-slave    ClusterIP      10.0.9.81    <none>           6379/TCP       3h22m

To access the application hit external-IP:port(104.197.147.92:80) in the browser and Guestbook is launched sucessfully.
