# HAProxy Role

This role installs haproxy servers as a load balance also configures port 80 and 443 with TCP mode by default.
HAProxy is a free, very fast and reliable reverse-proxy offering high availability, load balancing, and proxying for TCP and HTTP-based applications.
You can change configuration such as frontend and backend servers and ports in /defaults/main.yml.

## HAProxy Requirements

This special requirement is container_engine/podman role , although sometimes you need to change the DNS (change to shecan) when installing the Podman package or when pulling an image from Docker Hub.

## HAProxy Variables

| Name                    | Status   | Example                                           | Description                                                        |
| ----------------------- | -------- | ------------------------------------------------- | ------------------------------------------------------------------ |
| haproxy_podman_image    | Required | docker.io/haproxytech/haproxy-alpine              | Docker image url                                                   |
| haproxy_version         | Required | 2.8.1                                             | Docker image version                                               |
| haproxy_container_ports | Required | 80:80                                             | ports of podman container                                          |
| haproxy_listen_port     | Required | 80                                                | Necessary port for role verification                               |
| haproxy_frontend        | Default  | name,bind_address,port,mode,default_backend,state | Frontends information                                              |
| haproxy_backend         | Default  | name,mode,balance_method,servers                  | Backends information                                               |
| haproxy_proxy_protocol  | Required | true or false                                     | If true this role sets proxy protocol configuration in haproxy.cfg |

## TAGS

pkg: For installation HAProxy systemd package.
podman: For installation HAProxy podman service.

Role Variables including any variables that are in defaults/main.yml and inventory.yml.

## HAProxy Example Playbook

```
- name: ansible_role_haproxy
  hosts: all
  become: true
  roles:
   - podman
   - haproxy
```

## License
MIT
## Author Information
Amirhesamshahab72@gmail.com
