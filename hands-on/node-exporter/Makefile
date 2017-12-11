build-server:
	docker build -t opstree/prometheus:server .

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

run-server:
	docker rm -f prom-server || true
	docker run -itd --name prom-server --link node1:node1 --link node2:node2 --link node3:node3 --link node4:node4 -p 9090:9090 opstree/prometheus:server


run-all:
	make build-server
	make build-node
	make run-node1
	make run-node2
	make run-node3
	make run-node4
	make run-server
