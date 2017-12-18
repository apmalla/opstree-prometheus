build:
	docker build -t opstree/prometheus:server .

run:
	make build
	docker rm -f prom-server || true
	docker run -itd --name prom-server -p 9090:9090 opstree/prometheus:server
