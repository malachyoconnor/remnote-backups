1. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Guf1exbPhgo5Z2eHqD_6p41EcW-pvbqzLDBBZ_gOjY64bnMq11BYpEMCRjDD3_JWU3vMJWO67JNqmPSquhOyJkS2PxJKRzPY6XuzIcYWXPAbuDEVMGcvlSn9bpEIyR0F.png) 
    1. The load linked instruction ll r1 (0)r2 loads the value of the memory address in r2 from memory into r1, the store conditional sc r5 (0)r2 then checks if the value stored in r2 has been altered in-between operations (generally checking for alterations or reads by a different core), and if it hasn't it writes r5 to memory - if the write succeeds (e.g. r2 hasn't change and no hardware problem occurs with the write) then sc writes a 1 to r5 otherwise it would write a 0. 
    - This attempts to mimic an atomic operation - e.g. do the whole operation or do nothing, by only writing the result of the two operations if no changes have been made to the operands. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1rdxh0kr1BQ1jjIGbyqaSZ8W2c6wf4DwLBw-5RvlBmglt3WQDKr8tj0N7ni9qzJv8j-MwMl_epY5fYx-LhZR_yWnD56j0E2Ggjch1EbaAr2z58svi8htj_54ryx4vAPH.png) 
    - ```csharp
		membar // Ensures that loads before and after the membar cannot be reordered across the membar

label1: ll r2, 0(r1) // Store value in mem add 31 to r2
		sub r2, r2, #1 // Subtract one from the value
		sc r2, 0(r1) // Write-back the updated value
		beqz r2, label1 // Repeat this operation untill we successfully write-back without interruption
// Label 1 performs the atomic operation mem[r1] += 1

label2: load r2, 0(r1)  // Load r2 <- mem[r1]
		bneq r2, label2 // r2 is a lock which we are trying to get hold of, we keep spinning until
						// it equals zero 
```
2.  
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_U4TG3oypX8dYFLZO9RObBtRyB8CiCxGwFyqdIBjeCkDFKKdS24mEW7ZeWtP7DGgM0Hau_p5zXZC2zepjdNVfT9eaglGIqaHO5f5eI7RbA-wk7uzdG1YQM5jfVVbNjb-.png) 
    - i.) The process supports branch divergence through conditional execution, mask registers associated with the warp decide which threads will execute the commands based on commands within the code (e.g if (i%2)―0) then the inverse of the command is also calculated (else) and the other threads are selected to execute - we also have the mask registers being reset by the end ifs
    - ii.) 
        - ```csharp

r1 = load X[i]              0,1,2,3,4,5,6,7    100%
r2 = load Y[i]				0,1,2,3,4,5,6,7    100%
if (i%2 == 0) 				0,1,2,3,4,5,6,7    100%    //(They all have to calculate the i%2)
	if (i%8 == 0)			0,_,2,_,4,_,6,_    50%
		r1 = r1 * 2 		0,_,_,_,_,_,_,_    12.5%
		r1 = r1 + r2 		0,_,_,_,_,_,_,_    12.5%
	endif					0,_,2,_,4,_,6,_	   50%
else						_,1,_,3,_,5,_,7    50%
	r1 = r1 - r2			_,1,_,3,_,5,_,7    50%
endif						0,1,2,3,4,5,6,7    100%
store r1, X[i]				0,1,2,3,4,5,6,7    100%


Average usage = 725 / 11 = 65% 
```
    - iii.) 
        - Multithreading - the GPU can schedule warps based on their access to resources and if they are ready to run or not, if a given warp is stalled execute a command from a different warp.
3. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TNZR6cjY7oDvebFDH8Cku4Hqg0vqxF1BSYSpUjOiqgAWrDoYi2S5cFGlDfZP5rP65SgqJKwjyUXpj1qFqbQj14QsIMksEU5uqkf_dPBy8QcvdaTEkTbCPg3n67v5RIQZ.png) 
    - Accelerators allow for better energy usage, speed and efficiency - however the specialisation necessarily denies generality - meaning they can only accomplish the one task they are designed for. This specialization could be creating a custom ALU for the instructions or adding greater parallelism (less hold and wait time). GPUs are more general, and can compute a range of tasks with data-level parallelism additionally they can be purchased off the shelf, meaning they are usually the cheaper (and faster to deploy) option than designing a task specific accelerator. So for products not likely to be deployed to a million users, they are often the better choice regardless of higher latency and power usage.
4. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jdQXJHFRblXwGUT5JyMar0f0PdVC6YoHzUuZYif0STh_qA2hDyTnHtaY0G42L0jQ4LeVMdCHILzPoe-pEmhEOIshVbehstITpHUg6150ZIOgB6qnwTvXomUgOOdrP9N2.png) 
    - The store changes the source register to instead store a 1 if the store succeeded, or a 0 if the store failed - e.g. if the value stored in the address register had been updated. This operation has two reasons for overwriting the source register:
        1. So a third operand isn't required to the command specifying the register to store the 0 / 1, as we need to know if the operation succeeded or failed.
        2. Because we don't want to keep a stale value of the operand, if the value has changed we want to compute value to store again - there is usually no need to keep the stale value, and the overwrite promotes safer programming without usage of stale values.
5. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NajlrDgoopacMKkKoVyMrpgocQeL1ZzZluRfVJ3EblO8mKTajlNTXshswBRR0RBXh1G2ZweW-oFnOJwLUMfV0kauNuNe73ov5MOOtZe-i7jzZXH_IfZGPOOzy2jbYaeD.png) 
    - ```csharp
lock:
	si r1 1  // store 1 into r1
	xchg r1 LOCK // exchange r1 and the LOCK location in memory 
	bneq r1 lock // spin if r1 != 0, e.g. if the lock was 1 before hand
				 // If the lock was zero we'll advance
``` 
6. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6pCNKWTCJojnQ9ocytIxRRox7zAzsCnW7GLFj_qBYwN2RkQ08135G36BcSkP2eWadM_XBWCXPJaAOehbxZFTty-4odvJYJGgpZYMiMzwuMXTUkxhPpmiXPqBIhfBxCBd.png) 
    - A memory barrier ensures that load or store commands before the barrier cannot be rearranged to be after the barrier and vice versa - this ensures the memory consistency cannot be damaged by the rearranging of a CPU seeking high performance. Consider:
    - ```csharp
CORE 1:
	a = 3
	a = 100
	b = 4

CORE 2:
	if b==4 and a==100:
		print("This should be impossible")
``` We could fix the error here by doing the following:
    - ```csharp
CORE 1:
	a = 3
	a = 100
	membar
	b = 4

CORE 2:
	if b==4 and a==100:
		print("This IS impossible")
``` 
7. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iHIusEpcvm2NLeNyL3AhyejG8cbQ69rFfzL0jRTwwzXkKlf1HfJmUFGqLfK_Yy2P3P6Wcn3XoaCaH3l7IMIWRauhgEVLChvv4IAHzqvk5YSq9tzJCOEmzQxXhk1VYNUs.png) 
    - Because placing the memory locks after the lock ENSURES the lock inside the two memory locks runs after the lock is gained, likewise the final memory bar ensures the code runs BEFORE the lock is released. If we placed the memory bars before taking and after releasing, then rearrangement could occur resulting in us performing computation before we've gained the lock and potentially after we've released it. The memory bars create a contiguous set of code that can be jumbled around (within reason) but cannot be exchanged with commands outside those bars, placing the lock and release within those bars allows those two commands to also be jumbled.
8. 
9. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5uy3-Ave4JWzB5if7xDjyuptcRc2P18LQVLSyqhAchb4gpelNdsRmxiuPMTs_2w3d3ec0eGZe6o9o7XbZwYQvanclbcIt8VbOG6f2CjuFg2KnV0CWrbcnHtnfRTekPnz.png) 
    - Single instruction Multiple Threads is a method of parallelism, in which multiple threads are grouped into warps who execute together in lock step. These warps all work from the same code on the same data, however they may execute different commands due to branching paths in the code - they execute those commands on **different** data items. Each thread also has its own registers and memory, and the concurrency of the threads in the warp is coupled with concurrency of the processor executing multiple warps at the same time.
10. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ix1_1-b9Uqxg1LL281nlEESsr1Rsq0Xhfq_qPOmvSo9dIqP7XA-seCjj8CpabVZW9e5_0CL7GytshZayofYi5-Ys-jakOdh9-_dkhwn_n_kznVYpn-yS9zZF-PHHu-1I.png) 
    - The SIMT processor can choose from multiple warps (or even multiple instructions within the same warp) to execute, allowing it massive multithreading - this means if a given warp is blocked waiting on data the scheduler can choose a different warp to execute and the latency is avoided. This differs as in a CPU threads are in groups not one by one, and we don't wait for an interrupt to know that a resource has loaded instead the scheduler has that information all along - additionally multiple instructions are executed at once rather than one at a time in the usual pipeline.  
11. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GQ6bygtAaGCx0cF5VnHRJPttyMp5ex4FtV34sztbIaRH76EPEVxR8xztT-g_E9HxgIUydQBQXLoKNh1m2BNOvf2k1e0DlWIwfrNuthm4Km1QnqLFlTEQ95X5leTGFEcJ.png) 
    - The data cache must be larger to allow for a larger amount of data to be flowing through (we now have to provide data to far more threads), each thread has its own private cache and each warp has its own larger caches. However, the inherent data-level parallelism means less communication needs to occur between caches as our data is independent and changes need not be communicated. 
12. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NAEUQVtSV9DFM_c_whatVLAJ-LlLb8T2iCQASPraqNRYadmSa9p5hsl8X1ZQB9aSq41EvabBTqfCblhKpTJUl8ZZ9Nbcx6RVBCmc2OKe8Sjuv3xfR5QLZ6OAOJaJ1G9G.png) 
    - Each thread is given its own stack, and predicates are push and popped from it - the GPU decides which thread should execute using mask registers and will allow only those that are unmasked to execute. The threads still walk through the code in lock step, but only certain threads are allowed to execute.
13. Sum the total number of threads executing instructions, divided by the total number of threads times the number of instructions:
    - ```csharp
r1 = load X[i]              0,1,2,3,4,5,6,7    8
r2 = load Y[i]				0,1,2,3,4,5,6,7    8
if (i%2 == 0) 				SET PREDICATES    
	r1 = r1 * 2 			0,_,2,_,4,_,6,_    4
	r1 = r1 + r2 			0,_,2,_,4,_,6,_    4
endif						Restore Predicates
store r1, X[i]				0,1,2,3,4,5,6,7    8

Average usage = (8+4+4+8+8) / (8 * 5) = 32/40 = 80% efficient
``` 
14. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xNBXDXDISRgklZb-mFVvIiDg_mQ2q5YIYCPyEerp4me7-uhdHT0f0_6uOSB1wlZcvShNWDf0kcT97Y2sdGDs25PcjqhklqseiyRE4Kaha0KE4qajcJIQvLKel2vRm5Ic.png) 
    - Warp parallelism is multiple warps executing commands at once, this is done by a GPU with multiple cores wherein a given set of warps are scheduled and executed in parallel. SIMT parallelism, is the parallelism in the individual warps where multiple threads execute the same set of instructions (subject to branch divergence) in lock step.
15. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HTSklwp1g1oC-jOqXimSsTSqBEYpGHpEKvwn75yk1S7sooPub-mert71pd1W8ZyfLTCeNkbvKa-ZelnPnBg-k-rRme14lQaTdHNp3l9MO-4Zsp_f41BWLdSbgrD4mCos.png) 
    - Each thread has its own private local memory, this memory is very small but incredibly fast.
    - Multi-threaded processors has its own shared memory, warps executed on those processors can access that shared memory (different processors cant access each others shared memory). It is slower to access but **much **larger than that of the individual threads- this can be used for communication between threads. 
    - Global GPU memory is available for communication between processes, this memory is the slowest and largest - but is accessible by the host and can thus be programmed and changed.
    - Finally we have constant and texture memories, these are read only but are quite fast. Constraining the design to be read only can lead to performance or energy benefits.
16. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nXULcIhJFr_O7XGmj-_A0xcqUzMr6itAeNRtJnovL9geICqxQzFpqlhqaOrGGK2Rt1Idg7pqtXfDyoTw6zWU3MGgb7LlhhZwMZ0fsPdONqgGsfdPHcsiY6ZTyyS8v7WU.png) 
    - Atomic operations can be achieved with multiple instructions. The memory consistency model describes how loads and stores to different places are seen. Memory barriers and load-linked, store-conditional important tools for synchronisation.
17. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BAHk5Ew6Aadc2EIputQEPJ_blb8CdsP4EqgyMkmax37DCVDwd9QVOkSpqXQFqdc4ZlooNd0GgywjzgS4bEeyQd2-RisE8pzdvHTX22vuql90zZXHvM6UiKjWFbNVAimz.png) 
    - GPUs massively multithreaded processors, threads grouped for efficiency into warps - SIMT execution. Multithreading hides latency.
18. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pP4O5zBCdjQJYUWklv6yE2IM2zLCEYTh7q-a-5drkiw8_5Np4mmtonZuB6JqoYWM8wv2q5_fipmGMOL99neXPwVVIjlwu30pqRBEGDv5nupq0gePUC4ch0pp760WtpHW.png) 
    - CUDA Is the common NVIDIA approach, while OPENCL is more broad. Programming languages are designed to help code using GPUs.
- 
