```bash
certbot certonly \
  --dns-digitalocean \
  --dns-digitalocean-credentials /etc/letsencrypt/digitalocean/credentials.ini \
  --dns-digitalocean-propagation-seconds 60 \
  -d *.trung.link \
  -d *.blog.trung.link \
  -d trung.link

cerbot renew


sudo ./certbot-auto certonly \
  --server https://acme-v02.api.letsencrypt.org/directory \
  --manual --preferred-challenges dns \
  -d *.trung.cf -d *.lab.trung.cf
```
