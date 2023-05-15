A Pod can have multiple containers running apps within it, but it can also have one or more init containers, which is/are pre-requisite to be running before 
main container. if any pod definition has init container it is expected to provide output to the main container. Both are part of same pod so both container 
go through the lifecycle of pod. It init container fails, the main container will not start at all. 

Some of the common use cases for Init Containers in Kubernetes include:

a) Setting up volumes and secrets that will be used by the main container(s).
b) Waiting for other services or dependencies to become available before starting the main container(s).
c) Performing configuration or initialization tasks, such as applying database schema updates, setting environment variables, or installing required packages.

Init Containers are useful for ensuring that a Pod's dependencies are ready before the main container(s) start running. They can also be used to perform initialization tasks that are specific to the application being deployed. By using Init Containers, you can ensure that your application starts up correctly and has all the resources it needs to run successfully.
