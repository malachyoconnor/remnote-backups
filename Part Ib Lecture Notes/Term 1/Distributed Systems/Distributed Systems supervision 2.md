- 
-  _**Exercise 13**_ . Using the Lamport and vector timestamps calculated in Exercise 10 and 12, state whether or not the following events can be determined to have a happens-before relationship.   
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4atqIBUEAzm7OncyN5qB3j5Z5XjQtc_OHDZgMdXZh6kXNeqKApIIRpARrwbyAHUyX7k7ndM-H0MBpStyrugFtkC4DMVZEVYv2pTPR9uWBOaXYXUGmwbk1reIC3dx1sE2.png)    ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9jwOOpv8Z8WqVwxq7ynfW03XwQFEn7ipkP88FMsmB5DkrGrmrNBuwEUhIDojkOzdAeBx17jEOVmlWrU2whx6-qnXAjz4jqukHzSSGc3F-r53v3Rg82YAzsXevXp8Bh-Z.png)  
    - Lamport:  
        - Send(m2) ⇒ send(m3) - Yes, because they occurred at the same node, and L(m2) < L(m3) ⇒ $a \rightarrow b$ 
        - Send(m3) ⇒ send(m5) - No, because they didn't occur on the same node, it's not a message from a to b and there's no chain $a \rightarrow x_1 \rightarrow ... \rightarrow x_n \rightarrow b$ . $a||b$ 
        - Send(m5) ⇒ send(m9) - Yes, because we have the chain of events 4 (send m5) ⇒ 5 ⇒ 6 ⇒ 7 ⇒ 8 (send m9) - we can easily prove the happens-before chain is correct as they are all on the same node and all have L(x) < L(x+1) (they are in order in the execution order)
    - Vector: 
        - Send(m2) ⇒ send(m3) - Yes because all values of the vector clock are lesser or equal
        - Send(m3) ⇒ send(m5) - No, they are concurrent as some values are lesser and some are greater between the two vector clocks
        - Send(m5) ⇒ send(m9) - Yes, because all values of the vector clock are lesser or equal
-  _**Exercise 14:**_    We have seen several types of physical clocks (time-of-day clocks with NTP, monotonic clocks) and logical clocks. For each of the following uses of time, explain which type of clock is the most appropriate: ^^process scheduling^^; I/O; ^^distributed filesystem consistency^^; ^^cryptographic certificate validity^^; concurrent database updates.  
    - **Process Scheduling**: A monotonic timing clock, as each process will be apportioned a time quantum in which they can be processed - It should be monotonic as we don't want any sudden jumps backwards due to NTP corrections. While a logical clock consisting of clock cycles could be considered, this could result in some jobs takin inordinate amounts of time (consider I/O) as they require few clock cycles but take a long time - thus time should be used. 
    - ^^**I/O**^^^^: ???^^ 
    - **Distributed filesystem consistency**: Logical vector clocks (with tombstones), as we want a total order of events to ensure we can compare replicas and decide with certainty who is correct.
    - **Cryptographic certificate validity**: Physical time-of-day clocks with NTP should be used. Physical time because the certificate must be valid for a set of physical days. Time-of-day with NTP because we want the time to be human understandable and because it is the most ubiquitous form of time-keeping. 
    - **Concurrent database updates**: Logical vector clocks. We wish to know with certainty which event arrived last, and we'll choose using FIFO - if an update was issued after it should overwrite. Logical vector clocks provide this. We won't use time, due to clock-drift and leap-second issues. 
- ^^ _**Exercise 15:**_ ^^^^ Prove that causal broadcast also satisfies the requirements of FIFO broadcast, and that FIFO-total order broadcast also satisfies the requirements of causal broadcast.^^ 
    - 
    --------------------- Portal ---------------------
        - Part Ib Lecture Notes
-  _**Exercise 16:**_ . Give pseudocode for an algorithm that implements FIFO-total order broadcast using Lamport clocks. You may assume that each node has a unique ID, and that the set of all node IDs is known. Further assume that the underlying network provides reliable FIFO broadcast.  
    - ```python
timestamp = 0
buffer = [ [(None, 0)] ] * N # Initialize all messages, the message is None and the time is 0. Note that each node has it's own FIFO queue, storing messages and timestamps 

def send(message):
    timestamp += 1
    broadcast( tuple(message, timestamp, myNodeNumber) )

def receive((message, msg_t, nodeNumber)): # pattern match on tuple
    timestamp += 1
    if buffer[nodeNumber][0] == (None, 0): # if we aren't holding a message from this node
        buffer[nodeNumber][0] =  ( message, msg_t )
    else:
    	# otherwise add it to the node Queue
        (buffer[nodeNumber]).append( ( message, msg_t) )

def deliver():
    nodeIndex = buffer.getMin()
    item = buffer[itemIndex][0]

    for nodeBuffer in buffer:
        # We know this has the smallest lamport timestamp because it's FIFO:
        message = nodeBuffer[0]

        if message != item:
            if !(message.time < item.time):
                return False # Go back to waiting for a response

    deliver_to_software(item.message)
    # Either promote the next item in the node queue to the head OR
    # Set the item to have lamport 0, so next time we must wait for a value
    buffer[nodeIndex].deleteItem(index=0)
    if len(buffer[nodeIndex] == 0):
        (nodeBuffer[nodeIndex]).append( (None, 0) ) 
    timestamp += 1
    return True

while (input = listen()): # blocks until we get input
    receive(input)
    deliver() 
```
-  _**Exercise 17:**_  Apache Cassandra, a widely-used distributed database, uses a replication approach similar to the one described here. However, it uses physical timestamps instead of logical timestamps, as discussed here: [ ](https://www.datastax.com/blog/why-cassandra-doesnt-need-vector-clocks)[https://www.datastax.com/](https://www.datastax.com/blog/why-cassandra-doesnt-need-vector-clocks)[blog/ 2013/ 09/why-cassandra-doesnt-need-vector-clocks.](https://www.datastax.com/blog/why-cassandra-doesnt-need-vector-clocks) Write a critique of this blog post. What do you think of its arguments and why? What facts are missing from it? What recommendation would you make to someone considering using Cassandra?
    - The blog post describes problems in Performance, manages siblings and Vector clocks which they seek to solve
        - With regards to **Performance** their implementation will be faster for single field updates - however it may be slower for entire object updates. Consider, in a vector clock system if we go to update an object we need to iterate through a vector clock of size R (number of replicas) - in their system we need to iterate through a "vector clock" of size F (number of fields) as each field has a counter associated with it. So if we wish to update more than R fields in their implementation, that will be slower than in the vector clock implementation. 
        - With regards to **managing siblings** they discuss how LWW can result in lost data, yet their system uses LWW (within specific fields) the only difference is that the overwritten data **may** be smaller depending on how your objects are constructed - as you may just have individual fields overwritten and not the entire object.
        - With regards to **Vector clocks** they say: "Vector clocks are good at helping clients with simple merges like the above user object, but it's important to understand that vector clocks only tell you that a conflict occurred, and not how to resolve it;" - This is a feature not a bug, we **want** user intervention in certain situations in which it's **impossible** to decide what they want - the writer communicates this as a problem, while it results in data being as correct as can be. The downside is the user has to spend time to make this determination, however that is a trade-off  and not a strictly-worse scenario.
    - The blog post makes no mention of leap-seconds, and their impact on timestamp ordering (they provide a dead-link as explanation of how ties are resolved), additionally there is no mention of how they account for clock synchronisation and clock drift which is a large part of the reason for logical vector clocks.
    - This system could be faster for systems whose objects have few fields, and where updates are usually performed on only a few fields at a time. If someone was considering using Cassandra I would urge them to use monotonic physical timers (to protect from leap second problems) and ensure clients are close together (ideally in a single site) and using the same time synchronisation  server (to ensure the tightest clock synchrony and protect from clock-drift).
- 
- 
