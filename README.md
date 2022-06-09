# docker-swarm

# How to install Docker Swarm
```
docker init #


root@dev-server01 /myworkspace/docker-swarm # docker stack deploy -c stack.yml  front
Creating service front_postgresql
Updating service front_nginx (id: voo60kir1rtmmx2u88ortcl71)


root@dev-server01 /myworkspace/docker-swarm # docker service ls
ID             NAME               MODE         REPLICAS   IMAGE               PORTS
voo60kir1rtm   front_nginx        replicated   1/1        nginx:1.19-alpine   *:8080->80/tcp
j1gdj5xpakxi   front_postgresql   replicated   1/1        postgres:latest     *:5432->5432/tcp

root@dev-server01 # docker service logs --no-trunc front_postgresql
front_postgresql.1.kxmy65o33wv4yjygskpoqzhkv@dev-server02.jnrlabs.com    | The files belonging to this database system will be owned by user "postgres".
front_postgresql.1.kxmy65o33wv4yjygskpoqzhkv@dev-server02.jnrlabs.com    | This user must also own the server process.
front_postgresql.1.kxmy65o33wv4yjygskpoqzhkv@dev-server02.jnrlabs.com    |
front_postgresql.1.kxmy65o33wv4yjygskpoqzhkv@dev-server02.jnrlabs.com    | The database cluster will be initialized with locale "en_US.utf8".
front_postgresql.1.kxmy65o33wv4yjygskpoqzhkv@dev-server02.jnrlabs.com    | The default database encoding has accordingly been set to "UTF8".
front_postgresql.1.kxmy65o33wv4yjygskpoqzhkv@dev-server02.jnrlabs.com    | The default text search configuration will be set to "english".

root@dev-server01 # docker service ps front_nginx
ID             NAME            IMAGE               NODE                       DESIRED STATE   CURRENT STATE            ERROR     PORTS
zflfzubn4cd1   front_nginx.1   nginx:1.19-alpine   dev-server01.jnrlabs.com   Running         Running 23 minutes ago


root@dev-server01 # docker service ps front_postgresql
ID             NAME                 IMAGE             NODE                       DESIRED STATE   CURRENT STATE           ERROR     PORTS
kxmy65o33wv4   front_postgresql.1   postgres:latest   dev-server02.jnrlabs.com   Running         Running 5 minutes ago
root@dev-server01 /myworkspace/gestalt/DevelopmentEnv (Release_3.0.0) #


```
## Leave Swarm Mode
**docker swarm leave** is used when you want a worker node to leave from swarm , 
**docker swarm leave** **--force** is for a manager node to leave the swarm.
