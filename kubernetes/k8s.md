## Reading & Writing Yamls

yaml is a human-readable data serialization standard that can be used in conjunction with all programming languages and is often used to write configuration files.

## Kubernetes architecture

The image below shows the architecture of a Kubernetes cluster.

![Kubernetes architecture](https://kubernetes.io/images/docs/kubernetes-cluster-architecture.svg)

## Create a namespace

namespace is a way to divide cluster resources between multiple users. It is used to create a virtual cluster within a physical cluster.

# Create yaml file for namespace
```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: my-namespace
```

# Apply the namespace
```bash
kubectl apply -f namespace.yaml
```

## Create a deployment

A deployment is a Kubernetes resource that manages a set of identical pods. It provides declarative updates to pods and replica sets.

# Create yaml file for deployment
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
  namespace: my-namespace
spec:
    replicas: 3
    selector:
        matchLabels:
        app: my-app
    template:
        metadata:
        labels:
            app: my-app
        spec:
        containers:
        - name: my-container
            image: nginx
            ports:
            - containerPort: 80
    ```

# Apply the deployment
```bash
kubectl apply -f deployment.yaml
```

## Create a service

A service is a Kubernetes resource that provides a way to expose an application running in a set of pods as a network service.

# Create yaml file for service
```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
  namespace: my-namespace
spec:
    selector:
        app: my-app // this should match the label of the pods in the deployment
    ports:
        - protocol: TCP
        port: 80
        targetPort: 80
    type: LoadBalancer
    ```

# Apply the service
```bash
kubectl apply -f service.yaml
```

## Create a configmap

A configmap is a Kubernetes resource that provides a way to inject configuration data into a container.Example, you can use a configmap to store environment variables, configuration files, or any other configuration data that your application needs.

# Create yaml file for configmap
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-configmap
  namespace: my-namespace
data:
    MY_ENV_VAR: my-value
    ```
# Apply the configmap
```bash
kubectl apply -f configmap.yaml
```

## Create a secret

A secret is a Kubernetes resource that provides a way to store sensitive information, such as passwords, OAuth tokens, and SSH keys, in a secure manner.The difference between a secret and a configmap is that a secret is base64 encoded, a secret is not stored in the etcd database and should be used for sensitive data.

# Create yaml file for secret
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
  namespace: my-namespace
type: Opaque
data:
    MY_SECRET: c2VjcmV0 // base64 encoded value
    ```
# Apply the secret
```bash
kubectl apply -f secret.yaml
```

## Create a persistent volume

A persistent volume is a Kubernetes resource that provides a way to store data in a persistent manner. It is used to store data that needs to persist across pod restarts and reschedules.

# Create yaml file for persistent volume
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
    capacity:
        storage: 1Gi
    accessModes:
        - ReadWriteOnce
    persistentVolumeReclaimPolicy: Retain
    storageClassName: my-storage-class
    hostPath:
        path: /data
    ```

# Apply the persistent volume
```bash
kubectl apply -f persistent-volume.yaml
```

# Check the health of a pod
```bash
kubectl get pods
```

# Check the logs of a pod
```bash
kubectl logs my-pod
```

# Check the events of a pod
```bash
kubectl describe pod my-pod
```

# Check the health of a deployment
```bash
kubectl get deployments
```

# Check the health of a service
```bash
kubectl get services
```

# Check the health of a configmap
```bash
kubectl get configmaps
```

# Check the health of a secret
```bash
kubectl get secrets
```

# Check the health of a persistent volume
```bash
kubectl get persistentvolumes
```


