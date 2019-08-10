# DEMO 3

使用自己架設的 serveo 伺服器。

## Step (server)

```bash
git clone https://github.com/taichunmin/docker-serveo-server.git coscup-2019
cd coscup-2019

# 設定 letsencrypt 的憑證
cd dns-cloudflare

cp cloudflare.example.ini cloudflare.ini
chown root:root cloudflare.ini
chmod 600 cloudflare.ini
nano cloudflare.ini # 在這裡設定自己的 E-mail 和 API_KEY

cp docker-compose.example.yml docker-compose.yml
nano docker-compose.yml
# 本範例改成 certonly -n --agree-tos --cert-name serveo --dns-cloudflare --dns-cloudflare-credentials /cloudflare.ini --email taichunmin@gmail.com -d coscup-2019.taichunmin.idv.tw -d *.coscup-2019.taichunmin.idv.tw

sudo docker-compose run --rm certbot
cd ..

cp docker-compose.example.yml docker-compose.yml
nano docker-compose.yml
# 本範例改成 serveo -port=22 -http_port=80 -https_port=443 -private_key_path=/root/.ssh/id_ed25519 -cert_dir=/certs -domain coscup-2019.taichunmin.idv.tw

docker-compose up -d && docker-compose logs -f

# 移除憑證
cd dns-cloudflare
docker-compose run --rm certbot revoke --cert-path /etc/letsencrypt/archive/serveo/cert1.pem
cd ..
```

## Step (client)

```bash
cd demo3
docker-compose up
```
