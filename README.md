* Make sure you have enabled ingress addon on your local minikube
* Make sure your local docker registry is reachable by minikube

* Build foo docker containers:
  - `$ cd app_foo`
  - `$ docker build -t foo:0.1 .`

* Build bar docker containers:
  - `$ cd app_bar`
  - `$ docker build -t bar:0.1 .`

* Configure on minikube in default namespace:
  * Bar:
    - `$ cd kube/bar`
    - `$ kubectl apply -f deployment.yaml`
    - `$ kubectl apply -f service.yaml`
  * Foo:
    - `$ cd kube/foo`
    - `$ kubectl apply -f deployment.yaml`
    - `$ kubectl apply -f service.yaml`
  * Ingress:
    - `$ cd kube`
    - `$ kubectl apply -f ingress.yaml`

* Check if it available:
  - `$ minikube ip`
  - Go to `<minikube_ip>/foo` and `<minikube_ip>/bar` in your browser
