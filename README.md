# Vehicle Position Clients in K8s

### **Things you'll need to get started:**

1. A cluster in Confluent Cloud with a topic named `vehicle-positions`. Ideally, create this with 6 partitions so you can scale the consumer clients. 
1. You'll need to copy the client configuration properties from the **Clients** page in your cluster. This should give you a copy-able set of properties that you'll to use. 
    - This information is used in the `ConfigMap` found in `setup-properties.yaml`. You can find a placeholder version there for reference. Replace this with the contents of your client configuration.

### **Getting started:**

1. If you don't have it already, install `minikube`. 
    ```bash
    brew install minikube
    ```

1. Once `minikube` is installed, start `minikube`. 
    ```bash
    minikube start
    ```

1. With `minikube` running, use `kubectl` to build your setup.
    ```bash
    kubectl create -k .
    ```

1. Now, monitor the `Deployments` in order to verify everything launched correctly.
    ```bash
    kubectl get all
    ```
    If you have done everything correctly, your containers should have launched. 

### **Troubleshooting:**

- If you see `CrashloopBackoffs`, or other failures resulting from `kubectl get all`, use the following two approaches to see the logs or outputs from the containers. 
    - `kubectl logs <service>`
    - `kubectl describe <service>`