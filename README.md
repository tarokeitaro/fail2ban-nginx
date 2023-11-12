# fail2ban-nginx
Fail2ban Jail Configuration for nginx - Anti DDoS Protection

## How to use?
- Create a new file in `/etc/fail2ban/filter.d/` with the name **`badbot.local`**,
- Copy the contents of `badbot.local` in this repository to your server,
- Create or edit a file in `/etc/fail2ban/jail.local`
- Copy the contents of `jail.local` in this repository to your server, you can put it at the bottom.
- Restart the `fail2ban` service.

## Testing
**Test regex**
```shell
clear;sudo fail2ban-regex /var/log/nginx/access.log /etc/fail2ban/filter.d/badbot.local
```
You will see a list of IPs detected as suspicious from your Nginx logs.

## Cheat sheet
**Check badbot status**
```shell
fail2ban-client status badbot
```

**Ban IP via fail2ban**
```shell
sudo fail2ban-client set badbot banip [ip]
```

**Unban IP via fail2ban**
```shell
sudo fail2ban-client set badbot unbanip [ip]
```

**Export list of banned IPs**
```shell
clear;sudo fail2ban-client get badbot banip --with-time > banip-ddmmyyyy.txt
```
