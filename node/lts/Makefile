REPO=verybigthings
PLATFORM=node
VERSION=10

.DEFAULT_GOAL := build-and-push

require-%:
	@ if [ "${${*}}" = "" ]; then \
		echo "ERROR: Environment variable not set: \"$*\""; \
		exit 1; \
	fi

# ============= #

build: require-VERSION require-PLATFORM
	docker build \
		-t ${PLATFORM}:${VERSION} \
		-t ${REPO}/${PLATFORM}:${VERSION} \
		.

build-no-cache: 
	docker build \
		--no-cache \
		-t ${PLATFORM}:${VERSION} \
		-t ${REPO}/${PLATFORM}:${VERSION} \
		.

push: require-VERSION require-PLATFORM
	docker push ${REPO}/${PLATFORM}:$(VERSION)

build-and-push: require-VERSION require-PLATFORM build push
