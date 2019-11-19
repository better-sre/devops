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
