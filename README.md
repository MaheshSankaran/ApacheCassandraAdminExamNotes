# Apache Cassandra Admin Exam Notes
Apache Cassandra 3.x Administrator Associate Certification Exam Notes


### DS201: DataStax Enterprise 6 Foundations of Apache Cassandra - https://academy.datastax.com/resources/ds201-datastax-enterprise-6-foundations-of-apache-cassandra ###
* Partitions
  * Group rows physically together on disk based on the partition key.
  * The partitioner hashes the partition key values to create a partition token.
  * Used to place data on the ring.
  * https://www.datastax.com/dev/blog/the-most-important-thing-to-know-in-cassandra-data-modeling-the-primary-key
  * https://docs.datastax.com/en/archived/cql/3.3/cql/cql_using/useCompositePartitionKeyConcept.html
* Clustering Columns
  * Non-partition section of the PK.
  * Clustering columns order data within a partition. https://docs.datastax.com/en/dse/5.1/cql/cql/cql_using/whereClustering.html
  * Equality or range queries can be performed on clustering columns.
  * Default ascending order.
  * https://docs.datastax.com/en/dse/6.7/cql/cql/cql_using/useCompoundPrimaryKeyConcept.html
  * https://www.bmc.com/blogs/cassandra-clustering-columns-partition-composite-key/
* Application Connectivity
  * Drivers - https://docs.datastax.com/en/driver-matrix/doc/driver_matrix/common/driverMatrix.html
* Node
  * 6K-12K transactions/seconds/core
  * 2-4TB
* Ring
  * Notes can have four statuses in the ring UP / DOWN / JOINING / LEAVING.
  * https://academy.datastax.com/units/2017-ring-dse-foundations-apache-cassandra?resource=ds201-datastax-enterprise-6-foundations-of-apache-cassandra
* Peer to Peer
  * No one is a leader, no one is a follower. All nodes are equal.
* Vnodes
  * https://docs.datastax.com/en/archived/cassandra/3.0/cassandra/architecture/archDataDistributeVnodesUsing.html
  * https://www.youtube.com/watch?v=G4SMNU1aOJg
* Gossip
  * https://www.edureka.co/blog/gossip-protocol-in-cassandra/
  * https://www.linkedin.com/pulse/gossip-protocol-inside-apache-cassandra-soham-saha/
* Snitch
* Replication
* Consistency
* Hinted Handoff
* Read Repair
* Node Sync
* Write Path
* Read Path
* Compaction
* Advanced Performance

### DS210: DataStax Enterprise 6 Operations with Apache Cassandra -https://academy.datastax.com/resources/ds210-datastax-enterprise-6-operations-with-apache-cassandra ###
* Clusters
* Cluster Sizing
* cassandra-stress
* top
* dstat
  * Versatile tool for generating system resource statistics.
  * https://linux.die.net/man/1/dstat
  * dstat -am
* nodetool
  * A command line interface for managing a cluster.
  * http://cassandra.apache.org/doc/latest/tools/nodetool/nodetool.html
  * https://docs.datastax.com/en/archived/cassandra/3.0/cassandra/tools/toolsNodetool.html
  * https://www.youtube.com/watch?v=0qr9z0lsbuk
  * https://www.youtube.com/watch?v=Sz7OiUWgs5U
* JVM
* Adding Nodes
  * https://docs.datastax.com/en/archived/cassandra/3.0/cassandra/operations/opsAddNodeToCluster.html
* Removing Nodes
  * https://docs.datastax.com/en/archived/cassandra/3.0/cassandra/operations/opsRemoveNode.html
* Bootstrapping
  * http://cassandra.apache.org/doc/latest/operating/topo_changes.html
  * https://thelastpickle.com/blog/2017/05/23/auto-bootstrapping-part1.html
  * https://thelastpickle.com/blog/2018/08/02/Re-Bootstrapping-Without-Bootstrapping.html
  * https://de.slideshare.net/ArunitGupta1/boot-strapping-in-cassandra
* Replacing a Downed Node
* Size Tiered Compaction
  * Default compaction strategy.
  * Good for insert heavy and general workloads.
* Leveled Compaction
  * Groups sstables into levels of a fixed size limit.
  * Each level is 10 times larger than the previous.
  * Best for read heavy workloads or where there are more updates than inserts.
* Time Window Compaction
  * Designed to work on time-series data.
  * One sstable for each time window.
* Repair
* Nodesync
* sstablesplit
  * Splits SSTable files into multiple SSTables of a maximum designated size.
  * Do not execute when Cassandra is running.
  * We might sometimes wish to split a very large sstable to ensure compaction occurs on it.
  * sstablesplit -m 500 /path/to/massive/sstable-Data.db
* Backup
* JVM
* Garbage Collection
* Heap Dump
* Kernel Tuning
  * https://docs.datastax.com/en/dse/6.7/dse-dev/datastax_enterprise/config/configRecommendedSettings.html
  * https://tobert.github.io/pages/als-cassandra-21-tuning-guide.html
* Hardware
* Cloud
* Security

### Quiz Trivia ###

* What is the node that handles a request called? Coordinator node.
* Write Path Order Commitlog > MemTable > SSTable.
* Cassandra does not do any writes or deletes in place.
* SSTables are immutable.
* Compaction is the progress of taking small SSTables and merges them into bigger ones.
* Last writes wins - based on Timestamps.
*
