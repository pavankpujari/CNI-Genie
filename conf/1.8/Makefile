# git attributes
GIT_COMMIT              := $(shell git describe --dirty=-unsupported --always --tags || echo pre-commit)
GIT_SHA                 := $(shell git log --format="%H" -n 1)

# image attributes
IMAGE_REGISTRY          ?= infobloxcto
IMAGE_NAME              ?= sase.onprem.services
IMAGE_VERSION           ?= $(GIT_COMMIT)
SERVER_IMAGE            := $(IMAGE_REGISTRY)/$(IMAGE_NAME)
TAG_LATEST              := latest

DOCKERFILE		:= Dockerfile
.PHONY: genie clean image
default:image 

genie: image

clean:

	docker images -f=reference="infobloxcto/sase.onprem.services" -q | xargs docker rmi 2> /dev/null
image:
	cp oss_cni_bin/* ../../dist/.
	docker build --build-arg GIT_COMMIT=$(GIT_COMMIT) --build-arg GIT_SHA=$(GIT_SHA) -f $(DOCKERFILE) -t $(SERVER_IMAGE):$(IMAGE_VERSION) .
