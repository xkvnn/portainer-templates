# Portainer Templates

## Templates URL
https://raw.githubusercontent.com/xkvnn/portainer-templates/main/templates.json

https://raw.githubusercontent.com/portainer/templates/master/templates-2.0.json

## Stack Config
https://github.com/xkvnn/portainer-templates

stacks/*/docker-compose.yml

## Start Portainer
```
docker stop portainer
docker rm portainer
docker run -d -p 9000:9000 --name portainer \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /etc/localtime:/etc/localtime:ro \
    -v portainer:/data \
    -l diun.enable=true \
    -e AGENT_SECRET=AGENT_SECRET \
    portainer/portainer-ce:alpine
```
```
docker stop portainer_agent
docker rm portainer_agent
docker run -d -p 9001:9001 --name portainer_agent --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /var/lib/docker/volumes:/var/lib/docker/volumes \
    -e AGENT_SECRET=AGENT_SECRET \
    portainer/agent:alpine
```
