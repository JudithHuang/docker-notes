# docker-machine

## Create machine

- 确保 local 主机可以免秘密登录 server, 将 local 主机的公钥加入到 server root 用户的 /root/.ssh/authorized_keys 中
    
```shell
# 在 local 主机执行如下命令, 将 local 公钥文件复制到 server home 目录下
scp /home/user/.ssh/id_rsa.pub user@remote_host_ip:/home/user/
# 在 server 主机上执行如下命令, 将 local 主机的公钥追加到 authorized_keys 文件中
cat /home/user/id_rsa.pb >> /root/.ssh/authorized_keys
```

- 使用 generic 方式创建 machine

```shell
docker-machine create \
  --driver generic \
  --generic-ip-address=server_host_ip \
  --generic-ssh-key ~/.ssh/id_rsa \
  judith # machine 名字
```
