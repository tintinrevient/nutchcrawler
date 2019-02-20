# nutchcrawler

This crawler is based on Apache Nutch 2.3, MongoDB 2.6.7, Elastic Search 1.4.4 and Kibana 4.0.1.

**Nutch Setup**

> git clone https://github.com/tintinrevient/nutchcrawler.git
> cd nutchcrawler
> ant
> cd runtime/local
> mkdir urls
> cd urls
> vim seed.txt

A sample seed.txt looks like this:
https://www.freundevonfreunden.com/
https://...

> cd ..
> cd conf
> vim regex-urlfilter.txt

Update below line to limit the crawled URLs to your expected domain:
# accept anything else
+^https?://([a-z0-9-]+\.)*www\.freundevonfreunden\.com/
