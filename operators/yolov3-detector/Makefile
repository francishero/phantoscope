COMMIT_ID = $(shell git rev-parse --short HEAD)
GIT_TAG = $(shell git tag --points-at HEAD)
IMAGE_NAME = yolov3-detector

ifeq ($(GIT_TAG), )
  TAG=$(COMMIT_ID)
else
  TAG=$(GIT_TAG)
endif
TAG='latest'
cpu:
	docker build  \
 	--build-arg base_tag=ubuntu:bionic-20200219 \
 	-t psoperator/$(IMAGE_NAME):$(TAG) \
 	-f Dockerfile .

gpu:
	docker build  \
 	--build-arg base_tag=nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04 \
 	-t psoperator/$(IMAGE_NAME)-gpu:$(TAG) \
 	-f Dockerfile-gpu .
