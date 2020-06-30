SHELL := /bin/bash

##########################################################
# docker:
##########################################################

up-mq:
	docker-compose -f common-mq-rabbitmq.yml up -d

up-redis:
	docker-compose -f common-cache-redis.yml up -d

up-memcached:
	docker-compose -f common-cache-memcached.yml up -d

# 读写测试: https://www.jianshu.com/p/b851e4e1bec2
check.etcd:
	# enter docker container:
	docker exec -it local_etcd1_1 bash
	#
	# in container do:
	#
	# check:
	etcdctl cluster-health
	etcdctl member list
	etcdctl --write-out=table --endpoints=http://127.0.0.1:2379 member list
	# v2 write/read:
	ETCDCTL_API=2 etcdctl set /v2key1 hello
	ETCDCTL_API=2 etcdctl get /v2key1
	# v3 write/read:
	ETCDCTL_API=3 etcdctl put /v3key2 hello
	ETCDCTL_API=3 etcdctl get /v3key2
	etcdctl --endpoints=http://127.0.0.1:2379 put foo bar
	etcdctl --endpoints=http://127.0.0.1:2379 get foo
