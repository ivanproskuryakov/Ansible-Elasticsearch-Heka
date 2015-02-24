## Installation
Launch Vagrant
```
1. vagrant up
```
Provision vagrant with ansible
```
2. ansible-playbook -i hosts/vagrant.host playbooks/jenkins-playbook.yml -vvvv
```

## Access vagrant
```
ssh -p 22 vagrant@192.168.111.222 / password: vagrant
```

## Heka usage
Heka listen 192.168.111.222:8325 for a data. To check is her, just open in browser: http://192.168.111.222:8325/?ParamA=mydata<br/>
This will populate Elastic with the data "ParamA=mydata", to check use following
```
curl http://192.168.111.222:9200/_search?pretty
curl http://192.168.111.222:9200/_search?pretty | grep ParamA

```
or open in browser: http://192.168.111.222:9200/_search?pretty

Flush Elastic index:
```
curl -XDELETE localhost:9200/backend-general
```

Config: /playbooks/roles/heka-commands/heka/main.toml
```
[HttpListenInput]
address = "192.168.111.222:8325"

[ESJsonEncoder]
index = "backend-general"
es_index_from_timestamp = true
type_name = "%{Type}" #Type = heka.httpdata.request
#fields = ["Uuid","Timestamp","Type","Logger","Hostname","Payload"]

[ElasticSearchOutput]
message_matcher = "TRUE"
#message_matcher = "Type == 'heka.httpdata.request' && Fields[UserAgent] == 'somedata'"
server = "http://127.0.0.1:9200"
flush_interval = 5000
flush_count = 10
encoder = "ESJsonEncoder"
```