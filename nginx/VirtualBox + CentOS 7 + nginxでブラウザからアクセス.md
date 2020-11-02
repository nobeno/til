### VirtualBox + CentOS 7 + nginxでブラウザからアクセス

1. `yum update`

2. `vi /etc/yum.repos.d/nginx.repo`
```
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1
```

3. `yum install nginx`

4. `nginx -v`

5. `sudo systemctl start nginx`</br>
   `sudo systemctl status nginx`
   
6. SELinux・firewalldの設定

7. `curl localhost:"port number"`


参考URL：https://hrroct.hatenablog.com/entry/2018/07/15/214051
