# nutchcrawler

This crawler is based on Apache Nutch 2.3, MongoDB 2.6.7, Elastic Search 1.4.4 and Kibana 4.0.1.

**Nutch Setup**
```
user:~ admin$ git clone https://github.com/tintinrevient/nutchcrawler.git
user:~ admin$ cd nutchcrawler
user:nutchcrawler admin$ ant
user:nutchcrawler admin$ cd runtime/local
user:local admin$ mkdir urls
user:local admin$ cd urls
user:urls admin$ vim seed.txt
```

A sample seed.txt looks like this:  
```
https://www.freundevonfreunden.com/  
https://...
```

```
user:urls admin$ cd ..
user:local admin$ cd conf
user:conf admin$ vim regex-urlfilter.txt
```

Update below line to limit the crawled URLs to your expected domain:  
```
+^https?://([a-z0-9-]+\.)*www\.freundevonfreunden\.com/
```

**MongoDB Setup**
```
user:~ admin$ cd mongodb
user:mongodb admin$ mkdir data, conf, log
user:mongodb admin$ cd conf
user:conf admin$ vim mongodb.yml  
```

A sample mongodb.yml
```
net:
  port: 27017
  bindIp: 127.0.0.1
systemLog:
  destination: file
  path: "~/mongodb/log/mongodb.log"
  logAppend: true
processManagement:
  fork: true
  pidFilePath: "~/mongodb/log/mongodb.pid"
storage:
  dbPath: "~/mongodb/data"
  directoryPerDB: true
  smallFiles: true
```

Start MongoDB:
```
user:mongodb admin$ ./bin/mongod -f conf/mongdb.yml 
```

Verify if MongoDB is started:
```
user:mongodb admin$ ./bin/mongo
> show dbs
admin  (empty)
```

**Elastic Search Setup**

Start Elastic Search:
```
user:~ admin$ cd elasticsearch
user:elasticsearch admin$ ./bin/elasticsearch -d
```

Verify if Elastic Search is started:
```
user:elasticsearch admin$ curl -XGET 'http://localhost:9200'
{
  "status" : 200,
  "name" : "test",
  "cluster_name" : "elasticsearch",
  "version" : {
    "number" : "1.4.4",
    "build_hash" : "c88f77ffc81301dfa9dfd81ca2232f09588bd512",
    "build_timestamp" : "2015-02-19T13:05:36Z",
    "build_snapshot" : false,
    "lucene_version" : "4.10.3"
  },
  "tagline" : "You Know, for Search"
}
```

**Kibana Setup**

Start Kibana:
```
user:~ admin$ cd kibana
user:kibana admin$ ./bin/kibana
```

Verify if Kibana is started:  
Visit http://localhost:5601
