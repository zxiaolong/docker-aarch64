
NO_DOCKER_CACHE    ?= false

maas-mirror-local:
	sudo docker build --no-cache=${NO_DOCKER_CACHE} --rm \
        -f Dockerfile -t maas-mirror-local:latest .

maas-mirror-local-arm64v8:
	sudo docker build --no-cache=${NO_DOCKER_CACHE} --rm \
        -f Dockerfile.arm64v8 -t maas-mirror-local-arm64v8:latest .

run-trusty-arm64:
	sudo docker pull zxiaolong/maas-mirror:trusty-arm64
	sudo docker run -d --restart=aways -it -p 8080:80 --name maasmirror zxiaolong/maas-mirror:trusty-arm64

run-trusty-arm64-amd64:
	sudo docker pull zxiaolong/maas-mirror:trusty-arm64-amd64
	sudo docker run -d --restart=aways -it -p 8080:80 --name maasmirror zxiaolong/maas-mirror:trusty-arm64-amd64

run-local:
	sudo docker run -d --restart=aways -it -p 8080:80 --name maasmirror maas-mirror-local:latest

