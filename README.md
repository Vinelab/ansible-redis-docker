# Redis - Ansible Role
Configure & launch [Redis](http://redis.io) instances using [Docker](http:://docker.com) containers.

### Installation
Add this repository as a submodule of your git with:

```
git submodule add git@github.com:Vinelab/ansible-redis-docker roles/redis
```

Or simply clone this repository directly into your *roles* directory:

```
git clone git@github.com:Vinelab/ansible-redis-docker roles/redis
```

### Usage

##### Quickstart

```yaml
---
hosts: cache
roles:
    - redis
```

#### Configuration

Key                 | Description                           | Default
--------            | ------------------------              | ------------
image               | The image to be used when running the container. | vinelab/redis
name                | The name to be used by the container when it runs. | redis
host (ambassador)   | Used to indicate the Redis database host that the ambassador should connect to. | localhost
port                | The port to expose Redis on when running the container. | 6379
ram                 | How much RAM is this container allowed. | 256MB
ambassador          | Indicate whether this is an ambassador container or not. | `false`

##### Examples

###### Redis Database

```yaml
---
- hosts: cache
  roles:
    - role: redis
      name: cache
      ram: 2GB
```

###### Redis Ambassador

```yaml
---
- hosts: cache
  roles:
    - role: redis
      name: cache
      ram: 512MB
      host: 192.168.10.29
      port: 3636
      ambassador: true
```

###### Custom Image

```yaml
---
- hosts: cache
  roles:
    - role: redis
      image: dockerfiles/redis
      name: appcache
      ram: 128MB
```

### Tags
All tasks have the following tags:

- redis
- launch
