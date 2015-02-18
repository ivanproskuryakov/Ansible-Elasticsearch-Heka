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
ssh -p 22 vagrant@192.168.111.222 / user: vagrant
```

## Heka usage
Heka listen 192.168.111.222:8325, check just open in browser **http://192.168.111.222:8325/?ParamA=mydata**<br/>
To check Elastc Index run one of the following on Vagrant host
```
curl http://127.0.0.1:9200/_search?pretty
curl http://127.0.0.1:9200/_search?pretty | grep ParamA

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