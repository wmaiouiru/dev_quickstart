o run an application in a Kubernetes cluster that corresponds to the Docker run command you provided, you'll need to create Kubernetes resources like Deployment and Service. Kubernetes uses YAML manifest files to define these resources.

Here's an example of how you can translate the Docker run command into Kubernetes resources:

1. Create a Kubernetes Deployment:
Create a Deployment YAML (azimutt-deployment.yaml) that defines your application:

yaml
Copy code
apiVersion: apps/v1
kind: Deployment
metadata:
  name: azimutt-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: azimutt
  template:
    metadata:
      labels:
        app: azimutt
    spec:
      containers:
        - name: azimutt-container
          image: ghcr.io/azimuttapp/azimutt:main
          ports:
            - containerPort: 4000
          envFrom:
            - envFileRef:
                name: azimutt-env-config
Replace .env file configuration with Kubernetes ConfigMaps or Secrets. You can create ConfigMaps or Secrets to store environment variables and mount them as files or environment variables in the Pod.

2. Create ConfigMap or Secret:
Create a ConfigMap or Secret (azimutt-config.yaml) containing your environment variables:

For ConfigMap:

yaml
Copy code
apiVersion: v1
kind: ConfigMap
metadata:
  name: azimutt-env-config
data:
  # Add key-value pairs from your .env file
  KEY1: value1
  KEY2: value2
For Secret:

yaml
Copy code
apiVersion: v1
kind: Secret
metadata:
  name: azimutt-env-secret
type: Opaque
data:
  # Add base64-encoded key-value pairs from your .env file
  KEY1: dmFsdWUx
  KEY2: dmFsdWUy
Replace KEY1, KEY2, value1, value2 with your actual environment variables and values.

3. Create a Service:
Create a Service YAML (azimutt-service.yaml) to expose the application:

yaml
Copy code
apiVersion: v1
kind: Service
metadata:
  name: azimutt-service
spec:
  selector:
    app: azimutt
  ports:
    - protocol: TCP
      port: 4000
      targetPort: 4000
  type: LoadBalancer  # Change the type as needed (ClusterIP, NodePort, etc.)
4. Apply Kubernetes Manifests:
Apply these YAML files to your Kubernetes cluster:

bash
Copy code
kubectl apply -f azimutt-deployment.yaml
kubectl apply -f azimutt-config.yaml  # Use either ConfigMap or Secret
kubectl apply -f azimutt-service.yaml
This will create a Deployment, ConfigMap/Secret for environment variables, and a Service to expose your application in the Kubernetes cluster.

Remember to adjust the configurations as per your specific requirements and security considerations in the Kubernetes environment.