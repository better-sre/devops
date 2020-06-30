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
	etcdctl --write-out=table --endpoints=http://127.0.0.1:2379 member list
	# write:
	etcdctl --endpoints=http://127.0.0.1:2379 put foo bar
	# read:
	etcdctl --endpoints=http://127.0.0.1:2379 get foo
