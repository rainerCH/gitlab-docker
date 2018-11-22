# gitlab-docker Quickstart

### 1. Boot Gitlab
```
docker-compose up
```

### 2. Add Hosts to your Hostsfile

```
## /etc/hosts

127.0.0.1				gitlab.localhost
127.0.0.1				mattermost.localhost
127.0.0.1				pages.localhost
```

### 3. Start and Register a Docker Runner

```
### Register Docker DIND Runner

docker-compose exec runner gitlab-runner register --non-interactive --registration-token="secretToken" --url "http://gitlab.localhost:8888/" --executor="docker" --docker-image="docker:latest" --docker-network-mode="gitlab-network" --docker-volumes /var/run/docker.sock:/var/run/docker.sock --docker-volumes /builds:/builds:rw --docker-volumes /cache
```

---

## Access

```
http://gitlab.localhost:8888                # Gitlab
http://mattermost.localhost:8888            # Mattermost
http://<namespace>.pages.localhost:8888     # Static Project Pages
http://localhost:8025                       # Mailhog
```