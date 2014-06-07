# Instant MongoDB sharded cluster
This repository provides a Vagrantfile, Dockerfile and a bootstrap script to create MongoDB Cluster using a virtual machine built on Virtualbox software hypervisor. After setup is complete shared MongoDB sharded cluster on a single virtual machine running on your local machine.

MongoDB cluster consisted of the following docker containers

 - **mongos1-3r1-3**: Mongod server with three replica sets distributes on six mongo containers. 
 - **configservers1-3**: Stores metadata for sharded cluster distributed on three mongo containers.
 - **mongos1**:	Mongo routing service installed on one mongo container.
 - **skydock**:	Used for service discovery and inserts internal docker images records into skydns.
 - **skydns**: Used as internal DNS for containers.

There unfortunately some hard-coded timeouts due to timing issues with MongoDB. 

## Installation:

### Linux
Install Virtualbox based off the [installation instructions](https://www.virtualbox.org/wiki/Linux_Downloads).

### MacOS

#### Install Homebrew
First, install [Homebrew](http://brew.sh/).

	ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"

#### Install Virtualbox and Vagrant
Install VirtualBox and Vagrant using [Brew Cask](https://github.com/phinze/homebrew-cask).

	brew tap phinze/homebrew-cask
	brew install brew-cask
	brew cask install virtualbox
	brew cask install vagrant

## Check out the repository

	git clone git@github.com:jacksoncage/mongo-docker.git
	cd mongo-docker
	vagrant up

## Setup Cluster
This will pull all the images from [Docker index](https://index.docker.io/u/jacksoncage/mongo/) and setup Mongodb sharded cluster.

	vagrant ssh
	./docker/start_cluster.sh"

You should now be able connect to mongos1 and the new sharded cluster:

	MongoDB Cluster is now ready to use
	Connect to cluster by:
	$ mongo --port 49550


## ToDo
 - Save MongoDB data on persistent storage

## Built upon
 - [MongoDB Sharded Cluster by Sebastian Voss](https://github.com/sebastianvoss/docker)
 - [MongoDB](http://www.mongodb.org/)
 - [Skydock](https://github.com/crosbymichael/skydock)
 - [Skydns](https://github.com/skynetservices/skydns)
 - [Docker](https://github.com/dotcloud/docker/)