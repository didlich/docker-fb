Run all the parts needed for finderbox infrastructure with Docker and Docker-compose.

# TBD
The server part missing in this Docker-compose configuration.

# Requirements

## Setup

1. Install [Docker](http://docker.io).
2. Install [Docker-compose](http://docs.docker.com/compose/install/).
3. Clone this repository

# Usage

In the first step set your environment variables:

```bash
    export LOCAL_USER_ID=`id -u $USER`
```

the local user id is important if you use host volumes to persist container data. It's one
of the Docker best practice to avoid root permission in the container.
    
```bash
    export FB_PG_USER=???
    export FB_PG_PWD=???
    export FB_PG_DB=???
```


This information is used by the postgresql docker container to setup the database.
In the next step link your data directories to allow persist the data. 
Create symbolic links for
- elasticsearch
- postgresql

i.e.: 
    
```bash
    mkdir /home/user/docker
    ln -s /home/user/docker ./data/volumes   
```

Start the finderbox stack using *docker-compose*:

```bash
$ docker-compose up
```

You can also choose to run it in background (detached mode):

```bash
$ docker-compose up -d
```

To **stop** or **restart** all continer use docker-compose with these commands.