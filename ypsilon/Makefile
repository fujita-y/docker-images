# docker buildx create --use --name build --node build --driver-opt network=host

build:
	docker build -t fujitay/ypsilon:latest .

run:
	docker run --rm -it fujitay/ypsilon:latest

push:
	docker buildx build --push --platform linux/amd64,linux/arm64 -t fujitay/ypsilon:latest .
