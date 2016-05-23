# **Reddit** 


Group Elements
==================

 - José Soares
 - Marcelo Gomes
 - Maria Costa
 - Pedro Cabral
 - Ricardo Leite


#Table of Contents
==================
* [A Brief Overview](#a-brief-overview)
* [4+1 Architectural Views](#41-architectural-views)
  * [Logical View](#logical-view)
  * [Process View](#process-view)
  * [Development view](#development-view)
  * [Physical view](#physical-view)
  * [Scenarios](#scenarios)


#**A Brief Overview**
===================

[Reddit](https://reddit.com) is a social news and link aggregrator website where users, or ***Redditors***, post links from the Internet, as well as  their original content. 
It was launched in June 23rd, 2005, and as of the begining of 2016, it has a few billion monthly page views.
The backend is mostly built in Python, with a PostgreSQL database, and several side technologies added over time, as the website needed to keep up with the larger and larger traffic.


----------
####**System requirements:**
 The system requires a server-grade machine running a linux distributuion (of the users choise) and amd64.


----------
Its main technological components, by subjective order of importance, include:

 - Python: With a ton of extra libraries. A noteworthy library would be Pylons.

 -  Pylons: A web framework.

 -  PostgreSQL: Primary backend database. It is used for storing data on Accounts, Subreddits, Links, Comments, Votes, etc. 
PostgreSQL is an advanced object-relational database management system that supports an extended subset of the SQL standard, including transactions, foreign keys, subqueries, triggers, user-defined types and functions. It has native programming interfaces for C/C++, Java, .Net, Perl, Python, Ruby, Tcl, ODBC, among others.

 - HAProxy: Essentially an HTTP load balancer, suited for very high traffic web sites. In fact, it powers quite a number of the world's most visited ones.
 
 - Cassandra: Secondary database system, used for caching (NoSQL, key-value store).
 
 - Memcached: For caching and ad-hoc locking/synchronization between architectural components. Almost everything on reddit depends on memcached running properly.

 - RabbitMQ: An implementation of AMQP, used to store jobs for offline processing.


----------

####**Functional requirements:**

Reddit has to be able to serve a social news and link aggregator website, where users can submit content, and comment on other user's content.
Users are able to 'upvote' and 'downvote' submissions and user comments, and user comments for a given submission are presented in a orderable tree-style. Submissions belong to a given area, called 'subreddit'. Users can subscribe to subreddits.
Reddit presents a 'front page' for a given user depending of their subreddit subscriptions, and whether they are a (registered) user at all. This page has recent submissions ordered according to score.

####**Non functional requirements:**

- Response Time - Need to ensure a fast response so the  browsing is fluid even with big throughput or data volumes.
- Avaliability - The Downtime of the website must be minimized, having the service running as long as possible, keeping it avaliable to the user.
- Scalability - Need to ensure that even with an overload of the website service will continue to run ensuring acceptable QoS.
- Authentication/Security - Must allow the identification of users who try to access his account , while protecting the system from possible invaders.
- Usability - QoS affects the user's interaction with the website and his satisfaction with it , and the QoS will have to ensure that the user wants to re-use it so usability must be a point to take in count.


----------


Reddit is primarily deployed on AWS, along with S3 storage for static objects.

Amazon Elastic Compute Cloud (Amazon EC2) is a web service [AWS] that provides resizable compute capacity in the cloud. 
It was designed to facilitate cloud computing on the web scale for developers. The service interface simple Amazon EC2 Web makes it possible to obtain and configure capacity, with minimal friction.

###*Why AWS?*

 - **Scales up or down as needed:**
	 * AWS allows launching and destroying 'instances' on the run, with little wait time before the new 'hardware' is acquired. This is useful for websites that have spikes of traffic, as one can simply keep launching instances to meet the load requirements.
	 
 - **Instance management can be done via API:**
	* Meaning instance launch/destruction lifecycle can be done without having a sysadmin watching 24/7. Utilities such as instance reboot and reset are also provided, which eases up administration and allows 'cleaning up' as needed.

 - **It can be used with other Amazon services:**
	* It works in conjunction with Amazon Simple Storage Service (Amazon S3), Amazon Relational Database Service (Amazon RDS), 
Amazon SimpleDB and Amazon Simple Queue Service (Amazon SQS), to provide a complete solution for computing, processing consultation and storage of a wide variety of applications.

 - **It is reliable:**
	* Amazon EC2 guarantees 99.95% availability, and is widely used in industry. It eases some of the vendor lock-in fears.

<a href="#table-of-contents">Back to top</a>

#**4+1 Architectural Views**

#**Logical View
![Logical View Diagram](./diagrams/logical_view_1.png)

![Logical View Diagram](./diagrams/logical_view_2.png)

![Logical View Diagram](./diagrams/logical_view_3.png)

![Logical View Diagram](./diagrams/logical_view_4_package.png)

<a href="#table-of-contents">Back to top</a>

#**Process View

![Process View Diagram](./diagrams/process_view_1_post.png)

![Process View Diagram](./diagrams/process_view_2_comment.png)

![Process View Diagram](./diagrams/process_view_3_updown.png)


<a href="#table-of-contents">Back to top</a>


#**Development view

<a href="#table-of-contents">Back to top</a>


#**Physical view
![Process View Diagram](./diagrams/physical_view.png)

![Process View Diagram](./diagrams/postgres.png)

<a href="#table-of-contents">Back to top</a>

#**Scenarios


<a href="#table-of-contents">Back to top</a>

