# **Reddit** 

Group Elements
==================

 - José Soares
 - Marcelo Gomes
 - Maria Costa
 - Pedro Cabral
 - Ricardo Leite




**A Brief Overview**
===================

[Reddit](https://reddit.com) is a social news and link aggregrator website where users, or ***Redditors***, post links from the Internet, as well as  their original content. 
It was launched in June 23rd, 2005, and as of the begining of 2016, it has a few billion monthly page views.
It is built mainly in Python, with a PostgreSQL database, and several side technologies added over time, as the website needed to scale.


----------


Its main technological components, by subjective order of importance, include:

 - Python: With too many libraries to name, it brings a ton of components. A noteworthy library would be Pylons.

 -  Pylons: Open source project that improves web frameworks, it's written in python. Originally the project was a single web framework.

 -  PostgreSQL: Primary backend database. It is used for storing data on Accounts, Subreddits, Links, Comments, Votes, etc. 
PostgreSQL is an advanced object-relational database management system that supports an extended subset of the SQL standard, including transactions, foreign keys, subqueries, triggers, user-defined types and functions. It has native programming interfaces for C/C++, Java, .Net, Perl, Python, Ruby, Tcl, ODBC, among others.

 - HAProxy: Essentially an HTTP load balancer, suited for very high traffic web sites. In fact, it powers quite a number of the world's most visited ones.
 
 - Cassandra: For caching.
 
 - Memcached: For caching and ad-hoc locking/synchronization between architectural components. Almost everything on reddit depends on memcached running properly.

 - RabbitMQ: An implementation of AMQP, used to store jobs for offline processing.


----------


Reddit is primarily deployed on AWS, along with S3 storage for static objects.

Amazon Elastic Compute Cloud (Amazon EC2) is a web service [AWS] that provides resizable compute capacity in the cloud. 
It was designed to facilitate cloud computing on the web scale for developers. The service interface simple Amazon EC2 Web makes it possible to obtain and configure capacity, with minimal friction. 

###*Why AWS?*

 - **It has a Scale computing elastic web:** 
	 * It can increase or decrease capacity within minutes. It is possible to commission hundreds or thousands of server instances simultaneously. Everything is controlled with the Web services APIs, the application can automatically expand or collapse, depending on the needs.

 - **It is completely controlled:**
	* It can stop one instance, while maintaining the data on boot partition, and then restart the same instance. Instances can be reset remotely, using web service APIs.

 - **It can be used with other Amazon Web services:**
	* It works in conjunction with Amazon Simple Storage Service (Amazon S3), Amazon Relational Database Service (Amazon RDS), 
Amazon SimpleDB and Amazon Simple Queue Service (Amazon SQS), to provide a complete solution for computing, processing consultation and storage of a wide variety of applications.

 - **It is trustworthy:**
	* Amazon EC2 offers a highly reliable environment, where replacement instances can be rapidly and previously ordered. The service runs within the data center and the proven network infrastructure from Amazon. 

 - **It is safe:**
	* instances are located in a Virtual Private Cloud (VPC) with some IP range specified by the user. For additional insulation, you can provide your EC2 resources dedicated hosts or as dedicated instances.