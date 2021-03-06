---
title: 'Notes From Geeksessions: Beyond the Database'
date: 2007-10-02 00:00:00 Z
layout: post
---

Below are raw notes from tonight’s Geeksessions event in San Francisco. All told, while the speakers did fine, I wasn’t wowed with the content. See for yourself.

Josh Fergus from Sunthe pro-RDBMS guy
-------------------------------------

relational dbs good for some things (security), not others (scalability)
 data is durable: survives changes to the application
 not really much to say, use dbs for what theyre good for

Chad Walters from Powerset on Giant Scale Systems
-------------------------------------------------

ACID means constraints
 SQL is hard to grok at scale
 talking about very large computational domains delivered at very high volumes
 use a ton of commodity hardware to overcome failures
 modern rdbms dont deliver on reliability
 replication starts to be a headache with rdbms
 use something like GFS or Hadoop that was designed for the task
 why the application/db divide?
 move the computation to the data MapReduce, specialized data structures
 sounds in general like a digestion of the Google approach

Paul Querna from Bloglines
--------------------------

BloglinesFS: store every blog post ever
 currently storing several billion posts
 inspired by MogileFS and GFS, but different
 two main components: PodServer (serves metadata) on ItemDBs (storage nodes)
 PodServer: stateless, finds nodes on startup, provides cross-data center replication, spigots for dumping data
 ItemDB: serves web sites as chunks, local indexes for for attributes like Date, Post URL, etc.
 request goes from app server to PodServer to ItemDB
 crawler writes to PodServer which then writes to ItemDBs
 75 data machines of 2?300GB disks, one ItemDB per disk, no RAID
 crawl all blogs every 30 minutes, thousands of concurrent reads + writes per second
 wed do it all over again because there arent any choices out there
 Hadoop too specialized for web search, not good for write-heavy data
 goal isnt to build an open source project, but to launch a product

Arnold Goldberg from eBayeBay by the numbers
--------------------------------------------

(not talking about PayPal, Skype, just eBay ecommerce platform)
 tons of users, transactions, listings, api developers
 600 database instances, 20 billion sql statements per day (95% reads), 5600 active tables, 1.8 petabytes
 original pattern: separating writes and reads: write once and replicate to many
 replication will kill you if you try to do it at scale […] its a mess
 new pattern: lookup host finds where your data lives (by primary key)
 use persistent database connections, but know the costs: each connection takes a process/thread
 figure out where your scalability cliff is and test
 connection concentration tier was a pain
 to scale, vector based on what youre looking for and distribute
