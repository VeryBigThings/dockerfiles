# ============= #
# POOR MANS CLI #
# ============= #

require-%:
	@ if [ "${${*}}" = "" ]; then \
		echo "ERROR: Environment variable not set: \"$*\""; \
		exit 1; \
	fi

# ============= #

build: require-VERSION
	docker build \
		-t elixir:${VERSION} \
		-t verybigthings/elixir:${VERSION} \
		.

push: require-VERSION
	docker push verybigthings/elixir:$(VERSION)

build-and-push: require-VERSION build push
