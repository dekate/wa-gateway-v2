# Requirements

Linux
Whatsapp Beta Multi Device


# How-to-Run
## Using Supervisord (RECOMMENDED)
- install supervisord:
```
sudo yum -y install supervisor
```
- Enable daemon for supervisor:
```
sudo systemctl start supervisord
sudo systemctl enable supervisord
sudo systemctl status supervisord
```
- set config for apps in /etc/supervisord/dfywa.conf with:
```
[program:dfy-wagw]
command=/home/nginx/domains/wa.3278018.dekate.id/public/md_whatsapp
autostart=true
autorestart=true
startretries=10
user=nginx
directory=/home/nginx/domains/wa.3278018.dekate.id/public/
environment=APP_SETTINGS="/home/nginx/domains/wa.3278018.dekate.id/public/.env"
redirect_stderr=true
stdout_logfile=/home/nginx/domains/wa.3278018.dekate.id/log/wagw.log
stdout_logfile_maxbytes=50MB
stdout_logfile_backups=10
```
- update and restart supervisor:
```
supervisorctl update
supervsorctl restart
```

## or use nohup ./md-whatsapp &