## Uptime-Kuma with persistent sqlite database

Run uptime kuma with persisten sqlite database via [litestream](https://litestream.io)

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
  litestream-uptime-kuma:latest
```
with

```
LITESTREAM_ACCESS_KEY_ID=xxxx
LITESTREAM_SECRET_ACCESS_KEY=xxxx
LITESTREAM_BUCKET=xxxx
LITESTREAM_URL=https://s3.us-east-1.amazonaws.com
LITESTREAM_PATH=xxxx
LITESTREAM_REGION=us-east-1
```

Note that `LITESTREAM_URL` should be the appropriate region, or point to the endpoint of a compatible service if not using S3 directly (e.g., R2).

## Environment Variables:
  - `UPTIME_KUMA_VERSION`: Kuma version
  - `LITESTREAM_PATH`: Prefix for storage
  - `LITESTREAM_VERSION`: Litestream version
  - `LITESTREAM_ACCESS_KEY_ID`: Storage bucket acces key id
  - `LITESTREAM_SECRET_ACCESS_KEY`: Storage bucket access key
  - `LITESTREAM_BUCKET`: Storage bucket
  - `LITESTREAM_URL`: Storage url endpoint

## TODO
- Use disrtoless image  `gcr.io/distroless/nodejs18-debian11`
- Use `node:slim` - currently some ssl issues
