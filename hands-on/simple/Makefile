build:
	docker build -t opstree/prometheus:simple .

run:
	docker rm -f prom-server || true
	docker run -itd --name prom-server -p 9090:9090 opstree/prometheus:simple
