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
