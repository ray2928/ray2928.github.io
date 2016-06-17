---
layout: post
title: What I Have Learned from TDD Courses
category: Thoughts
tags: TDD refactoring
description: Thoughts after learning TDD
---

### Thoughts about TDD

TDD(Test Driven Development) is more of a learning process, which does not require you to give a perfect solution at the first time.

Try think of a simple test case, then use the simplest way to pass that test case. If the test pass, we should add another test to make our code more generic. It may take a lot more time to start with TDD, but since the most of time in software development cycle is maintainance, it would be a good solution to use TDD to increase our confidence of our code and shorten our time to fix the bug.

### About refactoring

Priority:
1. All tests passed
2. Easy for communication
3. All methods should be written once and only once
4. As simple as possible

From top to bottom, if anything on top can not be achieved then we should not consider below.
