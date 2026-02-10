`SMEMBERS` command is used to retrieve all members of a set stored at a given key.

`SMEMBERS` returns an array containing all the elements present within the specified set.
Redis sets are unordered collections.


## SADD

SADD Commands is used to add members to a set stored at the ley. If the member already exists, then it is ignored, then a new set is created and the members are added into it.


# PING

Redis `Ping` command is used to check the connection between a client and the Redis Server. It serves several purposes:
- Connection Testing: Verifies if the Redis server is reachable and responsive.
- Liveness Check: Can be used to determine if a connection is still active and alive.
- 
