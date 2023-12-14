Redis is an inmemry database primarly used for caching
Redis vs redisstack :- redisstack also provides GUI to monitor 

Comamnd to install:-
 podman  run -d --name redis-stack -p 6379:6379 -p 8001:8001 redis/redis-stack:latest
 8001 :- port on which redis stack will expose
 6379:- port on which redis expose 

Command  to check server is running or not 
 > ping
"PONG"

Exec into container and run redis 

➜  ~ podman ps
CONTAINER ID  IMAGE                               COMMAND         CREATED        STATUS        PORTS                                           NAMES
6810b9a9700a  docker.io/redis/redis-stack:latest  /entrypoint.sh  3 minutes ago  Up 3 minutes  0.0.0.0:6379->6379/tcp, 0.0.0.0:8001->8001/tcp  redis-stack

➜  ~ podman exec -it 6810b9a9700a bash
root@6810b9a9700a:/# redis-cli ping
PONG 

using cli 
root@6810b9a9700a:/# redis-cli
127.0.0.1:6379> set name aman
OK
127.0.0.1:6379> get name
"aman"

Key naming convention 
<entity>:<id> value

127.0.0.1:6379> set user:1 aman
OK
127.0.0.1:6379> set user:2 prem
OK
127.0.0.1:6379> set user:2 prem nx // this will set key value if key not exists 
127.0.0.1:6379> mget user:1 user:2 // to  get multiple keys 
127.0.0.1:6379> mset user:1 "aman" user:2 "prem" // to  set  multiple keys 
set count 0 
incr count 1 
incrby count 10 // 11 

Default string Size 512 mb 

list in redis used as stack and array both 
lpush messages hey
rpush messages bye 


blpop messages 10  // wait until message does not come in array for 10 seconds 
Sets 
sadd ip 1

hashmap 
hset bike:1 model hero brand abc  type 'battery bikes' 

REDIS STREAMS :- 
A redis stream  is a data structure that acts like a append only log but also  implements  several operations to overcome some of the limits  of a typical append-only log. 

commands :- xadd xread xrange xlen 
