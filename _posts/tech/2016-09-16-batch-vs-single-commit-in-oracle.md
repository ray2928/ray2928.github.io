---
layout: post
title: Batch commit vs single commit in Oracle using Java
category: Technologies
tags: Oracle Batch Java
description: By using batch commit, we are able to improve our performance
---
The slowness of loading data to Oracle has been a problem for a week.

After reading [this post](https://www.simple-talk.com/sql/performance/comparing-multiple-rows-insert-vs-single-row-insert-with-three-data-load-methods/), My colleagues and I came up with an idea to change from loading row one by one and instead using a batch to increase the speed.

### Pseudo code for using batch writer
/**
 *  def writer = new BatchWriter()
 *
 *  while (some condition... ) {
 *     writer.write(actions)
 *   }
 *  writer.flushCurrentBatch()
*/

###To create a BatchWriter Class:

BatchWriter(Sql oracleWriter) {
  this.connection = oracleWriter.getDataSource().getConnection()
  this.connection.setAutoCommit(false)
}

By using batch writer, we are able to increase our loading performance from 10,000/sec to 400,000/sec, a huge improvement!
