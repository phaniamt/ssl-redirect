# SSL Redirect

This docker container will redirect any traffic coming on to it from HTTP to HTTPS.

## How to use:

  * Deploy
  * Make public as front controller for your sites in HTTP only
  
How you accomplish this will vary from place to place. For instance, my use case is
  * Kubernetes
  * Kong docker (not kong-ingress)

I have a `LoadBalancer` service pushing traffic into Kong from the outside world. Kong's deployment contains one pod with two containers: Kong and SSL Redirect. The `LoadBalancer` service simply binds its port 80 to wherever you configure SSL redirect to.

## Whyyyyy
I made this little container to get around Kong's inability to upgrade HTTP connections to HTTPS - there are third party plugins for this, but since I run Kong in Kubernetes there's no easy way to add these plugins without needing to re-build the containers and publish them to a container registry.

# Docker image
 
 Clone this reposirory 
 
 docker build -t yphani/kong-ssl-redirect .
 
 docker push yphani/kong-ssl-redirect
