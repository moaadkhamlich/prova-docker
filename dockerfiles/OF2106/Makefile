ME=$(shell whoami)
clean:
	rm -f hello

build-ubuntu:
	docker build --build-arg myuser=$(shell whoami) --build-arg UID=$(id -u) --build-arg GID=$(id -g) -t ubuntu-apc -f ./Dockerfile .

run: build-ubuntu
	xhost +"local:docker" && \
	docker run -ti --rm \
        -v "${HOME}:/home/${ME}" \
		-e DISPLAY=${DISPLAY} \
        --security-opt seccomp=unconfined \
		ubuntu-apc


