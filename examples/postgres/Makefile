.PHONY: format
format: ## Format code
	goimports -w .
	go fmt ./...
	fieldalignment -fix ./...

.PHONY: lint
lint: ## Lint code
	golangci-lint run

.PHONY: test
test: ## Runs tests
	go install github.com/mfridman/tparse@latest | go mod tidy
	GOEXPERIMENT=nocoverageredesign PROFILE=local go test -parallel 20 -json -cover ./... | tparse -all -pass

.PHONY: update
update: # Install and update go modules
	go get -t -u ./...
