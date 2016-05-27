Process view 

Subtitle:
U - User
H - Http server
M - Memcached
C - Cassandra Database
P - PostGres Database
Q - RabitMQ
Co- Consumer


POST

When someone wants to insert a post on Reddit the first step is to send a HTTP POST to the HTTP server, in the next step, the server not only check Memcached to check if there is already information present using a GET through a unix or a TCP socket but also checks on Cassandra using a SELECT instead. Finnaly the server hits the Postgres with several queries getting the result from the database in a form of a Remote Procedure call. The final step of this procedure consists on the HTTP server sending the response to the the user.

COMMENT

The process of creating a comment on Reddit starts from a HTTP POST to the HTTP server by a user, that end his interaction with Reddit right after the server insert the comment on Memcached and on Postgres, receiving a OK response but will not see the added comment in the right place of the webpage. The process of reordenating the comment tree is done in "backend". 
After sending the response to the user, server add que comment to the queue waiting for the consumer to handle it, ordenating the comment tree and adding it to Cassandra and memcached in the last step.

UPVOTE / DOWNVOTE

When a user upvote or downvote a "thing" on Reddit the same mechanism are called, to start a HTTP post is sent to the HTTP server. Then Memcached increments the information displayed on the page instantly and the Up/Downvote is sent to the queue to recompute the information and proceed to reordenate the information on the page if needed, at this point the user receives the response from the server. 
After the Up/Downvote is on the queue it will be fetched by the consumer that will hit the Postgres database with queries in order to retrieve information and to instert the updated information into cassandra.