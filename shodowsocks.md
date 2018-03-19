 ubuntu翻墙步骤
 1. shodowsocks客户端下载与配置
  - sudo apt-get update
  - sudo python --version
  - sudo apt-get install python-gevent python-pip
  - sudo pip install shadowsocks
  {
  "server":"79.45.115.110",
  "server_port":12801,
  "local_port":10808,
  "password":"123456",
  "timeout":600,
  "method":"aes-256-cfb"
  }
  sslocal -c /usr/shadowsocks/shadowsocks.json
 2. 翻墙后:
 - sudo apt install supervisor
 - sudo supervisorctl status
 - sudo vim /etc/supervisor/supervisord.conf
 - sudo supervisorctl reload
 > [program:shadowsocks]
   command=sslocal -c /home/daath/SSproxy/shadowsocks.json
   ;autostart=true
   ;autorestart=true
   user=nobody
   redirect_stderr=true
   stdout_logfile=/home/daath/SSproxy/shadowsocks.log
