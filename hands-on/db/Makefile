build-server:
	docker build -t opstree/prometheus:server .

run-db:
	docker rm -f db || true
	docker run --name db -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=test -d mysql:5.6

run-db-exporter:
	docker rm -f db-exporter || true
	docker run -d --name db-exporter -p 9104:9104 --link=db:db  -e DATA_SOURCE_NAME="root:password@(db:3306)/test" prom/mysqld-exporter

run-server:
	docker rm -f prom-server || true
	docker run -itd --name prom-server --link db-exporter:db-exporter -p 9090:9090 opstree/prometheus:server

run-all:
	make build-server
	make run-db
	make run-db-exporter
	make run-server
