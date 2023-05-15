A Pod can have multiple containers running apps within it, but it can also have one or more init containers, which is/are pre-requisite to be running before 
main container. if any pod definition has init container it is expected to provide output to the main container. Both are part of same pod so both container 
go through the lifecycle of pod. It init container fails, the main container will not start at all. 
