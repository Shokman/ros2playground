### THIS IST THE VERSION WITH docker-compose
# From https://gist.github.com/mpneuried/0594963ad38e68917ef189b4e6a269db

# import config.
# You can change the default config with `make cnf="config_special.env" build`
cnf ?= config.env
include $(cnf)
export $(shell sed 's/=.*//' $(cnf))

# import deploy config
# You can change the default deploy config with `make cnf="deploy_special.env" release`
dpl ?= deploy.env
include $(dpl)
export $(shell sed 's/=.*//' $(dpl))

# grep the version from the mix file
VERSION=$(shell ./version.sh)

# HELP
# This will output the help for each task
# thanks to https://marmelab.com/blog/2016/02/29/auto-documented-makefile.html
.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

.DEFAULT_GOAL := help



# DOCKER TASKS

# Build the container
build_base: ## Build the release and develoment container. The development
	docker build --force-rm --tag $(APP_NAME)base "./$(APP_NAME)base"

build_intel: ## Build the release and develoment container. The development
	docker build --force-rm --tag $(APP_NAME)intel "./$(APP_NAME)intel"

build_nvidia: ## Build the release and develoment container. The development
	docker build --force-rm --build-arg FROM_IMAGE=nvidia/opengl:1.0-glvnd-devel-ubuntu18.04 --tag $(APP_NAME)base_nvidia "./$(APP_NAME)base"
	docker build --force-rm --build-arg FROM_IMAGE=$(APP_NAME)base_nvidia --tag $(APP_NAME)nvidia "./$(APP_NAME)nvidia"

run: stop ## Run container on port configured in `config.env`
	docker run -i -t --rm --env-file=./config.env --name="$(APP_NAME)" $(APP_NAME)

stop: ## Stop running containers
	docker stop $(APP_NAME)

rm: stop ## Stop and remove running containers
	docker rm $(APP_NAME)

clean: ## Clean the generated/compiles files
	echo "nothing clean ..."
