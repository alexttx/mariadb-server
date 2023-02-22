# Notes on MariaDB

The MySQL/MariaDB plugin API lets you implement subsets.  We could probably get
limited a prototype working quickly, and then have some team members focus on
completing the integration, while others worked on SSI.

## Source Code

https://github.com/MariaDB/server

## Building
```
rm -fr build
mkdir build
cd build
cmake .. -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DCONNECT_WITH_BSON=OFF -DCONNECT_WITH_MONGO=OFF
cp compile_commands.json ..
make -j
make install DESTDIR=install
```

## Variations
### MariaDB SkySQL (database as a service)

MariaDB SkySQL is a database-as-a-service (DBaaS) enabling you to deploy and
manage MariaDB Enterprise Server, Xpand distributed SQL or ColumnStore
analytical databases with only a few clicks. SkySQL combines automation with
human expertise to support and manage mission-critical deployments.

### MariaDB Enterprise Server (SQL Server)
MariaDB Enterprise Server is built on MariaDB Community Server and, with the aid
of MariaDB MaxScale database proxy, delivers best-in-class performance, data
security, replication, clustering and high availability. MariaDB Enterprise
Server can scale from a single node to global scale, for any workload – from
systems of record (OLTP) to analytics (OLAP), in any cloud: private, public,
hybrid, or multi-cloud.

### MariaDB Xpand (Distributed SQL)
MariaDB Xpand is chosen by developers when creating large, mission-critical,
read/write scale applications which require ACID-level consistency and
enterprise-grade reliability. Xpand combines the scalability of a NoSQL database
with the robustness of a SQL database. As with MariaDB Enterprise Server and
ColumnStore, Xpand is front-ended by MaxScale database proxy for high
availability, disaster recovery and enhanced security. Xpand can be deployed in
the cloud as a SkySQL database service on AWS or Google Cloud and runs across
multiple public cloud regional centers and on-premise for multi-cloud and hybrid
operations.

### MariaDB ColumnStore (Analytics)
MariaDB ColumnStore extends MariaDB Enterprise Server with distributed, columnar
storage and a massively parallel processing (MPP) shared nothing architecture,
transforming it into a standalone or distributed data warehouse for ad hoc SQL
queries and advanced analytics without the need to create indexes. With MariaDB
ColumnStore running in SkySQL you get a cloud data warehouse and DBaaS in one
service.

## Resources
Documentation:
- https://mariadb.com/docs/

General development:
- https://mariadb.com/kb/en/development-articles/

Storage Engines:
- https://mariadb.com/kb/en/storage-engines-storage-engine-development/
- https://mariadb.com/kb/en/choosing-the-right-storage-engine/

MyRocks Deep Dive:
- https://www.slideshare.net/matsunobu/myrocks-deep-dive

## Table Flags
See ../sql/handler.h
