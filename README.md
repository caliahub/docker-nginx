1、基于caliahub/alpine:3.11.5镜像制作

2、nginx版本1.18.0

3、nginx工作路径/etc/nginx

4、nginx静态文件路径/usr/share/nginx/html

5、nginx日志路径/var/log/nginx


#### docker启动示例：
```
docker run -d -p 80:80 -p 443:443 --restart=always caliahub/nginx:1.18.0
```

#### docker-compose启动示例：
```
version: '3'
services:
  redis:
    image: caliahub/nginx:1.18.0
    restart: always
    ports:
      - 80:80
      - 443:443
```

#### k8s application/deployment.yaml启动示例：
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 1
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: caliahub/nginx:1.18.0
        ports:
        - containerPort: 80
        - containerPort: 443
```
