build-server:
	docker build -t opstree/prometheus:server .

run-db:
	docker rm -f db || true
	docker run --name db -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=test -d mysql:5.6

run-db-exporter:
	docker rm -f db-exporter || true
	docker run -d --name db-exporter -p 9104:9104 --link=db:db  -e DATA_SOURCE_NAME="root:password@(db:3306)/test" prom/mysqld-exporter

build-node:
	docker build -t opstree/prometheus:node -f Dockerfile.node .

run-node1:
	docker rm -f node1 || true
	docker run -itd --name node1  opstree/prometheus:node

run-node2:
	docker rm -f node2 || true
	docker run -itd --name node2  opstree/prometheus:node

run-node3:
	docker rm -f node3 || true
	docker run -itd --name node3  opstree/prometheus:node

run-node4:
	docker rm -f node4 || true
	docker run -itd --name node4  opstree/prometheus:node

run-alertmanager:
	docker rm -f alertmanager || true
	docker run -itd --name alertmanager prom/alertmanager

run-server:
	docker rm -f prom-server || true
	docker run -itd --name prom-server --link db-exporter:db-exporter --link node1:node1 --link node2:node2 --link node3:node3 --link node4:node4 --link alertmanager:alertmanager -p 9090:9090 opstree/prometheus:server

run-all:
	make build-server
	make build-node
	make run-node1
	make run-node2
	make run-node3
	make run-node4
	make run-db
	make run-db-exporter
	make run-alertmanager
	make run-server
