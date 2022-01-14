# ansible-podman-wiki

Uses Ansible to deploy [WikiJS](https://wiki.js) with PostgreSQL storage (wikijs v3.x compatible) using (rootless) Podman

- postgres:11-alpine
- gitea/gitea:1.15.9-rootless
- requarks/wiki:2

It uses a bridged network and adds it's local IP to the `/etc/hosts` of every container so that we can use the hostname for resolving. 

The goal is to have all containers rootless and readonly

### TODO
* Let gitea use postgresql as backend
* ingress (nginx/traefik?) for incoming requests
  * Make sure port 80/443 can be used using sysctl for port <1024 binding
* `noexec` on shared directories might be good
