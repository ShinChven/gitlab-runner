# gitlab-runner

docker-compose deployment and configs

```yaml
version: "3.5"

services:

  runner:
    image: gitlab/gitlab-runner:alpine
    container_name: gitlab-runner
    restart: always
    volumes:
      - "/etc/gitlab-runner:/etc/gitlab-runner"
      - "/var/run/docker.sock:/var/run/docker.sock"
```

```toml
concurrent = 1
check_interval = 0

[[runners]]
  executor = "docker"
  [runners.docker]
    image = "ubuntu"
    volumes = [
      "/usr/bin/docker:/usr/bin/docker",
      "/var/run/docker.sock:/var/run/docker.sock",
      "/usr/local/bin/docker-compose:/usr/local/bin/docker-compose",
      "/cache"
    ]
    shm_size = 0
  [runners.cache]
    [runners.cache.s3]
    [runners.cache.gcs]
```
