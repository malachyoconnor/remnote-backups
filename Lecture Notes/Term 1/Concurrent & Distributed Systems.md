- ^^ _Concurrent Systems_ ^^ _ _   
- Supervision 2
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
- Supervision 1
    1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/sd2R5eXh_2n9qz1rlMJFYdNLd0tG-bE0UaLbKmCsWpDMrlH-pHYl-ZYXdacYEQIOuqaugFW1YRGzMEU9GQ6JOBONxdF-ugR7vRcWjB1AKZSipTorsRhQrosKThDmkULR.png) 
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
    3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hB68m6SGg36hFL_xPZrweB2Eqg7k_MVpuvzdel9hIGD09WTMEsLGbpsWbnxmyGvH09l_OM7wDs9nDkFSYcrrMckP0b-W4XChfeRFosc3SSgvINuuRlz1TegpO9zNM9qH.png) 
        - Yes, because if we have a context switch anywhere between the weights (including just after the wait command is run) the various producer/consumer threads have different conceptions of the state. For example, if a context-switch occurred (in the case of a producer) before we changed buffer[in] we could resume the thread when the list is full and cause an overflow. Alternatively, we could consume the wrong item by the same means.
    4. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/D19kr_2Pf7_0ZafdDz9-dTMCRWKuzsTeC3BNISA9-vMa91p5xUIbPtkAcO-FvWKG-BOYddEfZNGpxymen8EKKA9v6OFpxc89bqDSu4Y6cYZwpsad_kCWmOu6P2Fstjta.png) 
        - In the implementation of wait & signal presented in the lectures, the problem would be making checking the queue and changing S atomic (for signal) or checking & changing S atomic (for wait) rather than the question posed above. This is because in the version presented in the lecture, only the first and last threads in the door change S.
        - Wait would be unaffected - this is because we only perform a decrement if S > 0 - and we only block a thread when S = 0. This means the two can never be in contention.
        - If signal's integer & scheduler operation were not atomic, we could have a race condition - in between the integer operation and the scheduler operation another thread could call wait on the semaphore and perform a computation. While that thread is running, we would complete our scheduler operation and our awoken thread would perform the same computation - this race condition could lead to anomalous behaviour. Waking up the thread first, and then incrementing the value would solve this.
        - 
    5. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/33akS39qWNR2m71NzOgaRJBQFNkWyVBtTw06nG-8WkaHVY_RldW4gw2BUKle6mpGtR5l7Eizk96IOtfF0m8hj52Aznye1SsP6aGioBc16kDSvqDO1K60vUqc9_FwdWnM.png) 
        - Round-Robin - In a multi-core processor where each consumer thread is on a different core, we would spread the work to different cores to ensure temperatures of an individual core doesn't skyrocket which would result in a slowdown.
        - Prioritized Work - In a multi-CPU architecture where faster CPUs are in more demand for work, faster CPUs would be given a higher priority as they would complete faster and we'd like that time-save when those CPUs are available, while slower CPUs would be given a lower priority. 
        - MRU - If the CPU cores have caches that will have recent data stored in them, if a thread has been used recently it may happen that the required data to perform the computation is already in the cache (addresses of items etc.) meaning time will be saved which would have been spent fetching data from main memory.
    6. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/RdrlWILK0E0bNwSv0LdF4PR9LSwMfofFUuoeUnN2zZ51HMYhG-COY7mcbZQY7g0NXtGGAgopnKwofrjQhkZ-RW5b53cxNVacz10Dj-fph_bN_LdPWE_SrBDgb1eLYKHN.png) 
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
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bPGP_gNXPzszZu0_q37-gatUw0H5dw8izVNFee9drU-pzJ-qJsaKuetdA0NFulnHZLxjr7CjpzZMpGvCJCxYpVZWCmMPIlAGMK-4SQrszI27PiIeOky3BPa_hlCHoaQN.png) 
        - We can consider that the consumer and the producer interact with different sections of the buffer in their "guarded" sections - the consumer deals with out and the producer deals with in. We can then consider that the whole design of the spaces & items was done to ensure the back and front of the list cannot affect each other, that is we can never add to a full list due to spaces and can never detract from a full one due to items. So as in & out are safely independent, we need only protect our consumers from other consumers and producers from other producers. 
    7. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/y6BGMYo6C6AtmnKq8ltCZY67Be2lsy6CI2hVWujhK59XcjEncDNTVw9qCa3N4l3fOIbd_kzM-OmGGOfOdTIkNrFe_W9laL-85ipJVFLlCulSOooNdRFDJ1ZLkqcR-Mw-.png) 
        - Because generally there will be multiple (low priority) consumer threads in the guard queue ahead of the producer thread, they will necessarily be popped from the queue ahead of any producer threads. However, if you were using a mutex:
        - ```c
while (! test-and-set(note));
``` The thread that gets access to the resource, is the thread that runs test-and-set(note) first after the resource is freed - if the producer threads are set to a higher priority by the OS, they are more likely to run the command first.
        - 
    8. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/XtO2e4DqYfpL0B1gbYvMSEYqayEMkA50280I_JG5WD2FiCBcqtGMbZTY-fLOAmdiJLDuTOEe-alLzih8lCUPd9E7G_BCc0Dv_sxyKAGKcJd8IY8mq4XdPT6UXHgvTkhm.png) 
        - One could replace the queue structure with a priority-queue, rather than waking up the next thread in the queue in signal we would call popmin() (where a lower priority number signifies a higher priority) and the higher priority consumers would always go first.
    9. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Wy1sGRze451GrBUFtmUiDbaytnxBlC36EbdEbjjsWFZ2CaSDbQa78plAuoKq4hHoXQ5CslliK5YT_cJkEkuecGzqnKCKst6nEduav4Pibnv5blNuHzndlqfJqDSZCyOg.png) 
        - One solution would be to raise the priority of the producers (to high) whenever there's a high-priority consumer waiting - the wait() commands thus acts similarly to the signal() command, in that it allows another thread to run.
    10. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/cjRL7x0rri8fzqS45tGSxJ_lTt-r8ZbvSkwSlM-jlu96XC0v3j76VAMtqfibLO0JJQMDupkzyO4in-M9lDVC3LpA_f5UZ8DUvR3fXWzaR68yH9UANntExc4So-IiYXSf.png) 
        - Each thread has its own stack, register file and scheduling state, thus there will be two instances of each of these.
        - Threads share the executable program and virtual address space, so there will be only one instance of each of these.
    11. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gSeUH_wE-tW5DLaCuzxk0t7wair3fJw17i5FnYJAVLrFHH8d6hAQtJur1zWRVBjCKb5gsnuUcMNPlui8jIWfaKs-Wys6EhI_8toKLA9B3cFTitBM2p9WMPdN--zIbDxD.png) 
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
    12. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/r9xDNEUd21vdFWgQV_oBu_b-yT79qFcKluEGCeipA0baCbUXBf4g13mns3lEDnAmLdZwxbOyLpKM8587Ae9iw3K87JXbLdhpE_C6FkpF5JD65RNQAfDJqyiWzg03192u.png) 
        - n! As the OS is (modelled as) non-deterministic, we cannot know the order in which threads will be scheduled and execute thrprint.
    13. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rOmx9KUE6ei8U0fUQOOJT_dEeaW033n8VTJbWBYfwSH8oESnVDHu_5OpJl-KV63e0zBY8VNTCTXmF_RLMl1F0t5ujdZmkq99WLSKkC8Lk3_AKDNASEYiuUNcygfFIsWc.png) 
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
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gcADy-5emy1KJOIoJd595ND9GnD5-ptl-P6YS97lwBJayyx_m-ziHUyQeKJsIrMoEv3TZJd2euOaVtZE15SHtQdEbABINv6eTJNsILmfI65csyku1bmNsxdHQBmVlNKl.png) 
        - We could solve this problem using two additional pieces of state (and associated mutexes), an array of size N (number of threads) and a protected integer that starts as N. Whenever a thread is executed, it would do the following
            - First get control of the buffer and the protected integer
            - Then it would place it's debug message into the buffer at the index of it's thread ID.  
            - Then decrement the protected integer, if that integers value is now 0 print out all the debug messages and associated indexes and we're done.
            - Release the protected integer and the buffer.
- 
- 
- ^^ _Distributed Systems_ ^^ _ _  
- **Distributed Systems Lecture 1**
    - **Introduction**
        - What 4 advantages are there to make a system **distributed**?  ↓ 
            - Some Systems are **inherently distributed** (text messaging).
            - For better **reliability **- if one node fails others can be used
            - For better **performance **- different nodes for different parts of the world 
            - To solve **Large problems **- some problems consist of such a huge amount of data, can't fit on one computer.
        - The problem with distributed systems is that processes can {{crash }}and {{communications }}can fail without us {{knowing}}. Additionally, these may happen {{non-deterministically. }} 
        - We want **Fault Tolerance, **a system should continue working even if it faces these problems. 
    - **Computer Networking**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/J4ZxKhqnf7YPMc5Ea8liL9bMYQS-goUHpgeoYlVCrKv7VTkhfIle7j8MwYyoAPuOubzU79fQ5RZxTlDG74x2GtG5fd12tWrjFjdZ8LkE9qxWOodDrXj3pIubVuBOE0Ne.png) 
        - The fundamental abstraction of distributed systems is that of {{nodes }}sending {{messages }}to each other.
        - **Latency: **Is↔the time it takes for a message to arrive 
        - **Bandwidth: **Is↔The data volume per unit time
        - **Client-server comms over the web:**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/6IhRlUSXdP3733UVQmOFVDHC6Y0SLe-fYyKuwmLbL3b2U5a2oy4D7ZPz0nHz3m1t06uB3w_2pTNhRk2qpGDvSoLsQpaN92fCXiIZzljH8icC1Qndznxoklb3M_CdU0Df.png) 
            - URLs are separated into the {{server name}} and the {{path of the page}} you'd like to get.
    - **RPC (Remote Procedure Call)**
        - Consider an online shop communicating with a payment service:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/NHXB6R_B2KKd0WN4Dpvtf-FS0i_-AZwnXGdIDp-4KeagopAQLGHJdKnebhFw-cyNVYqG20tL2suIEBVbuKa7_l5sN7OtQ2-A53JtIsVMwGEaIr2-G8yAuLXLB5OzsoV9.png) 
        - We can have a function applied to the shops card object, that is processed on another node/s (that of the payment service). What looks like a function call, is **translated to a network request. ** 
        - **RPC **is used to→invoke a function call from your local machine, on a **different machine** via **network communication**.
        - RPC's are implemented using a **RPC framework:** 
            - RPC frameworks implements **stubs**, which are→function definitions with the same type and arguments as the function to be called via RPC. This stub function sends a message to the other node to process the payment.
            - The RPC framework "**marshals**" and "**unmarshals**" the arguments, this means→it encodes the arguments of the stub so they can be sent over the network, then on the other end the args are reencoded into the function:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/r037lljqIJLOb5QtnsdTRQFyTEq8ssiKFEVmqAV4vYTAhU1BleC9nB8lqX9fcHYH1Y9i0aaPShY4UuPiNLGOOjnppR4QRSBrY-L7djycaZ1vuuIvlWO_AoOhgYd7rpmM.png) 
            - The return value is then sent back, via the same process.![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3fJb_xRoqYCt3dK-TfmYos_wLSknPOsok2cuONek9VDV2yCb_PhIoxuDDhLMbTMX7rvHTUa6KYJJYoBcAB6SOaqktjRaobFagTDvg39xb5-sQ8dAkriVULQGXoWD0j2e.png) 
        - We would like our RPC call to look the same as a {{local function call}}. This is **Location transparency, **the location of resources is hidden. 
        - **RPC in enterprise systems**
            - RPC is used in **enterprise systems** because→these systems can become so large that they cannot be run on a single computer. 
            - A "**Service oriented Architecture**" (SOA)→is the architecture in which a **large service is broken down into microservices** on multiple nodes which **communicate via RPC.** 
            - If multiple services within SOA are **running different languages**, we use→Interoperability (**datatype conversion**) and IDLs (Interface Definition Language).
            - An IDL (**Interface definition language**) is a→Language independent API specification. Method of ensuring datatypes are stored in a method not specific to any one programming language.  
            - Example IDL: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/0xdtpuDkEuhCU8penCtWhT3yg4iFSQacbIje6oM4eGYy5K-eQRmFuyFQ7oE1txO74kASiw2cYLWza3bW8Ho_A9Ur1gMwi_U-gk95VJY_GhJL2GuRgF4IgJ9PpafguiKQ.png) 
    - 
    - 
    - 
    - 
- **Distributed Systems Lecture 2** **(Models of distributed systems)** 
    - **The two Generals Problem:** 
        - Consider two armies, if they **attack together they win** - but if either one **attacks alone they will lose**. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/kZF5kAjLXMdskp7Es7wh7db6UkMY_9NZcFf9DvSpP-6zUwEsFYgDhPIpmv9ovYPdIQwryWGSfXEzul_ZeP-_trYhNxI-asW1L4n7bEtV62xzcnLhcC1BrwMoEJndrbZj.png) 
        - The two generals can only **communicate via messengers**, however the **messengers may be captured** and the  _**sender could not know**_  (except if they receive a response).
        - Initial message delivered, but the response is captured: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bP57WAkbwWs9MDQXFH0vELMgsOf0iZkhPpGCCu2cYZXMwBbw0BcAZGgMpinj8FVjILtbJtjaWE77MbaPaEcPw4UNaQiW7X86i4TjGhQqxyze-gddSQENt1dJ-Yb57bNI.png) 
This is indistinguishable from the following (**from general 1's POV**): ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Ey46dnl7hwQePgXZ1o7bHuVw7OV6dgmdaS3mxrncvAibJNFQMW2JzRp0Hjg3CHDJdpgQJe1ks_lNrCWzAa0v5pvvzqe3NpjyUCiXLeskxHn_4bkAF0GDD-8UEPlzP54Y.png) 
        - **In the two Generals problem, General 1 has the following two choices**  ↓ 
            - **Choice 1**: **General 1 always attacks**, in this case they may **send lots of messengers to increase the probability of receipt** - then  _if the message is received General 2 knows it's safe to attack_  (even without sending a response).  __**However**__  __, __ if the message isn't received General 1 will die. 
            - **Choice 2: General 1 attacks if a positive response is received**, in this case General 2 is safe **if** a response arrives  __but __  _General 2 is in Choice 1 when they send the positive response._  
        - This can result in an **infinite chain back and forth of communications** where **no absolute certainty of an attack is reached.** 
This is the problem of **No common knowledge **in DS which is→when the only way of knowing something is to communicate it. 
        - An example of the two generals is the following:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/CfPVn-fTG7HNM1XhiINgF1iSMSKSHqv5Rny771BO2iMwu7RG4OxInE0oxC2IjB-5Gx98WFGcN6o2UB-bAvPjpe_fCoomhEBPbPBpRM0qZph8ADP66ZqlNx3rs9kE7IiS.png) 
The reason that this differs from the Two General problem is that→The **charge is a revocable action**, we can always return to the starting point.
    - **The Byzantine Generals Problem:**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/kVjnfDY9vy2AyF3x7MfD3YRsM_q6WT92dlh1O5oVermmNCANiw2qsOklQ7t9MwAEvRVMI8T9RSns63Oxj1ZLVqKrPlOnvNVfpGGtZbJzSsMiyZEUKDmymk_B4C_K77kG.png) 
        - Within the Byzantine Generals problem we make the assumption that communications are {{reliable}} but some of the generals are {{traitors.}} 
        - We further make the assumptions that {{up to }}{{$f$}}{{ generals are}} malicious, that traitorous generals {{may collude and know who the other traitorous generals are}} and that honest generals don't know {{who the traitorous ones are.}} We then require that the honest generals must agree on a plan. 
        - **Generals may lie**:
 ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5y7MCi0wsHxY59MPzWPIY-KL9gZc7jv7vo3MtTd6mxd-w5A8cbXB2dVuqGqFRn7tXBDkPwuSroBGKrMrS6APOTSaJBc47XpUQ7MXSuhSUPoqF40YQTYjbmRoSn0ehD3M.png) 
General 3 cannot tell who is lying!
        - **Theorem**:  _We need _  _$3f + 1$_  _ honest generals to tolerate _  _$f$_  _ traitorous generals._  I.e. $< \frac{1}{3}$ may be malicious 
        - **Cryptography: **Digital signatures help, as we can prove a certain party sent a given message, however the problem is still hard.
        -  _Real life agreement_ :
 ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/OxXWMFBndgJuLV8Z1-F3b7M6MusMgTuaDnq4kdDu1NCuYCwNFYLcf2ZWcy0x7MREMxDxTAFlZBvRqp2KYAy7vk9N5wUx_LGgLiiYJkQp5ge17R3NzXory9ZLFYnxV946.png) 
Customers can act fraudulently, online shops could be fraudulent etc. (could have asymmetric relationship where the payments service is trusted).
    - **System models**
        - We have seen the **two generals problem** in which the {{communication medium}} was faulty and the** Byzantine generals** problem in which {{the nodes}} were faulty. In real networks **both can be faulty**!
        - **Networks are unreliable**, can be damaged by nature.
        - **System Model: Network behaviour**
            - Assume a **bidirectional point-to-point communication** between two nodes. The **three models of such a link are**→a **perfect **link, a **fair-loss** link and an **arbitrary **link.
            - A **perfect link** is→a link where no packets are lost, reordered or damaged.
            - A **fair-loss** **link **is→a link in which some packets can be lost or reordered, however we make the assumption that **if we send a packet enough times** it **will be delivered**.
            - An **arbitrary link** is→a link in which anything can happen. We model this as having **an adversary acting on our communications**. They can replay, block or edit packets as they please.
            - A **Network Partition** is when a **link **between two nodes is **disconnected for a period of time.** 
            - ^^A ^^^^ _fair loss link_ ^^^^ can be converted to a ^^^^ _perfect link_ ^^^^ using^^→^^Continuously resending, and deduplicating at the other end. ^^ 
            - ^^An ^^^^ _arbitrary link_ ^^^^  can (*almost) be converted to a ^^^^ _Fair-loss_ ^^^^ link using^^→^^TLS. An internet protocol to guarantee successful communication has not been tampered with. 
This is only arbitrary, as the adversary could block all packets.^^ 
        - **System model: node behaviour**
            - Under the assumption that each node executes a given architecture, the three types of nodes are→**Crash-stop**, **Crash-recovery **and **Byzantine**.
            - A **Crash-stop** node means→the **node could crash** at any time and **never re-join the network** (dropping phone in toilet). 
            - A **Crash-recovery** node means→The **node could crash** at any time,** lose its memory** state but it **will re-join** the network at some point. 
            - A **Byzantine node** means→A node that **doesn't follow the algorithm** (although it could pretend to).
            - A node is either **correct **or **faulty.** 
        - **System model: synchrony (timing) assumptions**
            - The three types of **synchrony assumptions** about **nodes and networks **are→**Synchronous**, **Partially synchronous** and **Asynchronous**.
            - A **Synchronous connection** means→Message **latency is no greater than an upper bound**. Nodes execute the algorithm at a **known speed**.
            - A **Partially synchronous **connection means→communication has **(finite) periods of asynchronicity **but is synchronous otherwise.
            - A **Asynchronous **connection means→Messages can be **delayed an arbitrary amount of time**, nodes can be suspended an arbitrary amount of time. 
            - Real networks behave in a partially synchronous manner, under such a system an algorithm designed for a synchronous network could fail catastrophically.
            - We can have many **real life violations of synchrony**, within  _**message latency**_  we can have: 
{{message loss}} requiring retry - removing any hope of an upper bound on latency
{{Congestion }}causing queueing
Network/route configuration, meaning a packet could get stuck for long periods of time.

            - Similarly we can have changes in node execution speed:
{{OS scheduling}} resulting in a thread being suspended.
{{Stop-the-world}} garbage collection pauses.
Page faults, swap, thrashing (constant page faults).
            - **Real-time operating systems** (RTOS) can give some scheduling guarantees - however most DS don't use RTOS.
    - **Availability**
        - Online services being offline = losing money. 
        - We can **measure uptimes** using the fraction of time the service is operating correctly. For this we can **use "nines**" 
'Two nines' = 99% up ⇒ down 3.7 days/year
'Three nines' = 99.9% up ⇒ down 8.8 hours/year
...
        - **Service-Level Objective (SLO),** the period of times the service will be up and the response times. "99.9% of requests get a response within 200ms"
        - **Service-Level Agreement** (SLA), a contract specifying some SLO ⇒ there will be penalties for failure to meet the SLO.
        - **High availability: ****Fault Tolerance:** 
            - We have a **Failure **of the system, in which the system as a whole stops working. We have **Faults **where a node is faulty or communication with that node is hampered.  
            - **Fault tolerance** is the design of a system so→a given number of faults does **not **result in a failure.
            - A **Single-point-of-failure **(SPOF) is→a **single point** in the system where a **fault will result in failure**. 
        - A **Failure Detector **is an algorithm that→detects if a given node is faulty.
A **Perfect failure detector **is an algorithm that → says a given node is faulty **IFF **it has crashed. 
        - The **typical implementation** of a failure detector is to→**send **a message to the node, then **wait **a set amount of time for a response. IF the node doesn't respond in that time it will be assumed to have crashed.
            - The problem with this implementation of a failure detector is that→we can't know if that's because the node has crashed, the message was lost or the message/node was only very delayed.
        - **Failure detection in partially synchronous systems**
            - We can only build a **perfect failure detector** in a→**synchronous**, **crash-stop** system with **reliable **links.
            - Instead we have a **Eventually perfect failure detector **this can→**temporarily **label a working node node as crashed or **temporarily **label a crashed node as working. **But, **it will **always eventually reach the truth** of the labelling. 
            - This reflects the fact that detection is not instantaneous **and **we can have long timeouts from a working node. 
- **Distributed Systems Lecture 3 (Time)** 
    - **Physical Time**
        - Distributed need systems to measure time, used for:
            - Scheduling
            - Performance measurements
            - Log files
            - Data with time validity (e.g. cache entries, TTL)
        - The difference between a **logical **and **physical** **clock **is→Physical clocks count **number of seconds** elapsed while logical clocks count **events **(e.g. messages sent) 
        - **Quartz Clocks**
            - Quartz crystals can be engineered to vibrate at a particular **resonant frequency**, this frequency can then be detected (and fed back into the crystal again to keep the vibrating going). 
            - We use this **quartz vibration** by→counting the number of cycles to measure elapsed time. As we know $f$ 
            - Clock drift is measured in parts per million, meaning 1ppm = 32s/year of drift. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/acy_5LTVfZi7tnDFZQCnv__uIjFbqSiIwq8P9U5BQXY2cNJN_RXcJM9g1BVOQjjT9FwYNIKdhyhX248FmQyvO9sf7C7HX4nmYpXFVWvK-3_GpHMASP-kA3Al6KhMy0f-.png) 
        - **Atomic clocks**
            - Caesium-133 has a given **resonance** we can measure - about 9 GHz . The second is defined by 9192631770 periods of that signal. We are of by 1 second every 3 million years
        - **GPS as time source**
            - 31 Satellites in space broadcast their **location** and the **time **from their atomic clocks. We then pick that up, and can calculate the time taken for the signal to arrive (via c) and thus get the time.
            - We do need to correct for atmospheric effects and suchlike.
        - **Coordinated Universal Time (UTC)** 
            - **Greenwich Mean Time **is defined by→noon when the sun is in the south, as seen from the Greenwich meridian
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/R9jUYQZGK9nZ6IIhjhW_voek4fxcitDPk3Z3yWTRZj4hvYUVxeEFkbBKxIp1khhsXIy1YwU9mFeTkWVNR9tfhkVwGoKuz0MgWIt7384d0evYj6KJCVM3w2IsCIT7qFv5.png) 
            - **International Atomic Time (TAI (based on French)) is **→ time based on Caesium resonant frequency 
            - **Problem: **Speed of Earth's rotation is not constant
            - Because of the disagreement between GMT and TAI, UTC is→TAI with corrections to account for Earth rotation.
        - **Leap Seconds**
            - A leap second is→a second that can be inserted or removed (typically) twice a year
            - Every year on 30 June and 31 December at 23:59:59 UTC, one of 3 things happen  ↓ 
                - The clock jumps forward to 00:00:00 without waiting a second (a **negative **leap second) 
                - The clock continues to 00:00:00 after a second as normal
                - The clock continues to 23:59:60 after a second, adding a second (a **positive **leap second) 
            - Leap seconds are announced several months in advanced
        - **Most common timestamps**
            - **Unix time: **Which is→the number of seconds since 1 Jan 1970 00:00:00 UTC  _not counting leap seconds_  
            - **ISO 8601: **Which is→year, month, day, hour, minute, second and time-zone offset relative to UTC. E.g. 2020-11-09T09:50:17+00:00
            - Conversion between the two requires **Gregorian calendar** to calculate leap years and **knowledge of past and future leap seconds** 
        - Most software ignores leap seconds, however OS and DistSys require them.
        - **Smearing **is→The  _spreading out_  of a leap second  _over a whole day_ . This helps prevent software that doesn't manage leap seconds from crashing when encountering a discontinuity of a second.
    - **Clock Synchronisation**
        - Computers track physical time/UTC with a quartz clocks - and due to clock drift the error gradually increases.
        - **Clock skew** is the→difference between two clocks at a point in time 
        - A **solution **to clock skew is→periodically get the time from a server with an accurate time (based on an atomic clock/ GPS). Using the **NTP **protocol.
        - **Network Time Protocol (NTP)**
            - An **NTP server** is→A server to give an  _accurate time source_  for computers to sync with. Many OS vendors run NTP servers and configure their OS to use them. 
            - **Hierarchy of clock servers** are arranged into **strata, **these are→ __
Stratum 0__ : atomic clock or GPS receiver. 
 __Stratum 1__ : Something synced with Stratum 0 device
 __Stratum 2__ : Something synced with Stratum 1 device
            - NTP servers may query {{multiple clock servers}}, discard outliers and average the rest. Furthermore, servers are {{queried multiple times}} to remove network error
            - Using NTP we can reduces clock skew to a few {{milliseconds }}in good network conditions, but can be much worse over a {{bad network}} .
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3H78pNX0DSOHMqLDwyVPqkjGFU7zmOV7K0fZkHoGgXtkzVZAm7wjLcoEQttsBlj3Hrz4FkSwU39_HL7Ev8iQ5-vxPvQlrTV2aG0Uz4DBV2l7p856O5XpanEJArqHOIc2.png) 
                - The round trip network delay would be→$\delta = (t_4 - t_1) - (t_3 - t_2)$ 
                - We can't find the time taken for the request and response individually because→the two clocks aren't synchronised. We can only get the time difference between two timestamps of the same clock. 
                - The **estimated** the **server time** when **client receives the response** would be→$t_3 + \frac{\delta}{2}$ Because  _ __we assume the delay each way is half the total__ _ .
                - The estimated clock skew would be→$$\theta = t_3 + \delta/2 - t_4$$ 
        - **Correcting Clock Skew**
            - Once the client has estimated the clock skew $\theta$, there are **three options** for changing the time  ↓ 
                - If $\theta < 125ms$, **slew **the clock. Speed up or slow down the clock very slightly (around 50ppm) so it's correct after a period of roughly 5 mins.
                - If  $125ms \leq \theta \lt 1000s,$ step the clock - i.e. suddenly reset the clock to the server estimate. 
                - If  $\theta \geq 1000s$, panic and let the human resolve it.
            - What's wrong with this code? ```cpp
start_time = System.time()
code_to_profile()
print("Function took", System.time() - start_time)
```AND, what is the solution?→ _NTP could have stepped backwards_  while code_to_profile() was running - resulting in a negative time taken or too high of a time.  _Solve this by  using a monotonic clock, who still have slewing but will never jump backwards_  
        - What are **Time-of-day** and **Monotonic clocks** and **how do they differ**?→Time-of-day clocks is the  _time since some fixed date_ . Monotonic clocks are the  _time since some arbitrary point_  (e.g. since system booted up). 
The difference is that Time-of-day clocks can  _suddenly jump forwards_  or backwards subject to leap second adjustments, monotonic clocks  _simply go forward_  at some (near) fixed rate. 
Additionally Time-of-day clocks can be  _synchronised across multiple nodes_ , monotonic clocks  _cannot _ (only good for measuring elapsed time on 1 node).
    - **Ordering of messages**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/cSyRVfDprWQX6kkONyGuwzXN2cN0oyfX6oT83kiZLRpY4bOkHQ9lOXbG_D-03xvyuC8B0azFM9uvHw7Hj-wBD_IOpw0j4tNwiCrL28Yox_ow4OqhZpM2ERHovfopgoFu.png) 
        - The **problem **with using timestamp ordering→is that $t_2 < t_1$is  still possible if the  _clock skew is greater than the network latency._  
        - **The happens-before relation**
            - An **event **is something happening at {{one node}}. 
            - We say event a **happens before **event b ( $a \rightarrow b$ ) iff  ↓ 
                - a & b occurred at the  __**same node**__  and a occurred before b in the local execution order.
                - event a is the **sending** of some **message m,** and event b is the **receipt of said message** (establishing causality)
                - There exists an event $c$ s.t. $a \rightarrow c \ \text{ and } \ c \rightarrow b$ . Transitive closure!
            - The **happens-before relation is a partial order** - it is possible that neither a or b occur before one another (**i.e. they are unrelated, doesn't mean they occurred at the same time) **this is written→$a||b$** ** 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Bd6o0t7rZ1n8gzSYN0RPPgRQ-0aFu86YR9Wo9EaJDut_cwcndGwgL4ezC2i7DkZo5Ubp0Vma60xmCyP-z5RpbSZEo5C9ann8FL4-JWlOWaD7eTw5jUUabr3rb1uOTdaa.png) 
        - **Causality**
            - When $a \rightarrow b$, a  __might have caused __ b 
            - When $a||b$, a  __cannot have caused__  b 
            - Happens-before relations encode **potential causality.**  ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/E91bglfXDom_vwusocHwkGxcTDNMEX7Moxuhp-TSmcOwQBQSHlCAQmz19vRpVbCNDCsUnbsroqMQYgVVx19c46wt4vhTq1Ri2FbvYSdBOOZgASW6b1C-C2ALIPFo9r19.png) 
    - 
    - 
    - 
- **Distributed Systems Lecture 4 (Time)** 
    - **Logical Time**
        - Logical clocks are designed to **capture causal dependencies** $(e_1 \rightarrow e_2) \implies (T(e_1)  < T(e_2) )$ 
        - **Lamport clocks algorithm**
            - The Lamport clock algorithm is→```python
# for every node:
t := 0

on event:
	t += 1

send_message():
	t+=1 
	message = (t, m)
	send (message)
	
receive_message(M):
	t', m = M
	t := max(t, t') + 1
	deliver m # to application 
```
            - Within the Lamport clock algorithm, **L(e)** is→the  _time after_  an the  _increment due to e_ .
            - The Lamport scheme has the following Properties  ↓ 
                - if $a \rightarrow b$ then $L(a) < L(b)$ 
                - However, $L(a) < L(b)$ does **not **imply $a \rightarrow b$ . We could also have $a||b$. 
                - We can have $L(a) = L(b)$  
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/NWzGP1UyEkHkO4gREgLixeoi8cOAM4abaB3se7r0ImB-uzVNIeJLEEEilhXwyPSYFctCqAc8cLQLGqg2iXnPG5HF_yYSeGBjEAiTAUxkYYBLtQWAWq5JqrzjIa__JHhu.png) 
            - We can form a unique identifier for an event by→combining the name of the node (the event occurred at) and the time the event occurred $ID = (N(node), L(e))$. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xg2IfyouuRbVa9FbkOdHsZXyJrWZxa92DLDPqCaeqaBZR37C6_wCYtchKhkZaF1LKEjOHs1N8x3PyIv-OF-XxQr8SfrNiTL26-8Kc2Qfox0K7qERfYkVDVtK73NpHwmw.png) 
            - The main **problem with Lamport clocks** is→if we have timestamps L(a) and L(b) ^^we can't tell if ^^^^$a \rightarrow b$^^^^ or ^^^^$a||b$^^^^ .^^  _ __Remember, a||b simply means they're unrelated! If no messages have been exchanged all events are concurrent .__ _  __** **__ To solve this we need vector clocks. 
        - **Vector Clocks** 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/UvnFvkZTVzGPxEWZjr_kMUAUiA7FcxrCIors0myTDQknWQy0MOakHVv5DjhY0pPpkSIOxF37OGZ7cqINEulpWsY8VMVsTHrhChFYieuysBBZlfJpbEkqsvS5lL4yem04.png) 
            - The algorithm for **merging vector clocks** is→```python
 T = [0] * n
 i = index of us
 
 on_event():
 	T[i] += 1
 
 send_message(m):
 	T[i] += 1
 	send( (T, m) )
 
 receive_message(M):
 	T', m = M
 	# Max of each element
 	T = [max(a,b) for a,b in zip(T, T')]
 	T[i] += 1
 	deliver m to app
```
            - Example vector clock arrangement:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Nr5EZypRAEEhXIQ3kVwQIrAtEEzY7-1YKCseaafPouBz8U9SArWl5NBxnYxQ3E1DpzsTK0SW2zXUkMJ6qeaWYvFCBPj4Vv9vAHDxLtiFGC0w6xzAIX0AxjIhzxwrDRwd.png) 
            - The vector timestamp of event e represents→e and all it's causal dependencies: $$t = \{e\} \ \cup \ \{a \ | \  a\rightarrow e\}$$  
So $<2, 2, 0>$ represents the first two events from a, the first 2 events from b and no events on c.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jFFIw1x1E-_MHi9JcaPCEKgEPWcijXTumy-uCOmOWnKEh71Kj14VxJa0iETImwR0bE3qfHN_3vPgy6eXGfP15rhqUhXkak-Iou5cYI6cN6pmwg9CZgfn0wNNlMJuI95r.png) 
            - Two events are **concurrent in vector clocks** iff→**Some **events in T happened before events in T' **and **some events occurred after events in T'. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/fhN2SFw_h1aP_p7Qcn7UesaVszsVJ1kru10VOP5nlT890pjRlorhlOqw9B5dGM_DcWj7OAQb2rH12_9VM1BYQnevf-mC_886oGi05m1S6IeXHdc-Om81nVkytey9s-TF.png) 
    - **Broadcast ordering**
        - **Broadcast protocols**
            - Broadcast is **group communication** where  ↓ 
                - One node sends a message, but all nodes in the group deliver messages
                - Groups can be a fixed or variable size
                - If one node is faulty, the remaining group members carry on
            - Group communication **can be designed** to be {{best-effort}} (messages may be dropped) or {{reliable }}(non-faulty nodes deliver every message by retransmitting dropped messages). There is no {{upper bound}} on message latency, as we use an Asynchronous/partially synchronous timing model.
            - The layout of a broadcast system is→![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/mFs8TN1pTuSMYFTopeZB2CUFSaNOk2UVEs0gL8tcAuDdaJ1GFrg-gwSi5vUp1M-SvvrldgftFPs3ME__MzkOS4qXyRkFubKjHa6FQzd5bYKziVR0Vn8KHVcD7QaJG9hu.png) 
            - The broadcast algorithm may wait to deliver a message to the application, because→we wish the messages to arrive in a certain order
        - **FIFO broadcast**
            - Note that when a node broadcasts a message, it also sends it to {{itself}}.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/I8jo0cSS3gODTf6w8D-mqHvxH6IBkmHggRtWq7ZQ27V5108wBpOfUFy-f6iFOPAgFvy-xQp4AidZD7C1calXQ5p-qEngwFMCc8X8IREnv5zzoYSww9hYtWmapqTBp2Zb.png) 
            - For **FIFO broadcasts **we **require that**→**messages sent from a given node** are  _delivered in the order they were sent_ . Messages sent from different nodes have no required ordering.
            - Valid orderings of the above diagram are then $$(m_1, m_3, m_2) || (m_1, m_2, m_3) ||(m_2, m_1, m_3)$$ 
        - **Causal broadcast**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/L1nUAnI60q5QqXN8NehbVWovcNwsWgdNcwup_XbfUwGOx-93_iv4GtGP5E_b19fPyGA9SxZC81O5d5FmZTfsJGNX6f-M_wkVxHfnZloOIqmfxL0hY8tOXzgDfChYqMw6.png) 
            - For **Causal broadcasts **we require that→Causally related events are delivered in causal order, concurrent events can be delivered in any order. 
            - The valid orders here are (m1, m3, m2) or (m1, m2 m3). 
            - The **difference **between **Causal **and **FIFO**→If FIFO we could  _technically have m1, m2, m3_ . In Causal broadcasts this would not be allowed. Or m2, m1, m3.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/I8jo0cSS3gODTf6w8D-mqHvxH6IBkmHggRtWq7ZQ27V5108wBpOfUFy-f6iFOPAgFvy-xQp4AidZD7C1calXQ5p-qEngwFMCc8X8IREnv5zzoYSww9hYtWmapqTBp2Zb.png) 
        - **Total order broadcast**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JG3S3CbaHrwr0rjbwr8YSPGYh6GWcWdCw9q_Dt68yE8YD47hQlqUDWyyR6uOeZx-V0qgaufPQlakuX1RNi_zzdC7SRN-ce1ZlUOB9aSbmVIZuuppV0gX5nOdkwNoNUkU.png) 
            - For **Total order broadcast ** we require→that all nodes deliver the messages in the **same order.** This  _includes the nodes delivery to itself!_  
            - The above ordering is for the example m1, m2, m3, but we could just have easily have said  m1, m3, m2: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/G782ZOFwPUarYj_VHKvoWeHGWkbal8CP8CDza7d5sze5ffFJcnNtmgsUzVj1HvJsjnZtkoE4t0Svhhvf9d-Fug9YQ-x17gBueGzyuzJ0TtUQsUfX0J0meyQAk4v8-jEJ.png) 
        - **FIFO total order-broadcast:**
            - **Fifo total order-broadcast requires **→** **That all messages are delivered in the same order **and **messages from a given node are delivered in the order they were sent
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JLfDCSOtxO_AKEZA9k300iA46WVFHDVBzEUHdfxH2KpbRXALgOjd9Hm1L60e9Jle3lEBqCJ2FLwp08e_Bg1mYDRxoEUVVzEusDhrNLCXjnQ4aRzuYXBJT2xuA5dxeuw7.png) 
    - **Broadcast algorithms**
        - There are two sections for devising a broadcast algorithm  ↓ 
            - Ensuring the **best-effort connection becomes reliable** (retransmitting dropped messages)
Enforce **delivery order atop of the reliable connection** 
        - What is the **problem **with simply retransmitting and deduplicating dropped messages?→A  _node may crash_  in the middle of retransmitting a message, in which case not all nodes in the group will have received the message 
        - **Eager reliable broadcast**
            - Eager reliable broadcast is→![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/P3SNOBLC-Ooeys3gf9H7Qj0ZdDIu890t306QOWR0iqkivcEUNQE7tDaYU0LksM93348Hg3O__KEcRTbsTUpjmMjXGtwOJwLKmEhCdrDgkQbSb-pbnTVKMd4-Ja20jR5J.png) 
            - The **problem **with **eager reliable broadcasts** is→for n nodes, we have $O(n^2)$ messages being sent. 
        - **Gossip protocols** 
            - Gossip protocols works by→![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/AzHyQZqzTUIfVER7QY9jaTCTx-lgQzOZlK8nHdNeWaYKIvhopEjZU7JzK87ameqhPIbJ0HjY3nyWJixFvnQiV4T7PLY-OaTSLRv5NHcDstyN0dTnLbX7JMBuJ-MWsLTM.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_3X3m6GVxLKq8rUjorTbV_cZm4Sb0heFxEEyEPt1EO3EZbOX0o5r7U2QGz2FC9nT_oTen14u9eTrBZcTvud57w6f6uD8MvaFr1i1PTWg3ZgmDZ7hhZ1Q1n88MIVP7jSI.png) 
            - Note: if a node has **already received a message **it doesn't send it again. 
        - **FIFO broadcast algorithm**
            - The **FIFO broadcast algorithm** is as follows→```python
sendSeq, buffer, delivered = 0, [], [0,0,0...,0]
i = ourNodeNumber

send_message(m):
	send(i, sendSeq, m)
	sendSeq+=1

receive_message(msg):
	buffer.append(msg)
	for M in buffer:
		i', sendSeq, m = M
		if sendSeq == delivered [i']:
			send (m)
			delivered [i'] += 1	    
			buffer.remove(M)
```
        - **Causal broadcast algorithm**
            - The **causal broadcast algorithm** is as follows→```python
 sendSeq, buffer, delivered = 0, [], [0,0,0...,0]
 i = ourNodeNumber
 
 send_message(m):
 	dependencies = buffer[:]
 	dependencies[i] = sendSeq
 	# Remember we send dependencies to ourself too
 	send( (i, dependencies, m) )
 	sendSeq += 1
 	
 receive_message(msg):
 	buffer.append(msg)
 	for M in buffer:
 		i', dependencies, m = M
 		if dependencies <= delivered:
 			delivered[i'] += 1
 			send(m)
 			buffer.remove(M)
```
        - **Total order broadcast algorithms**
            - The **single leader** approach is done by  ↓ 
                - Choosing a single node to be the leader 
                - All nodes send their messages directly to the leader (FIFO)
                - The leader sends a FIFO broadcast to all nodes
            - What's the **problem **with the **single leader approach**→If the leader crashes no more message can be sent. Additionally, changing the leader safely can be hard
            - The **Lamport clocks **approach is done by ↓ 
                - Attaching a Lamport timestamp to every message 
                - The order messages are delivered in the total order of the Lamport timestamps
                - But -  _if we get a time stamp T, how do we know we won't in the future get a timestamp < T?_  We need to wait for a timestamp ≥ T from  _**EVERY**_  node! We **need to use FIFO links**
    - 
- **Distributed Systems Lecture 5 (Replicas)**  
    - **Replication**
        - Replication is keeping a copy of the same data across multiple nodes - could be on a database, filesystem, cache etc.
        - A node that has a copy of the data is called a {{replica}} 
        - There are three main reasons you would want replicas  ↓ 
            - To **spread load** across many replicas (can reboot or change a given node)
            - If **some replicas are faulty**, others can still be used
            - To **reduce latency** in areas far away from nodes
        - Replication is easy if data doesn't change, but becomes harder when it does change.
        - **RAID **is→a **Redundant Array **of **Independent Disks. **It's a method of replication within a single computer.  
        - **RAID** differs from replication of distributed system in two ways→RAID has a **single controller**, in DS each node **acts independently**. In Distributed systems nodes are distributed across the world not just within a single computer.
        - **Retrying state updates**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zAXYaRsuUHc51Km9hbNbnKDDitWvhZ50d3qvoCidJLcm6qeAarPNzPcwvxJcwh6suaom_FCxkHPyNw1aYaIk5-F-BqE7Q66syhUD2JtC9lOAIbxznkqEZL96X64iaxGZ.png) 
                - To deduplicate this request we would require→that the database stores all requests it's already seen 
            - If the acknowledgement to adding a like to a post never arrives, what's the problem with sending it again?→It could be that the acknowledgement got lost on the way, resulting in two increments.
        - **Idempotence**
            - A function f is idempotent if→$f(x) = f(f(x))$ 
            - The idempotent alternative to incrementing a counter is→creating a set of likes and computing $\text{likeset} = \text{likeset} \cup \{userID\}$.  
        - **Retry-semantics** 
            - **At-most-once **semantics means→the request is carried out at most once, as we don't retry the sending
            - **At-least-once** semantics means→The request is carried out at least once, as we retry until we get a response. This can result in duplication
            - **Exactly-once **semantics means→The request is carried out exactly once, through repetition and deduplication or idempotence.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/GSRTLxW-vEf4NUqlonf0KbkzGiGE7w-i-tN96YitYC_7leB8q2d6phZmfmFrQCyAAewjT5zeqnyD9EjG4EmX92DPJjK841ZBJpmk0LAPDioiCDBL77Uiyr01RlHFH1YS.png) 
            - What is **going wrong** here?→The request for the like is being sent again because the  _response was lost in the network_  - but in the meantime the user has unliked it (from a different computer) resulting in the  _unlike being cancelled._  
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/uD7MftKfvEoC5LNNYhjyJt-DBpM1_ssxmcNI5GANhHTpQlIW1Xlxnw53rQqoENeT32-aYaWuVefWVsdiKwySbRCjpWVmHve1p6ab5d01cp0USZ-2O5ZGYTio8e6j7zHN.png) 
            - What is the **problem here **→We would like overall operation add x then remove x to be detectably different than not adding x at all. In the above case we cannot tell the difference, so we **can't know which replica is correct**.
        - **Timestamps and tombstones**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gikFIFeyKZoBUH03f_PMFynWpLzcInN7lzSoBpvWv1sDGsezP-H0Sve1OEcxW7a5cwhHWCFGywKNEJePi2OLdQUoVug6X2X82BYJZDWIl8BgO0F-6UQ4E7vaqeP3sKNr.png) 
            - A **tombstone** is→a  _recording that an item was deleted_ , **even if the item is still held.** This is used to hold the fact that the item was once present in the database and has since been delete.
            - Every record has a **tombstone, **and a **logical timestamp.** 
            - Replicas use **tombstones **and **logical timestamps** to come to by→**occasionally communicating** with one another to **check for inconsistencies**. If such an inconsistency is detected a  _**anti-entropy**_  method is computed. The timestamps are compared to decide who's correct and reconcile state.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Xm41gzLVU0ErhY7SzQFYrxOtGB2mkoEfByN381ekrbHsn80I-k4fjuEGYG9GZ4LofTNezZ9DENA-dB-hKxZZWjuTANfA1TXebT0v4LKRRn5MRcUHGaQ-30Mr3G12GZH9.png) 
        - **Concurrent writes by different clients**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/69MpP4Pxk9RB8R8iIHmNCqbVW3VorxuevBfoCMMVuIVDgqo9AJ2wGe0cLTjKZGPCoeVnb2K-UeY5hvPYftc_IvY3vUt2hHgB3FjAKeQkJlEQf7t-DIWrd8M9XAq4NP3F.png) 
The two approaches for this problem are  ↓ 
                - **Last writer wins **this uses timestamps with a total ordering (e.g. Lamport clocks) - we choose the option with the larger timestamp, and discard the other one. **Note: Data loss, consider 5 such events occuring **only 1 datapoint will be preserved 
                - **Multi-value register** - use timestamps with a partial order (e.g. vector clocks) only replace one if one of the timestamps is strictly greater - if t_1 || t_2 we preserve both v1 and v2 (perhaps seek user involvement)
    - **Quorums ** 
        - **Probability of faults**
            - A replica may be **unavailable, **assume the probability p of a replica being faulty is independent of all other faults. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/XzsAVTwbLE2zEm2HVLKSpuxHwmyeXU4XJBvaIIB55XfoWRqF1qv75w0o4voabdUcUjKa5Ln9Gr_ivmBphhQYwtCeuf7EsOoOqZt2sTYD3UXFX_tzdpapB22NuDTRfHF-.png) 
            - More replicas ⇒ more likely {{at least one replica}} is faulty at a given time
        - **Read-after-write consistency**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ZV20Kz4WJfsbC1A4_9jWVz_T_VxpPSqOy1snJ6OJEIzvM1eoW62m6A_DUgs46e7W6so5qlh91oECbbg6Tp5-OdOQkPxWA1QAcjrRtRwsu-VaQu1VR-K2FV6ENOYpapKv.png) 
            - The cause of **read-after-write inconsistencies** is→when a client writes to one replica, then reads from another (and the **two have not been synced**). 
            - One solution to **read-after-write** inconsistencies is only allowing {{reads/writes to all replicas}} - if one replica is offline, however {{we cant do any reads/writes}}. 
            - **Quorum**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bKZieC-unJ2_3dE8Z9rCb3l3UjEZ-uKXpqesXSHJ9puS2MfsrL-ZWYprgf_dsSw2hZLCvuKUtxvLVZi8Au3p5rK2SLNmoQL8ph3W6O953DrelXRRN30iKJ2GAjoyYhmc.png) 
                - A **Quorum **is→a group of replicas who we compare responses from to decide on correctness. 
                - What are the **three requirements** for read/write **Quorums**?  ↓ 
                    - **Writes **are acknowledged by at **least w replicas ** 
                    - **Reads **are acknowledged by at **least r replicas** 
                    - **r + w > n **(Think  _pigeonhole principle_ )
                - **Read/write quorums guarantee**→we'll  _always read the most recent write_ !  
                - Typically form majority quorums
            - **Read repair**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TTTpPyP9EHF65J1DQ0v4KvzdtJ_cLFkv5TW_tNaU6UJyxo16qPIuE57oAKQtztbiKkm4umJi3ryBihS0iifNqH-DvHiujtZ9rJK8JfSBNZIdO1yeKbQZxUIdJSJQheZi.png) 
                - If we **receive **what we find to be an **out of date value** (via Quorums) then **send the correct value** to all incorrect senders or any replica that didn't send a value.
    - **State machine replication**
        - State machine replication is about using broadcasts to facilitate replication
        - **The Process of state machine replication is as follows ** ↓ 
            1. A FIFO-total order broadcast is used to communicate the state change to all replicas
            2. When a node sends the broadcast it also updates it's own state (so nodes sending the broadcasts will also update)
            3. Applying an update is deterministic
        - An **update being deterministic** in SMR refers to→the  _replicas acting as _  _**state machines**_ **,** they start in an  _initial fixed state_  (usually empty) and  _follow exactly the same state transitions_  in the same order and must then  _end up in the same state_ . 
        - The main limitation of SMR is→can't update state immediately, have to wait for the delivery through the broadcast (has to coordinate with other nodes to decide on order). 
        - Related ideas:
            - Serializable transactions 
            - Blockchains (total order broadcast in the chain), distributed ledgers, smart contracts
        - **Database leader replica** 
            - A leader database replica ensures a total order broadcast
            - Generally have the requirement that write requests can **only **be executed on the leader, read requests can occur on followers. The leader then makes these commits, and communicates these changes with the followers. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/wNQ5uytq-Djq-0AMvdNtPDVwqO6qipwM-ZwWvCQ0llB-EblhOrX0TmFVQjtZOKh2qKFaLD-cbKFGztrTJdS4i0B_Y_2uP5C2vTAbmLLCPUQo6Icr-1s6-EX9jpTBpIhd.png) 
        - **Replication using causal (and weaker) broadcast**
            - A replica **state update is commutative** iff→$g(f(x)) = f(g(x))$ where g and f are state updates.
            - The** causal broadcast** requires that if a message happens before another, it is communicated first. The **requirement for the state update function** is then→that concurrent updates commute. This with the other requirement ensures determinism. This is a bit like serializing the message.
            - For **reliable broadcasts** we would require that→the system is deterministic and that  _all messages commute._  
            - For **best effort broadcasts** we would require that→deterministic, commutative, idempotent and tolerates message los
        - 
        - 
        - 
    - 
- **Distributed Systems Lecture 6 (Consensus)**
    - **Consensus**
        - **Fault-tolerant total order broadcast**
            - In our leader follower system, what happens if the leader crashes/becomes unavailable?
            - **Manual failover: **This is→when a human operator manually changes the leader when it's detected the leader has failed. Will need to reconfigure follower nodes. This is fine for planned maintenance. The problem is humans are slow, can take a long time in unplanned outages (consider if this occurred at 3am)
        - **Consensus and total order broadcast**
            - **Consensus is **→several  _nodes coming to agreement _ on a given value.
            - In total-order-broadcasts this would be **the next message to deliver**. So if we can come to a consensus, TOB drops out. e.g. consensus and TOB formally equivalent
            - **Paxos, Multi-Paxos **and **Raft **are consensus algorithms
        - **Consensus system models**
            - Paxos, Raft, etc. assume a **partially synchronous, crash-recovery **system model. 
            - We don't assume a asynchronous system because→there exists **no** consensus algorithm that will **always terminate**! Even in a simple crash-stop system.
            - Paxos, Raft, etc. use clocks only for timeouts/failures however the correctness of the algorithm does not depend on timing.
            - There also exist consensus algorithms for **Byzantine **system models (used in blockchains) 
        - **Leader election** 
            - Use a {{**failure detector**}}** **based on time to determine a suspected leader crash. On a {{suspected crash}} we must then elect a new leader. Crucially, we want to prevent {{two leaders at the same time ("split-brain")!}} 
            - Raft Ensures $\le$ 1 leader per **term **this means→The  _term is an integer variable_  that is  _incremented whenever an election begins_ . Raft ensure that at most 1 leader is elected per **term **and that each  _node votes at most once_  per term. The  _leader is then selected via a quorum._  The quorum gives us the fault tolerance
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/oRKZVQPA2sewgXbqQXQuwNNxXS-hb89JPztSbjtVbzdVfHj2Ym0thNflC38IfB7DFepG9UiDi5zqttzWA3y_uEWDELnWIyMYUzLcXVUDXKAlG6Pnw4QKT9PUia4IYnRe.png) 
        - **Can we guarantee only 1 leader?** 
            - The **system of 1 leader per term **doesn't guarantee 1 leader because→we could have a leader disconnected from it's followers, who is replaced without it's knowledge. So it's the leader of term t and there's another leader of term t+1. I.e. **this method only guarantees on leader per term.
 **![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/V3tUykKyDgLFsDYH6S5IrhXdZQC2D6ubQvp1thFpCZjTFlzCu2vXSTteYMr2Q3DtV4nWWzT84-g0WmATUL0TAToeDTJxZJCInlfXt2xODhLhHvHhT7LE2KYpSXnKPivr.png) 
            - The solution to this problem of a leader being voted out without it's knowledge is→the leader ensures it can send messages via a quorum. 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/CHaFRGF--nZNN8hKVUQbJBTEehN0QFdy0H66cyAhIKONEOuPKt-LRQxotlsC_5hWZE6zGktq-hvjFjCcGptUh06SlQd94k8cxUqPbfTGXAKNFCC-eVGOEZpDlH6NA-yd.png) 
    - **Node state transitions in Raft**
        - The state transitions we will use are always within a certain term. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/oWqazBP_8nBcIola3uNH5oNL_j0GsbXTAyi9UhFPA0l_JlVCJbTrWk4KelPLQF3Dl_Pr-6bpmqNyzyQMHr4rEL-ASDVNnAoFuthUcVjViShxfQD6bJTk4IARODnl2kQR.png) 
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
        - In **RAFT** the **log** is→a list of  _messages with an associated term_ , the term is the term number that the leader sent the given message. It is the  _**total order of messages.**_ 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/VnP_X0y4qd74FjPvg_hresNYjUzjlgDUYiq6sHnVlGWZnzWMPvIAetoO8B7NBf-rY1_hKb43wUquGZ4RwjEl2As6e3wNnfPnJjmu5PiG0AlC7VoEC5w7yCEUJjRN1314.png) 
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
```→This is 
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
- 
- GO FROM HERE NEXT: [Distributed Systems 6.2: Raft - YouTube](https://youtu.be/uXEYuDwm7e4?list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB&t=946) 
-  _Distributed Systems supervision 1 _ 
    -  _**Exercise 1**_ . A TCP connection allows two nodes to send each other arbitrarily long sequences of bytes. You decide that you want to send multiple requests and responses over the same TCP connection. What do you need to do in order to implement such a request-response protocol using TCP?
        - You could **wrap each request and response with a header** which would encode the length of the message (among other possible pieces of information), the header would have to accord to a set code that both nodes understood (e.g. it could have the first 4 bytes specifying the length of the header, the next 4 specifying the length of the whole packet perhaps more data specifying the type of the request). Then when a node receives a stream of bytes, it can find the length of each individual message by examining the header - then if there are more bytes after the header they can know that is another message (whose header will be examined).
    -  _**Exercise 2**_ . How is RPC different from a local function call? Is location transparency achievable?
        - An RPC call is different in a few ways ↓ 
            - The function is not executed on your local machine
            - The arguments of an RPC must first be marshalled to be sent over the network
            - RPCs make use of an API to facilitate their use
        - Location transparency (the idea that the location of a resource (whether it be on our local computer or on another node) is achievable under perfect conditions (impossibly fast WiFi or having local resources slowed down to achieve such transparency) however in reality the lag between forging and communicating over a network connection is detectable and is much greater than the lag of local file being opened is large. So the very quick loading of a file would indicate a local file.
    -  _**Exercise 3.**_   Say you have a client-server RPC system in which a client repeats an RPC request until it receives a response. How could the server deduplicate the requests?
        - One solution would be to attach a request number and a repeat number to each request. So if I a request "GET : "img:coolpic.png"", it could be sent multiple times like this:
            "req:1, rep:1, GET : "img:coolpic.png""      "req:1, rep:2, GET : "img:coolpic.png"" ...
Then a second request "STORE : "img:coolerpic.jpeg"", could be sent like:
   "req:2, rep:1, STORE : "img:coolerpic.jpeg""        "req:2, rep:2, STORE : "img:coolerpic.jpeg""

This would allow for easy deduplicating in order of req then rep
    -  _**Exercise 4**_ . Reliable network links allow messages to be reordered. Give pseudocode for an algorithm that strengthens the properties of a reliable point-to-point link such that messages are received in the order they were sent (this is called a FIFO link), assuming an asynchronous crash-stop system model. 
        - ```python
buffer = []
received, messages_incoming = 0, 0
time = time.monotonic()
# read_message() blocks while waiting for a message
# Wait a max of 10 seconds before exiting the while loop
while (time.monotonic()-time < 10000 and msg = read_message()):
	time = time.monotonic()
    received += 1
    messages_incoming = msg.messages_incoming
    buffer.append(msg)

    if received == messages_incoming:
        break

if time.monotonic() - time > 10000:
	send_failure_message()
	return []
else:
	# Sort based on the message number
	buffer.sort(lambda x : x.number)
	return buffer 
```
    -  _**Exercise 5**_ . How do we need to change the algorithm from Exercise 4 if we assume a crash-recovery model instead of a crash-stop model?  
        - We would need to implement a mechanism for informing the receiver/sender that we have crashed and lost the data stored in our memory, in the two cases: 
        - **Sender node crashes: **We don't know how long the period of unresponsiveness will last, so we can't simply keep waiting until the node comes back online. Instead the receiver should cache the messages received so far in some non-volatile memory. Then when the sender wakes up again, a unique ID of the message should be sent, the recipient can then indicate how many (if any) messages were received and the sender can resume sending where they left off. 
        - **Recipient node crashes: **Once the recipient wakes up, it will need to signal the resending of the entire incoming message - on the senders side a non-volatile storage of outgoing messages will need to be held or a method of backtracking execution so the message can be sent again.
    -  _**Exercise 6**_ . Describe some problems that may arise from leap second smearing.
        - Floating point accuracy: The smearing of 1/86400 in binary form will introduce a very small error, and that error will be repeated 86400 times every time this update is done - if a small low bit floating point representation is used, the error introduced will defeat the purpose of the whole exercise. 
        - This is more reason for software vendors to simply ignore the problem. While this is not a problem  now, bugs mirroring Y2K could start to appear in the (far) future which go undetected.
        - This makes bugs harder to detect, as desync occurs over many hours rather than at one instant - while the latter would be noticeable in logs, the former would be very difficult to sus out.
        - Desync problems can arise if one node is doing smearing and another isn't. 
    -  _**Exercise 7.**_  What is the maximum possible error in the NTP client’s estimate of skew with regard to one particular server, assuming that both nodes correctly follow the protocol?
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/qpQ_ydxHmeLCcJOH6RsYAsXfSQmhKyB1tFdamdF6Ap_bDPQSH3D9yXDiDWlMRhPCDIbkBbsV34oweAqelXOk2YakrBsEOBexbuDNPmUFzd2RpaSGhmlB3zKHzVrmj3e5.png) 
        - delta = (t4 - t1) - (t3 - t2) = total network delay
        - skew = (t3 + delta/2) - t4 ^^ Question: should the skew not be the absolute value of this?^^ 
        - This estimate is worst, when the estimate of the time taken for the second response is worst - i.e. when request 2 took the minimum time (according to the speed of light & the distance) $\tau$ and the response took  (t4 - t1) - (t3 - t2) - $\tau$, resulting in a true value of: $$(t_3 + \tau) - t_4  = (t_3 - t_4) + \tau$$ 
        - and an estimated value of:
        - $$(t_3 + ((t_4 - t_1) - (t_3 - t_1))/2) \ = \ \frac{t_2 - t_1 + t_3 - t_4}{2}$$ 
        - Resulting in an error of:
        - $$\frac{t_2 - t_1 + t_3 - t_4}{2}  - ((t_3 - t_4) + \tau)$$ 
        - 
        - $$\text{error} = \frac{t_2-t_1-t_3+t_4}{2} - \tau = \delta/2 - \tau$$ 
    -  _**Exercise 8:**_   ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5S3daW4zY8nipJDU9bb6QDZFwpAKv76GLWXklLBsLwNMaHVyXCyqi6beHbSePSUh2wUUqfIM089PwNg7KdgKAG393iZn0TG3vKoFUqd6uZlbpIj28GT5HfxMznzEsjyk.png) 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JZ0cqETpk4kB-8uo8RsxSXte3C9NVDfOw4vemdbEKxinYe3CqfOPdSUNb_Fpyd4-ye6MCznEIu-9sZu06atSqyFY7bbC1aTgvSUTUTXT9mFmE5HTbSF5PSAVbnrb2wkH.png) 
    -  _**Exercise 9.**_  ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/yjzPiqfzh56oOnjdrWniK1-rmUzLvrJVHdmIi3wGYvHrNK61hUGjfCo6hw7JQp6f_L5YYwSlqfsN8hscm798IJxxy9ynwJuNREyNIPIdegj_vVikP0lJGqiVY31FzpHB.png) 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ob9D3CB9suoCvYxZxqxdjPsKhfoPPSYm6DlccDXCh0NtAPdvEKZA7Lly3ra6n6EQ8nrb-eQAqp-ly0gw__HevRFKuj9ebM1cP9wxXqeeExDvTyWgi-ry8nKXL0kJ1kY9.png) 
    - **Exercise 10.** Given the sequence of messages in the following execution, show the Lamport timestamps at each send or receive event   
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4atqIBUEAzm7OncyN5qB3j5Z5XjQtc_OHDZgMdXZh6kXNeqKApIIRpARrwbyAHUyX7k7ndM-H0MBpStyrugFtkC4DMVZEVYv2pTPR9uWBOaXYXUGmwbk1reIC3dx1sE2.png) 
    - ^^ _**Exercise 11**_ ^^^^. Not really sure what im doing in this Q^^ 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/OLpHgGNm5MfltmNel8M5Q5lLaLiOvEi-XeYkJSwWR2d7kXOaSbkgkSRhko_Iat92Wrqx24q4XCLZlBOuaCfxNSdmG60OZoL9OyAZd8aFGEzVQs2X26dJVDRGVZhjhzk1.png) 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/oBARg9P1D24HOK5JpsjKfxt9BYToaiGQaEFssa4ymDfFEdCvwPFRyS1POKECnRvToCUUSUDiGleDPpD1--KUBhU6sgaQqXCITyKlJIKliumPf_oMLkMtWVPrL2PwqsPV.png) 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_yytoqeaDujPLnHDbTmbdQ8mL45y-VCzC7OtvC2qnqKA8ofMwyZq15n7C4nYTpYnzbyjKVGghpq51wFQGApk_Zsmi4sMKo7jf3lGLupIBvMobBOH_MVgEeECiIBzpoqp.png) 
    -  _**Exercise 12**_ . Given the same sequence of messages as in Exercise 10, show the vector clocks at each send or receive event.  
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/9jwOOpv8Z8WqVwxq7ynfW03XwQFEn7ipkP88FMsmB5DkrGrmrNBuwEUhIDojkOzdAeBx17jEOVmlWrU2whx6-qnXAjz4jqukHzSSGc3F-r53v3Rg82YAzsXevXp8Bh-Z.png) 
    - 
    - 
    - 
    - 
    - 
-  _Distributed Systems supervision 2_   
    - 
    -  _**Exercise 13**_ . Using the Lamport and vector timestamps calculated in Exercise 10 and 12, state whether or not the following events can be determined to have a happens-before relationship.   
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4atqIBUEAzm7OncyN5qB3j5Z5XjQtc_OHDZgMdXZh6kXNeqKApIIRpARrwbyAHUyX7k7ndM-H0MBpStyrugFtkC4DMVZEVYv2pTPR9uWBOaXYXUGmwbk1reIC3dx1sE2.png)    ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/9jwOOpv8Z8WqVwxq7ynfW03XwQFEn7ipkP88FMsmB5DkrGrmrNBuwEUhIDojkOzdAeBx17jEOVmlWrU2whx6-qnXAjz4jqukHzSSGc3F-r53v3Rg82YAzsXevXp8Bh-Z.png)  
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
            - Lecture Notes
                - Term 1
 -- Avoided infinite recursion --     -  _**Exercise 16:**_ . Give pseudocode for an algorithm that implements FIFO-total order broadcast using Lamport clocks. You may assume that each node has a unique ID, and that the set of all node IDs is known. Further assume that the underlying network provides reliable FIFO broadcast.  
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
- 
- 
- 
- 
