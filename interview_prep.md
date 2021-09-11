 Interview Prep
TODO: more design practice. AWS solution-architect practice.

Design interviews:
1) DO NOT GO TO DETAILED. DO NOT DO FLOW AND BACKTRACK. TAKE PAUSES. 
2) keep it simple. Take a step back and have a look at entire architecture.
3) Form your thoughts. Avoid speaking without thinking the point through. Always pause
4) Name off the shelf technologies we could use
5) Avoid silver bullets

Clarity of thoughts. Flexibility. Knowledge 


#garage-question
Design a reservation/payment system for parking garage.
1) Clarify requirements.
reserve+get ticket, two people cant book same spot, 3 types of vehicles, cost based on time and type.
What is inputs/outputs. Who are the users. How are they going to use it. What do they need it for?
1.5) Clarify scope.
Endtoend vs API. What clients do we want to support. Do we require auth, analytics, integration with existing systems.
What is the scale? What is read/write ratio. What is expected response time.
2) Public endpoints
/reserve (garage_id,start_time, end_time,) -> spot_id,reservation_id
/cancel (reservation_id)
/createaccount (email, password,name,lastname)
/login
/payment (reservation_id)
3) Private endpoints
/calculatepayment(reservation_id)
/freespots(garage_id,vehicle_type,time)
/allocate_spot(garage_id,vehicle_type,time)
4) Table design
Reservation (id,garageid,spotid,starttime,endtime,paid)
Garage (id,zipcode,rate_compact,ratereg,ratemid,ratelarge)
Spots (spotted, garaged, vehicle_type, status)
Users (id, email, password, firstname, last name)
Vehicles (id, userid, type, license)

5)Infrastructure:
Loadbalanced Frontend webapp -> Backend  API -> cache -> DB
(We need to read more than write so add read replicas)
(High consistency so consider write locking. Also consider sharing)
Availability & Reliability & Scalability & Security

6) Tradeoffs. Why use db. What to use for cache.

#instagram-question
1)Get requirements:
Upload images from mobile client (what clients,
Users can follow other users (what 
Generate a feed of image (latency? Only people you follow or explore feature?
Should scale to 10 million users (10 million monthly basis, 2 photos per month, 5MB per photo
2) Data model (use relational model (we have relational model)) (Many to 1. 1 to 1, many to many.
Users (name, email, location)
Photos (userid, caption, location, path,
Following (userid, followerid)
3) Infrastructure
Database, withS3 path, s3, read replicas, app servers, cache, loadbalancer

#tinyurl

#words-in-documents

#tinder
Store profiles (images, how many 5) 
Recommend matches. 
Not matches 
Direct messaging
(Don’t do too many requirements)
1) Store profiles: gateway service + profile service + db + image service + s3
2)
 
#stockdata
Is there auth?
Need monitoring 
Poll or push? 
Can clients configure what they receive?
Is the content static?
What is specific to each client?
What are the access patterns of clients?

Cloud front -> LB -> Frontend web api -> backend -> DAX -> DB

Choose dynamodb since relational not needed.
Backend Endpoints: /open?symbol=  /close?symbol=  /high?symbol=  /low?symbol= /all?symbol.

Have frontend/backend emit /metrics endpoint and monitor with prometheus/grafana/alertmanager

Use ELK.

Ingestion service or etl for new stock data. 

Reliability, run services in HA. Kubernetes takes care of a bunch. Makes development and deployment easier. Can run on different nodes if you want.
security: no auth so main issue is DDOS? Add in a WAF. Prepared statements in the frontend queries.

sharding: could shard based on a key, say first letter of stock

#stockdata-solution
Your solution was good but propose different alternatives.
1) Store in simple text files and hold on s3 behind sftp server

I have assumed that we are sending data based on a frontend. This is not always the case. We can send files or json, or just design an api.

#social-network
? What is scale. Userbase and data store? Any limits on how many connections. What is data access patterns? Is it read or write heavy?
Data structure I recommend is adjacency list rather than adjacency metric. Don’t recommend relational since we store a list for each userid. Is the one request all I design for? What is latency required for the request? Should I precompute?

Algorithm well we can use djiktras shortest path.

SOLUTION: first clarify the problem and BASIC steps first before jumping into “we use djiktras”. (Which is wrong. Djiktras is for WEIGHTED graphs.
For search we would use BFS or bidirectional bfs. 
Think of simple to scaling instead of doing the scaling problem first.
Multiple machines shard users, sharing function to designate user, lookup on machine, shard to second machine.
Optimization. Shard people by location to reduce hops.
Optimization. Have a visited hash table. 
