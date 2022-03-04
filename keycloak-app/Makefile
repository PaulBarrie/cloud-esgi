

REGISTRY=quay.io/paulbarrie7

FRONT_IMAGE=keycloak-front
FRONT_TAG=latest
FRONT_DIR=frontend

BACK_IMAGE=keycloak-back
BACK_TAG=latest
BACK_DIR=backend

_build:
	docker build -t $(REGISTRY)/$(IMAGE):$(TAG) $(DIR)
.PHONY: _build

_deploy:
	docker push $(REGISTRY)/$(IMAGE):$(TAG)
.PHONY: _deploy

build-front:
	$(MAKE) _build IMAGE=$(FRONT_IMAGE) TAG=$(FRONT_TAG) DIR=$(FRONT_DIR)
.PHONY: build-front

build-back:
	$(MAKE) _build IMAGE=$(BACK_IMAGE) TAG=$(BACK_TAG) DIR=$(BACK_DIR)
.PHONY: build-back


deploy-front:
	$(MAKE) _deploy IMAGE=$(FRONT_IMAGE) TAG=$(FRONT_TAG)
.PHONY: deploy-front

deploy-backend:
	$(MAKE) _deploy IMAGE=$(BACK_IMAGE) TAG=$(BACK_TAG)
.PHONY: deploy-backend

all: build-front build-back deploy-front deploy-backend
.PHONY: all