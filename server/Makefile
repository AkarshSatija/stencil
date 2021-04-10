NAME="github.com/odpf/stencil"
VERSION=$(shell git describe --always --tags 2>/dev/null)
COVERFILE="/tmp/stencil.coverprofile"
DIST_PATH="out"

.PHONY: all build clean

all: build

build:
	go build -ldflags "-X main.Version=${VERSION}" ${NAME} -o "${DIST_PATH}/stencil"

clean:
	rm -rf stencil dist/

install-protoc:
	@echo "> installing protobuf-compiler"
	whoami
	sudo apt-get update
	sudo apt install -y protobuf-compiler
	which protoc
	protoc --version

test:
	go test ./... -coverprofile=coverage.out

test-coverage: test
	go tool cover -html=coverage.out

dist:
	@bash ./scripts/build.sh

test_ci: install-protoc test