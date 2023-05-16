
Readiness and Liveness Probes

In Kubernetes, readiness probes and liveness probes are mechanisms used to determine the health and availability of a container within a Pod.

Readiness Probe:
A readiness probe is used to determine if a container is ready to receive network traffic and serve requests. It checks if the application inside the container has reached a state where it can handle incoming requests. If the readiness probe fails, the container is marked as not ready, and Kubernetes stops sending traffic to that container. This ensures that only fully functional containers receive traffic.

Liveness Probe:
A liveness probe is used to determine if a container is running properly. It checks if the container is alive and responsive. If the liveness probe fails, Kubernetes considers the container to be in a failed state, and it takes action based on the defined restart policy, such as restarting the container.

Both readiness probes and liveness probes are defined in the Pod's configuration file or deployment manifest.

Here is an example of how to define readiness and liveness probes in a Kubernates deployment. 

apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  template:
    spec:
      containers:
      - name: my-app-container
        image: my-app-image
        ports:
        - containerPort: 8080
        readinessProbe:
          httpGet:
            path: /health
            port: 8080
          initialDelaySeconds: 10
          periodSeconds: 5
        livenessProbe:
          httpGet:
            path: /health
            port: 8080
          initialDelaySeconds: 15
          periodSeconds: 10

In the above example, the readiness probe and liveness probe are defined using HTTP GET requests to the /health endpoint on port 8080. The readiness probe starts after an initial delay of 10 seconds and checks every 5 seconds. The liveness probe starts after an initial delay of 15 seconds and checks every 10 seconds.

By configuring readiness and liveness probes, you can ensure that only healthy containers receive traffic and that unhealthy containers are automatically restarted by Kubernetes. This helps to maintain the availability and stability of your applications running in Kubernetes.