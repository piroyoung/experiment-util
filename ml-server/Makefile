IMAGE_NAME=jupyter-ml

build:
	docker build -t ${IMAGE_NAME} .
.PHONY: build


run:
	docker run -it -p 8888:8888 ${IMAGE_NAME}
.PHONY: run
