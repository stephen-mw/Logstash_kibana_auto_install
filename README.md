# What is Logstash?
Logstash is a log indexer built on top of elasticsearch. It aggregates logs from multiple sources and allows you to query them using the [Apache Lucene query parser syntax](http://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

Logstash is built on elasticsearch, which allows your data to scale easily. If you run out of space, simply add a new elasticsearch node to your cluster. It's easy to scale with your data.

# How it works
Logstash has two parts, the indexer and the server. The indexer works on a specific datasource to collect logs and ship them to the server. Before shipping the logs you can do interesting things, such as mutate them, add tags, or disgard them altogether.

Adding tags to certain types of logs allows you to quickly retrieve them and keep track of trending information.

The server keeps these logs in a redis queue until it can be drained into elasticsearch. Neither redis nor elasticsearch are required to be on the server, but they are nevertheless required. 

# The frontend
While not a direct part of the logstash project, Kibana works on top of logstash to give you visualization and montoring tools. Kibana also gives you the flexability to define patterns and filters and then watch the stream for these matches come in realtime.

![logstash running with varnishncsa](http://i.imgur.com/SwbL8eO.png?1 "Logstash running with Varnishncsa")

# Setup
The entire setup has been automated. Simply run:

```
$ sudo ./logstash_server
```

All of the logstash services (elasticsearch, logstash, and Kibana) will be listening on their default ports.

Some things you may want to change before running the bootstrap:

1. The data directory in elasticsearch/elasticsearch.yml
2.  
