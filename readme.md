logs message should have:
request id: can be that twitter handle
request with response data duration
request initiated datetime
request done datetime
response status

# To set client machine to push logs to remote server

Above the line “#First some standard log files. Log by facility” we’ll add the following:

*.*                         @@127.0.0.1:10514

# FILEBEAT
### SETUP PHASE

	docker run docker.elastic.co/beats/filebeat:7.17.5 setup -E setup.kibana.host=kibana:5601 -E output.elasticsearch.hosts=["elasticsearch:9200"]

### config yaml

	curl -L -O https://raw.githubusercontent.com/elastic/beats/7.17/deploy/docker/filebeat.docker.yml

### run filebeat

	docker run --rm  --name=filebeat --user=root --volume="$(pwd)/filebeat/filebeat.docker.yml:/usr/share/filebeat/filebeat.yml:ro" --volume="/var/log/:/var/log/:ro" docker.elastic.co/beats/filebeat:7.17.5 filebeat -e --strict.perms=false