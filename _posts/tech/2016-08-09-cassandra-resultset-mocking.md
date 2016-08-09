---
layout: post
title: How to mock a resultSet after Cassandra execute
category: Technologies
tags: Cassandra Mocking ResultSet
description: Step by step guidance from mocking Cassandra resultSet
---
I have never thought that using Spock to mock a resultSet from Cassandra execute method is that difficult.

After reading [this post](http://christopher-batey.blogspot.com/2013/06/mocking-iterable-objects-generically.html) I came up with a method that allows you to mock a resultSet.

Here is the step by step guidance:

### Mock a Cassandra Session

  def mockCassandraSession = Mock(Session)

### Mock a resultSet for Cassandra
  def mockResultSet = Mock(ResultSet)

### Mock resultSet methods from Iterable

  Since Cassandra resultSet extends Iterable, we also need to mock a iterator object.

    def mockIterator = Mock(Iterator)

  Then set it to resultSet's iterator()

    mockResultSet.iterator() >> { mockIterator }

  Mock hashNext() method, e.g:

    3 * mockIterator.hasNext() >> { true }
    1 * mockIterator.hasNext() >> { false }

    keep in mind that the last one is always false otherwise we may have infinite loop

  Mock next() method:
    mockIterator.next() >> { mockRow() }

  And then we can mock our execute() method
    mockCassandraSession.execute(_) >> { mockResultSet }

To be continued.
