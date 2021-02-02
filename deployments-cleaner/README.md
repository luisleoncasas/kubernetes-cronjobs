# Deployments Cleaner

The localenv wrapper uses [ktctl](https://alibaba.github.io/kt-connect/) to create a proxy container that is able to communicate with a given Kubernetes cluster and also allows traffic to be received from it.

However, using this tool creates Kubernetes deployments that are only deleted if the container terminations is handled propperly, otherwise there will be dangling resources that need to be cleaned.

This cronjob executes a python script that looks for duplicated deployments identified with a 'developerId' label and only allows the most recent one to persist.