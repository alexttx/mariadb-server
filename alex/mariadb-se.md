# List of MariaDB Storage Engines

SE Features:
- Transactions
- XA Transactions
- Table Partitioning
- Indexes
- Blobs
- Blob Indexes
- Parital Column Reads


## Recommended by MariaDB

These SEs are mentioned in the MariaDB's recommendations when [Choosing the
right storage Engine](https://mariadb.com/kb/en/choosing-the-right-storage-engine/).

### General Purpose
#### InnoDB

#### Aria (ha_maria)

Note: ha_maria implments both S3 SE and Aria SE.

The Aria storage engine was previously known as Maria, (see, the Aria Name). In
current releases of MariaDB, you can refer to the engine as Maria or Aria. As
this will change in future releases, please update references in your scripts
and automation to use the correct name.

Aria is a crash-safe alternative to MyISAM.

#### MyISAM (ha_myisam)

Non-transactional storage engine with good performance and small data footprint.

MyISAM was the default storage engine from MySQL 3.23 until it was replaced by
InnoDB in MariaDB and MySQL 5.5. It's a light, non-transactional engine with
great performance, is easy to copy between systems and has a small data
footprint.

Users are encouraged to rather use the Aria storage engine for new applications,
which has even better performance and the goal of being crash-safe.

### Scaling, Partitioning
#### Spider (ha_spider)

The Spider storage engine supports partitioning and XA transactions, and allows
tables of different MariaDB instances to be handled as if they were on the same
instance.

#### Column Store (ha_mcs.cpp)

From `storage/columnstore/columnstore/README.md`:
- MariaDB ColumnStore Storage/Execution engine 6.X.
- Built by porting InfiniDB 4.6.7 on MariaDB and adding entirely new features
  not found anywhere else.

#### Merge (ha_myisammrg)
### Compression, Archive
#### MyRocks (ha_rocksdb.cc)

#### Archive (ha_archive.cc)

From ha_archive.cc:

This example was written as a test case for a customer who needed a storage
engine without indexes that could compress data very well.  This storage engine
only does inserts. No replace, deletes, or updates. All reads are complete table
scans. Compression is done through a combination of packing and making use of
the zlib library

### Connectiong to Other Data Sources
#### Connect (ha_connect.cc)
From `storage/connect/ha_connect.cc`:

The ha_connect engine is a stubbed storage engine that enables to create tables
based on external data. Principally they are based on plain files of many
different types, but also on collections of such files, collection of tables,
local or remote MySQL/MariaDB tables retrieved via MySQL API, ODBC/JDBC tables
retrieving data from other DBMS having an ODBC/JDBC server, and even virtual
tables.

ha_connect will let you create/open/delete tables, the created table can be done
specifying an already existing file, the drop table command will just suppress
the table definition but not the eventual data file.

Indexes are not supported for all table types but data can be inserted, updated
or deleted.

#### CSV (ha_tina.cc)

The CSV Storage Engine can read and append to files stored in CSV (comma-separated-values) format.

However, since MariaDB 10.0, a better storage engine is able to read and write such files: CONNECT.

Limitations:
- CSV tables do not support indexing.
- CSV tables cannot be partitioned.
- Columns in CSV tables must be declared as NOT NULL.
- No transactions.

### Search Optimized
#### SphinxSE (ha_sphinx)

The Sphinx storage engine (SphinxSE) is a storage engine that talks to searchd
(the Sphinx daemon) to enable text searching. Sphinx and SphinxSE is used as a
faster and more customizable alternative to MariaDB's built-in full-text search.

#### Mroonga (ha_mroonga)

Supports full-text search of Chineese, Japanese and Korean content using column store.

### Cache, Read-only
#### Memory SE (ha_heap)

https://mariadb.com/kb/en/memory-storage-engine/

### Other Specialized SEs
#### S3 (ha_maria.cc)

Note: `ha_maria` implments both S3 SE and Aria SE.

S3 is a read-only storage engine that stores its data in Amazon S3.

#### Sequence Storage Engine

Allows ascending or descending sequences of numbers.

It creates completely virtual, ephemeral tables automatically when you need
them. There is no way to create a Sequence table explicitly. Nor are they ever
written to disk or create .frm files. They are read-only, transactional, and
support XA.

#### Open Query GRAPH (ha_oqgraph)

Open Query GRAPH computation engine for handling hierarchies (tree structures) and complex graphs.

#### Blackhole (ha_blackhole)

The Blackhole storage engine accepts data but does not store it and always returns an empty
result. This can be useful in replication environments, for example, if you want to run complex
filtering rules on a slave without incurring any overhead on a master.

## Other SEs
### Example (ha_example)

## Deprecated SEs
### Federated (ha_federated)
### TokuDB
