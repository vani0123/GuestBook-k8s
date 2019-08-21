# GuestBook-k8s

Please find the steps taken

Pre-requisites:
Kubenetes cluster is created on GCP.

1. Create the Redis master pod. File used- redis-master-controller.yml
$ kubectl create -f redis-master-controller.yml

2. Create the Redis master service. File used- redis-master-service.yml
$ kubectl create -f  redis-master-service.yml

3. Create the Redis slave pods. File used- redis-slave-controller.yml
$ kubectl create -f redis-slave-controller.yml

4. Create the Redis slave service. File used- redis-slave-service.yml
$ kubectl create -f redis-slave-service.yml

5. Create the GuestBook pods. File used- guestbook-controller.yml
$ kubectl create -f guestbook-controller.yml

6. Create the GuestBook service with type LoadBalancer as need to access the application from outside using External IP. File used- guestbook-service.yml
$ kubectl create -f guestbook-service.yml

Once all the objects created successfully and running we will be able to see the External IP for GuestBook service.

To access the application hit external-IP:port(104.197.147.92:80) in the browser and Guestbook is launched sucessfully.
