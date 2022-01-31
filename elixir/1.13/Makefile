REPO=verybigthings
PLATFORM=elixir
VERSION=1.13
PATCH_VERSION=1.13.2

.DEFAULT_GOAL := build-and-push

require-%:
	@ if [ "${${*}}" = "" ]; then \
		echo "ERROR: Environment variable not set: \"$*\""; \
		exit 1; \
	fi

# ============= #

build: require-VERSION require-PLATFORM require-PATCH_VERSION
	docker build \
		-t ${REPO}-${PLATFORM}:${VERSION} \
		-t ${REPO}/${PLATFORM}:${VERSION} \
		-t ${REPO}-${PLATFORM}:${PATCH_VERSION} \
		-t ${REPO}/${PLATFORM}:${PATCH_VERSION} \
		.

push: require-VERSION require-PLATFORM require-PATCH_VERSION
	docker push ${REPO}/${PLATFORM}:$(VERSION)
	docker push ${REPO}/${PLATFORM}:$(PATCH_VERSION)

build-and-push: require-VERSION require-PLATFORM require-PATCH_VERSION build push
