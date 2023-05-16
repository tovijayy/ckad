
Readiness and Liveness Probes

In Kubernetes, readiness probes and liveness probes are mechanisms used to determine the health and availability of a container within a Pod.

Readiness Probe:
A readiness probe is used to determine if a container is ready to receive network traffic and serve requests. It checks if the application inside the container has reached a state where it can handle incoming requests. If the readiness probe fails, the container is marked as not ready, and Kubernetes stops sending traffic to that container. This ensures that only fully functional containers receive traffic.

Liveness Probe:
A liveness probe is used to determine if a container is running properly. It checks if the container is alive and responsive. If the liveness probe fails, Kubernetes considers the container to be in a failed state, and it takes action based on the defined restart policy, such as restarting the container.

Both readiness probes and liveness probes are defined in the Pod's configuration file or deployment manifest.
