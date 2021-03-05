# Bookinfo Rating Service

Rating service has been developed on NodeJS

## License

MIT License

## How to run with Docker

```bash
# Build rating
docker build -t ratings .
# Run MongoDB Container
docker run -d --name mongodb -p 27017:27017 \
  -v $(pwd)/databases:/docker-entrypoint-initdb.d bitnami/mongodb:4.4.4-debian-10-r5
# Test connect
docker exec -it mongodb mongo
show dbs
exit
# Run rating with connect DB
docker run -d --name ratings -p 8080:8080 --link mongodb:mongodb \
  -e SERVICE_VERSION=v2 -e 'MONGO_DB_URL=mongodb://mongodb:27017/ratings' ratings
```

* Test with path `/ratings/1`

## How to run with Docker

```bash
docker-compose up
```
