- **Consensus**
    - **Fault-tolerant total order broadcast**
        - In our leader follower system, what happens if the leader crashes/becomes unavailable?
        - **Manual failover: **This is―when a human operator manually changes the leader when it's detected the leader has failed. Will need to reconfigure follower nodes. This is fine for planned maintenance. The problem is humans are slow, can take a long time in unplanned outages (consider if this occurred at 3am)
    - **Consensus and total order broadcast**
        - **Consensus is **―several  _nodes coming to agreement _ on a given value.
        - In total-order-broadcasts this would be **the next message to deliver**. So if we can come to a consensus, TOB drops out. e.g. consensus and TOB formally equivalent
        - **Paxos, Multi-Paxos **and **Raft **are consensus algorithms
    - **Consensus system models**
        - Paxos, Raft, etc. assume a **partially synchronous, crash-recovery **system model. 
        - We don't assume a asynchronous system because―there exists **no** consensus algorithm that will **always terminate**! Even in a simple crash-stop system.
        - Paxos, Raft, etc. use clocks only for timeouts/failures however the correctness of the algorithm does not depend on timing.
        - There also exist consensus algorithms for **Byzantine **system models (used in blockchains) 
    - **Leader election** 
        - Use a {{**failure detector**}}** **based on time to determine a suspected leader crash. On a {{suspected crash}} we must then elect a new leader. Crucially, we want to prevent {{two leaders at the same time ("split-brain")!}} 
        - Raft Ensures $\le$ 1 leader per **term **this means―The  _term is an integer variable_  that is  _incremented whenever an election begins_ . Raft ensure that at most 1 leader is elected per **term **and that each  _node votes at most once_  per term. The  _leader is then selected via a quorum._  The quorum gives us the fault tolerance
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oRKZVQPA2sewgXbqQXQuwNNxXS-hb89JPztSbjtVbzdVfHj2Ym0thNflC38IfB7DFepG9UiDi5zqttzWA3y_uEWDELnWIyMYUzLcXVUDXKAlG6Pnw4QKT9PUia4IYnRe.png) 
    - **Can we guarantee only 1 leader?** 
        - The **system of 1 leader per term **doesn't guarantee 1 leader because―we could have a leader disconnected from it's followers, who is replaced without it's knowledge. So it's the leader of term t and there's another leader of term t+1. I.e. **this method only guarantees on leader per term.
 **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V3tUykKyDgLFsDYH6S5IrhXdZQC2D6ubQvp1thFpCZjTFlzCu2vXSTteYMr2Q3DtV4nWWzT84-g0WmATUL0TAToeDTJxZJCInlfXt2xODhLhHvHhT7LE2KYpSXnKPivr.png) 
        - The solution to this problem of a leader being voted out without it's knowledge is―the leader ensures it can send messages via a quorum. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CHaFRGF--nZNN8hKVUQbJBTEehN0QFdy0H66cyAhIKONEOuPKt-LRQxotlsC_5hWZE6zGktq-hvjFjCcGptUh06SlQd94k8cxUqPbfTGXAKNFCC-eVGOEZpDlH6NA-yd.png) 
- **Node state transitions in Raft**
    - The state transitions we will use are always within a certain term. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oWqazBP_8nBcIola3uNH5oNL_j0GsbXTAyi9UhFPA0l_JlVCJbTrWk4KelPLQF3Dl_Pr-6bpmqNyzyQMHr4rEL-ASDVNnAoFuthUcVjViShxfQD6bJTk4IARODnl2kQR.png) 
    - Nodes that start-up or crash and then recover always start in the {{Follower state}}. However, we need some node to become a leader and it does this by transitioning to a {{candidate }}(when it suspects {{leader failure}}). If the node then receives enough votes{{ from quorum}}, it will become the leader. Alternatively, it may discover there's a {{new term}} and transition to a follower. Or the election may {{time-out}} in which case the election must be restarted with a {{higher term number}}.
- **Raft pseudocode Explanations:**
    - ```autohotkey
;; Entering yourself as candidate

on initialisation do
	;; Note that the first 4 variables
	;; need to be stored on disk
	currentTerm := 0; votedFor := null
	log := hi; commitLength := 0
	;; Remaining vars can be lost in a crash
	currentRole := follower; currentLeader := null
	votesReceived := {}; sentLength := hi; ackedLength := hi
end on

on recovery from crash do
	currentRole := follower; currentLeader := null
	votesReceived := {}; sentLength := hi; ackedLength := hi
end on

on node nodeId suspects leader has failed, OR on election timeout do
	currentTerm := currentTerm + 1; currentRole := candidate
	;; nodes vote for themselves
	;; stores votes received as a set
	votedFor := nodeId; votesReceived := {nodeId}; lastTerm := 0
	;; I.e. if we aren't the first leader ever
	if log.length > 0 
		then lastTerm := log[log.length − 1].term;
	end if
	;; Tagged with VoteRequest
	msg := (VoteRequest, nodeId, currentTerm, log.length, lastTerm)
	for each node ∈ nodes: send msg to node
	start election timer
end on
``` 
    - In **RAFT** the **log** is―a list of  _messages with an associated term_ , the term is the term number that the leader sent the given message. It is the  _**total order of messages.**_ 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VnP_X0y4qd74FjPvg_hresNYjUzjlgDUYiq6sHnVlGWZnzWMPvIAetoO8B7NBf-rY1_hKb43wUquGZ4RwjEl2As6e3wNnfPnJjmu5PiG0AlC7VoEC5w7yCEUJjRN1314.png) 
    - ```autohotkey
;; Voting for a new candidate 

;; c stands for candidate
on receiving (VoteRequest, cId, cTerm, cLogLength, cLogTerm)
at node nodeId do
	;; update our current term if
	;; votedFor=null indicates we've note voted for anyone
	if cTerm > currentTerm then
		currentTerm := cTerm; currentRole := follower
		votedFor := null
	end if
	lastTerm := 0
	if log.length > 0 then lastTerm := log[log.length − 1].term;
	end if
	;; Check if the candidates log is up to date with ours
	;; If their log's last term is greater than ours
	;; or it's equal with their log being at least
	;; as populated as ours
	logOk := (cLogTerm > lastTerm) ∨
			 (cLogTerm = lastTerm ∧ cLogLength ≥ log.length)
	;; if all the log checks are okay and we've not cast
	;; a vote for someone else then vote for this candidate
	if (cTerm = currentTerm) ∧ logOk ∧ votedFor ∈ {cId, null} then
		votedFor := cId
		send (VoteResponse, nodeId, currentTerm,true) to node cId
	else
		;; if we don't vote for them, we must tell them!
		send (VoteResponse, nodeId, currentTerm, false) to node cId
	end if
end on
``` 
    - ```autohotkey
;; Collecting votes at the candidate

on receiving (VoteResponse, voterId, term, granted) at nodeId do
	;; If we're behind in the term we'll have to 
	;; switch back to being a follower
	if currentRole = candidate ∧ term = currentTerm ∧ granted then
		;; idempotent update
		votesReceived := votesReceived ∪ {voterId}
		;; If we have a majority quorum we become the leader!
		if |votesReceived| ≥ cieling((|nodes| + 1)/2) then
			currentRole := leader; currentLeader := nodeId
			cancel election timer
			;; tell everyone we're the leader
			for each follower ∈ nodes \ {nodeId} do
				;; Initialize maps from each node
				;; to the number of messages sent to them
				;; and the number of messages they've 
				;; acknowledged
				sentLength[follower] := log.length
				ackedLength[follower] := 0
				ReplicateLog(nodeId, follower)
			end for
		end if
	else if term > currentTerm then
		currentTerm := term
		currentRole := follower
		votedFor := null
		cancel election timer
	end if
end on
``` 
    - ```autohotkey
;; Broadcasting messages

on request to broadcast msg at node nodeId 
	if currentRole = leader then
		;; add the message to the log which is simply the total
		;; order of messages
		append the record (msg : msg, term : currentTerm) to log
		ackedLength[nodeId] := log.length
		for each follower ∈ nodes \ {nodeId} do
			ReplicateLog(nodeId, follower )
		end for
	else
		;; If we aint the leader, forward the msg
		forward the request to currentLeader via a FIFO link
	end if
end on

periodically at node nodeId do
	;; This acts as a heartbeat, telling them the leader is alive
	;; this also ensures any messages that get lost will be 
	;; redelivered
	if currentRole = leader then
		for each follower ∈ nodes \ {nodeId} do
			ReplicateLog(nodeId, follower )
		end for
	end if
end do
``` 
    - ```autohotkey
;; The ReplicateLog function

function ReplicateLog(leaderId, followerId)
	;; prefixLen the number of log entries we think
	;; we've sent to a particular follower.
	;; suffix is all the entries we've yet to send
	prefixLen := sentLength[followerId]
	suffix := hlog[prefixLen], log[prefixLen + 1], . . . ,
	log[log.length − 1]i
	;; this gets the term number of the last log
	;; entry in the prefix
	;; e.g. the last log entry we think we've sent
	prefixTerm := 0
	if prefixLen > 0 then
		prefixTerm := log[prefixLen − 1].term
	end if
	send (LogRequest, leaderId, currentTerm, prefixLen,
	prefixTerm, commitLength, suffix ) to followerId
end function
``` 
    - ```autohotkey
;; Receiving a log request

on receiving (LogRequest, leaderId, term, prefixLen, prefixTerm,
	leaderCommit, suffix ) at node nodeId do
	if term > currentTerm then
		currentTerm := term; votedFor := null
		cancel election timer
	end if
	;; this is if we thought we were a candidate
	;; or if we thought we were the leader
	if term = currentTerm then
		currentRole := follower; currentLeader := leaderId
	end if
	;; if we aren't actually behind their log
	;; and either the prefix is empty
	;; and their prefix item is the same as what we've got
	logOk := (log.length ≥ prefixLen) ∧
	(prefixLen = 0 ∨ log[prefixLen − 1].term = prefixTerm)
	if term = currentTerm ∧ logOk then
		AppendEntries(prefixLen, leaderCommit, suffix )
		ack := prefixLen + suffix .length
		send (LogResponse, nodeId, currentTerm, ack,true) to leaderId
	else
		send (LogResponse, nodeId, currentTerm, 0, false) to leaderId
	end if
end on
``` 
    - What is the purpose of this code? ```autohotkey
 logOk := (log.length ≥ prefixLen) ∧
	(prefixLen = 0 ∨ log[prefixLen − 1].term = prefixTerm)
```―This is 
    - 
    - ```autohotkey
;; AppendEntries function

function AppendEntries(prefixLen, leaderCommit, suffix )
	if suffix .length > 0 ∧ log.length > prefixLen then
		index := min(log.length, prefixLen + suffix .length) − 1
		if log[index ].term 6= suffix [index − prefixLen].term then
			log := hlog[0], log[1], . . . , log[prefixLen − 1]i
		end if
	end if
	if prefixLen + suffix .length > log.length then
		for i := log.length − prefixLen to suffix .length − 1 do
			append suffix [i] to log
		end for
	end if
	if leaderCommit > commitLength then
		for i := commitLength to leaderCommit − 1 do
			deliver log[i].msg to the application
		end for
		commitLength := leaderCommit
	end if
end function
``` 
    - 
    - ```autohotkey
on receiving (LogResponse, follower , term, ack, success) at nodeId do
	if term = currentTerm ∧ currentRole = leader then
		if success = true ∧ ack ≥ ackedLength[follower ] then
			sentLength[follower ] := ack
			ackedLength[follower ] := ack
			CommitLogEntries()
		else if sentLength[follower ] > 0 then
			sentLength[follower ] := sentLength[follower ] − 1
			ReplicateLog(nodeId, follower )
	end if
	else if term > currentTerm then
	currentTerm := term
	currentRole := follower
	votedFor := null
	cancel election timer
	end if
end on
``` 
