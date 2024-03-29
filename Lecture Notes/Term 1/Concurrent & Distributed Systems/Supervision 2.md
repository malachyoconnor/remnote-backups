1. 
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Swiev7gzpJr99rrNiwQ5TgxsXFzzJnb9TDsw3XEAIPEcszEutqMEGgth5IkZjGmHMjrbrsUpMTebpMmwY6gia6b6fzs4e40gkgUjNsAa24VjL1d4CfQ3xROkgAYKh1rb.png)  
        - Atomicity: Not necessarily true that we do all of the transaction or none of it, as we could crash during the system and we have no specific roll-back procedure. More work needs to be done to ensure rollback should we crash - could copy shadows of the data.
        - Consistency: Not necessarily, one could still for example remove money from a system - invariants not necessarily preserved.
        - Isolation: More work is needed, as we must implement strict 2PL to guarantee this. This falls out with strict 2PL, as our work on the objects is not affected by any other threads as only we can access those objects because we hold our locks.
        - Durability: The system can still crash while running commands, we now have the additional task of having to release locks after a crash. 
    - b.) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3www75KrC9L4l9rLhFcV3IN-01D-iZpqMqQg3uMdruRyWkCnPbJNPuERRhQogTsi0qvReyD3RoKQC_EPUjkAp8XfhCp67_aBwKbHr5S6_w5A3z7S0n1FF8nscRIkJgRr.png) 
        - ```c
Serial possible results: 
	T1: A = A + A * interest
	T2: A = A * (1 + interest) + 100; B = B + 100;
	(A,B) = (A*(1 + interest)+100, B + 100)
	OR
	T2: A = A+100; B = B+100;
	T1: A = (A+100) * (1 + interest)
	(A,B) = ((A+100)*(1 + interest), B+100)
``` 
        - ```c
Interleavings:
1: a = A.getBalance();
2: A.credit(Interest*a);
3: A.debit(100);
4: B.credit(100);

1,2,3,4: Serial
1,3,2,4: Result for A: A = A(1+interest) + 100. Conflict Serial
1,3,4,2: Result for A: A = A(1+interest) + 100. Conflict Serial

3,4,1,2: Serial
Below will be Conflict Serial: Doesn't matter who we arrange change in B, since 1&2 dont alter B
3,1,4,2: Conflict Serial
3,1,2,4: Conflict Serial
```
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tzUTAneZ0s9AsmnNR00hdVj71jlOLoBLAjVEsRjWBDQPY5L5USmZY5KjscqZIsDiqTD8jfVjRTYrvmwV1b8RUCJhAUkQTtrvbwM3XZjAplhqnONhEFVHbui1ZWRKevyf.png)
            - Because with OCC works on local copies of the data, and only does its commit right at the end when all computations have completed. Thus, if a computation does not complete it is not committed. However, with 2PL commands that augment the dataset can occur before we commit - thus crashes can occur after augmenting commands have run. We would need to implement some form of a roll-back mechanism.  
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ZxmkFIv7FVtFhWDGJNEmNntWkAPkBx0ji8GPHQCqzvHfPji44haQVbAwjVhOwWcShYuKjSG_iE6O-BQG920FrNyxo199WYCRcGgZHxwgH-GGmlqjXWM_oMQorNyEzdjV.png)
            - ```c
T1: 
	lock(A)
	a = A.getBalance()
	A.credit(a*INTEREST)
	unlock(A)
T2:
	lock(A)
	A.debit(100)
	lock(B)
	unlock(A)
	B.credit(100) // If T2 aborts here, T1 could have acquired the lock of A and done some work, T1 would then have to abort in sympathy with T2.
	unlock(B)
``` Strict 2PL would have avoided this problem because no work that could have caused an abort would occur while we're unlocking A & B - as we do our unlocks at the very end of the program. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zeXb8Y8jfZNbfPh9thhE-nn5c8NptqY5l3TRNLFjBN-_NmXcNv-ZlkWqE89Y2A32wrZ-0fW1nu3tr3ILAENnmP1Ce3ZIQfr_2lTbjlgcvWlwCc5lHaYQqKbnIpnVbWLP.png)  
            - If the program crashes after having written some object updates to disk, as then the transaction hasn't completed but has still changed the state of the data. We would need a roll-back mechanism.  
2. 
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/8Gmm-oC6vjMBJtvL4PA9fP7zCsvZyUlL-qzd3B5wtClDSZDbUl5q09Pws4pc_mrRL3mN7NYIIt4d7PPbQQDrCecLxizAZhJgkym_3PnZWsJ3OqZv6xe6wz3Xm0-eaq9G.png)
        - ```c
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C
// A deadlock is now in effect, no further work can be done
```
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/A2Sp068a8HqNXoBYDmO99qWukv3ScfW2dHTrDsZ-xOUwZupjRty6_bn1htMfxrytwMjq1Bd2bc-rqRxZ3bZLMwdO5UgpqBvhTH5LqtcHKAdLzNZfx0_TrvbYcO0pBqox.png)
        - ```c
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C
A Deadlock will be detected at T1 all processes will abort.
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C

This process of all processes aborting and restarting will continue.
```
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/FE29KtXxq3a2RPGt-6SQkq_ZmPfUGq4obesyhGD56B1hBGbiGG4E2FMBGdDaxaencwVoGQSKI0QUGaUewM1vpjHwiFFLuMjJKYsDaiHF1uXhuXkMGjBmefVzFzv66yXG.png) 
    - When deadlock is detected, we abort the next thread we operate on and continue. 
    - ```c
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C
A Deadlock will be detected at T1 and T1 will abort
// T2.L2 skipped, no lock for C
T2.L2 // T3 will acquire the lock for A, then release locks for C & A
T1.L1 // T1 acquires the lock for A
T2.L2 // T2 acquires the lock for C, then releases locks for B & C
T1.L2 // T1 acquires the lock for B and then releases locks for B & A
```   
3. 
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/vN_VbUS8amAxLCs-AOhqqxAur_W_tYyXlN2WybuBBo5j7uiEavHAl7gChERgXUax844uyMNik7Ls2WjWzgR_JehImsbRLJySqF3P5gUnieydjoYVyYrZJSH95wDSm42u.png)
        - ```c
T1:
	a = A.gb()
	b = B.gb()
	return a+b
T2:	
	A.debit(100)
	B.credit(100)

Interleaving:
A.debit(100)
a = A.gb()
B.credit(100)
b = B.gb()
return a+b

T2: timestamp 1. T1: timestamp 2.
 
A.debit(100)
a = A.gb() // Abort here, as V(T2) < W(A) but final result would have been correct
B.credit(100)
T1 -> Gets new timestamp 3
a = A.gb()
b = B.gb()
return a+b 
``` 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/CPdhUdYYYwwg7iW6ACw3pMXPZmGXASdwc5aRJ4MdLmnuDbdz7WN9ACNex7r5uCM1tbFiRDOHXE4JoVgyk-DNkIAi0G-RnVexfzrWOclPFaUgPI8VyB1G8HHobO6nxjed.png) 
        - TSO can result in situations akin to an even worse spinlock - This occurs when a thread needs a resource a later thread has accessed before it, and thus the thread has to abort, like a spinlock the thread will be restarted but will be spinning over it's entire code contents rather than a single while loop - that is all computation before the abort needs to be recomputed (To to ACID requirements). So, if the mentioned resource is never freed the threads could continually 'spin' over their whole codebase - continually computing the same results and then throwing them away. 
        - Also, for a multiple resource case - a live lock could occur when multiple threads are trying to hold a lock on all the resources:
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gJrEJWDYlmX2Q9E3k9-OCYAzelh1401QHiC5_6LVvhEBgXMmKidk9IVDW15tVHKE1PDebbVxV85pL9ojHgKOXuy31beFjQWPscTcmuqqTOPlGdfMEqvQFX_NTn6yAgno.png) 
        - Case where T1 gets lock of R1, T2 gets lock of R2 - T1 aborts meanwhile T3 gets the lock of R1... This pattern would continue.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/QEfpCL6My-m7761W-3ZbSyaqMfX5WKrbxSg48JYQR1NDZXX__BAGkf5jkASIGBZG2nS7G7XjCNXMmeRvWUhep_U31MN9Ox7KQZ_9L6paneWAQ4_U67n1fdftT672yiRQ.png)
    - ```c
T1: 10
	A.debit(100)
	C.debit(100)
T2: 11
	A.debit(100)
	B.debit(100)
	

T1: A.getBalance() (0,0) 

T2: A.debit(100) ()

T1: B.getBalance()

T2: B.debit(100)

// As OCC distinguishes between write VS reads, while by default TSO doesn't
``` 
    - d.)  OCC executes transactions against local copies of data (‘shadows’) rather than globally visible 3 original copies, which avoids the need to explicitly handle cascading aborts. However, copying all objects at the start of the transaction is problematic if the set of objects to be operated on is determined as part of the transaction itself. Why does on-demand copying of objects complicate transaction validation?  
    - Because using our current system, the previous state that decided on demand the object should be loaded - could have been referring to an earlier version of the item that has since been changed (by another thread). And since we would be copying it on demand (and thus getting it's timestamp when we load it) we would have no way (within this system) of determining if this was the version the state referred to. So the transaction would be valid by our current system, even if the object had been changed to a different (unwanted) object just before we actually loaded it.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/IHsATz-UZGEawcPlhHwr-fQBPo2GeTACbAb6eaeIyZlNZb2M1CPnhclXl_dtuQsY9L01l4AkOEF4_QID_hg0tOnjvjGX8jTB2cjuGwT0SbyXybhL1XMkkyK_ejpfoi_r.png)
        - Because TSO aborts simply when transactions don't follow it's one prescribed schedule, while OCC seeks only to abort conflicting commits. So as TSO aborts more, more live-lock situations will occur when perfectly correct schedules are disallowed.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gslF3mNNmDHVxaPjwqK3JmnsluwJTXFPvI39tdrA2MQg_Sp8cZXQCJVJw3CUryCqRKZ5IWDZml6eoKi6e5KVvT1q-qCptOaRxVa6gA7O_j7To72jCGQVF-Oy2sN6aBYE.png)
        - If a given transaction does a lot of computation in it's body, it may be slower than other threads who use the same resources - in such a case, the thread will continually find that once it's finished computation a faster thread has modified the used resources, forcing us to restart our slow computation. Consider a case where we're performing a statistical analysis of some database, this is a slow operation which will require shadows of multiple different fields - meanwhile one or many fast threads could change the values used in the statistical analysis, meaning once our slow thread has concluded it discovered it's used stale values and must restart. If a database is continually being added to, the slow thread could be starved forever.
4. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tt68NLsWYZBlsWdYWq-ZfTPlVMtMZMMxIeiiadDE8gkDHP1rrUj30jF_zmobxPhdwmMZ9LYWpyJMFLTYJgpBUFZwBW8QFW9gfS3OShawlETDGMD_se7_T7r6TeG6hnW-.png) 
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Fh51IxHMCTYmMkjSu0vg7Zr9psKsZquDCBnOGirStWM76-uwrBGw3Moa17c4hOgwhMUMZOMA0CCOevAty9w_g7YMxf9LjNugU7xThtFkM3Vf8LCSTmKMMXnSbAjFqIcT.png) 
        - Edges represent a "is-before" relationship between nodes.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/h-UuK42dzShBvMy6BZKKVy9nxj85tKJTgxX6fY000655jnaru8NGXJEZ94y2Oc_HSs75GiIB41jfWQcIrJ8M1ViUwOgwAsPRq-8zxfYAbFm13xzd7ivT_XLIPrjuX9B3.png) 
        - A Cycle will be present. I.e. both threads have operations that occur before operations in the other thread - a temporal impossibility.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/k9dHfdy-m5Bm1Eh4nEabAx6LZQo4HfDy5d7XcTZc9ZLOc87gNUEhqyyianbsfSc-0y-QXgxdDKkJ2j7dYa0nlJaeQScECu4ifV3BcNMKri-JIlFhwagPLhzuvDerZvxQ.png) 
        - Isolation & Atomicity
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/lsFX9NuhzszQ6riLY5SF10nNuNddizzb2_KRElUbL73415zKh3CQen490K6g0gEZ4CQiU_un_kVQ4SUV86nbwqyTn4fm5gdJLjSqnvUsIpnjC6DVt5nohO5ezn8spbCN.png) 
        - Serial execution is when threads complete their whole execution before another thread can begin and complete it's whole execution. Serializable is when commands from threads are interleaved, but the result is the same as the serial execution. Serializable executions are a superset of serial executions, as serial executions clearly produce the same results as themselves. 
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/uXFO19F5I8DmY5Z7OaAZvp1OCZxkVIdYFBPvVU3CH7wsdY0yXABb27KDwQhcXAxFWV2jDo0GdQCURa77rgG7UBmwHX_dZ0c8pnZJL5izrJX03bYhPyPSZjJKqTDaqw3v.png)
        - A dirty read is when a thread reads a value that has been modified by another thread, hear we could read the value of A after it's been debited (a dirty read) and read b before it's credited resulting in a result 'v' less than it should be.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/qvlb9mw6AyME0cDsNXhKYb5hPJHHP8jZCC2YSiNwg5GH8MTA4oIHZkKCLgs7iQ96f0__8rfLHJIt3-RbJyDVpn7OgwFWnWGaM2Q2v11sn02SX-n2KRZcGzsCVF4CdFPm.png) 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Ah4OrMb9r7ElHo9fqdvI3fits0ZlHtYDXNv5C0LxsOnCMi1PEYfKS1j7Gxrpqo-ls1s3qoHqq-PmZrtfhIMZ6mGrOGESeSMf_yJsOOJKTdqEBziY9QtbWTdsHpa_Dadc.png) 
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Dq_JxVQqJdUaj6lqnlApNCeWstzIj_u0XzVkiOIVwyfUlxb8htFtTObOn340pTU-tVbtaVwprsSKa6GnLTKzquscQgSw3MDMfWTdDLQY5ql5am_9kJNZvcZ8XAfxDS6D.png)
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7rCJGSabjZmRl1LewnIgITcgke_b5wYjbn4wOGZI5HDIY7q-QNd6xKWmFnHA_yo6l9c3MpUV-stiEmAP05LuKZyyNJv6K0tPCmly-W2RnHqnq5noQABzyfvk_lr2qOia.png)
        - Not necessarily, after roll back the transactions could travel along the same execution path and cause the same commit error - resulting in livelock. However, there will be some cases which are solved by this addition, at the cost of large overhead of generating and testing this graph.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4KdOPCU5sQRPvkY0iFyRQMmkUlkcPEKxeLPdF1ldpMQ8VgM8VbJyiB3mSW_EUC4-b7hFhKs-EIeE1qpsdhuUYOW6H_Vvp-NE_8HZQhN_QyEdnDO-WFfeJGNuoCI_m9WJ.png)
        - It accepts more, because it will never reject a good schedule. While TSO accepts a single correct schedule as transactions come in.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/43Q_Ib1cOqV0P8xcRYdZMwJmJt1eP3PSh7ie0ZEadmfnt0Vw7ljIT6_I1Z5gf-uOtiOQ2C6u5Q4fk-Gg1ZeKTLjRxm6Yt4v3JnFy0jE7cqgbrX_V-5frhNiPZP7zgCs3.png)
        - This method accepts more schedules, so could result in less cascading aborts resulting in less wasted time. However, this scheme has a huge performance overhead of generating a history graph and checking it for cycles at every step.
- 
- 
