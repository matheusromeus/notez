public ip -> only servers have it
tunneling?

- install node on VM as super user
- copy over source code
- run the app on port 5173 in dev mode or port 80 in prod. ideally you should use a reverse proxy and not run it directly on these ports.
- build the project
- how to serve dist? you can use nginx, you can use 'serve' package, serve -p 80 inside the pwd. install serve using sudo.

you should create a firewall rule because the VM is facing the internet. like what ports are open, who can connect etc.

security groups define a bunch of inbound rules to your machine. 

add A record for pointing to ip addresses

nginx as reverse proxy
certbot - add ssl certificates

VMs are hard to scale.

### CDNs & Object Stores

CDNs have POPs all over the world. It goes and fetches data from the <u>source</u> and caches it. When we request data it fetches the cached data from the nearest point.

which cdn? cloudfront is what AWS provides. cloudflare has one.

here, the source is an object store. S3. its good if we are serving content, videos, images, big files. static websites. if SSR is happening, then we cant use cached data right?

- create an object store
- create a cdn
- connect object store to cdn
- connect domain to cdn


backend apps can't be scaled by a cdn. because everyone has a unique backend data. it cant be cached.


## Tunnelling using Cloudflare Tunnels

For hosting it locally on your machine and exposing it to the internet.

because we don't have a public ip, we cannot expose processes in your lical machine to the internet. 

so cloud providers give us machines with public ips that then tunnel the requests to our local machine.

you need to run a daemon in your machine for cloudflare to know

### how to scale when you're self hosting?

aws provides auto scaling groups
- start an instance
- create an image
- creating a launch template
- start script in your launch template 
- create an asg with a load balancer on top

EBS does all this under the hood

dynamic scaling policy determines how and when the ASGs scale. based on network bytes or cpu usage etc

## Containerisation of apps

whenever you deploy a backend, it's always good to containerise it.

write a dockerfile
run docker build
push image to docker hub

for every github commit, you can push a fresh image to docker hub and that can be pulled by various container orchestration engines.

using k8s
- create a k8s cluster
- create the deployment
- create a service
- create/update the ingress
- add a certificate
- update the dns record
- add a CNAME to the service