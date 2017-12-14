build-server:
	docker build -t opstree/grafana:server .

run-server:
	docker rm -f grafana-server || true
	docker run -d --name grafana-server --link prom-server:prom-server -p 3000:3000 opstree/grafana:server

run-all:
	make build-server
	make run-server
