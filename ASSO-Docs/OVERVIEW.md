# Reddit - A Brief Overview

Reddit is a social news and link aggregrator website where users or *Redditors*, post links from the Internet and original content. It was launched in 23 of June in the year of 2005. As of begining of 2016, it has a few billion of monthly page views.
It is built mainly in Python, with a PostgreSQL database, and several side technologies added over time as the website needed to scale.

Main technological components (by subjective order of importance)
* Python (with too many libraries to name, although a noteworthy one would be pylons [web framework])
(of course Python itself brings a ton of [hopefully seperate] components)
* PostgreSQL (primary backend database. It is used for storing data on Accounts, Subreddits, Links, Comments, Votes, etc. PostgreSQL is an advanced object-relational database management system that supports an extended subset of the SQL standard, including transactions, foreign keys, subqueries, triggers, user-defined types and functions. It has native programming interfaces for C/C++, Java, .Net, Perl, Python, Ruby, Tcl, ODBC, among others.)
* HAProxy (essentially an HTTP load balancer, suited for very high traffic web sites and powers quite a number of the world's most visited ones)
* Cassandra (for some fancy caching)
* Memcached (for caching [duh], and ad-hoc locking/synchronization between architectural components. Almost everything on reddit depends on memcached running properly)
* RabbitMQ (fancy implementation of AMQP, used to store jobs for offline processing)

Reddit is primarily deployed on AWS, along with S3 storage for static objects.

Amazon Elastic Compute Cloud (Amazon EC2) is a web service[AWS] that provides resizable compute capacity in the cloud. It was designed to facilitate cloud computing on the web scale for developers. The service interface simple Amazon EC2 Web allows to obtain and configure capacity with minimal friction. 
Why AWS?
Scale computing elastic web

* increase or decrease capacity within minutes. It is possible to commission a hundreds or thousands of server instances simultaneously. Everything is controlled with the Web services APIs, the application can automatically expand or collapse, depending needs.

Completely controlled

* can stop one instance while maintaining the data on boot partition and then restart the same instance. Instances can be reset remotely using web service APIs.
Can use with other Amazon Web services

* works in conjunction with Amazon Simple Storage Service (Amazon S3), Amazon Relational Database Service (Amazon RDS), 
Amazon SimpleDB and Amazon Simple Queue Service (Amazon SQS) to provide a complete solution for computing, processing consultation and storage of a wide variety of applications.

Trustworthy

* amazon EC2 offers a highly reliable environment where replacement instances can be rapidly and previously ordered. The service runs within the data center and the proven network infrastructure from Amazon. 

Safety

* instances are located in a Virtual Private Cloud (VPC) with some IP range specified by the user. For additional insulation, you can provide your EC2 resources dedicated hosts or as dedicated instances. .
  