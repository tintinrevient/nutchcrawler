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
