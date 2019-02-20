# nutchcrawler

This crawler is based on Apache Nutch 2.3, MongoDB 2.6.7, Elastic Search 1.4.4 and Kibana 4.0.1.

**Nutch Setup**

1. git clone https://github.com/tintinrevient/nutchcrawler.git
2. cd nutchcrawler
3. ant
4. cd runtime/local
5. mkdir urls
6. cd urls
7. vim seed.txt

A sample seed.txt looks like this:
https://www.freundevonfreunden.com/
https://...

8. cd ..
9. cd conf
10. vim regex-urlfilter.txt

Update below line to limit the crawled URLs to your expected domain:
+^https?://([a-z0-9-]+\.)*www\.freundevonfreunden\.com/
