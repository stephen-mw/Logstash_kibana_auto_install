[![Build Status](https://travis-ci.org/stephen-mw/Logstash_kibana_auto_install.svg?branch=master)](https://travis-ci.org/stephen-mw/Logstash_kibana_auto_install)

# Update
You probably want to use the newest version of Kibana. This one is no longer supported. You can find the auto install for that here:

https://github.com/stephen-mw/Logstash1.2_kibana3_auto_install

# What is Logstash?
Logstash is a log indexer built on top of elasticsearch. It aggregates logs from multiple sources and allows you to query them using the [Apache Lucene query parser syntax](http://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

Logstash is built on elasticsearch, which allows your data to scale easily. If you run out of space, simply add a new elasticsearch node to your cluster. It's easy to scale with your data.

# How it works
Logstash has two parts, the indexer and the server. The indexer works on a specific datasource to collect logs and ship them to the server. Before shipping the logs you can do interesting things, such as mutate them, add tags, or disregard them altogether.

Adding tags to certain types of logs allows you to quickly retrieve them and keep track of trending information.

The server keeps logs in a redis queue until they can be drained into elasticsearch. Neither redis nor elasticsearch are required to be on the server, but they are nevertheless required.

# The frontend
While not a direct part of the logstash project, Kibana works on top of logstash to give you visualization and montoring tools. Kibana also gives you the flexibility to define patterns and filters and then watch the stream for these matches as they happen in realtime.

![logstash running with varnishncsa](http://i.imgur.com/SwbL8eO.png?1 "Logstash running with Varnishncsa")

# Setup
The entire setup has been automated. Simply run:

```
$ sudo ./logstash_server
```

Elasticsearch, logstash, and redis will be listening on their default port. Kibana will be listening on port 80.

You may want to change the default data directory for Elasticsearch.

### Requirements
There's no special requirements other than Ubuntu 12.04.

The script does make some wide assumptions about the state of your system. It assumes mostly it's a fresh machine without any previous version of elasticsearch, logstash, or java installed (or anything at /etc/logstash).

If these files or directories exist, please remove them before running the script. You can also turn off the "exit on error" flag (```set -e```) at the top of the script to try and resume a broken installation.

# Testing
You can test the installation out in Vagrant first before running it. There's an included Vagrantfile. Simply clone the directory and run:
```bash
$ vagrant up
```
