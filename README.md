[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Ffluential%2Flitestream-uptime-kuma%2F&count_bg=%2379C83D&title_bg=%23555555&icon=github.svg&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

## Uptime-Kuma with persistent sqlite database

Run uptime kuma with persisten sqlite database via [litestream](https://litestream.io)

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template/UfDasl?referralCode=373)

## Usage

### Build

```
docker build -t litestream-uptime-kuma .
```

### Run

Upstream repo recommends a method that logs credentials to the console if run in the shell. The following will load credentials from a .env:
```bash
docker run -d \
  --name uptime-kuma \
  --restart=unless-stopped \
  -p 3001:3001 \
  -v uptime-kuma:/app/data \
  --env-file ~/.uptime-kuma.env \
  fluential/litestream-uptime-kuma:latest
```
with

```
LITESTREAM_ACCESS_KEY_ID=xxxx
LITESTREAM_SECRET_ACCESS_KEY=xxxx
LITESTREAM_BUCKET=xxxx
LITESTREAM_URL=xxxx
```

## Environment Variables:
  - `UPTIME_KUMA_VERSION`: Kuma version
  - `LITESTREAM_VERSION`: Litestream version
  - `LITESTREAM_ACCESS_KEY_ID`: Storage bucket acces key id
  - `LITESTREAM_SECRET_ACCESS_KEY`: Storage bucket access key
  - `LITESTREAM_BUCKET`: Storage bucket
  - `LITESTREAM_URL`: Storage url endpoint

## TODO
- Use disrtoless image  `gcr.io/distroless/nodejs18-debian11`
- Use `node:slim` - currently some ssl issues
