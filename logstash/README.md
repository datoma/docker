# build image with 
docker build --label "debian-jessie" -t debjessie:latest logstash

# run container
docker run --name "debian-jessie" -d debjessie

# connect to container
docker exec -ti debian-jessie bash
