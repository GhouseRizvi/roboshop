WEB --> Catalogue-->mongo

1. mongodb should be running
2. Catalogue should be running
3. connect mongodb with catalogue (it should have a proper name to establish the connection between the containers)
So here connecting to caontainer would not resolve in name suppose you logged into the catalogue and ping mongodb from there it says unknown host. whereas if you take the ip of the mongodb and try to ping from the catalogue it'll ressovle.
So here ip to name mapping should be done first.
so here we need docker networking to take care of the ip to name mapping
-bridge -by default
-host
-overlay
-macvlan
Default bridge network cannot ressolve to names.
Docker recommends to create our own bridge network.
# Advantages of creating a Bridge networks 
- once created bridge network for specific project, project network is isolated.
- it can resolve the ip to name between the containers
4. connect werb to catalogue
