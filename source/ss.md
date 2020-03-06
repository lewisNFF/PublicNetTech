#个人账户启动
ss-server -c /etc/shadowsocks-libev/config.json
## 启动ss
ss-manager -m aes-256-cfb -u --manager-address 127.0.0.1:6001
ss-manager -m chacha20-ietf-poly1305 -u --manager-address 127.0.0.1:6001

## 启动ssmgr
ssmgr -c ~/.ssmgr/ss.yml
## 启动webgui
ssmgr -c ~/.ssmgr/webgui.yml


ss.yml
```yml
type: s
shadowsocks:
  address: 127.0.0.1:6001
manager:
  address: 0.0.0.0:6002
  password: '123456'
```
webgui.yml
```
type: m
manager:
  address: xxx.xxx.xxx.xxx:6002
  password: '123456'
plugins:
  flowSaver:
    use: true
  user:
    use: true
  account:
    use: true
  email:
    use: true
    type: 'smtp'
    username: 'username'
    password: 'password'
    host: 'smtp.your-email.com'
  webgui:
    use: true
    host: '0.0.0.0'
    port: '8098'
    site: 'http://xxx.xxx.xxx.xxx'
    # icon: 'icon.png'
    # skin: 'default'
    # googleAnalytics: 'UA-xxxxxxxx-x'
    # gcmSenderId: '476902381496'
    # gcmAPIKey: 'AAAAGzddLRc:XXXXXXXXXXXXXX'
db: 'webgui.sqlite'
# 从 0.30 开始需要配置 redis
redis:
  host: '127.0.0.1'
  port: 6379
  password: '6677'
  db: 0
```