- 
-  _Concurrent Systems _    
- Supervision 2
    1. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Swiev7gzpJr99rrNiwQ5TgxsXFzzJnb9TDsw3XEAIPEcszEutqMEGgth5IkZjGmHMjrbrsUpMTebpMmwY6gia6b6fzs4e40gkgUjNsAa24VjL1d4CfQ3xROkgAYKh1rb.png)  
            - Atomicity: Not necessarily true that we do all of the transaction or none of it, as we could crash during the system and we have no specific roll-back procedure. More work needs to be done to ensure rollback should we crash - could copy shadows of the data.
            - Consistency: Not necessarily, one could still for example remove money from a system - invariants not necessarily preserved.
            - Isolation: More work is needed, as we must implement strict 2PL to guarantee this. This falls out with strict 2PL, as our work on the objects is not affected by any other threads as only we can access those objects because we hold our locks.
            - Durability: The system can still crash while running commands, we now have the additional task of having to release locks after a crash. 
        - b.) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3www75KrC9L4l9rLhFcV3IN-01D-iZpqMqQg3uMdruRyWkCnPbJNPuERRhQogTsi0qvReyD3RoKQC_EPUjkAp8XfhCp67_aBwKbHr5S6_w5A3z7S0n1FF8nscRIkJgRr.png) 
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tzUTAneZ0s9AsmnNR00hdVj71jlOLoBLAjVEsRjWBDQPY5L5USmZY5KjscqZIsDiqTD8jfVjRTYrvmwV1b8RUCJhAUkQTtrvbwM3XZjAplhqnONhEFVHbui1ZWRKevyf.png)
                - Because with OCC works on local copies of the data, and only does its commit right at the end when all computations have completed. Thus, if a computation does not complete it is not committed. However, with 2PL commands that augment the dataset can occur before we commit - thus crashes can occur after augmenting commands have run. We would need to implement some form of a roll-back mechanism.  
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZxmkFIv7FVtFhWDGJNEmNntWkAPkBx0ji8GPHQCqzvHfPji44haQVbAwjVhOwWcShYuKjSG_iE6O-BQG920FrNyxo199WYCRcGgZHxwgH-GGmlqjXWM_oMQorNyEzdjV.png)
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zeXb8Y8jfZNbfPh9thhE-nn5c8NptqY5l3TRNLFjBN-_NmXcNv-ZlkWqE89Y2A32wrZ-0fW1nu3tr3ILAENnmP1Ce3ZIQfr_2lTbjlgcvWlwCc5lHaYQqKbnIpnVbWLP.png)  
                - If the program crashes after having written some object updates to disk, as then the transaction hasn't completed but has still changed the state of the data. We would need a roll-back mechanism.  
    2. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8Gmm-oC6vjMBJtvL4PA9fP7zCsvZyUlL-qzd3B5wtClDSZDbUl5q09Pws4pc_mrRL3mN7NYIIt4d7PPbQQDrCecLxizAZhJgkym_3PnZWsJ3OqZv6xe6wz3Xm0-eaq9G.png)
            - ```c
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C
// A deadlock is now in effect, no further work can be done
```
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/A2Sp068a8HqNXoBYDmO99qWukv3ScfW2dHTrDsZ-xOUwZupjRty6_bn1htMfxrytwMjq1Bd2bc-rqRxZ3bZLMwdO5UgpqBvhTH5LqtcHKAdLzNZfx0_TrvbYcO0pBqox.png)
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
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FE29KtXxq3a2RPGt-6SQkq_ZmPfUGq4obesyhGD56B1hBGbiGG4E2FMBGdDaxaencwVoGQSKI0QUGaUewM1vpjHwiFFLuMjJKYsDaiHF1uXhuXkMGjBmefVzFzv66yXG.png) 
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
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vN_VbUS8amAxLCs-AOhqqxAur_W_tYyXlN2WybuBBo5j7uiEavHAl7gChERgXUax844uyMNik7Ls2WjWzgR_JehImsbRLJySqF3P5gUnieydjoYVyYrZJSH95wDSm42u.png)
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CPdhUdYYYwwg7iW6ACw3pMXPZmGXASdwc5aRJ4MdLmnuDbdz7WN9ACNex7r5uCM1tbFiRDOHXE4JoVgyk-DNkIAi0G-RnVexfzrWOclPFaUgPI8VyB1G8HHobO6nxjed.png) 
            - TSO can result in situations akin to an even worse spinlock - This occurs when a thread needs a resource a later thread has accessed before it, and thus the thread has to abort, like a spinlock the thread will be restarted but will be spinning over it's entire code contents rather than a single while loop - that is all computation before the abort needs to be recomputed (To to ACID requirements). So, if the mentioned resource is never freed the threads could continually 'spin' over their whole codebase - continually computing the same results and then throwing them away. 
            - Also, for a multiple resource case - a live lock could occur when multiple threads are trying to hold a lock on all the resources:
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gJrEJWDYlmX2Q9E3k9-OCYAzelh1401QHiC5_6LVvhEBgXMmKidk9IVDW15tVHKE1PDebbVxV85pL9ojHgKOXuy31beFjQWPscTcmuqqTOPlGdfMEqvQFX_NTn6yAgno.png) 
            - Case where T1 gets lock of R1, T2 gets lock of R2 - T1 aborts meanwhile T3 gets the lock of R1... This pattern would continue.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QEfpCL6My-m7761W-3ZbSyaqMfX5WKrbxSg48JYQR1NDZXX__BAGkf5jkASIGBZG2nS7G7XjCNXMmeRvWUhep_U31MN9Ox7KQZ_9L6paneWAQ4_U67n1fdftT672yiRQ.png)
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
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IHsATz-UZGEawcPlhHwr-fQBPo2GeTACbAb6eaeIyZlNZb2M1CPnhclXl_dtuQsY9L01l4AkOEF4_QID_hg0tOnjvjGX8jTB2cjuGwT0SbyXybhL1XMkkyK_ejpfoi_r.png)
            - Because TSO aborts simply when transactions don't follow it's one prescribed schedule, while OCC seeks only to abort conflicting commits. So as TSO aborts more, more live-lock situations will occur when perfectly correct schedules are disallowed.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gslF3mNNmDHVxaPjwqK3JmnsluwJTXFPvI39tdrA2MQg_Sp8cZXQCJVJw3CUryCqRKZ5IWDZml6eoKi6e5KVvT1q-qCptOaRxVa6gA7O_j7To72jCGQVF-Oy2sN6aBYE.png)
            - If a given transaction does a lot of computation in it's body, it may be slower than other threads who use the same resources - in such a case, the thread will continually find that once it's finished computation a faster thread has modified the used resources, forcing us to restart our slow computation. Consider a case where we're performing a statistical analysis of some database, this is a slow operation which will require shadows of multiple different fields - meanwhile one or many fast threads could change the values used in the statistical analysis, meaning once our slow thread has concluded it discovered it's used stale values and must restart. If a database is continually being added to, the slow thread could be starved forever.
    4. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tt68NLsWYZBlsWdYWq-ZfTPlVMtMZMMxIeiiadDE8gkDHP1rrUj30jF_zmobxPhdwmMZ9LYWpyJMFLTYJgpBUFZwBW8QFW9gfS3OShawlETDGMD_se7_T7r6TeG6hnW-.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Fh51IxHMCTYmMkjSu0vg7Zr9psKsZquDCBnOGirStWM76-uwrBGw3Moa17c4hOgwhMUMZOMA0CCOevAty9w_g7YMxf9LjNugU7xThtFkM3Vf8LCSTmKMMXnSbAjFqIcT.png) 
            - Edges represent a "is-before" relationship between nodes.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/h-UuK42dzShBvMy6BZKKVy9nxj85tKJTgxX6fY000655jnaru8NGXJEZ94y2Oc_HSs75GiIB41jfWQcIrJ8M1ViUwOgwAsPRq-8zxfYAbFm13xzd7ivT_XLIPrjuX9B3.png) 
            - A Cycle will be present. I.e. both threads have operations that occur before operations in the other thread - a temporal impossibility.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/k9dHfdy-m5Bm1Eh4nEabAx6LZQo4HfDy5d7XcTZc9ZLOc87gNUEhqyyianbsfSc-0y-QXgxdDKkJ2j7dYa0nlJaeQScECu4ifV3BcNMKri-JIlFhwagPLhzuvDerZvxQ.png) 
            - Isolation & Atomicity
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lsFX9NuhzszQ6riLY5SF10nNuNddizzb2_KRElUbL73415zKh3CQen490K6g0gEZ4CQiU_un_kVQ4SUV86nbwqyTn4fm5gdJLjSqnvUsIpnjC6DVt5nohO5ezn8spbCN.png) 
            - Serial execution is when threads complete their whole execution before another thread can begin and complete it's whole execution. Serializable is when commands from threads are interleaved, but the result is the same as the serial execution. Serializable executions are a superset of serial executions, as serial executions clearly produce the same results as themselves. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uXFO19F5I8DmY5Z7OaAZvp1OCZxkVIdYFBPvVU3CH7wsdY0yXABb27KDwQhcXAxFWV2jDo0GdQCURa77rgG7UBmwHX_dZ0c8pnZJL5izrJX03bYhPyPSZjJKqTDaqw3v.png)
            - A dirty read is when a thread reads a value that has been modified by another thread, hear we could read the value of A after it's been debited (a dirty read) and read b before it's credited resulting in a result 'v' less than it should be.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qvlb9mw6AyME0cDsNXhKYb5hPJHHP8jZCC2YSiNwg5GH8MTA4oIHZkKCLgs7iQ96f0__8rfLHJIt3-RbJyDVpn7OgwFWnWGaM2Q2v11sn02SX-n2KRZcGzsCVF4CdFPm.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ah4OrMb9r7ElHo9fqdvI3fits0ZlHtYDXNv5C0LxsOnCMi1PEYfKS1j7Gxrpqo-ls1s3qoHqq-PmZrtfhIMZ6mGrOGESeSMf_yJsOOJKTdqEBziY9QtbWTdsHpa_Dadc.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Dq_JxVQqJdUaj6lqnlApNCeWstzIj_u0XzVkiOIVwyfUlxb8htFtTObOn340pTU-tVbtaVwprsSKa6GnLTKzquscQgSw3MDMfWTdDLQY5ql5am_9kJNZvcZ8XAfxDS6D.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7rCJGSabjZmRl1LewnIgITcgke_b5wYjbn4wOGZI5HDIY7q-QNd6xKWmFnHA_yo6l9c3MpUV-stiEmAP05LuKZyyNJv6K0tPCmly-W2RnHqnq5noQABzyfvk_lr2qOia.png)
            - Not necessarily, after roll back the transactions could travel along the same execution path and cause the same commit error - resulting in livelock. However, there will be some cases which are solved by this addition, at the cost of large overhead of generating and testing this graph.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4KdOPCU5sQRPvkY0iFyRQMmkUlkcPEKxeLPdF1ldpMQ8VgM8VbJyiB3mSW_EUC4-b7hFhKs-EIeE1qpsdhuUYOW6H_Vvp-NE_8HZQhN_QyEdnDO-WFfeJGNuoCI_m9WJ.png)
            - It accepts more, because it will never reject a good schedule. While TSO accepts a single correct schedule as transactions come in.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/43Q_Ib1cOqV0P8xcRYdZMwJmJt1eP3PSh7ie0ZEadmfnt0Vw7ljIT6_I1Z5gf-uOtiOQ2C6u5Q4fk-Gg1ZeKTLjRxm6Yt4v3JnFy0jE7cqgbrX_V-5frhNiPZP7zgCs3.png)
            - This method accepts more schedules, so could result in less cascading aborts resulting in less wasted time. However, this scheme has a huge performance overhead of generating a history graph and checking it for cycles at every step.
    - 
    - 
- Supervision 1
    1. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sd2R5eXh_2n9qz1rlMJFYdNLd0tG-bE0UaLbKmCsWpDMrlH-pHYl-ZYXdacYEQIOuqaugFW1YRGzMEU9GQ6JOBONxdF-ugR7vRcWjB1AKZSipTorsRhQrosKThDmkULR.png) 
        - 0 - Condition synchronisation where one thread is producing items and another thread is consuming them. Initialising this to zero signifies that there are no items to consume and thus the producer must run. The consumer will wait for items to be produced (S > 0) and will then be signalled (whenever the producer produces an item it will call signal()).
        - 1 - If we have 1 resource available for use between multiple threads, in this case the first thread that arrives get's access to the resource - i.e. only one person can print from a printer at a time.
        - n - If we have n resources available between multiple threads (more than n threads), in this case the first n threads get access to the resource immediately - i.e. only n people can use the n printers at any one time.
    2. ```c
chopsticks = new Semaphore(2);
int chopstick_1, chopstick_2 = 0, 0;
// Thread 1
while (1) {
	if (chopstick_1 == 2) {
		eat();
		chopstick_1=0;
		signal(chopsticks);
		signal(chopsticks);
	} else {
		wait(chopsticks);
		chopstick_1 ++;
	}
}

// Thread 2
while (1) {
	if (chopstick_2 == 2) {
		eat();
		chopstick_2=0;
		signal(chopsticks);
		signal(chopsticks);
	} else {
		wait(chopsticks);
		chopstick_2 ++;
	}
}

// This can result in both threads getting one chopstick and starving
```
    3. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hB68m6SGg36hFL_xPZrweB2Eqg7k_MVpuvzdel9hIGD09WTMEsLGbpsWbnxmyGvH09l_OM7wDs9nDkFSYcrrMckP0b-W4XChfeRFosc3SSgvINuuRlz1TegpO9zNM9qH.png) 
        - Yes, because if we have a context switch anywhere between the weights (including just after the wait command is run) the various producer/consumer threads have different conceptions of the state. For example, if a context-switch occurred (in the case of a producer) before we changed buffer[in] we could resume the thread when the list is full and cause an overflow. Alternatively, we could consume the wrong item by the same means.
    4. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D19kr_2Pf7_0ZafdDz9-dTMCRWKuzsTeC3BNISA9-vMa91p5xUIbPtkAcO-FvWKG-BOYddEfZNGpxymen8EKKA9v6OFpxc89bqDSu4Y6cYZwpsad_kCWmOu6P2Fstjta.png) 
        - In the implementation of wait & signal presented in the lectures, the problem would be making checking the queue and changing S atomic (for signal) or checking & changing S atomic (for wait) rather than the question posed above. This is because in the version presented in the lecture, only the first and last threads in the door change S.
        - Wait would be unaffected - this is because we only perform a decrement if S > 0 - and we only block a thread when S = 0. This means the two can never be in contention.
        - If signal's integer & scheduler operation were not atomic, we could have a race condition - in between the integer operation and the scheduler operation another thread could call wait on the semaphore and perform a computation. While that thread is running, we would complete our scheduler operation and our awoken thread would perform the same computation - this race condition could lead to anomalous behaviour. Waking up the thread first, and then incrementing the value would solve this.
        - 
    5. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/33akS39qWNR2m71NzOgaRJBQFNkWyVBtTw06nG-8WkaHVY_RldW4gw2BUKle6mpGtR5l7Eizk96IOtfF0m8hj52Aznye1SsP6aGioBc16kDSvqDO1K60vUqc9_FwdWnM.png) 
        - Round-Robin - In a multi-core processor where each consumer thread is on a different core, we would spread the work to different cores to ensure temperatures of an individual core doesn't skyrocket which would result in a slowdown.
        - Prioritized Work - In a multi-CPU architecture where faster CPUs are in more demand for work, faster CPUs would be given a higher priority as they would complete faster and we'd like that time-save when those CPUs are available, while slower CPUs would be given a lower priority. 
        - MRU - If the CPU cores have caches that will have recent data stored in them, if a thread has been used recently it may happen that the required data to perform the computation is already in the cache (addresses of items etc.) meaning time will be saved which would have been spent fetching data from main memory.
    6. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RdrlWILK0E0bNwSv0LdF4PR9LSwMfofFUuoeUnN2zZ51HMYhG-COY7mcbZQY7g0NXtGGAgopnKwofrjQhkZ-RW5b53cxNVacz10Dj-fph_bN_LdPWE_SrBDgb1eLYKHN.png) 
        - ```c
int buffer[N]; int in = 0, out = 0;
spaces = new Semaphore(N);
items = new Semaphore(0);
producer_guard = new Semaphore(1);
consumer_guard = new Semaphore(1);
// Producer threads
while(true) {
	item = produce();
	wait(spaces);
	wait(producer_guard);
	buffer[in] = item;
	in = (in + 1) % N;
	signal(producer_guard);
	signal(items);
}
// Consumer threads
while(true) {
	wait(items);
	wait(consumer_guard);
	item = buffer[out];
	out =(out+1) % N;
	signal(consumer_guard);
	signal(spaces);
	consume(item);
}
``` 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bPGP_gNXPzszZu0_q37-gatUw0H5dw8izVNFee9drU-pzJ-qJsaKuetdA0NFulnHZLxjr7CjpzZMpGvCJCxYpVZWCmMPIlAGMK-4SQrszI27PiIeOky3BPa_hlCHoaQN.png) 
        - We can consider that the consumer and the producer interact with different sections of the buffer in their "guarded" sections - the consumer deals with out and the producer deals with in. We can then consider that the whole design of the spaces & items was done to ensure the back and front of the list cannot affect each other, that is we can never add to a full list due to spaces and can never detract from a full one due to items. So as in & out are safely independent, we need only protect our consumers from other consumers and producers from other producers. 
    7. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/y6BGMYo6C6AtmnKq8ltCZY67Be2lsy6CI2hVWujhK59XcjEncDNTVw9qCa3N4l3fOIbd_kzM-OmGGOfOdTIkNrFe_W9laL-85ipJVFLlCulSOooNdRFDJ1ZLkqcR-Mw-.png) 
        - Because generally there will be multiple (low priority) consumer threads in the guard queue ahead of the producer thread, they will necessarily be popped from the queue ahead of any producer threads. However, if you were using a mutex:
        - ```c
while (! test-and-set(note));
``` The thread that gets access to the resource, is the thread that runs test-and-set(note) first after the resource is freed - if the producer threads are set to a higher priority by the OS, they are more likely to run the command first.
        - 
    8. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XtO2e4DqYfpL0B1gbYvMSEYqayEMkA50280I_JG5WD2FiCBcqtGMbZTY-fLOAmdiJLDuTOEe-alLzih8lCUPd9E7G_BCc0Dv_sxyKAGKcJd8IY8mq4XdPT6UXHgvTkhm.png) 
        - One could replace the queue structure with a priority-queue, rather than waking up the next thread in the queue in signal we would call popmin() (where a lower priority number signifies a higher priority) and the higher priority consumers would always go first.
    9. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Wy1sGRze451GrBUFtmUiDbaytnxBlC36EbdEbjjsWFZ2CaSDbQa78plAuoKq4hHoXQ5CslliK5YT_cJkEkuecGzqnKCKst6nEduav4Pibnv5blNuHzndlqfJqDSZCyOg.png) 
        - One solution would be to raise the priority of the producers (to high) whenever there's a high-priority consumer waiting - the wait() commands thus acts similarly to the signal() command, in that it allows another thread to run.
    10. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cjRL7x0rri8fzqS45tGSxJ_lTt-r8ZbvSkwSlM-jlu96XC0v3j76VAMtqfibLO0JJQMDupkzyO4in-M9lDVC3LpA_f5UZ8DUvR3fXWzaR68yH9UANntExc4So-IiYXSf.png) 
        - Each thread has its own stack, register file and scheduling state, thus there will be two instances of each of these.
        - Threads share the executable program and virtual address space, so there will be only one instance of each of these.
    11. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gSeUH_wE-tW5DLaCuzxk0t7wair3fJw17i5FnYJAVLrFHH8d6hAQtJur1zWRVBjCKb5gsnuUcMNPlui8jIWfaKs-Wys6EhI_8toKLA9B3cFTitBM2p9WMPdN--zIbDxD.png) 
        - Consider the following case: 
        - ```c
if (!beer) {
	// printf(note);
	if (!note) {
		note = 1;
		get_beer();
		note = 0;
	}
}
``` A race condition can occur between checking for beer and checking the note - if another thread is just about to write to the note. However, as printf() takes a non-zero amount of time to execute that added time could result in the second thread changing note  in time, meaning the first thread will check the note once it's been changed (e.g. desired logic flow occurs).
    12. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r9xDNEUd21vdFWgQV_oBu_b-yT79qFcKluEGCeipA0baCbUXBf4g13mns3lEDnAmLdZwxbOyLpKM8587Ae9iw3K87JXbLdhpE_C6FkpF5JD65RNQAfDJqyiWzg03192u.png) 
        1. n! As the OS is (modelled as) non-deterministic, we cannot know the order in which threads will be scheduled and execute thrprint.
    13. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rOmx9KUE6ei8U0fUQOOJT_dEeaW033n8VTJbWBYfwSH8oESnVDHu_5OpJl-KV63e0zBY8VNTCTXmF_RLMl1F0t5ujdZmkq99WLSKkC8Lk3_AKDNASEYiuUNcygfFIsWc.png) 
        - 1 - As pthread uses signal-and-continue style conditions, the if should be a while loop - as the value of the condition could have changed while the thread was waiting on the condidtion.
        - 2 - We do our printf after unlocking the mutex, this defeats the whole purpose of the safety - another thread could legally access the state and complete it's printf before we've completed ours (this could be due to a context switch or simply another core that's faster).
        - 3 - We never signal ordering_cv to wake up other threads.
        - ```c
int next_thread_id = 0; // Next ID to print
pthread_mtx_t ordering_mtx; // Lock protecting next ID
pthread_cond_t ordering_cv; // next_thread_id has changed

void ordered_thrprint(int thread_id, char *message) {
	pthread_mtx_lock(ordering_mtx);
	while(thread_id != next_thread_id) {
		pthread_cond_wait(ordering_cv, ordering_mtx);
	}
	next_thread_id = next_thread_id + 1;
	printf("Thread %d: %s\n", thread_id, message);
	pthread_mtx_unlock(ordering_mtx);
	pthread_cond_broadcast(ordering_cv);
}
``` 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gcADy-5emy1KJOIoJd595ND9GnD5-ptl-P6YS97lwBJayyx_m-ziHUyQeKJsIrMoEv3TZJd2euOaVtZE15SHtQdEbABINv6eTJNsILmfI65csyku1bmNsxdHQBmVlNKl.png) 
        - We could solve this problem using two additional pieces of state (and associated mutexes), an array of size N (number of threads) and a protected integer that starts as N. Whenever a thread is executed, it would do the following
            - First get control of the buffer and the protected integer
            - Then it would place it's debug message into the buffer at the index of it's thread ID.  
            - Then decrement the protected integer, if that integers value is now 0 print out all the debug messages and associated indexes and we're done.
            - Release the protected integer and the buffer.
- 
- **Concurrent Flashcards**  ↓ 
    - 
    - What is a Process, and what are they allocated? ↓ 
        - Processes are instances of programs inexecution
        - They are allocated one or more threads
        - virtual address space, local memory etc.
        - They are given OS unit of protection and memory allocation. 
    - What is shared between threads of a process, and what isn't?  ↓ 
        - The heap and code is shared
        - The stack and each threads program counter are not shared.
    - Describe 1:N threading, including it's benefits and downsides  ↓ 
        - The kernel only schedules processes, it doesn't generate threads. Threads are instead implemented by user-space libraries, e.g. the JVM implements threads.
        - Benefits: Lightweight thread creation, OS independence, more programmer freedom
        - Downside: Can't spread threads across multiple CPUs. Blocking syscalls or context switches are expensive.
    - Describe 1:1 threading, including it's benefits and downsides  ↓ 
        - Kernel provides all threads, processes are initially allocated with one thread but can call for more. Used by most OS's
        - Advantage: Pre-emption handled by OS. Straightforward to use multiple CPUS
        - Downsides: OS overhead added. Less flexible and portable.
    - Describe M:N threading  ↓ 
        - Kernel offers a small number M of activations. The user then schedules a large number N of threads to each activation. So OS controls maximum amount of concurrency N.
        - The OS upcalls a thread to userspace when it blocks or wakes up. Then userspace code can be used to schedule it.
    - What is a critical section, how does it relate to mutual exclusion?  ↓ 
        - A critical section is a piece of code that should only ever be executed by one thread at a time
        - Mutual exclusion is when if one thread is executing a critical section, no other threads can enter it.
    - Describe the code of the atomic read-and-set operation―```python
def read_and_set(note)
	while True:
		if (note == 0):
			note = 1
			return 1
``` 
    - Describe spin-locks and give pseudocode  ↓ 
        - Can be implemented to define a mutual exclusion zone. We start such a zone with a LOCK(L) call and end it with an UNLOCK(L) call. Note that the thread is continually doing useless work spinning.
        - ```python
def LOCK(L):
	while (!read_and_set(L)):
		continue
		
def UNLOCK(L):
	L= 0
``` 
    - Describe how a process moves between Running, ready to run and blocked under OS guidance. How does the OS store data about the processes? ↓ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dBHlW8_3iaVSPqMu4t2yjQ32cClI5OcsHlCjJA-OEV5M427R2XQ34RDzA3msfaSC_ChRJ-v9cnyfEgQ5BUtF-gV0q_mJfmFk8CTZbNeZg7Jb1zCDhUiLtE3i7D0C5XYA.png) 
        - TCB contains registers of non-running processes/tasks. The TCBs are stored in a queue handled by the OS. The blocked TCBs point to a semaphore or similar that they're waiting on.
    - Describe Atomic compare-and-swap (pseudocode or otherwise)  ↓ 
        - Check if the prior value equals the one currently stored, if so store the new value. Otherwise fail - in the fail case return the stored value.
For example we could check if mem_addr = 0 and store a 1 - to get an atomic read-and-set
        - ```python
def compare_and_swap(prior, new, mem_addr):
	if (prior == mem[mem_addr]):
		mem[mem_addr] = new
	else:
		return FAIL
``` 
    - Describe Load linked, store conditional. Why is it often preferred to Load-Linked ↓ 
        - We start with a load-linked of a memory address, which is moved into a register where it is operated one. 
        - The when we go to store that value back using store-conditional - store-conditional fails if the memory neighbourhood has been modified **or if an interrupt has occurred**. Otherwise it writes the register back to memory.
        - Doesn't lock up resources while an atomic action is taking place.
    - What are synchronous and asynchronous products of finite state machines?  ↓ 
        - Asynchronous means the actions of threads is interleaved - e.g. we can step multiple ways in the product.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/smCAxdGAVeidbbPWc18G6773tdKSEGCVPsyR47wcwyPx6Xs8qn-ydA5pNVjAZ0KMzrrr4cjCI_PtqvY6hLnqi3zil32y2jNJus3OouIGYemFA71K59Q13x3x8HuoNEdW.png) 
        - Synchronous means all threads move at once, via a diagonal step.
    - What is the reachable state algorithm used for?  ↓ 
        - The reachable state algorithm generates every possible reachable state by the system, e.g. each possible interleaving. We can then check if certain properties hold in every such reachable state - a safety property. 
    - Describe the **Lamport bakery algorithm **- why is ENTERING necessary? ↓ 
        - We enter a bakery, take a number and wait for everyone else to get their lock and for our number to be lexigraphically greater
        - ```python
ENTERING = [False * num_threads]
NUMBER = [0 * num_threads]
def lock(tid):
	ENTERING(tid) = 1
	my_number = max(NUMBER) + 1
	ENTERING(tid) = 0
	
	for j in range(0, num_threads):
		# While other nodes still getting numbers, spin
		while ENTERING[j]:
			continue
		
		# If the NUMBER[j] is zero then exit
		# If the NUMBER[j],j is lexically smaller than us
		# then exit 
		while (NUMBER[j] != 0) and 
			  ((NUMBER[tid],tid) < (NUMBER[j],j)):
			  continue
			  
def unlock(tid):
	Number[tid] = 0
``` 
        - ENTERING is necessary, as it ensures that even if another thread gets the same number as us and then get's pre-empted **before it can set it **then even though it's number would be zero it doesn't get skipped. 
    - Describe semaphores and give pseudocode for wait and signal ↓ 
        - Semaphores encode the amount of a given resource currently available. They avoid the wasted resources used in spin-locks by instead sleeping.
        - ```python
## NOTE THAT THE INSIDE OF WAIT and SIGNAL IS ATOMIC!!!!!!!
## VERY IMPORTANT

def wait(sem):
	if (sem > 0):
		sem -= 1
	else:
		suspend-calling thread
		add calling thread to queue
		
def signal(sem):
	if len(queue) == 0:
		sem += 1
	else:
		wake the first thread on the queue
``` 
    - Describe Inter-Process-Interrupts ↓ 
        - Thread marked as runnable
        - Interrupt sent to target CPU
        - IPI handler invokes **thread scheduler**, which preempts running thread. Triggers a context switch to target thread. 
    - Describe the producer consumer solution using semaphores. How would you change this solution if you had MULTIPLE producers and consumers. ↓ 
        - The producer wants to create items if there's space. The consumer wants to consume them if there's space. So the producer waits on space, and signals that there's another item when it's created one.
The consumer waits on items, and signals that theres space once it's consumed an item.
Note that the buffer (queue) is built on a circular array.
        - ```python
head, tail = 0, 0
space = new Semaphore(N)
items = new Semaphore(0)

def produce():
	while True:
		item = Produce()
		wait(space)
		buffer[tail] = item
		tail = (tail+1)%N
		signal(items)

def consume():
	while True:
		wait(items)
		buffer[head].remove()
		head = (head+1)%N
		signal(space)
	
``` 
        - If you have multiple, need to set the area inbetween wait and signal as mutual exclusion zones. Use a Semaphore(1) as a guard.
    - Describe invariants and when they can be violated?―Invariants are facts that should always hold true about your program. E.g. in a linked list a node should never have no links to it. 
Invariants can be violated in a mutual exclusion zone, but the invariant must be held true if other threads can view an inconsistent assignment of states.
    - Briefly describe multiple reader single writer solution―Mutual exclusion zone for writing, need a write Semaphore(1). Resource blocking semaphore for readers, can only have so many so need Semaphore(N). 
    - What's wrong with this 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7AtNr_WcgbY9WcPUlPc8qeaqGXNOXsHuNNN9caOfGkNCV4duIBzM6x7svZlf-wO_d8taq0BFrTtjlDXt2qPFX2nr45DBvWsejgx6N3YMP7Y4g3oQWxelv1b-TlE-iUM4.png)―Writer can starve. Solution is:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ro_eGgtYR044CvQ2JdjMxq9aKc0RromI0Cb3-YOL4Umzjpo-KWVZ7pNHok2d3T_inR7g_mKfG8rQ97hCKEssSsFoTXIgoRKNEGL-pKAjwcrktKRRXZyZP8zoobEvaMAi.png) 
    - Describe Conditional Critical Regions  ↓ 
        - Certain variables are set as 'shared'. The programmer can the define a region where certain variables are being used Then the compiler handles the mutual exclusion: 
        - ```python
shared int A,B,C;
region A,B {
	# use A,B safely
}
``` 
    - What do Conditional Critical regions do when an await expression isn't True?―They leave and try and re-enter the critical region - this is just spinning though, and is inefficient.
    - Describe the basic idea of monitors―Monitors encapsulate all the data and methods that a group of threads would want within itself. Then, whenever a thread calls a monitor method - the thread is blocked and added to the monitor queue. The monitor **only **allows one thread to execute in it at a time - thus ensuring mutual exclusion on it's methods. 
You condition on a certain set of pre-defined variables.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kHqv1H2SwKJOMW4s0zRPowSrEjiC2VF2OqqFT02OooFvM-IVkGYPk5uZTAofmkV6-P0JTDiz1fTyA-4dWfrKHCmNTBx55lQlPRu-2oJCDzcJ4_uwulXRq-RcTe2zsp-t.png) 
    - Describe what happens when a standard monitor calls $\text{wait(condVar)}$ or $\text{signal(condVar)}$   ↓ 
        - A call to wait, suspends the calling thread, **releases the monitor lock **and adds it to the condition thread
        - A call to signal releases the monitor lock and wakes up a thread in the CV queue.
    - Describe monitor condition variables/condition queues―If we need to wait for a condition, we need the standard wait and signal on that condition and associated queues (but no number like in semaphors). We also add broadcast which wakes all threads in the queue. 
Wait call:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SJ3VIJknxs1tHV2xDXD2bq8kZQGqyZv1jiXdKQfhOqDs3gl12-OYtp50L6XuuzY51cwxarnjFg-tueeGIZTXmiKsSqfdgnItCdjfOfj-CnoWc2xUz3YGv5RvsaCAHWIn.jpeg) 
    - Describe Signal-and-wait ("Hoare monitors") and what problem they solve ↓ 
        - Instead of having two queues you have three, a **condition queue C** an **entry queue E, **and the new **S queue**. Then when a thread T1 invokes **signal**() on some condition - the thread it would have woken up in C (T2) takes over the monitor and T1 is placed in **S**. 
        - Then when T1 leaves the monitor, some thread from the S queue is selected before the E queue.
        - This solves the issue where we could signal() and still have work to do, and then two threads would be within the monitor.
    - Describe signal-and-wait, how does it differ from signal and continue?―Signal-and-continue instantly pauses the signal()ing thread when it calls signal, thus the condition it checked before calling signal **must still be true**. Signal and continue on the other hand could add multiple threads to the E queue, and thus the condition it called one thread on could be violated before it is invoked. 
So we need to continually test on the condition in signa-and-continue.
    - What is a mutex―Essentially binary semaphore.
    - Describe barriers―All threads must reach a certain position in the code before they can continue. E.g. in a simulation, they all must reach the end of the day before continuing.
    - What is a re-entrant lock?―A re-entrant lock is a lock you can grab multiple times, without blocking yourself. You need to unlock it as many times as you've locked it before other threads can use it. 
Java uses them.
A usecase could be graph traversal, you want to lock a node but can't check if a previous recursive call already got the lock. So you grab it again (possibly) and unlock it after your recursive calls. 
    - Describe java wait and notify primitives. What are they used within?  ↓ 
        - Wait and notify are used within synchronized blocks, you can synchronize on a class or on state within that class - or you can synchronize a method. 
        - When you call wait, the thread drops the mutex it had on the state and sleeps
        - When you call notify, the sleeping thread gets awoken
        - Inspired by monitors, woken up threads go into a waiting queue - so need same signal-and-continue spinning on conditions. 
    - There area four conditions for deadlock, Mutual exclusion, Hold-and-wait, No Preemption and  circular wait - Describe them AND possible countermeasures ↓ 
        - Mutual exclusion - resources have **bounded **owners. 
We could allow anyone to access a resource but not very safe.
        - Hold-and-wait - A thread can hold lock X while waiting for lock Y
We could make sure to allocate all resources at the beginning of running, but we don't always know what we'll need.
        - No Preemption - A thread can hold a lock X until it chooses to release it.
Mutex timeout - or resource stealing both unsafe.
        - Circular wait - Cyclic dependency. A waiting on B waiting on C waiting on A
Impose a **partial order **on resource acquisition (need X before Y) , can work but is hard. 
    - What do thick vs dotted lines mean and what does a cycle mean in a resource allocation graph.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0afr7yxJXKXQE74LmtHCuGJ0pr_81-lQX5l3F0N6EnNVNFujerjYvuDWmaV_Q7F7qEvhjw_8AJwHfUnfDgKA_w1K6WHgBDRFzEBftcnf0YHeLe4x2xHEVzKw1ocf1Oa9.png)―Thick lines means a thread **holds **a resource. Dotted lines means a thread **wants **a resource. A cycle means we will have a deadlock. There's a cyclic dependency in the graph.
    - What is deadlock dynamic avoidance, what are the assumptions made?―We assume that if a process receives all required resources it will complete without error. We also assume the maximum possible resources required.
Thus, we track the resource usage and only grant requests if they won't cause deadlock.
    - Describe Baker's Algorithm and give a little description of why it works ↓ 
        - Start with an Allocation matrix for each resource and each thread, e.g. what they're currently using. And a request matrix, what each thread is requesting.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WfiXswtcWtAw08ZS6-bHFWKTB-t25vbhlFvuKCRiYrjaIEoAEAmwYZ8Kon8OXeM5rEUvn18EM8rcTPou1k1CaYRH2EUqtbnEwKKVoHS-BrymCwfmBGcUGMhbTgZNcKCx.png) (Ignore the red lines)
        - Additionally, we need a resource vector (amount of resources left) and a W matrix **initialized to v at the beginning**. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5Wtd_ciWF_GLnesBvcGE299NUmbuiUQTapOnsFKPP87QmkEiRmpZAcQ3UKoOlRv28fE7ngx3Xz4kzPXCgkTxV3LPBHdjg19dqwYQarmNxE-N0Cf7ixdIxgoHdottWWwL.png) W will be the same as V to start with.
        - Then repeatedly find requests that can be satisfied in R and add the corresponding A row to W. When you do, mark of that row in A. When all rows are marked then there is a path of no deadlock, if we cannot find an appropriate row in A then we'll have deadlock. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bfLHmtD15qEYwh7w4Sk_SZDSgwzU3fH-Ioya86zNW6SHvD6FE9iKTstQIpRmWcx3IRyidrXMw4URYxmKZRQAkf8t2dttfjAEczJTen7yC2nHpRkFSgbLpukM_RcpGxSl.jpeg) 
        - This works, because we assume if a threads resource desired can be fulfilled it will give back all it's currently used resources to the pool. We work out if there is a possible ordering which would lead to fulfilment. 
    - Describe priority inheritance, what does it solve? Give 2 problems with priority inheritance  ↓ 
        - Priority inheritance solves priority inversion, where a higher priority thread is waiting on a lower priority thread.
        - Priority inheritance means, when a thread T1 (high priority) is waiting on a thread T3 (low priority) in a critical section T3 takes on T1's priority. 
OTHERWISE, when T1 sleeps while it waits for the critical section - T2 would be queued first as it has a higher priority than T3.
        - Hard to reason about what will happen in the program. Much harder to implement with semaphores or similar, easier for locks as you know who holds them.
Avoid sharing between threads of differing priority, otherwise you get problems like these.
    - What is the available parallelism for:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ruH9smrhvVZGI5piYGfjtnNXHK3jf6UmN87SwMt7IlC3sntm0_Eawc6vM5_eT4jiDCYUpTgGFSHSW6FeffJGPhEefXANI0jzUX0QKovJjf2aqVOZySON8WacazgBLbaQ.png)―Time taken = 4+8+2 = 14
$$\text{parallelism} = \frac{35}{14} = 2.5$$ 
    - How do you do concurrency without shared data?―We ensure that every thread owns a particular piece of data, then when they need operations performed on other data - they request the thread that owns it. This "requesting" would need to be concurrency safe!
    - Describe Active Objects  ↓ 
        - Like monitors, but the threads request commands to be completed not time to use the monitor. Thread makes its methods, clients make requests and the active object returns a value when the request has been completed.
        - Need to queue requests. Need to manage mutual exclusion when needed. May need to **delay requests** pending conditions (e.g. if a buffer is full). 
    - What does the ! mean in :
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YAlEOujFZQU8dDm2DYaKVO7N8-ubW6llwbsp1bUJOkMen2T0T64HoGeRsgw03dDAL6imu3C_e3iXzK-7FsCtTIuun_r_zNNgQ6QqHGtz7zBnhKgcHZ81DW3qZ2ZCSsnx.png)―It means we're piping 18 as a message through c1:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ae2NczUC-PZ4EuBJWyuJz2Mosq3eHb2mp1Fp643rPcnELKPw9rtsBt-0L9Yo8JTmnA3ZynS8R9FHuSSbz1eCufZ-w-KWwiLw5UrHchhNfZiVs8Buxil7MRgnwyK0C2wr.png) 
    - Give 3 message passing advantages ↓ 
        - Flexible API - can batch messages, schedule them etc.
        - Copy semantics avoids race conditions (hides asynchrony)
        - Works between and within machines!
    - What are composite operations and how are transactions related?―Operations on multiple objects, which we want to be thread safe in their entirety:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eU4YjlosPq93AyGV79EtrtktyG9H6yyDsTrZrG05f1LdLtj-7C8XwQy8H8T7HXOx4kC3F4lEwMMKrR3_H2rhZs6V_aXVJv9bt4iaTFLFjAvVoZsNwmJHGwOpEMWD4kuZ.png) 
Transactions are "atomic" operations that either succeed, or have no effect - e.g. if we move money from one account to another, we either succeed or **no money get's moved**. We want to be fault tolerant, so this occurs regardless of any crashing. 
    - What are the 4 ACID properties?  ↓ 
        - Atomicity - this means either whole command passes or fails. 
        - Consistency - Want to preserve invariants.
        - Isolation - want the operation to not be affected by any other concurrency in the system.
        - Durability - want completed operations to survive subsequent crashes 
    - What does it mean for two transactions to be serialisable―It means we can execute the transactions concurrently (e.g. interleave computation), but get the same results as if they were executed serially.
Code is serialisable if we can swap the ordering of non-conflicting operations.
    - Describe when two processes are conflict serialisable―IFF we can rearrange the operations and no two conflicting operations change order. Conflicting being non-commutative e.g. load then store vs store then load.
    - How do you construct a history graph?―Nodes represent individual operations, edges represent the happens before relation. Insert nodes in program order with edges between them as normal. Then insert edges between nodes of different programs that don't commute.  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pNKK4dPmKVhlAuU9wImIo11MK4OLeGxGFUTmFRa5MQrr9ecIm6NpC9C8IGnNoG-iIW7akRYyT3yCuLroEoa9t5ItCdSkrTbDQRhRwE9o7j7Gvyo5zxnLbiiua27zZvMM.png) 
    - Give 3 negative effects of bad schedules ↓ 
        - Dirty read - read an item in the middle of it being updated. Lack of isolation.
        - Unrepeatable reads - reads an item then updated by another thread, can't read that value again. Lack of isolation.
        - Lost updates - overwritten write. Lack of atomicity.
    - Describe two-phase locking and it's issues. What is strict 2pl? ↓ 
        - Expanding phase - where locks are acquired but none are released. 
Shrinking phase - where locks are released but no new ones are acquired.
This is to ensure isolation, but you must ensure you release and gain locks in the correct order - otherwise a dirty-read/write could occur elsewhere.
This guarantees serialisable execution!
        - Requires knowledge of which locks we need at the beginning. Can cause deadlock, but can abort if deadlock is detected.  
        - Strict-2pl release all locks at the end.
    - Describe Rollback - how does it help with deadlock?―Rollback is where we reverse the effects of an aborted transaction. It helps because we can delete processes in the case of deadlock, and safely perform a rollback.
    - Describe the two methods of implementing rollback  ↓ 
        - Undo - keep a log of all operations and undo them if we rollback.
This causes issues because if we undo a setBalance() what if we didn't read the previous balance? 
        - Copy - save the state of the object you're operating on before beginning our transaction, and if we need to rollback just restore the copy. High overhead, which we can reduce with partial copying. 
    - What is time-stamp ordering?―Give every transaction a number (think current time, or other increasing number) and objects record the transaction numbers that operated on them. When a new transaction tries to access an object, it must have an equal or higher transaction number than the previous transaction.
It would then have to abort and restart with a later timestamp if unsuccessful.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i_01BHOHJY7em6R7iZQdbZ2f5Xpyyu0UJXl7meKB5586Tj3MMK7REQkJMpc5Sh-vBGYT9-36wNo2sa3ASOLeT-0CZpMV64wLT7t3nFaE0TPwl0VP2ESUV03cMzX_p95E.png) 
    - Give code for read and writes for time-stamp ordering which distinguishes between reads & writes  ↓ 
        - ```python
def READ(O,T):
	if (V(T) < W(O)): abort # If written to after us, abort
	# do the read
	R(O) = max(V(T), R(O))
	
def WRITE(O,T):
	if (R(O) > V(T)): abort # if someone has read after us, abort
	if (W(O) > V(T)): return # if someone has written after us, they win
	# Do the write
	W(O) = V(T)
``` 
    - What are some problems with TSO? ↓ 
        - Struggles with contention, can have transactions repeatedly aborting and retrying
        - Imposes a single serialisation, even if others would have been possible 
        - Not strict isolation ⇒ cascading aborts. Needs a rollback mechanism.
Best for distributed systems, where conflicts are uncommon.
    - Describe the basics of optimistic concurrency control, what are it's advantages? ↓ 
        - OCC assumes conflicts are rare. And we work on shadow copies of the data, then when we're ready to commit make sure there are no conflict. E.g. No-ones committed any later changes to the data
        - No deadlock, no cascading aborts, and rollbacks area free.
    - Describe how OCC is implemented  ↓ 
        - Each object stores a timestamp of when it was last written to. Then when a thread wants to make a change they submit their edited shadow to a **validator**.
        - The validator then decides on the optimal subset of transactions such that maximal concurrency is achieved, the remaining transactions are sent back to be aborted.
    - What is Read validation and Serialisability validation in OCC?  ↓ 
        - Read validation - must ensure that the order of transactions reading objects is correct, the time they read them becomes their (tentative) start time. We'll then check if that time is correct or if there's a conflict. **E.g. read before the latest commit.** 
        - Serialisability validation - must ensure that committed transactions don't conflict. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-bq1ANpOgQtKteQPeRzDpW6ylcjcY6jzssHK8I1n327vtVoeFZujbAUSMGujD7pFFWj-LcIuUWonAmYkcCNcPpIdjUd2G8b2PWF3Nj8RqgxvvCCEFvhF76xxipeLSbPF.png)
What will happen?  ↓ 
        - First T7 will make shadows of B and E with timestamps B@10, E@9. After doing it's work, it'll submit it for validation.
        - The validator will first check if the reads are in the correct order. We note that the latest commit was at 11, and both 10 and 9 are earlier than that.
Additionally, both B & E haven't been committed to since 10 & 9. So all is well.
        - The validator then performs serialisability validation and checks all "later" transactions, and finds that T7 is writing to E but T8 read the old E. And must then abort the transaction.
    - Give an issue and benefit of OCC validation ↓ 
        - Doesn't perform well under conflict, working for long periods with stale data. Starvation possible and the transaction system does not necessarily always make progress.
        - Will find more serialisable schedules than Time stamp ordering 
    - What's the problem with improving durability by just writing to disk, what's the solution? ↓ 
        - Writing to disk, could crash during a write. We won't know what data is correct and what's garbled.
        - Use write-ahead-logging - FIRST, write updates to a log. SECOND, commit those updates to disk. If we fail on 1, then the update isn't done (no problem). If we fail on 2, then we use the log to undo or redo. 
    - Describe the write-ahead log, and what happens when we move an item from the log to disk ↓ 
        - Write head logs store <transactionID, which_object_updated, OPTIONAL(operation_performed) ,old_version_of_obj, new_version_of_obj,  >. Note these logs are **append only.** 
        - When updating to disk, write the <txid, START> in the log. Then write lines describing the operations performed (Which bit of memory updated where etc.) then write <txid, COMMIT>. Always write the log BEFORE writing to disk - use fsync() or similar to force a write to disk
    - Describe updating a checkpoint to a write-ahead log, a necessary action to conserve space  ↓ 
        1. First flush your current log records to disk 
        2. Then start a new CHECKPOINT section, then record your still active transactions - e.g. latest reads/writes
        3. Flush any dirty objects to disk (Ensure values on disk are updated)
        4. Write the location of new checkpoint atomically in a known location on disk. Then truncate the log, and discard parts not need
    - What is the benefit of checkpoints?―In the event of a crash, it allows you to decide which transactions need to redo, and which need to be aborted (and which transactions are fine). 
If an transaction completed before checkpoint, we don't need to consider it.
If a transaction completed after the checkpoint but before the crash, then we need to redo it.
If a transaction hadn't completed by the crash, it needs to be aborted.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9y5K6Eqyt94keD6fg5cmxeD9WW-zmRlDV3fjeMuldyQ3TUndTNv1KtytaJu2Ces5YpWe541Lb1_hfelmvOlgyGPkDZ29bKHu-sxEAwaRs9aq3xCM-TIFrgZUuZLsirYo.png) 
    - 
    - Describe the Recovery algorithm with checkpoints ↓ 
        - Start with an UNDO set (initially filled with the currently active transactions) and a REDO set {empty}.
        - Move through the log, if we find a START message add that transaction to UNDO - if we meet a COMMIT message move that transaction from UNDO to REDO 
        - When we reach the bottom step back up, aborting anything in the UNDO set.
        - Then iterate down and redo everything we meet in the REDO set.
        - After recovery, we've effectively checkpointed - so truncate the log.
    - Give some problems with locks ↓ 
        - Easy to make a mistake
        - Don't scale well 
        - Don't compose well (deadlock)
        - Can cause cache slowdown (not spread out on the cache system, can have multiple threads all smashing the cache at once)
        - Can be expensive
        - Priority inversion!
    - Describe how the lock-free approach would work with a linked list with functions find() insert() and delete().  ↓ 
        - Iterate over with find as normal.
        - When a thread is running insert, we do a compare-and-swap with the pointer we're updating - so we don't get a write-after-write hazard.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BHSYSyHuDwtNh5YLlOAqVoTzifwBw_vUyu_jY4uSP6jU1R_u91e6rxnOAXKP4tPq9JUfsTMdg8HF5fhnE6-J3qXMHbW3m-T5pF_SU_IP4D1gzZ_FudgE_h116DEvtl03.png) 
If we fail, then we need to restart, and find the spot for our node again.
        - When running delete on 35, first remove the link from 35 - 47 then CAS the 21 pointer to point to 47. If we fail then return the link from 35 to 47 and retry.
Or CAS 21 to 47, not really sure lol.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TJsOYjHjxBV05RtGWNFbdKaSDQ2GHWM3PzgEx-GJRhoVMPRDWKUe74yQTvdHw8EMH74EWnq8l9MoJXYvL8i6FlgogAFj8TzyrbuZmoKnHV0X8fvzjYArPoVcVzuTSn4z.png) 
    - What is a linearizable schedule, how does this relate to lock-free data structures?―If all ordering of events, i.e. all changes and returns are consistent with some serial view.
Lock-free data structures must be able to handle multiple serial schedules, we can get read/write races - but we assume someone will handle this at a higher level of abstraction with locks or summat'.
    - What is transactional memory (TM)?  ↓ 
        - Convert: ```python
lock(&mutex)
sharedx[i] *= 3
unlock(&mutex)
```TO: ```python
atomic {
	sharedx[i] *=3
}
``` 
        - Under the hood, this is transactional: ```python
do {
	txid = tx_begin(&thd, sharedx)
	sharedx[i] *= 3
} while (!commit(txid))
``` 
    - Give two advantages of Transaction Memory (TM)  ↓ 
        - Easy to compose, as you can nest atomic commands in other atomic commands:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vsGZGynC1A1Tv2jyQcEAFpBKpiGIXaTJMb-Eazp2xruLmbj2F6iBFbhYA25OgYeaa6pzDFhqV6PvUXN92abwQ1B3iC08RM5jtymV6Rl_b5wEVrjsAI8D19Ni9bKOrhFq.png) 
        - Simple to use.
        - Can't deadlock, and no races
        - Very scalable - and fast because it's OCC.
    - 
