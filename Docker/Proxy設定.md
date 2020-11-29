## Proxy設定

### Dcoker 17.07 and higher
`$ vi ~/.docker/config.json`
```
{
 "proxies":
 {
   "default":
   {
     "httpProxy": "http://127.0.0.1:3001",
     "httpsProxy": "http://127.0.0.1:3001",
     "noProxy": "*.test.example.com,.example2.com"
   }
 }
}
```

### Docker 17.06 and lower
|Variable|Dockerfile example|`docker run` Example|
|----------|--------------------------------------|----------------------------------------|
|HTTP_PROXY|ENV HTTP_PROXY="http://127.0.0.1:3001"|--env HTTP_PROXY="http://127.0.0.1:3001"|
|HTTPS_PROXY|ENV HTTPS_PROXY="https://127.0.0.1:3001"|--env HTTPS_PROXY="https://127.0.0.1:3001"|
|NO_PROXY|ENV NO_PROXY="*.test.example.com,.example2.com"|--env NO_PROXY="*.test.example.com,.example2.com"|

### Others Way
`$ sudo mkdir -p /etc/systemd/system/docker.service.d`
`$ sudo vi /etc/systemd/system/docker.service.d/http-proxy.conf`
```
[Service]
Environment="HTTP_PROXY=http://proxy.example.com:80/"
```
`$ sudo systemctl daemon-reload`
`$ sudo systemctl show docker --property Environment`
`$ sudo systemctl restart docker`

### 参考
- [Configure Docker to use a proxy server](https://docs.docker.com/network/proxy/)
- [Amazon Linux 2 に Docker をインストールする](https://www.softek.co.jp/SID/support/sidfmvm/guide/install-docker-amazonlinux2.html)
