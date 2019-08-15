# DEMO 2

把一個本機端的 PORT 轉成 https 網址。

## Step

```bash
cd web
docker-compose up -d
docker-compose ps
cd ..

cd serveo
docker-compose up -d && docker-compose logs -f
cd ..

cd web
docker-compose logs -f
cd ..

# close
cd serveo
nano docker-compose.yml # 需要確認一下 docker-compose.yml 裡面的指令
docker-compose down
cd ..

cd web
docker-compose down
cd ..
```

## 參考資料

* [從容器內連線到 Host 的方法 (Windows / macOS)](https://nickjanetakis.com/blog/docker-tip-65-get-your-docker-hosts-ip-address-from-in-a-container)
* [Docker for Linux 的功能請求 issue (尚未合併)](https://github.com/docker/for-linux/issues/264)