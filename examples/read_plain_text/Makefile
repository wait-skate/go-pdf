
name ?= $(notdir $(shell pwd))
targets += ~/$(name)

domain = $(shell hostname -d)

go.mod :
	go mod init $(domain)/$(name)
	go mod tidy

~/$(name) : go.mod
~/$(name) : $(wildcard *.go)
	go build -tags osusergo,netgo
	go test
	if test -e ./test.sh ; then ./test.sh ; fi
	mv $(name) $@


.PHONY: all
.DEFAULT_GOAL = all
all : $(targets)
$(info targets = $(targets))
