# Overview
This project involved the containerization and deployment of a full-stack yolo application using kubernetes.


# Requirements
- [Minikube](https://minikube.sigs.k8s.io/docs/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/)


## How to run the app

1. To start kubernetes environment, run the command on the terminal
```
minikube start --driver=virtualbox
```

2. Fork the repository on Git Hub.
3. Clone the repository into your local machine.

    ```
    git clone https://github.com/Michael-Otieno/yolo.git 
    ```
4. Change into the project directory.
   ```
   cd yolo
   ```
5. Apply the kubernetes file using the commands

    ```
    kubectl apply -f manifests/mongo.yaml
    ```

    ```
    kubectl apply -f manifests/backend.yaml
    ```

    ```
    kubectl apply -f manifests/client.yaml
    ```

6. Add database credentials by typing the following command on the terminal:

    ```
    kubectl create secret generic mongodb-credentials \
    --from-literal=username=$MONGO_USERNAME \
    --from-literal=password=$MONGO_PASSWORD
    ```

7. To view frontend application on the browser, run the command below on terminal:

    ```
    kubectl get svc
    ```
    view cluster-ip for  ```client-app-service```




8. Deployed url
- http://34.125.158.162/
