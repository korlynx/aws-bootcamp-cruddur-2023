# Week 1 — App Containerization


```sh
cd backend-flask
export FRONTEND_URL="*"
export BACKEND_URL="*"
python3 -m flask run --host=0.0.0.0 --port=4567
cd ..
```

## Build and Run container

- Create a docker file here : backend-flask/Dockerfile

```sh
docker build -t backend-flask ./backend-flask
docker container run --rm -p 4567:4567 -d backend-flask
```

## Send Curl to Test Server

```sh
curl -X GET http://localhost:4567/api/activities/home -H "Accept: application/json" -H "Content-Type: application/json"
```
## Check logs

```sh
docker logs CONTAINER_ID -f
docker logs backend-flask -f
docker logs $CONTAINER_ID -f
```

## Debugging adjacent containers with other containers

```sh
docker run --rm -it curlimages/curl "-X GET http://localhost:4567/api/activities/home -H \"Accept: application/json\" -H \"Content-Type: application/json\""
```

busybosy can be used for debugging

```sh
docker run --rm -it busybosy
```
