# fail2ban-nginx
Fail2ban Jail Configuration for nginx - Anti Abuse & DDoS Protection

## How to use?
- Copy the file of `filter.d` in this repository to your server,
- Create or edit a file in `/etc/fail2ban/jail.local`
- Copy the contents of `jail.local` in this repository to your server, you can put it at the bottom.
- Restart the `fail2ban` service.

## Testing
**Test regex**
```shell
clear;sudo fail2ban-regex /var/log/nginx/access.log /etc/fail2ban/filter.d/nginx-abuse-protect.conf
```
You will see a list of IPs detected as suspicious from your Nginx logs.

## Cheat sheet
**Check nginx-abuse-protect status**
```shell
fail2ban-client status nginx-abuse-protect
```

**Ban IP via fail2ban**
```shell
sudo fail2ban-client set nginx-abuse-protect banip [ip]
```

**Unban IP via fail2ban**
```shell
sudo fail2ban-client set nginx-abuse-protect unbanip [ip]
```

**Export list of banned IPs**
```shell
clear;sudo fail2ban-client get nginx-abuse-protect banip --with-time > fail2ban-banip-$(date +'%Y-%m-%d').txt
```
