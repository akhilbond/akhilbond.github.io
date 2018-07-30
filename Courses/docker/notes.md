---
layout: page
title: Docker and Containers: The Big Picture
permalink: /Courses/docker/
---

# This course is a Pluralsight course taught by Nigel Poulton.

## What are containers?

- Setting the scene
  - Applications run businesses
  - Applications run on servers
    - Procurement lead times
    - Up-front capex costs
    - Ongoing opex costs
  - Hypervisors allow multiple apps per server
  - Trouble with Hypervisors
    - Each app on the hypervisor has an individual OS and VM which use CPU, RAM, and disk just in order to run.
    - May have license costs
    - Requires admin time

- Containers - They allow companies to setup more apps on a single OS on a server. This removes the requirement of having separate VM's and an OS for each of them.

## What is Docker?

- Docker Inc is the major company and sponsor behind container technology.
- The Docker Project
  - This is different from the Docker Project. Docker Inc began the project, however the Docker Project is opensource.
  - It is the technology behind running and controlling containers.
  - It is being heavily backed by big name tech companies and is also being heavily used.

- The Open Container Initiative(OCI)
  - It's like a governance council that is responsible for standards around the most basic and fundamental components of the container ecosystem, the container format, and the container runtime.

## What kind of work do containers do?

- A stateless app or service is an app or service that does not keep any data.
- A stateful app or service is an app or service that keeps track of previous data and remembers what it has done.
- Docker and containers can handle stateful and stateless workloads.
- Docker containers are data persistent by nature.

## Docker Hub and Other Container Registries

- Container registries are centralized hubs to store and retrieve docker container images.
- Docker Hub is the official Docker registry from Docker Inc.
- Container registries are becoming central to application infrastructure and application delivery.

## Are Docker and Containers ready for Production and the Enterprise?

- Offerings from Docker Inc.
  - Docker Engine - The core of Docker that runs all the apps.
    - Experimental channel - Nightly releases
    - Stable channel - Two-month releases
    - Commercially Supported channel - releases every six months
  - Docker Swarm - Native Docker clustering
  - Docker Content Trust
  - Docker Hub
  - Docker Tutum
  - Docker Trusted Registry
  - Docker Universal Control Plane

## Container Orchestration

- Apps are comprised of multiple parts
  - Thousands of containers
  - Hundreds of hosts
- Orchestration:
  - Defines our app
  - Provisions infrastructure
  - Deploys our app
  - Scales our app
- Docker Orchestration Products
  - Docker Machine
  - Docker Compose
  - Docker Swarm
  - Docker Tutum
