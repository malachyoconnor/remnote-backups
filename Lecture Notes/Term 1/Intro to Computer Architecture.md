- Supervision 5
    1. Discuss an example of a problem that we can solve efficiently by using CUDA.
        - CUDA works only for Nvidia GPUs, so the problem needs to be parallelisable (problems like video decode, rendering, deep learning etc.) and preferably with enough data to take advantage of the large scale compute GPUs offer. Due to CUDAs relative succinct syntax, the solution can be developed quicker than with OpenCL and will run faster than OpenCL code **on nvidia GPUs. **I.e. while OpenCL code can be run on NVidia GPUs, CUDA exploits methods to make it's code run faster.
    2. Discuss an example of a problem that we can solve efficiently by using OpenCL.   
        - OpenCL can be used for problems where the final device the code will run on varies. Because the code is compiled at runtime, OpenCL can cater to many different device types (CPUs, GPUs, FPGAs...) as the ISA is optimized for at runtime. Thus, if you were planning on implementing your code on a microchip without space for a GPU, and on an FPGA OpenCL would be a good option. However, the hardware you're planning on running your OpenCL code on must have support from the vendors as otherwise the API will not work with the device. OpenCL can provide many of the same parallel features that CUDA does, however on some of it's application domains those features will not be applicable (For example CPUs with modest numbers of cores).
    3. How is it possible that so many different devices, with completely different internal  architecture are compatible with OpenCL and enable acceleration of execution?
        - This is possible due to two reasons
            1. OpenCL code is compiled at runtime, allowing the system to implement system specific optimizations when the physical characteristics of the device can be determined. The alternative method would be to have separate binaries for every device.   
            2. OpenCL gives the programmers set ways of abstracting away from the metal. Memory is viewed abstractly, threads and thread grouping is viewed abstractly and the platform model abstractly models the system with one host and multiple devices. 
    4. In CUDA, what’s the difference between a thread block and a warp?
        - In CUDA thread blocks contain multiple warps - while thread blocks describes a set of warps all executing the same kernel, a warp describes a set of threads all executing the same kernel. Warps within a thread block can communicate. Thread blocks are executed on a single streaming multi-processor, with individual threads being executed concurrently. 
    5. Why does OpenCL require an application to discover the available platforms and devices?   
        - Because we don't know before runtime what platforms and devices are available, OpenCL code can be run on a wide range of different platforms and devices. This also forces the programmer to consider that fact.
    6. Compare and contrast the OpenCL programming model with CUDA.   
        1. CUDA built for NVIDIA GPUs only, OpenCL heterogenous. Meaning OpenCL requires more general programming approach that will work for many devices.
        2. CUDA specifies host and device, OpenCL specifies host and devices. Both have sections run on the host CPU and the devices. OpenCL uses the kernel keyboard while CUDA uses device.
        3. OpenCL much more verbose than CUDA, more code required as less guarantees about the devices and their capabilities.
        4. OpenCL has work groups and NDRanges - while CUDA has warps, thread blocks **and grids. **NDRange comes from a use of mostly 1, 2 or 3d problems in most target applications of parallel processing, CUDA gives you more freedom to structure your solution how you'd like.
        5. Compilation at runtime with OpenCL, meaning you can't know the exact machine code your program will generate - with NVidia you have more guarantees.
    7. What types of application best suit GPUs and how can you program to take advantage of the  various forms of parallelism available? Try to describe examples.
        - The best applications are so called 'embarrassingly' parallel applications. These applications require the same operations to be applied on a wide array of data items, with (crucially) individual operations being independent. This allows all the operations to occur at once, with minimal consideration on whether another operation has completed or not. However, one must program in such a way that the parallel operations are truly done in parallel - for example in graphics the different types of the Phong light model are independent, so rather than doing them one by one in - load them all into the immensely capable GPU and let the cores work away. Another example would be machine learning, while layers depend on each other for back-propagation, we can pipe in partial results from one layer to start working on the next - partly parallelising a linear sequence. 
    8. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4ouCT39UXVo_2Bj7qJhThMxfe_vyMST5gsBkVM-nYLDRVEczCQPWTeC682qd3XYi7ev-Yxp_eS8B81hHJxaArA1PcHIuWtWGLg33HbqWjk-UfwxRh92RVUusa5o9yQEf.png) 
            - Platform Model - Describes how one host interacts with multiple devices. Using a rich API to facilitate communications to disparate devices.
            - Execution Model - Describes how the host interacts with devices, an abstract environment is prepared to manage memory objects and interact with devices.
            - Memory Model - Describes how memory is logically (not necessarily physically arranged) where work groups have their own shared memory, work units have private memories and there are device global memories - one read only and one writable.
            - Kernel execution model - Defines how concurrency is mapped. ^^This wasn't really discussed in the lectures, would be helpful to go through this.^^ 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/H3ilrOTcONHsImYWvjkSJBeFEo9leITtzTe7jiTnlRn4YtakmfeQyrbb_Qkmf5FxDwUSwoP6vq3qjhEol_xbZoZRgvNVYRZVQ2Oixupxv0-lRigrvS1dtv3qu5D415Gs.png) 
            - Individual work items have their own private memory containing their stack and registers for computation, this is very fast to access with no congestion. Then work groups are given a shared memory to facilitate communication and allowing for a single fetch for all work items rather than multiple different fetches, this is slower to access but is still quick. Multiple work groups can be running the same kernel, and each of those can access a global memory, which is part constant read-only memory this is slow to access - but large chunks can be loaded to work group local memory at a time. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hIyewZoz0zMszjLOw_8Fhc9vO2cWNX9KLO1Y8Fj1AQo2SEjqXrRCp5jE8pFEUQBWnDyj57QuFpxZPgHD039DzVEJ-UqOX1K3dYrptvYfgwdv34jySrYMs-rQnMdx_Y1I.png) 
            - In CUDA calls are scheduled based on if they are blocked, the scheduler orders commands for maximum efficiency - the programmer must specify the grid size and the number of warps in each thread block. The function must be specified as running on the device, and is then launched form the host computer. 
            - In OpenCL command dependencies replace the scheduler, with guards used to ensure dependencies are not violated. Each command is given an event and a wait list, where other threads are dependent on a given threads event. NDRanges containg work groups much like warps.
    9. Why is energy efficiency the “new fundamental limiter of processor performance”, as Borkar  and Chien say?  
        - The problem is no longer the number of transistors that can be fit on the board, we now have the issue that we cannot control the heat produced when a large proportion of those transistors are switching. With the breakdown of Dennard scaling (due to transistors requiring more static power), transistors are used actively sparingly to not overheat the board. A similar effect describes why frequency cannot be easily increased as it had in the past, the heat cannot be easily dissipated and hotter transistors perform slower.  
    10. Describe Arm’s big.LITTLE system.
        - Arm's big. LITTLE system pairs a smaller more efficient CPU with a larger more powerful (and more power hungry) CPU into a single SoC, such that the system appears to be a single multicore processor to users and the OS. This allows for real-time selection of the appropriate processor for the task, depending on the required computation intensity and the power budget. The vast majority of the time, the smaller low power CPU will be in operation saving battery power - however when the user undertakes demanding tasks like gaming, video decode and certain web browsing the larger more powerful CPU steps up to take the load.
    11. When might it make sense to implement functionality in a specialised accelerator rather than  within a general-purpose core?
        - If energy efficiency and speed are a important, and the task is specific and unchanging then a specialised accelerator is a good option. Accelerators are faster and more energy efficient than a general purpose core, this is because they can make much better sue of parallelism and take advantage of the fact that not everything needs to be routed through a CPU. However, they are custom designed for a singular purpose - so if a better algorithm is found then the accelerator would need to be replaced to be upgraded, which can be expensive. 
    12. **Discuss a general multicore CPU vs ASIC vs DSP**  
        - A general multicore CPU does implement some parallelism, but is designed to carry out any problem one can dream up to throw at it (albeit not hugely efficiently for all) - DSP and ASIC on the other hand are designed to solve specific problems efficiently and quickly. DSPs are for signal processing problems generally concerned with mathematical operations, they are SIMD and allow for lots of parallelism. ASIC are designed for a very specific operation, customized for high performance and efficient power usage. ASICs are more general than DSPs in that more problems than digital signal processing are solved with them, but only one problem is implemented at once on an ASIC. ASICs have a much higher one time cost than CPUs or DSPs as a specific solution must be painstakingly designed and implemented on silicon, while CPUs are very general and can be bought off the shelf and DSPs are cheaper to specialize to a given signal processing problem. 
    13. **Discuss Approximate Computing:**
        - Approximate computing is computing in which (generally small) errors in results are accepted, allowing for far less error checking and the use of algorithms that sacrifice correctness for speed. Approximate computing is deployed in areas where correctness is not critical such as videos, gaming, graphics, audio, etc. The thought process that a missing pixel here or there in a single frame of a > million pixel image will not go amiss.
    14. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/HJi56y0nwzE0cilTtsd0vFKyRasLtGjNsw1DJmHZ2k_Z5AZbF26xUzydqNZ8R4cDZGqlx-uz2Mr-vqVET3nPtWYHUTRVkzh9IpfC04h0gM2H0H8no3diZPWaPBipsAAb.png) 
            - Computational sprinting would be perfect for workloads where the general case is simple, manageable computation - but rarely a heavy serial amount of execution needs to be undertaken, for which a speedup of clock speed will reduce the time taken to compute. In the case of serial execution, accelerators usually take advantage of parallelism to make gains in speed and energy efficiency, thus accelerators would fall behind. Additionally, if the general case the CPU can manage the load. This system would also be cheaper than a specialised accelerator and allow for on the fly patching.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/IYi4VtVDDSvT6SSNeJaOQg40uKCtASXOwlFUH6X8fD715TIU5JbCDXzquNypf5adAkXxMJorq5-LTdmZf3hapXwMQqZpgvTuQcEaPVjeMhAJhLpTMtxS9URgZlW0hExL.png) 
                - Advantages:
                    - Can speedup tasks that the CPU regularly uses, as well as reduce energy usage.
                    - Can change the function the FPGA (acting as an accelerator) computes, depending on requirements, changing of the algorithm or depending on user habits (e.g. a user that does more graphical processing could convert the FPGA to do rendering).
                - Disadvantages: 
                    - Added cost of buying an FPGA. Additionally, FPGA need a lot of power supplier for their constituent controllers - need to have access to lots of those.
                    - Need to keep the FPGA close to the CPU, so time isn't lost transferring the data (energy will be spent during transfer).  
                    - FPGA slower than an ASIC and less energy efficient, so if we end up not upgrading the system we've lost out. Additionally, while ASICs have a high up-front cost they are cheaper per-unit - thus if a large number of these boards are to be produced use ASICS.
                    - Reprogramming the FPGA can be arduous as you need to use a hardware design language like verilog, which requires a lot of expertise and low level knowledge (far more than a language like c), and a very long compilation process (hours long) needs to be undertaken (place and route very slow). 
    15. **Discuss the Spectre bug** 
        - Spectre takes advantage of speculative execution to extract kernel information the program should not have access to. This is done using speculative execution, where commands within branches are computed under a probabilistic assumption that the branch is likely to be computed - while the CPU does roll the changes to registers back if unwanted computation was performed, it cannot roll back the changes made to the cache. The cache can then be probed by repeatedly getting the CPU to read data and timing the speed it takes, if the data is read quickly (you start this process by flushing the cache so you know you aren't reading an unrelated value) then it's in the cache and must have been what was read from the kernel. 
        - This is an interesting bug, because it was prevalent under many different CPU manufacturers and was caused by a design issue within **hardware **not software - meaning it couldn't simply be patched on the fly. This resulted in millions being spent patching the bug, CPUs having to be redesigned to address the issue. 
    16. **Create a diagram with all discussed elements of a computer system (e.g., cache, RAM). Discuss  common units of time for operations that these elements perform (e.g., time to fetch memory  from cache and RAM, time to execute an instruction).  ** 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/f-uF3MGr2QyRTAJRFcKgoGMmxdh6wtTBzNR1fJGCFn25DufzT_OEp61iAggmyk0HybwuVUX0zMdRTKlP5KijPkXPlLmrsYAdEzukkCjPYvOAPdKvLCq4mWxzAKZv3Kdt.png) 
    17. 
        - Write a 1-page essay (no longer) describing how topics discussed in different lectures are related, and how in your opinion they relate to software engineering. Focus on identifying conceptual solutions discussed in different lectures and explain how these abstract concepts are applied for different concrete problems, on different abstraction levels.
        - Discussion of GPUs, FPGAs and parallelism improvements -> Moore’s law and breakdown of Dennard scaling -> Discussion of increasing complexity of computer architecture -> System Verilog and HDL -> Abstraction to and away from the metal -> Using different cache levels and relation to C programming -> relation to security with spectre and meltdown
        - Three areas that had direct relations between lectures were that of GPUs, FPGAs and concurrency in general. All of these topics move away from serial ­computation, and towards parallelism allowing multiple computations to be performed at once (with individual instructions often taking longer to compute than in a serial CPU). GPUs user a huge array of threads which are split into ‘warps’ which operate serially in lock step, FPGAs design varies and makes use of concurrency as sections of the program can be computed in parallel and then combined. Abstractly concurrency is used in both, but on the metal, they employ the technique in different ways.
        - Concurrency is something programmers are increasingly having to take account of if they wish to gain large speedups in code, this is because of (and relates to) the decline of Moore’s law and the breakdown of Dennard scaling.  Dennard scaling relates to the increasing amount of static power transistors use, resulting in power requirements not shrinking with the size of transistors – this is part of the reason for the slowdown of Moore’s law, as a large number of transistors cannot be made use of due to temperature constraints. The solution to the decline of Moore’s law is twofold, one is increased parallelism of architecture and software and another is cleverer architecture making further use of techniques like speculative execution, accelerators (which make use of concurrency) and pipelining (also uses concurrency, different stages of execution computed at once).
        - These techniques relate to the discussions of increasing complexity of computer architecture. As systems become larger, more complex and with more people working on them the design of chips has long surpassed what can be contained in the brain of a single person. Computer architecture is now developed using the cognition of hundreds of engineers over tens of thousands of man hours. While systems like System Verilog and other Hardware Design languages be a solution to reduce complexity, computer architects still need to be incredibly focused and detail oriented to make progress (the required focus is rewarded with a big fat salary). Another tool for conceptualizing massively complex systems is abstraction, allowing for thinking at the level of individual transistors up to the level of communication between different components on the board. Similarly, programmers should have some conception of these abstractions when writing performant and accurate code – for example, a thorough understanding of the working of a cache can help write more performant code using techniques like preloading, loop-blocking and struct-of-arrays.
        - However, when a large system of huge complexity is deployed, unseen problems can occur (despite extensive testing through fuzzing and other methods) as they did in the use of caches. The problems in discussion being Spectre and Meltdown, these two disparate functions of the CPU, that of speculative execution and caching, to leak kernel information to people who should not have been able to access it. These bugs cost (and is still costing) companies across the globe millions as they rushed to fix the problem, also resulting in a palpable slowdown in the computing devices of all large vendors across the glove as systems were needed to ensure the exploit isn’t employed. Similarly, software developers need to be cognisant of the security of the code they write – and ensure exploits are detected or ideally caught before they make their way into the codebase.
    18. Summarize the main message from “Lecture 15: Cuda, OpenCL” in 1-3 sentences?
        - New programming languages can help build better code in specific areas. CUDA is Nvidia's approach while OpenCL is more heterogeneous. Modern GPUs are multithreaded multiprocessors, with multithreading hiding latency from stalls.
    19. Summarize the main message from Lecture “16: Future directions. Energy efficiency.  Performance. Reliability. Security” in 1-3 sentences?  
        - Computer Architecture is changing rapidly, with the rise of multicores and accelerators. There are lots of good solutions already, with more sure to arise. We are in a new golden age for computer architecture.
- Supervision 4
    1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Guf1exbPhgo5Z2eHqD_6p41EcW-pvbqzLDBBZ_gOjY64bnMq11BYpEMCRjDD3_JWU3vMJWO67JNqmPSquhOyJkS2PxJKRzPY6XuzIcYWXPAbuDEVMGcvlSn9bpEIyR0F.png) 
        - The load linked instruction ll r1 (0)r2 loads the value of the memory address in r2 from memory into r1, the store conditional sc r5 (0)r2 then checks if the value stored in r2 has been altered in-between operations (generally checking for alterations or reads by a different core), and if it hasn't it writes r5 to memory - if the write succeeds (e.g. r2 hasn't change and no hardware problem occurs with the write) then sc writes a 1 to r5 otherwise it would write a 0. 
        - This attempts to mimic an atomic operation - e.g. do the whole operation or do nothing, by only writing the result of the two operations if no changes have been made to the operands. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/1rdxh0kr1BQ1jjIGbyqaSZ8W2c6wf4DwLBw-5RvlBmglt3WQDKr8tj0N7ni9qzJv8j-MwMl_epY5fYx-LhZR_yWnD56j0E2Ggjch1EbaAr2z58svi8htj_54ryx4vAPH.png) 
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
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_U4TG3oypX8dYFLZO9RObBtRyB8CiCxGwFyqdIBjeCkDFKKdS24mEW7ZeWtP7DGgM0Hau_p5zXZC2zepjdNVfT9eaglGIqaHO5f5eI7RbA-wk7uzdG1YQM5jfVVbNjb-.png) 
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
    3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TNZR6cjY7oDvebFDH8Cku4Hqg0vqxF1BSYSpUjOiqgAWrDoYi2S5cFGlDfZP5rP65SgqJKwjyUXpj1qFqbQj14QsIMksEU5uqkf_dPBy8QcvdaTEkTbCPg3n67v5RIQZ.png) 
        - Accelerators allow for better energy usage, speed and efficiency - however the specialisation necessarily denies generality - meaning they can only accomplish the one task they are designed for. This specialization could be creating a custom ALU for the instructions or adding greater parallelism (less hold and wait time). GPUs are more general, and can compute a range of tasks with data-level parallelism additionally they can be purchased off the shelf, meaning they are usually the cheaper (and faster to deploy) option than designing a task specific accelerator. So for products not likely to be deployed to a million users, they are often the better choice regardless of higher latency and power usage.
    4. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jdQXJHFRblXwGUT5JyMar0f0PdVC6YoHzUuZYif0STh_qA2hDyTnHtaY0G42L0jQ4LeVMdCHILzPoe-pEmhEOIshVbehstITpHUg6150ZIOgB6qnwTvXomUgOOdrP9N2.png) 
        - The store changes the source register to instead store a 1 if the store succeeded, or a 0 if the store failed - e.g. if the value stored in the address register had been updated. This operation has two reasons for overwriting the source register:
            1. So a third operand isn't required to the command specifying the register to store the 0 / 1, as we need to know if the operation succeeded or failed.
            2. Because we don't want to keep a stale value of the operand, if the value has changed we want to compute value to store again - there is usually no need to keep the stale value, and the overwrite promotes safer programming without usage of stale values.
    5. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/NajlrDgoopacMKkKoVyMrpgocQeL1ZzZluRfVJ3EblO8mKTajlNTXshswBRR0RBXh1G2ZweW-oFnOJwLUMfV0kauNuNe73ov5MOOtZe-i7jzZXH_IfZGPOOzy2jbYaeD.png) 
        - ```csharp
lock:
	si r1 1  // store 1 into r1
	xchg r1 LOCK // exchange r1 and the LOCK location in memory 
	bneq r1 lock // spin if r1 != 0, e.g. if the lock was 1 before hand
				 // If the lock was zero we'll advance
``` 
    6. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/6pCNKWTCJojnQ9ocytIxRRox7zAzsCnW7GLFj_qBYwN2RkQ08135G36BcSkP2eWadM_XBWCXPJaAOehbxZFTty-4odvJYJGgpZYMiMzwuMXTUkxhPpmiXPqBIhfBxCBd.png) 
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
    7. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/iHIusEpcvm2NLeNyL3AhyejG8cbQ69rFfzL0jRTwwzXkKlf1HfJmUFGqLfK_Yy2P3P6Wcn3XoaCaH3l7IMIWRauhgEVLChvv4IAHzqvk5YSq9tzJCOEmzQxXhk1VYNUs.png) 
        - Because placing the memory locks after the lock ENSURES the lock inside the two memory locks runs after the lock is gained, likewise the final memory bar ensures the code runs BEFORE the lock is released. If we placed the memory bars before taking and after releasing, then rearrangement could occur resulting in us performing computation before we've gained the lock and potentially after we've released it. The memory bars create a contiguous set of code that can be jumbled around (within reason) but cannot be exchanged with commands outside those bars, placing the lock and release within those bars allows those two commands to also be jumbled.
    8. 
    9. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5uy3-Ave4JWzB5if7xDjyuptcRc2P18LQVLSyqhAchb4gpelNdsRmxiuPMTs_2w3d3ec0eGZe6o9o7XbZwYQvanclbcIt8VbOG6f2CjuFg2KnV0CWrbcnHtnfRTekPnz.png) 
        - Single instruction Multiple Threads is a method of parallelism, in which multiple threads are grouped into warps who execute together in lock step. These warps all work from the same code on the same data, however they may execute different commands due to branching paths in the code - they execute those commands on **different** data items. Each thread also has its own registers and memory, and the concurrency of the threads in the warp is coupled with concurrency of the processor executing multiple warps at the same time.
    10. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ix1_1-b9Uqxg1LL281nlEESsr1Rsq0Xhfq_qPOmvSo9dIqP7XA-seCjj8CpabVZW9e5_0CL7GytshZayofYi5-Ys-jakOdh9-_dkhwn_n_kznVYpn-yS9zZF-PHHu-1I.png) 
        - The SIMT processor can choose from multiple warps (or even multiple instructions within the same warp) to execute, allowing it massive multithreading - this means if a given warp is blocked waiting on data the scheduler can choose a different warp to execute and the latency is avoided. This differs as in a CPU threads are in groups not one by one, and we don't wait for an interrupt to know that a resource has loaded instead the scheduler has that information all along - additionally multiple instructions are executed at once rather than one at a time in the usual pipeline.  
    11. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/GQ6bygtAaGCx0cF5VnHRJPttyMp5ex4FtV34sztbIaRH76EPEVxR8xztT-g_E9HxgIUydQBQXLoKNh1m2BNOvf2k1e0DlWIwfrNuthm4Km1QnqLFlTEQ95X5leTGFEcJ.png) 
        - The data cache must be larger to allow for a larger amount of data to be flowing through (we now have to provide data to far more threads), each thread has its own private cache and each warp has its own larger caches. However, the inherent data-level parallelism means less communication needs to occur between caches as our data is independent and changes need not be communicated. 
    12. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/NAEUQVtSV9DFM_c_whatVLAJ-LlLb8T2iCQASPraqNRYadmSa9p5hsl8X1ZQB9aSq41EvabBTqfCblhKpTJUl8ZZ9Nbcx6RVBCmc2OKe8Sjuv3xfR5QLZ6OAOJaJ1G9G.png) 
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
    14. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xNBXDXDISRgklZb-mFVvIiDg_mQ2q5YIYCPyEerp4me7-uhdHT0f0_6uOSB1wlZcvShNWDf0kcT97Y2sdGDs25PcjqhklqseiyRE4Kaha0KE4qajcJIQvLKel2vRm5Ic.png) 
        - Warp parallelism is multiple warps executing commands at once, this is done by a GPU with multiple cores wherein a given set of warps are scheduled and executed in parallel. SIMT parallelism, is the parallelism in the individual warps where multiple threads execute the same set of instructions (subject to branch divergence) in lock step.
    15. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/HTSklwp1g1oC-jOqXimSsTSqBEYpGHpEKvwn75yk1S7sooPub-mert71pd1W8ZyfLTCeNkbvKa-ZelnPnBg-k-rRme14lQaTdHNp3l9MO-4Zsp_f41BWLdSbgrD4mCos.png) 
        - Each thread has its own private local memory, this memory is very small but incredibly fast.
        - Multi-threaded processors has its own shared memory, warps executed on those processors can access that shared memory (different processors cant access each others shared memory). It is slower to access but **much **larger than that of the individual threads- this can be used for communication between threads. 
        - Global GPU memory is available for communication between processes, this memory is the slowest and largest - but is accessible by the host and can thus be programmed and changed.
        - Finally we have constant and texture memories, these are read only but are quite fast. Constraining the design to be read only can lead to performance or energy benefits.
    16. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/nXULcIhJFr_O7XGmj-_A0xcqUzMr6itAeNRtJnovL9geICqxQzFpqlhqaOrGGK2Rt1Idg7pqtXfDyoTw6zWU3MGgb7LlhhZwMZ0fsPdONqgGsfdPHcsiY6ZTyyS8v7WU.png) 
        - Atomic operations can be achieved with multiple instructions. The memory consistency model describes how loads and stores to different places are seen. Memory barriers and load-linked, store-conditional important tools for synchronisation.
    17. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BAHk5Ew6Aadc2EIputQEPJ_blb8CdsP4EqgyMkmax37DCVDwd9QVOkSpqXQFqdc4ZlooNd0GgywjzgS4bEeyQd2-RisE8pzdvHTX22vuql90zZXHvM6UiKjWFbNVAimz.png) 
        - GPUs massively multithreaded processors, threads grouped for efficiency into warps - SIMT execution. Multithreading hides latency.
    18. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/pP4O5zBCdjQJYUWklv6yE2IM2zLCEYTh7q-a-5drkiw8_5Np4mmtonZuB6JqoYWM8wv2q5_fipmGMOL99neXPwVVIjlwu30pqRBEGDv5nupq0gePUC4ch0pp760WtpHW.png) 
        - CUDA Is the common NVIDIA approach, while OPENCL is more broad. Programming languages are designed to help code using GPUs.
    - 
- Supervision 3
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jf-UuofY17s1TjPGvIF8ZS9eJEGHmrfT6Dtk0fNmdAlw730xbsBUpcv3s28ChgFS2TM2cTESgdTonLNfsyKo82RUWXrUehVixXxz1GrdTSRgtEiPUrhlTh0PBrIs_iYQ.png)
        - Interrupts are caused be factors external to the programmers, and cause a context switch in which the kernel takes over and performs certain commands - this could be scheduling different operations to take place, in which case the operations stack space and registers are saved and a different operations starts work. These occur occasionally and we have no control over them, and cannot predict when they will occur.
        - Environment calls are made by the programmer, and are used when the program needs to make use of an OS feature - such as allocating more memory, changing access level (generally decrease) or make use of IO. The kernel will take over, execute the relevant command and then return control back to the user space process. We can predict when these will occur and have control over them.
        - Exceptions are also caused by factors instigated by the instruction stream, usually errors like division by zero. These cause the same sequence where we jump to some privileged piece of code & in this case we detect whether this can be recovered from or we simply have to core dump and abandon the program.
    - 2. [2008 Paper 6 Question 2](../../y2008p6q2.pdf.md) a, c
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rSCemIkz1ebYPPCOr7SiSWifHvnyMGhn6yrZ9to0JpDF1YhzqazpR0aBclMH_lj0DloczVqRw5a47AgXdpLRkVsQ2IYDWR1NA60tCiDN30tXtTWFlVRF_z3ZGBMGkceV.png)
            - RISC stands for Reduced Instruction set Computer while CISC stands for Complex Instruction Set Computer. In practise RISC commands are fixed length, while CISC commands are variable length (1 to 15 bytes) this means RISC commands are faster to decode as we don't have to wait for all 15 bytes to arrive - additionally, when CISC commands are decoded they are broken down into many short RISC like commands that go into the pipeline. However, given the greater length of instructions, you can often write complicated instructions faster (by hand) in CISC than RISC.
            - RISC tends towards making the common case fast (based on Amhdahl's law of diminishing returns of speedup) while CISC often pushes for specific domains of commands being made as fast as possible - e.g. adding a specific integer division command.
            - RISC has less pre-packaged instructions than CISC, but more can be emulated using subroutines that are attached to many of the Instruction types - CISC attempts to handle a wide range of instructions out of the box while RISC prefers the architecture to be built upon for specific usages.
            - CISC attempts to minimize the number of instructions per program, the logic being fetching instructions takes time - however the result is long instructions that take time to decode. RISC attempts instead to minimize the number of instructions available by default and thus the cycles per instruction (while still offering a good amount of functionality). 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/WZL6Sadbb6pgxZVdsiw95Y6XfhAd9nu9lmRaLHS618gTWt-VuLb_R7g1HiKWz7yOgUknIgOPRjJLlg7Vwxiy8TUcGgV774gb4Jrk8dEUdGp5aOCrhIEphZe3_cRJUzTQ.png)
            - For an accumulator to run an instruction on two operands, it needs one to already be in it's accumulator and the other needs to be fetched from memory - so the operation is run on the value in the accumulator & the value fetched from memory, finally the result is placed on the accumulator. For stack operations we need both operations on the stack, and then the two are popped from the stack the operation is applied and the result is pushed back onto the stack. 
            - In stack based we need to fetch the two values (if they're not already on the stack) and then apply the operation (which is a dense command, causing two pops, some arithmetic and a store) while for an accumulator we would need to fetch one value, apply the operation (which is less dense just one fetch, an operation and a store). Thus the stack is narrowly more dense.
    - 3. [2006 Paper 6 Question 2](../../y2006p6q2.pdf.md)- part b:
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ae32BTrZ-dV7nLJGOy84Vjb38Zcr5CHMvCizurI6cEumjHdLdYWRWpseLfZoW_MaM56457SlgWeI7KxpeVYNir2vq5LEvUElvflyby7X80EKYYOCUe7UrmzeTn-tZTHt.png)
            - One reason is that while transistor speed & density continues to increase, the speed of electrons in a wire cannot be increased through engineering effort - as CPU speed increases, the clock cycles taken for electrons to reach different cache levels continues to increase to our detriment (no useful work done in that time). 
            - Another reason is the problems caused due to ever increasing parallelism, an increasing number of cores that need to share data between them requires the creation of shared caches - we then have the overhead of ensuring the values stored by different caches is coherent and we also have the increased time of accessing caches further away from us than the L1 cache. 
            - We also continue to live in a world governed by the Von Neumann bottleneck where Instructions and Data flow along the same buses, and although we have separate L1 caches for Instructions and data this separation causes a slow-down when fetching from caches higher up the hierarchy. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/N2z2HfJ2xfd2fMm_8q2AY3g1spuGcmNGdYAqgGKe2nVAmUHSlooSzcnxnw8TonaSGIieAKfswunhEfudtuSIKlINozST-DoJR5sPNSWjVzu-MSWvPEqJNf2C2qgNQD2h.png)
            - Spatial locality: 
            - We adapt our caches to take advantage of Spatial locality through architecture to improve cache hit rate, we do this by reading items around our desired value into a cache line in the event of a compulsory miss. This decrease in hit rate makes memory accesses (appear to be ) faster as we can often fetch the data we need from cache. Similarly, for temporal locality in that we make the choice to evict the Least Recently Used item from the cache - even employing a victim buffer to stop pathological misses. 
            - We also employ a hierarchy of caches, where if one cache further down the hierarchy misses another is likely to hit - this decrease in misses results in faster reads. These SRAM caches are faster than DRAM, and are positioned closer to the core (L1 cache often being part of the core) resulting in FAST read speeds.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/p03-uxf6e0ERGAz1XawaYCw7btJszLgaAdOl_9LioV5SIYV9M_mSybKikb1jwSu-tf5rClW2ZW2npscjSUTC6xHOmS0OB6fD3L2aYHFFG7HSDSV_X7KwBxpPJT9EcRJJ.png)
        - The TLB improves performance as it can decrease the number of RAM accesses made - TLB is close to the CPU and can typically be accessed faster than level 1 cache (because we need to determine the page to fetch very quickly, before destination register flushed), if we do get a TLB 'hit' then we don't need to consult the page table in main memory, instead the TLB serves up the address of the PTE directly which can then be fetched. 
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/DWS_DbhGbc1gfIswk9CSqZ45WLZrf9UPdQHZRIsWfvwQNEa4LUS-7LN3ZTONqD4l32WulBKQ6vEeh61WDP8bjVaW9FwQW7_R6km3bdSFypp-552Dfv-HHSbZvoiZpiAf.png)
        - When a program attempts to access memory outside of it's virtual address space, this will be detected as the PTE will not be in the application specific page table (or on disk) and a page fault will be thrown. Thus, an application cannot access memory managed by different applications.
        - Additionally, virtual memory provides permissions on who can read, write & execute a file - whether or not a process is allowed to access a file is checked dynamically and if the process does not have the required permissions it is denied access. This is possible because the actual address is hidden from the process, and hardware can decide whether or not to supply the real address.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TsQ1TzHmnIZh5ASUJrgWmNdalT2Zw2lQ1gChLh3aBI1DCJ2z37OJ3-onlMT0sr1ZQdr9V4wufI_vCt25EgM4-6292xa0NpHZpbPp83Gp_7CcxJF5Um7CO1zm-6IVqKap.png)  
        - Processors, memories and interconnects.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/F_LCdAJw_NvkBinFS1Gf3VgNHiTkHy8SR9hyIqFeWs7ZDgDljRLP2Yr9aHash8P-S1J4EgtjKeVXKMQdI-h1IghV1NsyUmNzs08g_0n9Cydxxupmz8HK-7obw5I7Mz0G.png)
        - If all run in parallel, the bottleneck is the slowest member - and as D is now doing 60% of the work in the time it takes to do 20% of the work, the speedup is 3x.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7iZx4ZweGdvOvzu5z_l70StyotqciorBogTQ6HIlyEXejW8oGySnXQQfZCUZhw2tU6rTH-01veBC5M7vS31eFkBzdRBLQ3ICvBuolW6SbLwQDIkIruoq87qCMzXkPvy5.png)
            - $\frac{1}{0.15 + 0.2 * 0.5 + 0.05 + 0.6 * 0.\overline{3}} = 2$ times speedup 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/cY6QT7bsC9lo6AwrvC6bshytYsneI0Hw01nqLGFF74XMVHNoFR1aiMWmRvU9zDkm96sQ1QKHnzZ7l_0qY-sGa6ZgT3K9iWmc_KtliJetZvTqQNpWLw4OKchJdbPsoa7m.png)
        - Sequentially: If B & D are instant we have $\frac{1}{0.15+0.05} = 5$ times speedup
        - Parallel: If B&D are instant, the bottleneck becomes A so $1/0.15 = 6.\overline{666}$ times speedup
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/KwpkuAQjVok9cAmJfeDWPSi6oD4n6EUgpULx4L_MeBp9qelxjRMHG8cqi8mnKxJhZpR7xXflxIOMJxLE9p6JdL5UdFgHo2D2rxvpU7_rh3ekNroZr1WgKZ1jJ9D46sr7.png)
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/GROvBCPnzUMS58cVrT3Cj0AK5Lml2PHMrLGzq7qHqdvCFxTqpSpzlcU9qywrd8F_wkJMNTLhCzEn1T8NNIcKIouGy01kJyUJoGh3GEL2su4bnhr8puZW-1W_Dl_AQNr9.png) Drawn by hand.
        - The DRAM cell is a method of storing data in a mediumly fast, volatile and cheap manner. There are two methods of operation ↓ 
            - Reading From Dram - In which the Word line is set to high, and the Bit line is set to some 'floating' value between low & high (say 1.5v) then the capacitor either outputs to the bitline if it was holding charge (a logical one) causing a voltage of $1.5V + \delta V$  to be read at the sensor below OR if the capacitor contained no charge (a logical zero) and gets charged by the voltage causing a voltage of $1.5V - \delta V$ to be read at the sensor.
            - Writing to DRAM - In which the word line is set to high for 1 and low for zero depending on what we wish to input, if zero then the capacitor will expunge it's value to the BL - if 1 then the capacitor will either charge up or remain the same. 
        - The capacitor ambiently leaks the charge stored within it over time, thus we need to periodically (every ~64 ms) read the values held in the DRAM cells and write those same values back to them - recharging the capacitors who held 1s.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/fq2nVqfEASe2rnCEpIIB2dL4wn9JaIZo1qx0FAHCetvWKlRNXoDp8gYk2ux0o77RDN4Ro3VigSt_yze77Jh-2UXANVxx-u99AV8ctH75RxR8mAR8fAQ7hfMj9-E7VnsX.png)
        - Because a bank that's just been accessed may be in the middle of refreshing the values stored in the arrays (since reading from the arrays is a destructive process), we can mitigate the time taken waiting for the refresh to complete by accessing a different bank first.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Mmrjr3lJSwf2HGb3SEYjiUKgGoC_g_F0kimsPV6k_2xFRkZ0A6igeyMEd_tqeBSKrmR3DI-gBBzMiFEN-YNgHIqIGHyhLEn7QBHcYdOAJUdv3cPHOrQxvhGYKxH_Tc3Y.png)
            - If we're in a Open-Page scheme, wherein the sense amplifiers are not reset by automatically after reading a bank, we can simply read the data stored in the amplifiers without having to fetch the data again - this saves time, and thus is beneficial.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dS9yzQZbCPSxlszPvk9vMGJBUhD26m5AgQr5_qloo3ztSp3LGRDaNwWZmAu5rWuUwGxgHB6Wz2wVfmoQ_klivUNkYoj3yVhVS2ntTuQ56YwIIXr_d_NN5nYWoa2Ygde1.png)
        - The row access enables the transistor, allowing the transistor to emit or charge and the column access then allows us to read the value detected by the voltage sensor.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hFCKZctPGzZ4iaV3m296g8bI9xVITUwrowz8mkSRk3vgg9FevcflRk0umaT_oB4dNRsSCktLVAOykLSWqm8VGBeRn6WOfTASMY-cjZIW_GH3-s6e_sg6EzAJNStZnoZk.png)
        - Single Instruction Single Data: A simple single core, sequential processor who reads instructions one at a time to process data serially.
        - Multiple Instruction Single Data: used in systems designed to cater for robustness, i.e. when we have multiple CPUs voting over results from data inputs such as rockets. This voting process makes correctness more likely.
        - Single Instruction Multiple Data: Vector operations where a single operation is applied to a host of datapoints, this is efficient and low energy.
        - Multiple Instruction Multiple Data: The commonly used multi-core parallel processors of today, wherein multiple cores operate different instructions on different data at once.
        - A multicore process with a short-vector instruction set would fit within MIMD, this highlights the breakdown of Flynn's taxonomy for use today - as almost all use cases are multi-core.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bkqqQkjhlzBDEmrYDKbLncwWBjl4nfafP6NZ5sIS9AZ11TZe8Uff_d-RhB6y5uHGDwUSadY6o3Q8BnforMTm7i-C8f93mPgyHG0tr96jZocEoD4J4RuIboucDnA7H84A.png) 
        - Amdahl's laws concerns computation of fixed instruction size, evaluating the speedup as number of cores increases. Namely: $\text{speedup}(n) = \frac{1}{B+\frac{1-B}{n}}$ Where B is the serial proportion of the code, and n is the number of cores. It makes clear that for a large speedup, one requires a significant process of the code to be parallel.  As we increase the number of cores, the speedup becomes more significant.
        - Gustafson's law concerns computation of a fixed time, wherein the volume of the problem varies. For such a problem: $\text{speedup}(n)= n - (n-1)B$. This law explains that even when problem volume is scaled up, the parallel part still gains increasing speedup but the relationship becomes linear rather than sigmoidal.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/PCW_aIZZjTdu7vAWNNYXs1SCIspDtj-FJfICVMl0rMpOguJqmOjQAEti0fEDQYBLgNVutmTfoEN_9h16fi3c04prxuHmgEvO2WYtsVu_GYawovf9i1GV5UnOeXZPrjF6.png)  
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/vvC6eIv17JNOfYPFCIjZjixAGSJU0u7t0rYbRD6Rjln0rhC2Oil3z1gmJl4Jhe0BVV6yG4UwTq14ZcXWFePWclF7RrTBlfNYZlYz7ynWsW1exuY4nJPZ2JKwbvmzQqvw.png) 
        - DRAM is organised in a hierarchical structure, Devices are combined into ranks who act together (their results are concatenated) where ranks are independent. In devices within ranks, the data is gathered from a bank (only one at a time), the bank gets its output from individual DRAM cells concatenated into arrays. In this case we have 2 devices where each of their banks has 12 arrays,  resulting in a possible 24 bits.
        - ^^I don't understand the below excerpt from a slide, if we have 512 columns why only 16 bits?^^ 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Ha_YYFQAifCByvjCuocyUgozmMrufyZe2HmoWyQEwRCgg7NHMoS_ALKGvZj-DJDxn1TX0BwBVqXxTaHSps4j4sMu91wuKIfxHaKz4Qls6sDc6V3l_zkfO5d2bMIAM2NV.png) 
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/s5cRytkd_TEPs8P-ywDIKKBH2Wgremx2bFpd2YLXnDvfbbtZqoanRSfNgVaHxKxPnr0tTxE7gLemr26vugi0EUihzKgW1ZIFwSYsSZL6tQQGsPcLNK3bPuZbtziODcBQ.png)
        - Open Page: Results stored in the Voltage-Sensors are not flushed by default when results from a bank is read. This benefits processes which are likely to access the same locality repeatedly, as we don't need to re-fetch the values.
        - Closed Page: Stored results are flushed after reading. This benefits processes which are likely to access differing localities, as we flush the buffers before the new locality fetch is required.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/QGN4oxkVDnrIU52JdgYHePNfoYhX_cMCGGZx5x4ocIjBwWGWPZczL9Hu_fx7unVcBnOZKJ2ZaVHfMWoaES-nb_R6rNO5qRRfngwCWRdkyE-hr_G3tCaw6zkzv9Y7aKXM.png)
        - Shared memory is a useful concept as it gives an easy to conceptualize method for threads to act in unison. It's disadvantage is in the effort that must be done to ensure the threads are reading the same values, in ensuring this uniformity of values we have to implement some serial sections - e.g. the MSI Protocol which forces cores to wait for each other in order to communicate updated results. If this necessary aspect of data synchronisation is not upheld we can have data overwritten, incorrect calculations (based on incorrect input) and general undefined behaviour.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bFXtw7UfA25j4KUr2DJJUcsjAxscfdX-35LYuYejGdzHRyY4kdhrOC5d503-rnVmjiQ4u-YYuIXP2PyuvFRetOJZyw3b5HXa-7V6b-dvPmqK7tbhGDfigV1Ik-pNNSgu.png)
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3JlfPD9eb-Go6IkvwXCQJQwV-gJPBgRjyHUFwSqajFROt9wz7C5lEwuI9s6PhgKxsJN2TbmSp8UmX3Q2ipWLea8CoO8j_MBJioz6Qxi5oLFuz6gVNfD3fNCw9HV1TrDA.png) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TS1Nt5YEigxRgtW21hBSS8kqzIL47DstMDt2jtVksbpi4U7ScTIEqG8YB900s-M9LoSntSCNOiL76knagGsjSa7g6yiDvxz6CXDHKJwVDWsiSS2aE5s8uyS26E6bBvvy.png) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/OEtTI8My8XSioVO0Fju6T0ioO0N3yT_0PgAM0j28ogNebOiJNjON2n_zZxQ_TKlC_LeRDwFwuPpFVxvaaZcdUOLvq_kQ_i8hdoKStO-ZXyuie8nEygfTeaPu5w8JrpNQ.png)
        - Method 1 has the benefit of quick communication of values between all cores in the fast L2 cache, each core has it's own fast private cache and not a huge amount of data is repeated as only one cache holds repeated data. However, the central bus could have a lot of traffic slowing down processing and a lot of effort would have to be done to ensure consistency between caches.
        - Method 2 has the benefit of reducing traffic on individual buses by spreading it across two levels, additionally every pair of cores has a fast method of communicating. It has the downside that for the two pairs to exchange values they have to use very slow memory. Additionally this method makes bus sniffing more complex as the L2 cache would have to communicate the sniffed results to the L1 caches.
        - Method 3 has the benefit of expanded private use space for the cores, reducing the chance of having to resort to memory. Additionally, it is more straight forward for cores to communicate via bus sniffing than in method 2 as the private caches & the public cache are clearly separated. However, this results in more repeated values being stored needlessly (in L2 cache) and a lot of processing has to be done before it's decided a value is missing (search L1 cache, search L2 cache, send a message to search L3 at which point we have to wait for the other caches to run a check after sniffing the bus then finally we check L3 and at last we have to resort to memory).
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ALKU8hSSW9mdiBjiPYuDGLsx0Yl4N1tAyPEOjyemUzf0V5Qnp09h7t0pF8FsR4kWqM3fsbMiT7BPGslH8kAKeBK4w4aQG8BduX9nUZ36TEHQYmUwr466QGue4LicVYun.png)  
        - Inclusive: All values stored in smaller caches, will be stored in larger caches.
        - Exclusive: Values will only be stored in a single cache.
        - NINE: Values in smaller caches may be stored in larger caches, though there is no guarantee. 
        - By smaller caches I mean caches lower in the hierarchy & larger means the opposite.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gnGeaQmtcoNy5ZhjROBvVzAwXMfdjSG3C5kxJSC1R9dsEAKRSGo7La2Kh__bK0IqcThPgZFWL6EVgJ40BaDlG0R15A5Z3ygZm4ecv5AXzMAgqGhykj_kpllr7QCOI1-i.png)
        - Under the MSI cache coherence protocol, caches can be in 3 separate modes:
            - $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {I}}}$ mode, where the cache-line is marked as invalid - i.e. we act as if we don't have it stored (but don't actually take the action of removing it, it will be replaced). If we wish to read the data we must issue a BusWrite call, read the value from memory and upgrade to $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {S}}}.$ If we wish to read & write values we issue a readWriteX call, read the value from memory and upgrade to $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {W}}}$. 
            - $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {S}}}$ mode, where we store the value as a reader NOT as a writer. If we sniff a BusWriteX call, we must become invalid - If we decide to want to write to the value, we issue a BusWriteX call and update our value from memory before upgrading to $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {W}}}$ mode.
            - $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {W}}}$ mode, where we are the exclusive holder of the value and can read or write to it. If we detect a BusRead call, we must write our value to memory and downgrade to $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {S}}}$, because a cache in $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {W}}}$ mode must be the only holder of the value. If we detect a BusReadX call, we do the same but the down $\raisebox{.5pt}{\textcircled{\raisebox{-.9pt} {I}}}$.
        - This ensures all caches hold the same values, as only one cache can hold a value that's being written to - after which any reads to that value are synchronized from memory.
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zvEuBYjnX_eiFcabqGcgI7WQeE3cwisMx6wIcGbV_ZNC8yuXiSQ_QbKt9YoH9AGmPE3nAK5Zxw984u6aeLkgmviAX7qWDeEpq_fkZf5I3060QNzC3RfrUYed19J4R8Vn.png)
        - You first write your data to memory (^^Wasn't really explained how the precedence works here, how does the other cache know to wait? And for how long?^^) then transition to S state.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/FLBiBIzm4AwpDjF5bcxLv5v2J-QpDrRQiIZ3-U4ywuFOuLlp5wtq5620H_U4i83aERdqZOCaCjqbyp3O9n6rhEtsONWsDM8eFJF06RDYT_sUUjj-IBRcLj9OkqSubU13.png)
            - You do nothing. One could extend MSI to send your value along the bus as that would be faster than fetching from memory.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/esM97s0emvnAHg5JhST0ezKtEWoXS0lquJCV3hWl-OV8mfsa04RPXrXaPXm8stTTTnWe9l71sxFURzzUkrG8nCc1oFmH-FUIcBCmdgm5S33WwNah0wEdFDIEViBeOWb7.png)
            - You do nothing.
    - 21. [2018 Paper 5 Question 3](../../y2018p5q3.pdf.md), part b.  
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7bgda-H3OLiUSJ063JyXJ8hE_s3S8ODxBRThEtdRTcAvpZBsXTcvLesI5jMCnQHKsNqaZMBGHWC-sO4GO7NUTejpenn2Fduf-I0DaX3OMVlRSIlDYf-x0G3Pi95ccwxd.png)
            - Cache coherence ensures values written in one cache are seen by others, while memory consistency attempts to ensure the ordering between reads & writes doesn't cause improper behaviours.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5sIceteoEqGQoCKvfF8ey7aWgLHquJ87-RSGWsI1jBVqxzH51ZjWAVVN0bXAsIYoA_Ag7Br1dFR-YusLhlkFbHuah8oaUtQEJCJiubLqCynCqx00PrnKEH8ooq3Xj1nr.png)
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_ZQbCuIDZz0b7M3HkNsf6nTPaV3HqYI82Jpr810QCnTppzPYXgokn6juAkBg-3vUXrYgXirk_6iXKppd_Mhb9RyCETtt1mvUpix-lqgAyYxW7b7yi1XLPBs6BlwQ5ojh.png) 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/PDJPOQqzMhDtFwmkSxYgzwPaNArVL2To06Gd2Vj1BVTOFgrKjfF4Gu5z-ubiAH-T6NP3JpuUd5xvQMyEbTBpmWlK51W_u4WPtiEYpMMvuG31e8qJCvjsgykieZJspy2l.png)
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/8a68vLHMj-2N5qVbfqbGSlhp4lOGjEmuoQ2L7vprEQu9SHKgVq2P3EcR6RU2WcKkQ0eLJ6EFSaQ03JFc7mEAqSXjaDufcacKCBFWAH9hQBPCX0PmB-Uwqi3unoKivYn1.png) 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ZjGTjLTqjWMKO282PNdtrnKWSu7g-SzttsWD3jlULbBncXDZd2j-ap8qG2JDUwTpU4FeoSyCizFVhpO1ex3ayr4ZgjgLSTh7c66SzzkqfzNG0UNBqRSgxTp89T4bS22J.png)  
            - Passing from the cache to other caches is faster than fetching the values from memory.
            - If we're in the M state and another thread issues a read, we transition to the O state - after which if we wish to transition back to M we no longer have to process an extra memory transaction - we know we have the most up to date version.
    - 22. Summarize the main message from Lecture 9 in 1-3 sentences?  
        - There exist lots of methods of hardware support for operating systems. Different processors have different implementations. 
    - 24. Summarize the main message from Lecture 10 in 1-3 sentences? 
        - CHERI protects from improper memory accesses by explicitly linking bounds measurements to processors. Stack based ISAs can have very compact instructions.
    - 25. Summarize the main message from Lecture 11 in 1-3 sentences? 
        - SoCs come in all shapes and sizes, designed for specific domains (whatever that may be). Lots of opportunities for customization within an SoC.
    - 26. Summarize the main message from Lecture 12 in 1-3 sentences? 
        - Multicore processors provide MIMD parallelism. Using shared memory paradigm intuitive for programmers, but propagating writes to data can be hard.
    - 
- Supervision 2
    1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ujcL6v4TPBhwrAcC9U-DaheF_SZq6DZo4qsSSIJ_y5ZWZw2da0KoPhAc-IC7-96muSFQa3iDtOcZFGvVILKMMqKF8thbd7P8VPDM5HDH-kPnflEeHP0Iu8ue1pvtHVLD.png) 
        - An immediate is a value that does not need to be fetched from a register or memory, that is it represents a value directly rather than an address of that value. The only computation that needs to be computed is extracting the immediate, involving sign extending.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Bp04bTw83jaJ9i3BiMwlJkcbV2zGungrBbTZkiONosl6IIUNJIY44FN8t0FxPPXLej7ilSAiBcFsEAvBObuzn9CT5dsZGLDwxryh2ouy-blZW25weMm4z1xKCbkLAbPx.png) 
        - ```javascript
AUIPC rd -1000; // rf[rd] = PC - 1000
BEQI x5 x4 100; // if (x5==x4) PC = PC+100;
ADDI x5, x0, -5; // This stores -5 in x5.
```
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TeoYGLDUjRa7z5q-5Sn9A1w67YUAcm-CNL2WnXCz09VzCz1Y1eAmoGrncZiSqTrcIBx5hleeoQ8KLbe3CDOo3AHBFzl_korJ4nzpcqvhA0TUp8CJZVWmEYJoi97vraU9.png) 
            - Because immediates take up space that can otherwise be devoted to funct3 & funct7 fields, which extend the opcode space and allow for thousands of more instructions. R-type instructions contain no immediate and thus have a funct3 & funct7 field, while I-type uses an immediate and thus only have a funct3 field - 6 bits less opcode control results in 2^6 times less possible instructions you can perform. The reason in general is that register-to-register instructions require only 5-bit register addresses, while immediates often need to be longer than 5 bits.
    2. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TYJ8_gFTsVYCGehDl-wZLT7Wk-FpYNQne44DtqUNd_0Py1Jv5aJylbRJ4IaeaoUsJeyOuexaycxFPcKAOd--yodGGGFhyijXf2dy-_R2Ffu7kqihZ0lBTMsOzn79_bnA.png) 
        - ISA level simulations are programs that interpret machine code and run said machine code in a higher level language, they are often "bare metal" (they don't run an OS) and also ignore factors like varying clock speed & interrupts from other programs. An example would be SPIKE which is the ISA simulator for RISC-V.
    3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/J7L7np4Dby_9cLgtwDrxVP_rCQvCdpja652qu3tqA_9_zf00zFxmlz5Y1Y91Q67pxNMadtl_1T3b4jNQSVQnK436sCLkhjdhDGUyd30sLe-CNjCeLVA7cAOgRoHtkRP5.png)
        - The data path is the actual flow of information (be that immediates, addresses or register values) while the control path is the signal that controls the flow of information. They tend to flow together because certain control decision can only be made once the instruction has been decoded, and the data values can be examined - for example, the values of the registers in a BEQ command control the control-flag the ALU emits. 
    4. 
        1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hUXO8mnviRXtruya41BN9kijy81S75f1t4yhCe2D_F-K5Xcfy00i2Whwvtj99jatVA46g22xuuDOv_P9KBet5IdEGrYBfqtoWorSMisBVdFzpaJ7X8lrnVRKxaSQIBiq.png) 
            - Performance can mean many things, in terms of CPU we have Clock speed, Cycles per instruction, Cache fetch speed, Number of cores, Individual core speed etc. A benchmark could be developed to measure any one of those metrics, but there is no overall metric of performance.
            - Performance varies as outside conditions vary, a benchmark could be run when the CPU or other components are already hot or when the room is abnormally cold, which can lead to incorrect predictions when the system operates outside those conditions.
            - Performance can change due to conditions inside the system. for a CPU we could have lots of OS interrupts during the benchmark or lots of other processes being used that hog resources - making the benchmark innacurate for normal operation.
                - Performance can vary for the use-case, for example a CPU can favour high core frequency vs more parallel cores - where the higher core frequency system could do better in a non-parallel use-case the system with more cores would do better on tasks like video-decode that are suited for parallelism.
        2. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/DHrxwCXTlVqaXyaqr4YJu0IbL7nGyZFwnlKjLGPDeZMf46R9iyOaHoTqqmMn5aIdtOCMtTu4BuB1UhY87LdrVnJM-IsjP_GRWLZyIzpINdk3GP7_nPBvnq869JBRisYq.png)
            - Instructions per second varies wildly depending on the program used, some instructions take more cycles than others - thus, a computer running software with more lengthy instructions would inherently be considered slower by this metric.
            - Two computers using identical hardware but with different ISAs would result in different measurements for performance, consider CISC vs RISC - a given CISC instruction could encode multiple RISC instructions into 1, and even for the computations would thus compute less instructions. 
            - Again, this measurement would vary with the conditions of the two computers - a higher temperature computer would likely throttle and result in a lower clock speed, leading to less computations being computed per second.
            - Under Von-Neumann architecture, much of the time spent is data fetching & setting - and while we wait we can simply perform polling instructions. Thus, the most critical factor for performance is not captured by this metric as we can compute a load and then repeatedly poll to see if the data has arrived - this will result in a high instructions per second although nothing useful is calculated.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/oJoZsvB6MsmJwvU8JTK0mCpOZwXsO74aGqk67D3Kj0BtNaS0ZZ3ub3GzMCUEzROzFokhWOllo9mU1Ht2Rdzvp0omRBRQ756XZfOpMBsc7tz53YwTOfD_naTefMAxWsxm.png)
            - Peak performance is only useful as an upper bound on performance, can't tell you anything about the common case.
            - Common case can vary wildy from the peak performance.
            - The difference between peak performance and common case performance will vary wildly from program to program.
            - A computer with much higher peak performance may complete a task slower than a computer with a higher average case performance as the peak performance cannot be continuously upheld (temperature throttling, data starvation etc.). 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jazhr05nvPg_iVt0LtIBeOZTQuMCyOcdNOviCvlVf8W-KmER0h5cIj1Gy4QVqy27RU2Mf6u2qwK0glP-aOVH4hOEofmgDjSUeOpeV9vqStLxou_cxkEC8iLi0bDwCb7X.png) 
            - Some applications are orthogonal, e.g. best performance and lowest price, meaning you can't have both. 
            - General purpose CPUs are usually slower than FPGAs computing the same algorithm, due to the allowance for greater parallelism. Thus, serving multiple purposes results in slower speeds. This similarly goes against making the common case fast.
            - The design is always a trade of between performance, energy use and area - these trade offs cannot be thrown aside, as some applications want small area & energy use with a lower requirement for performance (phones) while some require high energy & performance resulting in larger areas (compute servers). So no ideal processor can be developed for all applications. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Dpic-8nsa3ExxGcMZkvAmhuAwT4wbYgoy6GScYpcugSf2Dc3x02taF2oTvhMwuRzlhJIHprRr0jXl8fTvSyvfLNlzpcchdPBLJhtQxoF8eFn_67EheC2FgQxVtZv5h56.png) 
            - While longer pipelines can allow for higher clock speeds (less work per stage, allows for higher clock speed), there are associated trade offs. 
            - Diminishing returns from performance increases, Amdahl's law - if an operation time is barely used, adding a pipeline stage can decrease performance as time needs to be spent waiting for that stage to complete while a fast operation may be waiting.
            - Additionally, resolution of control and data hazards increases time taken (we need to fetch the correct instructions and flush state causing bubbles in the pipeline). Mis predicted paths have a greater effect on longer pipelines - ^^Got this from notes, but don't really understand why it's the case wouldn't it be the same?^^ 
    5. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/HrcWNFR_E2HESaJNxYOc7XrcKLX7vDuEmKx5F6q0Ap4tlz7gLbVz46xUZcZFdvFK8tcDtriByoZ1znxvUBVKmXSTWuBOSG3FdtkBC2qTP4jjZxoijgI4vGt2mfKPaIf8.png) 
        - No, more complex pipelines can have more stages - the 5 stages is what RISC-V uses and can be modelled as an abstraction for more complex pipelines. For example, CISC pipelines can have a second decode stage where longer instructions need to be further examined but this would be put under the umbrella of DI.
    6. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3Uy5_FV4LoCFD69iUHoN_NLwWYbbpIANN4-7dl7wqsadCZTdSr4xD-zcEHF0qNv23_lY9jodR7L4rdJ2zgKOFGKC_LU5288COxmEU7NaLzdlxbKOIQJjtXzlziqGeyJz.png) 
            - From a birds eye view, data & control hazards are a necessary feature of parallelism - if we are to run sequential programs concurrently we are going to have instructions which rely on the results of a currently executing instruction. More specifically, data hazards are when an instruction needs one or more of the items that are to be "written-back" by an executing instruction as it's operand/s. This hazard is caused by operations wanting to use transformed data. Control hazards are caused when conditional branch instructions need to wait for there condition to be evaluated before we can update the program counter and fetch the next instruction. This can be mitigated by trying to predict the outcome of the branch, and rolling back if the guess was incorrect.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/p7VHTCavrC_gDoAR3T0SQE-x2lZ_lO0XFya-WFeB8v6O2zvBO6s58odYJIEVdVIHLepDOIV3hatj8h8JZdGnpm9wZjd81eZD7Yeh9vuEx_fffZQ2FUQWL9_RZI45vFYL.png) 
            - ^^Can we go through this question - don't know what it's asking ^^
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/fzxrPBHAxm4NkUXqKIIy3xlM1J658qmhBqCZWn75WRdHYpWMNfBPKWKdz_GVO_imF2vt0XpRlyQLUNFiCsbEkHOa2w2Cam9dfqed3WxBz8dZ6CMFjiYVFaTwaSLC4WdA.png) 
            - Pipeline A:
                - Data hazards cannot happen in pipeline A, because once we've decoded the instruction the previous instruction has concluded and the register has been updated so when we fetch the register the results will be correct.
            - Pipeline B:
                - We can introduce forwarding from end of the 3rd stage of the 1st instruction to the beginning of the 3rd stage of the 2nd instruction:
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/I_OZbM7nhza2JNMJh9i2jbqw_hqkjESg5n2cqMqBOB5aHntnRGYE-eWc_xiuCoxd86If-izdy5APWDfFTaUwprErMbypg7j-UDXOSqc8QYz1J78Ht_rHpij5uhmKKGSh.png) 
                - This forwarding would overwrite the values in the registers if they were changed, for example: ```javascript
 ADD x1, x5, x6;
 SUB x2, x1, x6;
```
                - We would have to feed the updated value of x1 from the 1st instruction to the second.
            - Pipeline C:
                - This can be resolved using standard forwarding if this is an R-type instruction, where the result of the execution of the first instruction is fed into the operands for the second execution stage:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/2X9HLoPP_olxS3qMxdKywBN3qrUQgBv4Kf1gqfUKzKNf0TriTV0CpKUE2BvwaQrnlAVIwM7SmYywV8nKXZauyItrAKNbnAdUzyMExe8igbYJHystbNYxCkDFFvGOvzwU.png) 
                - HOWEVER, if our first instruction is a load that the second instruction relies upon we will have to have a bubble and use forwarding from Memory to execution.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/1iYR9GJRtRBen6sgG7ruEOkFMcgFH1yGk9-keOL-hwq0rO_NbQwSkqMITqdFblngsP9H1TSsdhYrqlPyp7_pYQ3nO1B8moL3fvPWS0_tSq2TYDbf0Sl4P_D2up8CNA64.png) 
            - Exceptions do introduce control hazards, as they result in the pipeline being flushed. For a precise exception, the exception is recoverable and this will simply result in bubbles in the pipeline according to the number of clock cycles the exception took to resolve. However, for an imprecise exception we cannot recover and must simply exit.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rj3My9YwE1oxjg_TS7tLeqXizhP0fVSeBZvGTt2ve4bmbMWPQx7skKXtO1nEQyuIwAIIMTOB6YrXpcvSAXWF2iVxhwW8_c-mpR3DUg3SjHZGkZiofmio1q8VIZBtSeVB.png) 
            - Interrupts do not introduce a control hazard, as the entire pipeline would be pushed onto the stack in the event of an interrupt and resumed after the interrupt was handled. We never add incorrect instructions to the pipeline while the interrupt is running.
    7. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/E7o0ebzVnw8np-AE1bfqtq4SmA7zbpTWTm-KLVnaK_u4T80CWJvAXgZpbBOgPh4J56uQ4qBtn1GzFJSpo6w6QmNmH-NJvJhJvQJ09P40jKqdpBMgVJjx2UR11VtZah4J.png)
            - Branch prediction is when the processor does not wait for the arithmetic operation section of a conditional branch to be executed, instead we make a prediction about what leaf of the branch we'll follow and roll back if we are found to be incorrect. This can avoid control hazards (if it predicts correctly more often than incorrectly) as we don't begin fetching items while we wait for the branch to execute, instead we instantly make our prediction and update the PC resulting in less instructions needing to be flushed.
    8. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/E3_cpU7FhIMFMosx0KRu0eo_OaU7N78GMgNKn6Z4mK05y9ZFcbgrbb_xNb5vFRQhmDFCxO9uEGx9vqsbmy8p0InfYnVHSLIG032U0pjFECdo8YqrRwhM5RB2uJCC_tJB.png) 
            - This is contents of lecture 9 which has not occurred yet.
    9. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/XqoBtTygBlIN6uHJnGQFh8I3qcG5IFvD87VmbkDnkztk5tUxtfQOmQ40ltDXkkhsoRbKPujZEQQmJ1r7D0-xwc8AfWKfENyGLKqnF8dNeNZPx3Hzb5rcMjgZsBNdVUPU.png) 
            - Memory latency is the amount of time it takes for memory to arrive after being fetched, while memory bandwidth is the amount of memory that can be fetched within a certain amount of time (generally a second but sometimes 1 clock cycle).
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4MbwB78Gg0rz54Ex-HTTS495wkzxAFFrId7boZPkYTW-NPvTw84Qy-53SoNYxxl69wJs1_1j2r8vQFsyMWfBPaiv3mkT0CgYqPKrqdf5aOTBKXc-hPD3KD_pC3UhqCiU.png)
            - Exceptions are caused by processes in the CPU, whether that be a division by zero error or a syscall, while interrupts are caused by an outside I/O controller like the OS. Interrupts require the registers to be put on the stack until the handler is completed, while exceptions can cause irrecoverable flushes of register files.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/64IDOmAG3--v5FSz06UBv19TM9Ten3RMit5FpFJrCZQedy_Pgck5FP-1510pdgGPPtl5qPy-9vTc09QwuPVdvnZrrzZiJBbbQO3Ao__BU6FBh4ye4wZ_zhLPMo43xFM7.png) 
            - The programming model of a flat linear address space is the most intuitive and easiest to reason with model, we assume the programmer doesn't need to know the fine details and abstract them away. The CPU is then tasked with making this intuitive process fast. A hierarchy of memories is used because the speed of light is slow (and because very fast memory is expensive) , calls to fetch data from DRAM can take hundreds of cycles so we position fast caches nearby the CPU that can be polled very quickly. Only if we miss our poll do we need to step up the hierarchy and fetch data from DRAM or potentially even HDDs. This is also a result of the Turing tax, as most of the time is spent fetching and manipulating data rather than performing computation.   
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/CjzrJJe0a3jCVrKSznbuZBlZa6b775Anpio3P0U3NAmDXWuekow4eGuAqN7z0olkCfSAxcq0RR6HeaMfRf00bPhCXCBf0EgKikgvbJN88Rgdaj0FmQZeFT_L1NBYBygS.png) 
            - A direct mapped cache consists of many cache lines that contains data that was spatially-bunched on memory when it was fetched - each line is referred to by a unique hash which is usually some combination of it's index, it's tag and the word to be fetched. A set associative cache is a large collection of direct caches, where all direct caches are polled simultaneously to find data. In direct-mapped we have no choice of which cache-line is replaced, as it is built into the memory address. In Set-associative we have certain options, such as least-recently used, not last used and random. 
    10. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Ayul6TLMRCoxjIc4cAeVdla03F32FFZBHs2WOkxOm2JoUTWhDDDPHb8vr82sLaKnJBgFSvWweZFPG13haPBzu_i3HkOIMibSi3Dl2xp5QEaUlmmq0CIc6xsAEWPCUWJZ.png) 
            - In control-flow machines, values need to be accessed and consumed quickly to allow for the progression of the program - as later instructions will require the results garnered from the consumption of the aforementioned value. Thus, if the memory access latency is high the program cannot proceed - this lack of progress while waiting explains the sensitivity.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/6XbZtfmhU9YoHSaiiAAH83hNSuVF-1TFe30ZdN-KZp1KnKiYdasyjpow9irpDz__J0zagsIWnV0Khhi2GcNVi-DMhcImhRCB06PwBVLuNLgsTvXFz3zIms49CxjvSPPJ.png)
            - Temporal and spatial properties of data access patterns are exploited. Spatial: if a certain piece of data is accessed, it is likely that nearby data is going to be accessed soon. Thus, we cache requested data and data spatially close to it (in the linear memory) on a miss. Temporal: If a piece of data has recently been accessed, it is likely it will be accessed again soon. Thus, don't just flush data after it's been delivered to the CPU - cache it for reuse.  
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BubVqInmQH73h3cTr6eb56u3QrOMDUy5kFkJzxcyS4I_rHKgLZAQl5X7WiVh5fbXXb0d-BcUAOC62OoAj4WKHekVCLk6dpp5CjkD76PMcil9bcVpM3nVLQdjz19D5dBH.png)  
            - Direct-mapped caches have no choice as it is governed by the address of the item. However, set associative can use least recently used (hard to manage for large sets), not most recently used (easier to manage) or random (easy to implement and around same performance as LRU). They might also implement a victim buffer, to avoid "pathological misses" 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/x42S6Ceps_2HqEL8DCX2MNjn47hCcBIv9BnoibcAplrSNuL_RqflsWNePHiY5N5eqrUFDV2Wm8SpJfcq6qwtGCjYEhto6W3BFUAt7d3m4rdWi9Mim0FhrzSw8TvhPmWe.png)
            - Write back & Write through. Write through is where you keep a write buffer, when a data-write hits update the item in the cache and add it to the write buffer. Only stalls if the write buffer is full, in which case memory needs to be synced. Write back is where we mark updated items as dirty on data-write hits, then when we attempt to remove the item and it's dirty then we must sync memory. Both of these are methods of keeping memory and caches synchronised while keeping the CPU occupied with computation rather than memory management (as much as possible).  
    11. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tSOQjmd979Wel0vDmCZMaa4dj7gHcSLmRnHZGNq-uA1Gb4DFVOomMrCrDVhBVXvV9Cxt50j0SrgvZUOg3hsJqdi3K1aOOmmrVFslMiHiQztfSseQ-kh8ZOlfQIHFQgdf.png)
        - Cache miss rate is the rate at which we poll the cache for a certain value, and it's not there - meaning we have to fetch the data from higher up in the memory hierarchy, if that's DRAM then hundreds of clock cycles can be spent waiting for memory to arrive rather than the 1 or 2 for the data to come from cache. If our cache miss rate is very high then we are constantly accessing from DRAM, resulting in huge slowdown of our code as we wait for memory to be shipped over to operate on.
    12. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/neVpREEPM9QEQh0eE3YLO6iHU2MOTJ8UiE2T7JCPv6ylofruCHwLnLNZxJUANvvPIw5kajdAq7yl4xxj7T7OJgd_Pjuc4SmLGKzDApXwbEKWsi1JFjIsiPUVq-HFBqUE.png)
        - Single sections of the pipeline can take less time than others:
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/QgDYiw-84BUNbSgRI6NeWKTsYHXqJqKIWtTbVWCEnfVMsvlGWNfH5W5BeOhrrU5w0y9YksdAxhGCdVecxuyuDUb4iJjyRvl6EzU7QIohyaNRMn-pQ631fgHoWeTquEbn.png)
        - Thus, if a given instruction wasn't waiting for the proceeding instruction to finish it could complete the execute stage quickly and advance to the memory stage - however in the pipeline model, every stage takes as long as the slowest stage - resulting in: 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Mu_iWQF_bZD1YvTf0XGvMi35rlo8rUysvGO3fuqEI3NB9t-5Gn3tTOVaLJEIMSSn0JHGqE_6up5Rok71mWSeQJahF-fzbRXKp5m9o7AZUGIw25izDnqQ1xJ4OkzYnv1n.png) 
        - While individual stages can be slower, we can compute up to 5 stages simultaneously using the pipeline model, resulting in the overall execution being faster.
    13. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xBcTxIj0lgc1qrOs4Tz9MmVw0eVOqdOgEF_xlwQ3nmMJXJNAb2DWCYVTLvC9tinnMJxqkmtRZYWBUOLadV3iTFoi4cPNaDDMkYTXclrfMWae96U6qY0svUk7ndFljEBZ.png) 
        - Compulsory misses occur on the first access to the block and will always occur.
        - Capacity misses occur because the cache is a finite size.
        - Collision misses occur (only) in non-fully associative caches due to competition for entries in a set.  
    14. **Discuss the main message from lecture 5 in 1-3 sentences:**  
        - The ISA provides the interface between hardware and software, however that interface can be misunderstood as its often explained in English prose rather than a formal language. We desire a formal language of an ISA to allow for easy ISA simulation of a processor. We can then compare the models of the processor using tandem verification.
    15. **Discuss the main message from lecture 7 in 1-3 sentences:**  
        - ISA influences the design of the data & control paths. Multiple issue and dynamic scheduling can be used to reduce hazards and increase parallelism.
    16. **Discuss the main message from lecture 8 in 1-3 sentences:**  
        - Because physical constraints prevent the creation of a huge low-latency memory, we must rely on a memory hierarchy. Caches (widely set-associative caches) take advantage of the temporal and spatial statistical features of memory access to store data that is likely to be used close to the processor.
    - 
    - 
    17. **Discuss the main message from lecture 6 in 1-3 sentences:**  
        - Pipelining improves performance through parallelisation, each individual instruction has the same  (or higher) latency but the overall computation time is decreased. However, it is subject to hazards that must be handled with care. Instruction set design affects the complexity and feasibility of a pipeline.
- Supervision 1
    - 
    1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/2UQdpnQ1FkPkFUL4c5t1kWXX8y3CADrCFDn91MYJHDc14YPQZRJNraIwCbbIp89K4lKp_c4rP_kIcGIvHYGgzPMxlPie8s-mfFv3OwXYC4kPYjfGX5OrK1qSldMXblyW.png) 
        - Moore's law states that the density of transistors on integrated circuits, doubles (about) once every two years. This continues to apply for the time being, however we are approaching the limit in size of transistors - given that the smallest transistor we could produce lithographically would consist of a single atom in size, it stands to reason that Moore's law cannot continue forever (although we cannot predict future discoveries). However, for the time being the doubling of transistor density every two years is still being upheld. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xYXHCdBxVEZ6SpLlP-ayz2XFjwCy7rNKi_33h8Ft17-nd85USY418aMCx8u1LRpktHyZtvLU8yMgvokFrZkmRMFDkL0vk1EJmqRIId_2caDaXUokQUVpOl0smC6Vz0Ut.png) 
            - While the density of transistors continues to rise, the computing power you can leverage from said transistors is not increasing at the rate it used to. This is due to the breakdown of Dennard Scaling, Dennard scaling is the idea that the decreasing transistor size results in higher clock frequencies at the same power. However, this has broken down as transistors require more static power to run and the working voltage of the system cannot be scaled down at the rate Dennard scaling requires - this means relying more on specialised chips (accelerators) and improving processor architecture rather than continuing to miniaturize it.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Q4ZZGTuw-9knew4SIejsy_O4NY5MIENMPj9WtraKgVUfPcSKFU4XeS2GoYszaS6keQ62ydV4udorTU2XdJ9BwbPsD6FykSnC-dIDlRpqDT5no4GOWHQdqm53hiHH5EYz.png) 
            - The doubling in density of transistors every two years would result in a pattern of Dennard Scaling, namely
                - Chip area halves every two years
                - Frequency can be increased (by about 40%) as the length of the critical path would have decreased dramatically
                - Voltage must be decreased to maintain the same magnetic field over the chip
                - Power & energy decrease in sympathy with the voltage
                - Thus, frequency has increased 40% but power draw is unchanged
            - Before 2006 this relationship of doubling transistor density resulting in increasing frequency at  the same power draw was feasible, however after 2006 this relationship broke down for a few reasons:
                - Transistors leaked more power, static power use rose and transistors required relatively high voltage even when not switching
                - Semiconductor technology no longer could improve at Moore's law like rate
                - Wires don't scale with same chip area -  __Writing this from notes, but don't really understand what it means - would be helpful to go through this.__ 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Fw_FBajQEF-Q1GHz6GAARODE3VXBhH3R0LRSkqdRZBXYmxqRgG7vn8gy-EfmFUvKbVD4PG8R6E4mtm2ATTTyn4E3hlZyrRlAn8ZcsIpWvWI84T60DpyNFqGCSomlzvtp.png) 
            - The breakdown in Dennard scaling requires a changing in approach in the design of high performance general purpose chips, the 1.4x frequency increase every generation can no longer be relied upon to bring hardware improvements. Alternative strategies to improving performance must be employed including:
                - Domain specific FPGA chips known as accelerators
                - Limiting the number of transistors active at any one time - in that vein is race-to-dark, turning of cores when not in use
                - Improvements to chip architecture & ISA
                - Employment of different chips for different workflows, e.g. a more powerful CPU (or a GPU) being employed when doing rendering work
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rEOnDKh22cKdx73dq-PcN_vOV8Cxn89SGxibA9BzJ7xQI8S8uQLf6rULEmAM-eaeTDB4Ug_Uer2MECtP2NkXhQ72OTzE_UTYrbJTWJwoOjKvDbK3WuAUaRsHuiK6WyxQ.png) 
            - Dark silicon is the amount of chip area in a integrated circuit that cannot be powered on while maintaining suitable working temperatures. As described above, the efficiency of transistors has not increased as Dennard scaling would have it - so if all transistors were supplied with power in increasingly dense chips, the resulting increase in temperature could damage the chip or cause a fire.  
    2. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/IT2dql__fLGqf4GVNEhdRVjR6-BnrpjXNiugp6PTQvw_I9j5k69Tv1Ks--Ykd6G55c_eFnSdr0NXF0Bnfq2S51OWqpezgQTjtNyZgIA6LYsNC6ur2O8y0tNYxfYTKSUa.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/p6oneUwYrLCGTrHJs9vTxCUgjN_tN_NPdlHLiLcZ2R31Mlpdau-G6wEKpokuFnXG7JYy8TBo0PPh_tqb-dvSq4DmiVNA-T1lLxeiegE0vgor63iFn6gkmX20JkzBeyQZ.png) 
            - ```c
module seven_bit_nor(
    input [6:0] a,
  
    output [0:0] b);
  
  assign b = !((a[0])||(a[1])||(a[2])||(a[3])||(a[4])||(a[5])||(a[6]));
endmodule
``` 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hvLJ8_w-jNwTuRhid60ORFMQI6QKJZXkC8LH76ZnP4iZ2IE4w0g0eVxf3OW6r5RkQ5ioCwFNi-he9qQbhhPmCi0M9x7sdqXKWkrrkduxhT2DJdtzGg8MmwysRT1TuKr3.png) 
            - ```c
module four_bit_adder(
  input [3:0] d,
  input [3:0] e,
  
  output [0:0] carry,
  output [3:0] result);
  
  wire [4:0] temp = d+e;
  assign carry = temp[4];
  assign result = temp[3:0];
endmodule
``` 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/cIXgZzNJHK2WR6WlPb5Xa5O2WJKh45GL9qCrPopl3SFPcaCG-s-u1w9WGvjhgCbyIFpB6r2kDBj2h2Wab-OzxI5hjcdWEk1dr9jAQXL6Hcg3EMaZL8Whr8K88mR2V78B.png) 
            - ```c
module multiplexer(
	input [3:0] a,
	input [3:0] b,
	input load,
	output result);

 	assign result = (load == 1'b0) ? a : b;
endmodule


module thing(
	
	input clk,
	input load,
	input r,
	input [3:0] g,

	output h);

	reg [3:0] ff_out;
	wire [3:0] adder_out;
	wire [3:0] mux_out;
    wire who_cares;
    four_bit_adder adder(4'd1, ff_out, who_cares, adder_out);
	multiplexer mux(adder_out, g, load, mux_out);

	always_ff @(posedge clk or posedge r)
		if(r)
			ff_out <= 0;
		else
			ff_out <= mux_out;
		
	assign h = ff_out;

endmodule
``` 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/6K7crCiuD-NaTWO5HDkgVM6FkAe0Of2_sqJQvWVP3upsUajztlz2m-KGH70D7eVV_cRR_H2gri3BqPGzELahOpgmJNKlqGC3AkLtPehk75w1wo19H5XEy5BjYc71zyOa.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BUjnDkUsxRvCapdfbOZPBKiFsYzgeUIhACSbI38k3SkiAJHDSdGse8ICaWWLaDhY1QPEzayhsBQazHEWL8mEiPFuKe6xKYh2ACD0Ay86olZl4U2_cY3jZ_Q8vlc3HAPC.png) 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rOhjWwznStNn4uT7WgYJKTEYQY4qRLbaELNgyfAg_NM3wpopMfnPgCTJQjnNMs_sWeE2SDwzHA8sfu83f4BRt2tp23FdJE-wgyPDlw-hZDFfbhuxHmg4VccfcEJn3ofm.png) 
            - Whenever Ain is 0 & Bin is non-zero, 
    3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/62jYcXcvp5-K-KT9jGUFLq0G8ymM7zsMMkrns5IvjLMBDOFIj_hYmDl0Uu-FPw3unnSyFYHrkKInj3tYN7P7WcJIENoO7_UWgxJx9CieJwrKeJ72aOLVsCwi4GZLAmri.png) 
        - The mystery module behaves like a stack. 'head' is the index of the head of the stack and mem is the equivalent of an array (that head points into) that stores that items in the stack. The opIn command puts the value in dataIn onto the top of the stack and opOut simply moves the head of the stack back one (allowing that value to be overwritten in the future). When the module is full, if we try and add an item error will be set to 1, meaning we will not be able to add another item. Similarly, when we are empty and we try and take an item out error will be set to true and we will be stopped from doing so. When we are empty we have the additional side effect of outputting -1 in dataOut. op decides whether we are inputting data or outputting data or neither.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hUkjVm7UBOSGw-ABIHcSOtftvD9mLbfGtF8VIgib2ETzsgFn_3vwsXGxUFPyBesxk70KJMVN-DGsja5FjlBTelQFspG3eQMSnM_LpRYyv_H9nyR77FhX4LWjKMsxofik.png) 
            - Production tests are used when the chip comes off the production line, it tests whether the correctness of the board is maintained throughout the manufacture process. Functional tests are done before production, and ensure the correctness of your HDL code.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ufaK7X_Tg3kA8QzEtneISxNOefoDhJE0V6Bwh8EMdc0lNl24lQDjdz45KY_jSQnZ3BoMOUZaiGkFQh7PHbsB_cERPZb1pGLlXTkJ7_H-wzYumQeY3U19dJK9j7kMQG_s.png)
            - The mystery module is parameterized by the width & depth variables, thus there are a huge amount of permutations of those values that would need to be tested. The opIn, opOut & opNeutral values would all need to be tested - and varying ordering of the commands would  to be tested, resulting in thousands of possible permutations. Additionally the correctness of the outputs of the stack would need to be tested according to varying inputs.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/61sohsSD65S5uRDO7M5mmOgV9Cl-ttxt3bT7agOqJCBQKBffyOlE7wriUFv-K7DgJEA2Ypjvj8YJOmEqUlqVRJrugPn9eJvIEfwbDq9tse1AiMDeUsoDqHjZyftziDRh.png) 
            - Similarly, the correctness of opIn, opOut & opNeutral and permutations thereof would have to be examined as well as the effects of varying width and depth - however less permutations need to be tested, as we have concluded the logic is correct and are now testing the physical board where any problems would appear with less nuance than a small logic error. However, this process is made more difficult as we are using a physical board - it becomes more difficult for testing in parallel, and physical factors like temperature and humidity need to be considered. So individual tests may take longer, and we must ensure the board is kept at the conditions it was designed to be used in by users.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/L9w2S79jAzPJe-B5MEgJrZ03BGSBkt6ryzB0yvzSWy6YJnEalCGKflbVuEEnCT8EnxOGZGmphXuvmJHHIgbQbo5e1g2J3nlZ3sSZhNL8s3thrK64Ai1YlI9irxlIGCQq.png) 
            - SystemVerilog is a hardware description & verification language used to build logical models of hardware that can then be simulated & tested before finally being implemented in silicon.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/s_dGIjzu1_bYbflvHG1GqIQhDr3wBoOryD0wRVWVCyiN6pAc-21l-DmB-dHReBb1K4qy7jBN09IW3LXdZ_Er7L0PsQNeynZaSeNrZK5awAt4wP1JLQnjySt3ubgF1bHM.png)
            - Meta-stability is when the output of the flip-flop takes a value with voltage between that of a high & low signal. It occurs when the input to the flip flop changes during it's setup or hold time, and the flip flop captures the value of the input as it's changing.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rljtTxKhNSKzEPi1Q5loesdd1fpx_6hXt-vg42OuntEKsxFmYR8YCUiuM_cGTjeV4PMnY7az-5OR-AB6gUor50g7dvs4gHpRrUzmsOADWhjf35daaVoLOl9YYuVEt_5U.png)
            - FPGAs comprise a sea of interconnected logic blocks & IO units. These logic blocks can contain complex features like flip flops and lookup tables, and can be programmed to implement a variety of functions. They benefit from being directly programmable by the user, that is one needn't invest in a chip negative for millions and produce your design in silicon - this means programming one is much cheaper than the alternative. Because of the vast array of logic blocks, FPGAs can take advantage of massive parallelism resulting in quick computations. However, FPGAs are much slower per gate so this parallelism is necessary to reap a performance benefit.  
    4. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/9JfvfQNG88PPatL-LGthmAf1ekA6VqJBTBChY92IumRxKw24x0ntjkLvUzM3ZV_UObXKGqhdW8oZCKDv9HvetY8ptV4R6SvHMBd1ReiQGfLE3VqcKcrEsKWXtP0KCHIi.png) 
        - In C's case first pre-processing is done where the plaintext elements of the code is changed. Then the compiler compiles the C code to assembly code, this is ISA dependent as different instructions will be deployed in different architectures. The compiler will employ tricks to improve performance while keeping the semantics of the code the same. The assembler then converts this assembly code to object code and finally the linker combines various .obj files into a single executable file containing machine code.
    5. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Sdh8cPzeyLI-XzDa6wMfkiZYUB6H_Zki2pKhO_YN3Ns3c_Cd1JHwxAtAhDZ1pu1Ami8Tl67xRH55V6FFll45UCaBIp_jWUQ7AO4j4wtkLEoRCqk4knF7CI_GcEe-lMhw.png)
        - Clock Speed - The number of times per second the CPU clock flips, equal to: $f \leq \frac{1}{\text{Time taken to traverse critical path}}$ . Operations can be segmented based on the number of clock cycles they take to complete, and all are sped up by increasing the clock speed.
        - Number of cores - more cores allows for greater parallelism and thus a potential speedup, this does require software to be written to take advantage of parallelism.
        - Cache size - as fetching from memory is such a slow task, having a cache large enough to minimize those expensive calls is very important when trying to improve CPU performance.
    6. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/g0pdH_L0Ima0pUXs9OKScuB2D6KMgpQBOK8bRQXVNuGGd4YUOCHTjIuTOuDn4mbe9YjsJu96F3uCt8T5d5g8-3koJVb3dsY5T-P1_ZtOeXm0cm2F_khcU2PV50yInyY_.png)
        - An ISA is the set of primitive instructions the CPU can perform, ISA matters for a number of reasons:
            - Ease of programming - One can design ISA instructions that couple multiple commonly combined instructions together to make the life of assembly programmers easier. In RISC such instructions could be left as subroutines.
            - Making the general case fast - Including certain operations into the ISA can result in speed ups in specific operations that will rarely be used (e.g. supporting integer operations) due to pipelining. Thus choosing which instructions to leave out, or how to use non-special-purpose components for a given instruction requires careful thought.
            - Some parts of the modern software stack is ISA dependent, meaning porting those sections to modern systems would be incredibly expensive. 
    7. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hSiQu5PlT8ACwIkSvrP7QR59BevxaMb9YVZOVrd72gcmD7ONRE87Qq0XY_iUHb-sZke0qV9Mo3060_YtFMjL3kjOJu2x8zQoyUG6we5DDRM8kYSGECzgwqA61IXsyqee.png)
            - Moore's law makes predictions about the density of transistors on the CMOS chip (namely that it will double once every ~2 years) while Dennard scaling makes the prediction that clock frequency will increase by 40% every 2 years while keeping power the same. While Dennard scaling is based on the assumption that Moore's law is true, it goes further and assumes increasing transistor efficiency. Dennard scaling broke down in 2006 as transistors required too much energy even when not switching, however Moore's law still holds today.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/UY0yfJpN6phy-eB9hvgQ8zb-XyGz1uy9gljT2bTMYvVfdOY_EehHgKuHVUtdm-aK4iLXdRS_gJN8kk9kNvtfh5QBu_Ks21NuUw_QuEqCXalCgUT-Su4MqvY2lq6OPKZp.png) 
            - The critical path is the longest path that data can travel in the circuit - an exhaustive search could be carried out by testing every input for every state & measuring the time taken to finish computation. Alternatively, we could model the circuit as a type of graph and compute a breadth first search - recording the largest number of steps in the search. The critical path directly impacts the maximum clock frequency, in that the clock frequency is:
            - $$f \leq \frac{1}{\text{Time taken to traverse critical path}}$$
            - Thus, decreasing the length of the critical path would allow you to increase the clock frequency.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/sZU5STJY-guUdE3BQKXz05R38ufvi96_JuO8__Gyvy-s_Q1IZ9jQ2FMe83wU57ZB1AyOmj6Q6vhwYopP9mIrqF_gwdK52wpZVyQFbII2GpcxT6E7JRL7sJiwee9hg3wq.png) 
            - A calling convention is a low level scheme for how functions receive parameters from their caller and where they do with results, for example MV r0 r1 moves the value stored in r0 into r1. It can impact the design in a big way, calling conventions imply certain big decisions such as:
                - Max instruction length, decides the total number of instructions possible
                - Max number of immediate parameters to a function, e.g. parameters that don't need to be fetched
                - Where return addresses are saved
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BlFcoIXChRxj-7sJ7kp-w1qtgRgmJVcwHgNY9niWjD3TvdTtUvetXCboQ-cPtmM99T17rV38pCr_s6_zcGGjV1gQjSxxBDzzPhZrcLgC062aMOSSTZ4l6eEFqpLRvye4.png) 
                - Section A: This section checks if we need to do another round of the function or if we're finished. If a1 ≠ 0 then jump to .L7 otherwise jump to ra (this will either be to the initial function caller or to another instance of gcd)
                - Section B: This section allocates space in the stack, and saves registers so we can make our way back up the stack frame to the initial caller. Allocate 4 spaces on the stack, store the current return address in the first segment of the stack.
                - Section C: This section computes the modulus and recalls the function with these new values. Set temp = n2, n2 = n1 % temp and finally n1 = temp. Then jump and link to gcd (storing the current instruction location into ra).
                - Section D: We'll reach here if we've previously completed section C and section A finds $a1 = 0$. Here we retrieve a previously store return address from the stack, free up the stack and jump to the return address. This starts the process of unravelling the stack frame.
    8. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/sBPoSMEcGwfeclHCQG5umDhvhCzuEURc3ZFKjKlKxZWrAqVUb05SDX2eaWMJOC8QpkfIjBRGoNxhcRdC4XDdaIiJtDvfcRC-5S02rkInpNg2NzzkCnvWZBbX9yoCyJl0.png) 
        - Von Neumann style processors are not the be all and end all of general purpose processing, the incurred Turing tax results in slowdown & massive power use. As the golden age of silicon is over, we need to consider accelerators & other methods of improving performance that our outside the Von Neumann box. 
    9. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xzHKmOBmsp5VTUoRYJqnaeoGLIMjg6wfYAlFayAT7WDYyE3UH1rDsBABqCNr8M6_ZfUR7SyD0-tUrPiXdfiXuO3t1uuT3vqOiMDug6FC-Z0X_z9Z_q2JxwWc_W0nGfvb.png)
        - Clocked digital designs are used everywhere, propagating the clock signal is very hard and requires careful thought & design. Designers need to ensure that their system meets timing requirements and handles asynchronous inputs safely.
    10. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/KnuI9ow0ir_IgodEqmPCY7IHvLAA5uGz_W4OqIwyGOIrbGVgtUaub1gRxD2OMrQg2JLYTmNUH5OKJLuUMoJLFzyHknqz358TnMcq-rMQVSx21tmKPfKUcYzwonBnDHlT.png)
        - There are many possible elements to optimize in processor design, and while one optimization could help a given workflow it may hinder another - thus there's no perfect CPU architecture only compromises. The Von Neumann model doesn't help with improvements, most transistors are used moving & storing data rather than performing computation. 
    11. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/M6Mcdr232g4ok7gXv5Jnt0aBIXo-zv-LY1wfcfH3O-o8qTWJ_IbgZSIJJN-ma2PeMKIeiC8JlpD4XwHqS3srsVvlCk8lnU8OBJjeMph6pjP8HqEP4LLLL_GZ1rw1InkS.png)
        - RISC processors are often simpler and lower power, but CISC still dominates the PC industry (ostensibly due to backwards compatibility issues). RISC is used in the phone & microprocessor space and also in the research & teaching space as it is open-source and (relatively) easy to understand. 
- 
-  _**Lecture 1:**_   Technology Trends  
    - Different Processors are created to fulfill certain requirements, what are the 3 main requirements?↔Power, Area and speed
    - Give two factors that constrain the production of CPUs with higher speed↔Instruction set parallelism and Power
    - What is the main benefit of devices having general purpose CPUs when a preprogrammed gate array would work?↔General purpose CPUs allow for firmware upgrades in the field
    - **Von Neumann Architecture**
        - Almost all processors use this architecture 
        - What are the two main features of Von Neumann architecture ↓ 
            - A linear memory storing data and commands
            - Control flow processors that execute sequentially 
        - ![](https://www.cs.mcgill.ca/~cs573/fall2002/notes/lec273/lecture8/vnb.jpg) 
    - **Memory Hierarchy**
        - Various different memory storage types with increasing size and decreasing speed. 
        - Processor Core, L1 Cache, L2 Cache, DRAM
        - What feature of processors poses a problem for fast memory fetching↔Sequential execution, means the processor cannot asynchronously fetch data
    - **Manufacturing cost**
        - What is the most crucial factor for determining a chip production profit margin, and what is that item proportional to?↔Yield, which is proportional to Chip size
        - One of chip production cost is going up, and semiconductor fabrication foundries are getting  more expensive exponentially
    - **Wire Scaling**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/1T9JycMAAFENrnfZUO0ti3ABwW9gPPx7tlIvpaxhOCk1D53dJNi65eBCRM6mtfzcDtHO6cPcfvmz_juAgfvUAO6oZ3_swOANtSJ3F89qkLy0QdS604_CmJIUBd_MtVwp.png) 
        - $$R \propto \frac{L}{W+H}$$
        - $$C \propto w \cdot L$$
        - $$T \propto RC \propto \frac{L^2}{H}$$ 
        - Where T is the "charge time", e.g. the time between applying a voltage at one end of a wire and reading it at the other. So performance doesn't increase with the same chip area
        - Halving L makes the wire go 4 times faster, so can add buffers
    - **Dennard Scaling** ↓ 
        - Sequence of Dennard Scaling ↓ 
            1. Transistor dimensions reduce by 70% each year
            2. Area decreases by 50%
            3. Frequency increases due to more densely packed chip
            4. Voltage must be decreased to keep electric field the same
            5. Voltage decreases 70% reducing energy by 65% and power by 50%
            6. So every generation, transistor density doubles, frequency gets 40% faster and power stays the same
        - Causes of the 2006+ Breakdown of Dennard Scaling ↓ 
            - Cannot further decrease supply voltage as transistors leak too much, static power demand increases vs dynamic power (when transistors actually switching)
            - Improvement of semiconductor technology slows - no longer delivers on Moore's law like performance
            - Wires don't scale for the same chip area
        - Is Moore's law dead?→Moore's law is still (just about) delivering on the doubling of transistor density every 2 years, however due to this leakage and static power issue we need to constrain the number of transistors active at a time. Move to accelerators.
    - **Age of Dark Silicon**
        - What are three methods to improve processor power efficiency in the age of dark silicon? ↓ 
            - Use domain specific processors (accelerators) which are more efficient and often faster
            - Race to dark - Keep transistors depowered when not needed
            - Use a range of processors for different work loads
    - **Voltage and frequency trade-off**
        - $$Active Power = C \cdot V^2 \cdot f \cdot A$$ 
        - Where A is the proportion of transistors actively switching (Activity Factor)
        - For a limited range of V, f is proportional to V - so why not just crank V?↔Heat could pose a fire hazard, and CMOS circuits get slower as they heat up
        - What is DVFS?↔Dynamic Voltage Frequency Switching, adjust voltage with frequency to trade off performance and power use. Similar to overclocking
    - **Low power at idle**
        - Would like power use to be proportional to load, however the i7 uses 258W at 100% and 121W at 10%
        - Static power makes this difficult, and having a lower static power results in slower transistors
    - **Moore's law for storage**
        - Moore's law for density applies to DRAM and flash memory, because they are made of transistors
        - What is Kryder's law?↔Kryder's law is the equivelant of Moore's law of increasing density for magnetic HD. However, the size of HD increased much faster than Moore's law
    - **Design and verification gaps**
        - As computers get larger and more complex we get problems with managing designing them
        - Solutions to the design and verification gaps caused by large and complex systems ↓ 
            - Hierarchical Decomposition
            - Replication of parts
            - Libraries
            - Abstract interfaces
            - Higher level hardware description languages
    - **General Purpose Chips**
        - Not power efficient and slower than the equivalent FPGA which have 15x slower gates - this is due to parallelism being exploited. 
-  _**Lecture 2:**_   Digital Systems Design  
    - **Setup & Hold Times**
        - Setup time is→the time an input is stable before a clock edge 
        - Hold time is→the time input stable after a clock edge. It is typically negative
    - **Clock trees**
        - Clock trees are a method of distributing the clock around the board. Distributing the clock takes **30% of the power.** 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/RNWvNUP8E-F1Z3BSv0mWWJJT24TTB1ecMszjTAPsmjXzwE1YNxg6N57BULPNDoVedNlxRWWWdmHUkEF05vrioBLBVG4o-fOtXUlAHcxZ9_1puIyceF2vQ2kFi9_z-VqR.png) 
    - **From HDL to implementation
**  ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/mzaVgamHApPBW1cFzJkRSZR4GyKnbc2ZjRhgDkdo0qN1aPDd0JAf8-w_V8ri2KvrsOlEiGoN1_oYQrj2eXG-_mSutGOZmKJBMI4ozWiafquWcXTB0AZh4SISPQiBCXBW.png) 
        - The **Synthesis step** can provide **optimizations **like→Boolean function opt, Optimal state assignment, retiming of timing closure e.g. parallelization: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/N-I0g_1_6868oJ_oBQ2btiiLKAmJjVvCFyVtNpAbiz-KxBTaaJ6xDTw0UEfbcE4MvmeUotl2deP0FvgF48jP3ajn46FLQznvmFXFKAUSUg6et_J0qI1nIYDKulLKI9De.png) 
        - **Place & Route**
            - What is **Place & Route** given to use?→A directed graph of components linked by wires. A Netlist!
            - What happens during **Place & Route?**→Components are placed on an FPGA route, wires are routed between them and items are moved around in an attempt to find the optimal placement.
            - What are the **constraints, limitations and benefits** of **Place & Route**?→Area, location of pins, set performance/timing constraints. 
The automated approach is **SLOW**, but can often find a better solution than a human.
Automated system **STOPS **once constraints are met!
        - **Timing Analysis**
            - What does **Timing analysis find** and what needs to be **input**?→given the **physical netlist** and a **detailed physical model** - it gets the** longest combinational path**. 
This determines the **max safe frequency**. Place & Route is critical!
This process ensures the digital time abstractions are valid.
Timing Analysis is PASS OR FAIL!!!
            - What is the **main limitation of the Timing Analysis**?→It tells you if the **clock speed you give it is safe**, it **doesn't **tell you what the max clock speed should be. If it finds the speed to be safe - you **can then rerun place and route** with a higher clock speed.
            - What is the **main critical path**?→The longest path in the circuit.
        - **Simulation**
            - **Model inherently parallel circuits**
            - What is **discrete event simulation**?→A method to **improve simulation speed** using the fact that only a small proportion of gates are active at a time active - so independent events are simulated separately.
            - What are the benefits and downsides of a **high-level simulation of Verilog** to simulate your system?  ↓ 
                - **Benefits **- no place & route or Synthesis required so can be **done quickly** during programming. 
                - **Downsides **- no timing delay from gates or wires so inaccurate -  _Semantic understanding of sim may vary from the synthesis tool!_  
            - What is the **benefit and downside** of **Gate-level simulation**?→Post synthesis and place & route so **accurate **- if a **bug is found, we have to redo everything** so using only this would be too slow.
        - **Structure of a FPGA**
            - What are FPGAs made up of→Many reconfigurable components with wires going between components in a grid pattern. The components could be Look up tables, SRAM, ALUs, Digital Signal Processing blocks ETC.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/X1s98mFwX2cqCgx77_C9QzPyQotGBgdwML3Z38_6WbPlXJYVFENn4GRyaX0BjT5uu0BJ16A-113f73PVjajpIm9QYdZUKF3VDlOYbMfqp9drn3yAoUjVJiedcskUmmgI.png) 
        - **Structure of an ASIC**
            - What is an ASIC→And ASIC is an application specific Integrated Circuit. It is specifically designed for it's purpose and thus is very expensive.
            - Why would you use ASIC over FPGA and vice versa→ASICs have the potential to be much faster. But ASICs have a much higher one-off-cost, which can only be recouped after selling thousands of boards - FPGA if selling only a few.
    - **Synchronisation and Metastability**
        - What's the **problem **with **external input** for simulations?→They break digital abstractions, input can occur in-between clock edges - violates setup and hold times. 
Makes simulation much harder.
Can cause **metastability**! 
        - What is **metastability and how does it occur**?→When the voltage stored in a flip flop is between the threshhold of a 0 or a 1.
It occurs when the input to the flip flop changes during it's setup or hold time, and the flip flop captures the value of the input as it's changing.
    - 
-  _**Lecture 3:**_   7 great ideas
    - **Designing for Moore's law**
        - Describe Microsoft's **Tick Tock model**→A** new design** would be **created on the current silicon **node (**Performance through architecture**), then after design would be ported to the newest silicon technology node (Perf through better silicon)
        - How has design shifted→Nowadays focus is on parallel design, using more transistors rather than assuming performance will increase hugely. 
    - **Levels of Abstraction**
        - High-level > Assembly > hardware representation
        - Give two benefits of High-level languages→Closer to problem design. Productivity and Portability!
    - **Defining Performance**
        - Give three metrics for rating CPUs→Clock Speed, chip area, power use.
        - **Measuring Execution Time** 
            - What does Total-response time include and what does it determine?→Processing, I/O, OS overhead, idle time. Determines system performance.
            - What does CPU time include→Time spent **processing a job**. So no I/O time is included. Different programs are affected differently by this.
            - The equation for CPU time is→$$\text{CPU TIME} = \text{clock cycles} \times \text{clock cycle time} = \frac{ \text{clock cycles}}{ \text{clock freq}}$$ 
            - What are the two main factors affecting the speed of a CPU command→Clock cycles vs clock frequency. TRADEOFF !
            - What is CPI, and how can it be used to find CPU time?→Clocks Per Instruction, clock cycles per instruction bro. $$\text{CPU TIME} = \frac{ \text{CPI} \times \text{Instruction Count}}{ \text{clock freq}}$$ 
            - What decides the instruction count and what decides the average cycles per instruction?→Instruction count decided by Compiler, ISA and the program. The average cycles per instruction decided by CPU hardware. 
            - Computer A: Cycle Time = 250ps (4 GHz), CPI = 2.0 
Computer B: Cycle Time = 500ps (2 GHz), CPI = 1.2  
Which faster and by how much? 4/2 = 2 - 
2/1.2 = 1.66
The first is faster - 1.2 times faster
    - **Make the Common case fast**
        - What is Amdahl's law and when is it relevant?→the law acts on **sequential programs** and is ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/pS5PMlfDvIWly9ASCfp-wvg0l1aGEp9dCVaDSvnGv5jP3-YS4CX9jR9Z--1FH2r7v7Y45S55jLSbs2hqKEOlDi0DokzNn4bMQDloEFB0GTS2zhgSMWW2M1yOUn01iPM4.png) or in another way:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4fE0uNtkoLgGTJ2F7PzA05nPdm7XV_eCCZUZCsoopuyxkhk2t4F0lnF6ExfOieefF-57npbbE7HvqwnBzVYr9ia4aw4f5pMGt3CLWlnWqDHU3TnoMXB67zP0qW0yaf9U.png) 
        - What does Amdahl's law imply?→If a command is used very rarely, it's not as important to optimize that as optimizing a more commonly used feature. E.g. if integer division is used 1% of the time and we make it 9 times faster - the overall speedup is 0.9%
    - **Parallelism**  
        - Instruction level parallelism is→parallelism achieved by executing multiple instructions in the same clock cycle.
        - Thread level parallelism is→having sequential threads on multiple cores.
        - Data level parallelism is→Vector processing. Instructions act on >1 data item. Think numpy Bratan
    - **Pipelining**
        - What is Pipelining?→A production line for executing instructions, where at each cycle multiple instructions are having a specific operation computed. While on instr being executed another is being decoded
        - What are the main five sections of pipelining? ↓ 
            1. Fetch
            2. Decode & Fetch registers
            3. Execute Instruction (alu)
            4. Memory Access
            5. Writeback result to register file
    - **Prediction**
        - What is prediction & what is it used for→Predicting what might happen next to make the pipeline and control flow more efficient
        - What is Control flow prediction→Predicting what instruction will be executed next & predicting the result of conditional branches
        - What is Data-value prediction→predicting that a value will not change or that 2 pointers don't alias to the same address.
        - What is Data-access pattern prediction→Ensure data needed is close for low-latency access. Predict stride of array access. Takes advantage of spatial and temporal statistical properties of data access.
    - **Memory Hierarchy** 
        - What are memory hierarchies and why do we need them?→A hierarchies of caches, so if data isn't in one it's likely in another fast access cache. Needed because DRAM takes >300 cycles. 
    - **Dependability via Redundancy**
        - Give some examples of dependability via redundancy→RAID: Redundant array of inexpensive disks. Bit error detection & correction. Larger transistors used in ALU than memory, less likely to fail!
    - 
-  _**Lecture 4:**_   RISC
    - What is an ISA?→An Instruction Set Architecture, it comprises the primitive operations of the CPU.
    - **RISC Philosophy**
        - How does RISC make the common case fast?→Smaller, highly optimized instruction set. As opposed to RISC which gives a rich tapestry of commands for an assembly programmer to use - RISC leans towards compiled languages where this is less relevant.
        - What is Orthogonal Instruction set design→An instruction set where instructions have the same format and all registers and addressing modes can be used interchangeably - the choices of op code, register, and addressing mode are mutually independent (loosely speaking, the choices are "orthogonal"). This contrasts with some early Intel microprocessors where only certain registers could be used by certain instructions.  
        - How does RISC have an orthogonal ISD?→All registers are general purpose. All arithmetic instructions use the same operands  
        - How does RISC have "Simple Instruction Decode"→All instructions are fixed length 32 bits (with an option for compressed 16 bits). As opposed to intel with instructions being possibly multiple data lines - resulting in more time spent decoding.
    - Why are ISA's important?  ↓ 
        - Large cost to port code to a different ISA
        - Large cost to recompile supposedly ISA independent parts of stack
        - Might not have the code, if using closed source - can lose the code if corruption occurs
    - Why aren't ISA's important ↓ 
        - Most of the cost of developing a new ISA is software dev cost
        - Most of the speed of a system is independent of the ISA - Algo, code, compiler etc. more important
    - **RISC OpCode details**  ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ewaZ8u8KVX8O3PE6jke-UOqLxj5YC0Pq72stOigK-avZZUg1XlEoSCfWn-jDmp2SDv2WdYHTkbS5j5b3jr2r0Z5B8-FI02SlOHBCSEjOheajUvQU0ZiRuIpIMMxHhsgH.png) 
        - What does x0-x32→x0 holds zero - x1-x32 are integer registers
        - What is sign extension?→Increasing the size of a binary value by adding bits. Note that negative values will have to have 1's added to the most significant side while positive values will have zeroes.
        - What are rs1, rs2 and rd?→rs1 & rs2 store the register addresses (source registers) of the arguments to the operation, while rd is the destination register.
        - What would the assembly code for x3=x2+x1 be?→add x3, x2, x1. Result first, operands next.
        - What does JAL do?→The jump and link command takes a register destination and an immediate - it stores the PC+4 in the register destination (where to return to after completion) and then jumps to the part of the code specified in the immediate. 
        - How do you return from a JAL call?→JALR (jump and link register) saves the return address to a register, and takes an **indirect address **(from a register) to jump back to. It also takes an offset to add to that indirect address. So: JALR zero, ar, 0 - we use zero because we dont care about the return address, ar is the address we set in the JAL and 0 is the offset.
    - **RISC-V Calling Conventions**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dlHtv1a4j_El6lpUtfcsD0aspQ5hCJsdmI4N_4ImNVRycespgIBKGq7Xo284Qx9v1IJN54Oy1z1izp2soicQ5Xm007OClnTIckuqzbeGz4_KAetsYphI9M97c5s3kAI9.png) 
-  _**Lecture 5:**_   RISC commands in more detail
    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tc63rQlPnsgzhr7HGAUaXHOBCK-_v5DG9Z9STTjCB01EaJPE7HJCqtIMl94zBKnv_m-l4X-DfZidOEzUe89SMiNLMowGCKP2lRVMCVlzWW91PRtdoLdAOEkCfKIVFLgh.png) 
    - Instruction function encoded in the {{opcode, funct3 and funct7}} fields (where  present). So there can be a large number of R-type instructions but few U-type, etc. Source (rs1, rs2) and destination (rd) registers are always in {{the same place}}. Immediates formed in {{various ways}} 
    - **Decoding immediates**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BmG5FfWL4T38FbaDw7mA_ZWjINDNHV5fm2P-FjhMYKGey6YUcSP2Bk92o4zQMxpFzKSd8Rv8VzR2jnoFPNBqHWOAfW3NCDJVXJJrkWHNDNQ0aobKwuIX0oknkdxd4Brs.png) 
        - inst[31] means we take the first bit and copy it through sign extension
    - **Different types of instructions**
        - R-Type instructions are for→register to register arithmetic instructions
        - I-Type instructions are for→arithmetic instructions where one operand is an immediate
        - S-Type instructions are for→Store instructions. They store values from registers to memory. 
        - B-Type instructions are for→Branch instructions
        - U-Type instructions are for→commands with large immediates
        - J-Type instructions are for→jumping to functions
    - **R-Type instructions**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bAx5CPGovBiurdeVjtQdaiBLhbVr9GNP-lVrlXHyQQTypMdCoM3Cz1D-Nt9WOtZ-ttm8cgA2-TM_Sffo47k1W1WL91pRve3GK5ChYl0e5QxXtzYBg3_jQzf530EOfg0Y.png) 
        - R-type instructions have many operations under the same {{opcode}}, with funct3 and funct7 specifying the {{function}} 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/SjqaajqS06UDROmY7ESbUP-YmmPaPwcIln1Rhqxw5qCT-8mnaZ81A_NSQ408mgM3stCEvgfBRl9g3XIjmIi-4iIT96KeA-476uLB8FSAOsP8h2wib89Mn5ZtLeVxLoRx.png) 
    - **I-type instructions**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/PPCj3xbCKcXdLnl58yGqP-MMZTzZwcb5iplYXCuLa5fOFhLFhEOL_W_EDCUg654SC_xC7oI_fgMgRRlXf8Y2JNd6AQwM3k6DubQnUiswZW_EKke-o3VQAg3MYIjobrDb.png) 
        - I-type instructions can perform {{arithmetic and stores}}, note there is no {{func7 }}so far {{fewer functions}} can exist than in the R-type instruction. The immediate for I-type instructions get's {{sign-extended}} from 12 bits. Can perform LW, LB and LH which {{load a word, byte or half-word into a register}}.
        - How would I store 1 into register x1 using assembly?→addi x1, x0, 1
    - **S-type instructions** ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TE1aJoMV427ggNZe-uViZSjoqyIUXwbQ5jIpr5tmQNisJ9u59yV-8CD_Zs8AIZCaYQcv9Tc5Z0s1kgf3pqbZ5xdIed-lSEXaH7xxx1FEIPrEhjkytLFZDmqSWp-SPZdy.png) 
        - What would the assembly command be for storing a word and what does it logically compute?→SW x1, x0(0) - this logically compute memory[ rf[x0] + imm ] = rf[x1]
        - Why do store instructions have their immediates separated? ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_HSqr1Ba3T2KirPQGDeu3vMs52C-j_MmI5n0Q0dsBqHA6vYI-qDrgMoswNqqxfV0m1G1HiCuJfccC3oyPi9fFt9ikm6H7WwX3UGT2pn5hc0UrTaSgGYNLrbcHzuPVxjc.png)→because in RISC, rd, rs1 and rs2 are always in the same place. And as S-type instructions have no return address - that an immediate can be placed there. The two immediates are combined by hardware to form a single immediate/.
    - **B-type instructions** ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/VTcfLxAEYEyBbo8son0fr_tOGMla-i_bidBSNuAHX3ykCNhUytnIyihpQgtOI_OqO-raXVXgKkZBGffWpgdI1p2879yyK3_bPTTjJCXE3idaBtk6EPyoaXpA1pe154NI.png) 
        - How would I branch 10 instructions forward?→BEQ x0, x0, 40
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/i_avbOSjziwNqd4dXHR884uyp3a3tJU6AZO2AclBvk49UzBQ_KpLCucp7gAB0Wg1-VGXNxKISW-vrXA50PJ_8Cqkq95JRbmkX5M3hDOlonJvCbHVdcxT8bELqsU3qWSr.png) 
    - **J-type and I-type jump instructions** 
        - What is ra?→ra is commonly known as x1 under the calling conventions. It's where you store the address to return to in a JAL
    - **U-type instructions**  ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/RkOVYxsgJP8HBaZ7fuOCh6668EAuEBzUfm2z2ZJn_VFjuQ26tbEoINJQqa3zk-h0MFTsHJDuTtVfsKQQxtoEg1EeqhYlxWjrUAkVC_539nCzUFYLjSuTx3VIjHLYm5b0.png) 
        - What do LUI and AUIPC compute?→LUI stores the 20 bit sign extended immediate to a register and AUIPC adds the upper immediate to the pc
    - **Pseudo Assembler instructions**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xoEKZ0lWldIRDt_AVMJM3jIYdPfLPKBu-azEObXEGdnLfhheN9M76im53a6Ey-bKgbNlT69u5za0MIsrshzOKqkoC8aSn6PzCdCIOWJk1X0dgBMqV4qzJlsQYH64lADA.png) 
        - What are Pseudo-Assembler instructions, how do they work and finally name 2.→Human readable assembler instructions. The risk 5 assembler converts them to correct commands. CALL (goes to JAL ra, +4) and RET (goes to JALR zero, ra, 0).
    - **Decoding Instructions**
        - What three things need to be done to **decode** an instruction?→First we determine the class of instruction via the opcode. 
Then we fetch rs1 and rs2 (we always do this and discard them if we don't need them. 
Finally, we extract the immediates.
    - **Execute** 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/yGn0mss-e6x51YxjAzHg5K1NeS0DOUKOesIQIik-q-mfMW7mIxNbVf1GodDTctHE9TYy3v4ifY8kEmUbNk7n5Ct8QlXjZ3OJf5f2RfaVjTdIkDA6d7TQlRm-6vc7ZImC.png) 
Describe the steps of executing using the ALU→The Operands are fed into the ALU. The function code (or ALU opcode) is also supplied. 
Then the result together with a status is outputted. The status is things live overflow, negative result, zero etc.
    - **Branch** 
        - Branches often {{occur in parallel }}with decode and execute stages.
    - **ISA-Level Simulator**
        - What is an ISA-level simulator, and what are they useful for?→ISA-level simulators simulate assembly commands. They have a method for bringing code into memory and then they simulate the fetch, decode, execute etc stages. They are useful for **bringing up software while hardware is being developed.** 
    - **Formal model of ISA** 
        - What is a formal model of an ISA and why is it useful→A formal model is a unambiguous description of the ISA not written in plain English. They can be executable and used to generate a simulator.
    - **Tandem Verification**
        - What is RVFI?→RiscV Formal Interface. A standardised method to report completed commands
        - What is tandem verification and why do you need it?→Tandem verification uses a golden formal model and a simulation, runs the same code on them and compares the RVFI streams - if they are the same the simulator is correct. The simulator could diverge due to Interrupts or different I/O behaviour - this checks for that.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hZWUFJ-Wq0kuutWiqA5tJjvgPVXwUzB52sW4ozeCLFxNGpYhaayWsjriNQIcEZMVD2KFd6WHPrP4Ou28tpqlMTJzCwQFWDVyPJFqJdy9XxXQNHpKH9QxXU2uqywgmGtu.png) 
    - 
-  _**Lecture 6:**_   Processor Pipelines
    - **CPU overview focusing on Data Path**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/m0bCdoTVaC8poTqwCHEPoT4ARZPFC98hoo--bRIRgtV8C0skvgvC0GiGnS4EUfVS1Mi7DnJgLA0qtt7eAaK8O6YBTUOarKPA9ddJw2JgHD-zX0L2dG6VVIYGjPe6o0Mx.png) 
    - **Control logic**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Z7On8YIWAkJLhGon-BLEe_UNN--ulADC9rXUEHqbvlSyJ80BIpGYA95kEy9U3u-8I4s-9FkvGiVqvMAWixczzkCb35r58vaa0ZrEt-cNSTB7J4YvB1syXbfT2TV3PYCR.png) 
    - **Instruction Fetch**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TBlFF1M7OqoZdVYjWpmgR8l_WA5NzkUOK_nlqFjtrCUlHBLnLDxl99w6SGitCwffMTOVrTi-6BnkiGHygVu1Ic4NafK6mQmwK3IaWj4R1cbPIDTkKTk25yOyM3xbHnCA.png) 
        - What 4 numbers are (2 fed into each multiplexer) inputted to the branch unit, 2 of which are added together after multiplexers are used (hint 2 are obvious)→The first multiplexer is fed the current PC AND rf[ra] for a JALR instruction. The second multiplexer gets a constant 4 (progress to the next word since 4 byte instr) AND an immediate for branch instructions. 
        - What decides the output of the multiplexers in the branch unit?→the decoded branch type and the ALU flags (sign,zero consider BEQ x2, x3). 
    - **R-type instruction**
        - What 3 steps are performed in an R-type instruction? ↓ 
            - Read the two register operands rf[rs1] & rf[rs2]
            - Compute arithmetic or logical command
            - Writeback to register file
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/9J2wlztwAIMGv7KSwHlM9Nw0HqYgA8zhBVbQlcrxGaguX7MKFUiKVtbXNg2AMvXXg7ymWWEfNH6v7n6cbhPYhGCEkkCdrwswiw3wpxsnjgCGHK8Azf4sdd9TcmhfYR1_.png) 
    - **I-type instructions**
        - What 3 steps are performed in an I-type instruction? ↓ 
            - Read the two register operands rf[rs1] & rf[rs2] even though rs2 isn't present
            - Decode the immediate 
            - Compute arithmetic or logical command
            - Writeback to register file
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zpv5W9yPhFOUAvwivFdGmThG_xsEa4tQa3zDBQyjnLXiLcKOI5P149xZLhJj78Vt4CZs9v6S0BJdJ7Gjl4wX9p3fSnGMRCI0IeuuRZU-h6kqpJbG7MFq55zS5fIsdoJp.png)  
    - **Load/Store instructions**
        - What 3 steps are performed in an I-type instruction? ↓ 
            - Read the two register operands rf[rs1] & rf[rs2] 
            - Decode the immediate and calculate operand2 + immediate
            - Store: Store the value rf[rs1] in operand2 + immediate in memory
            - Load: Load the value operand2+immediate into rs1 in the register file
            - Writeback to register file
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/oXu9xazpFnLrzldxhKKqNe3_-55dVug7ha9P4ijAEo0RCXeXspWyFsrpekI2Q1V3ROoWfTXqUUCXG8FgNsLeweKp6qfapDnaVZTe6gwDfagKKzhM-9WTnXCCvhW1u2CB.png)  
    - **Branch Instructions**
        - What are the steps in completing a branch instruction ↓ 
            - Decode the two operands
            - Then get the ALU subtraction flags - zero/sign
            - Then decode the immediate (and sign extend it) and shift it left one place. The immediate has already been shifted right to **save space**, as the PC is a multiple of 4 we can never have odd access! Also the **smallest instruction is compressed 16 bits, so we only need 2-byte access.**  
            - Finally add the result to the PC
    - **All elements together**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/YcIYtf0I1Ws1t55sZYKl7ibRLRavvi47e6cTFBzq8yDA_uc3nhCLReoGnzG0JUbZN1HMx1FXjXFpNA3oXjP9isCqQsqvYfEqGNGLC_CUrW33C68aexLMLMAPPnM54qPv.png) 
    - **Control signals for R-type instructions**  
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/iwmCEdAGMK7RzhbW_eAr5PKDPNXhBxH0oGUAH0W9mXOyVc7QG51ZIvEtzXdChxRoa2uV1NnT6fjmXADdRSC0K35eYJkZAOk2-d_VXvf83RIfYVLjxGyGD_hLYTCCQ4Gt.png) 
        - What 6 things does the decode unit supply for R-type instructions?(good luck) ↓ 
            - The branch type to the branch unit
            - rs1,rs2 and rd to the register file 
            - write-enable to the register file
            - Selects operand 2 to be used in the ALU
            - The ALU opcode
            - And the result source from the ALU not data memory
    - **Control signals for I-type instructions**  
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/iwmCEdAGMK7RzhbW_eAr5PKDPNXhBxH0oGUAH0W9mXOyVc7QG51ZIvEtzXdChxRoa2uV1NnT6fjmXADdRSC0K35eYJkZAOk2-d_VXvf83RIfYVLjxGyGD_hLYTCCQ4Gt.png)  
        - What does the decode unit supply for arithmetic I-type instructions?(good luck)→Same as R-Type but the immediate is selected to be input to the ALU
        - What does the decode unit supply for LOAD I-type instructions? ↓ 
            - Same as R-type but the immediate is selected to be fed into the ALU
            - The data memory is set to read mode
            - The result source is set to come from the data memory
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/2u35Z0wCP6DTmyNp1BlsZVQlhEiYLjs6ure8e9CQr3K6TibSQkwAl_aZ7K2TrVrecXcmGmpuHFoCWxCo7O3keJ1IUzUz1IN2rkLp-7RM2BvI4d7yoauxw1p3eJsouv0e.png) 
    - **Control signals for S-type instructions** 
        - What does the decode unit supply for S-type STORE instructions? ↓ 
            - Same as I-type LOAD instructions but the memory is set to store not load.
            - And the register file is set to **not **write-back data. This means we don't care about the writeback result source
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/WZ7k2oKk5w9UjNKILYeCLuXTte8QBMh28Xp30s3kImIpgvc6BA00fhOiTN_G6OybVMvgiRwaORN0EqPDalOHRXFzfquDWtm5YduDAJxmKVI7eWcziGrot7z6yZR7fhcL.png) 
    - **Control signals for B-type instructions** 
        - What does the decode unit supply for B-type instructions? ↓ 
            - The branch unit is set to a conditional branch 
            - Write-Enable on the register file is set to false 
            - The operand 2 is selected to input to the ALU
            - The ALU opcode is set
            - The ALU zero/sign is fed into the branch unit
            - We don't care about the rest
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/txL8jW5jxdFtRhaQ7DT8mvS76ZHCOZ7-qiIInEE5duJwGwWIZfPBiMuUHKayp5jEGIT65WS_LcsShbpbUAJlStWOIsQxsVaMRRjAcE2vDIfrhw6iWxgW7CELY1dzVdU2.png) 
    - What performance issues does the load instruction have and how can we improve it?→It is the critical path - the instruction memory ⇒ register file ⇒ ALU ⇒ data memory ⇒ register file. This means the common case is slow ); - performance can be improved via pipelining
    - **Pipeline performance**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/-SLiRpHjwKfayFDlfQLPPPk4pKIyfh8gRRqe6wSuQlxCPDzhh--q2EKELoTHBuRg7cKATxlLFlqfzRW8BCpNiJwEn9UmyzQRndxw330W5jjIBDMG6QC9nJQAZeh6r2_Q.png) 
    - **RISC-V 5 stage pipeline**
        - Describe the 5 stages of the RISC-V pipeline ↓ 
            1. IF: Instruction Fetch from memory 
            2. ID: Instruction decode and register fetch
            3. EX: Execute command or calculate address
            4. MEM: fetch data from memory
            5. WB: Writeback to the register file
    - **In what 3 ways is RISC-V designed for pipelining?** ↓ 
        1. All instructions 32 bits, so you can fetch them in 1 cycle
        2. Few and regular instruction formats. Means we can decode instructions and fetch operands in the same step 
        3. Load/Store addressing (Only Load/Store commands can access memory and because the memory calculations are so simple) means we can calculate the address in step 3 and access memory in step 4
    - **Hazards**
        - What are **Hazards** and describe the three main types ↓ 
            - **Hazards **are **situations **that **prevent starting the next instruction in the next cycle** 
            - **Structural Hazard**: A required resource is busy
            - **Control Hazard**: An instruction decision depends on the result of the previous instruction
            - **Data Hazard**: Need to wait for previous instruction to complete memory read/write
        - Why do **pipelined data paths** require **separate instruction/data memories**?→Because otherwise we would have a structural hazard whenever memory was accessed - Instruction fetch would stall for a cycle and we'd have a **pipeline bubble**  
        - **Give an example Data hazard, provide the solution and a situation where the solution fails**   ↓ 
            - An example is ADD x1, x1, x2. MULT x1, x1, x1. 
            - The solution is **Forwarding, **where we use the result from the ALU right after it's computed and don't wait for memory writeback! 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ujv6s6fkOdGv8O0HH9hBI6c2nyLuNxY9BzAkoWU7YIPq5IHy-PygYiVuA4M3wdj8HuK_P3efuoTFkoxFAFRzpA7W_4hT1H25xxZTWFGvfj13EG0c4Br91PNlT7imuXQb.png) 
            - This requires a connection between the ALU output and the ALU input.
            - **HOWEVER, this fails in a Load-use data hazard.** I.e. if we're loading the value from memory, we cant just grab from the ALU will have at least 1 bubble - we fetch from memory before writeback.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bYbPy4_rUFIC50N_CLivRiyE1ui0AQcIUAMU-lC0R3XzgYQ0OBPH6ZgFjob1XG7_gFfdMquAsa1-N45_FWqQFr3Fh_yq3eP7JFRSmp5TCxmkhMyeencKK0me1bqy-RcA.png) 
        - How can the **programmer reduce stalls due to data hazards and what is the technique called**?→Place loads more than 1 instruction before they're used, can group all loads at the beginning of the program
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zv_5EtCmyOCjFPCfkMbIM-yIIPfKgrHcp9PINQHqEfDb-KidvTxS8FAKPA5uQVishZ_X6p_lI2IJz-0tywUXm59k1srFJ-Yt5abyWwifpe_M194O5mROFMGU-zzvxvfJ.png) 
This is called **Load hoisting. **Often compilers will do it automagically 
        - What **two types of branches** cause **control hazards** and **which is worse**?→**Unconditional branches** and **conditional branches**. Conditional branches are worse because you **only know which instruction to fetch after the execute phase**. 
Although, **unconditional branches will still cause 1 bubble** as they must be decoded.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Yd-CxNKvoeb470jvIjb_jHIHJ-XbG0UJIppFBMiy8zYi1zSjpgbVlijV_DDVPr6lFMUFK0AiONDRgNp4rS77DMYElSY0RnsdwnYpll7bSE862I2ARQzAPDGaK0-qO2qK.png) 
    - **Branch Prediction**
        - Why is branch prediction necessary→In larger pipelines, can't quickly determine the branch to fetch - stall time becomes unmanageable.
        - Describe the 3 (possible) stages of branch prediction ↓ 
            - Predict a branch
            - Stall if prediction wrong
            - If prediction wrong, we need to clean up state and reverse our changes to preserve the sequential execution model.
        - What are Static and Dynamic branch prediction? ↓ 
            - Static branch prediction is based on common branch behaviour. For loop / if-statement branching, always take the backwards branch not the forwards one (in a loop from 1 to 100, only 1 time in the 100 do you branch forwards).
            - Dynamic branch prediction hardware stores branch history and assumes that the trend will continue.  
    - 
-  _**Lecture 7:**_   More Processor Pipelines
    - **Pipeline Latches:**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/RrfZllD94G3n1d2zwt8iTAL2FFD6mLiN4zd7quhZJySfWgiTQ1r0WJHNU8nyDvYe3ZjFujTJPGHQstQyhSQAHH0mii0TJRepAVodkN6KHWMruK_kMi3myRKgta-sJkBU.png) 
        - The black bars are arrays of D-type flip flops
    - What problem does Pipelining cause for write-back and what's the solution?→The rd input to the register file will likely have changed since the command was executed: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BUZ_SkG_i6YcfxoNZuq7_Pd3vaPscCHpP2XnEjClyqk4z_sYCiVj3rYDlnr_nIVEm3YuC8lqjcuRYNGlKGs2RunPheVkYJvlq7nDcN2ncIfgPCLwKHWscOY9xXmvj5Zv.png) 
We have to propagate the control information from the original instruction, along the data path. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ZV27jhdv4eojFzXT7zUt3m4wznjbHSHINQU_IejitACgad8fW0JKFImlB2Hfqvy1zV0TM4Wjg9wUvRcMghvFCkUqmhTIzO9iJjJH6HKyEr9IXYs-H110dWum562rFXLJ.png) 
    - **Forwarding **
        - How do we forward results from a load?→Forward the writeback directly to execute. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/PFX-8fd8jFUhQVKjtqCg5Qe_4lFthMnkiAfqB1XnO0gJlwIr0dl-1St-GPpq1oCeQc8tcueJI2icOmrOY1EPrSzfD0_qIqmK4BgsZF1I-U3zkDz9ymEINeHAg9C-TZPr.png) 
        - **ALU forwarding**  
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/-CKrzKVRg6UgyhYJeXhCdY16wNBmtjByW3wktzEYcbA2Nel2cyyjcZ0QjH49vpP6waV71wrxlqVEU729dtiHHaiW8HdkxpPcYZlbK0qbcxXQGA7smPWJzuHs57YHCydS.png) 
        - What if we have instructions A, B and C - and both B and C need the ALU result from A? ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/0tAQ2Y7ukTGvAaDDxSRvo37lEOePkRCIgsVgAfx42O_Z05LJh9ZelL98i7gkkSDixx8xKoW22cqKBommKzeDA710pIROY6inEp36XEBsWYRZnxd7Qk7mhkT4vOpB3TXx.png)  Remember, memory access is before write-back.→While B can get the result by ALU Forwarding, we need to establish a second forwarding line for C. 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/pdDUbfEJgusSq8hjqBEHz2Md6Lt0iFWM9wBoweAaIuA9dJApPEC6c8StLUUUMY21R5nFqpaWnSqyRiV7g7nSxSThTVsZkDNWgqwzEGmDRZes1m09fuXudXYLsS0gkJFq.png)
For arithmetic operations, 2 forwarding paths remove **all data hazards** in the pipeline. 
    - In a large pipeline, many** erroneous instructions may be fetched in error**, and they may affect the sequential execution model. **What are 2 solutions** to this?→We must not allow erroneous instructions to complete their computation. 
We can either flush the instructions from the pipeline (mark them as invalid) 
Or we can add a epoch number (colour) to the pipeline, and when we find the instructions to be invalid increase the epoch number - the instructions will then be ignored.
    - What is a **branch prediction buffer** or **branch history table **and how do you use it? ↓ 
        - This stores whether or not branches were taken indexed by the location of the command

        - To use it you first check your current branch command in the table, and assume the same branch will be taken
        - If not, flush the pipeline and flip the prediction
    - What is the **branch target buffer?**→This is a map of addresses branches have branched to indexed by the Program Counter - this means you don't have to wait for the ID & EX stages to check if a command has failed.
    - **Handling Exceptions**  
        - What are the 3 basic steps to handling exceptions ↓ 
            1. Save PC of offending instruction 
            2. Save cause of exception - 32 bit 
            3. Jump to handler at predefined register
        - What's the difference between Precise/restartable exceptions and Imprecise exceptions? ↓ 
            - Precise/restartable exceptions are hard to implement. They entail flushing the pipeline and the instruction then jumping to the handler, then after the handler finishes return to the offending instructions.
            - Imprecise exceptions simply flush pipeline without recovering it - Illegal instructions **need this** 
    - **Instruction-level-Parallelism**
        - Give 1 benefit & 1 drawback of a deeper pipeline ↓ 
            - Benefit: More stages means less work per stage, which means a higher clock speed can be reached 
            - Downside: This also means more hazards and bubbles
        - What is Multiple issue Pipelining, why is it not more prevalent?→Having more than one pipelines and all of them operate in tandem. But instruction dependencies make this very difficult in practise
    - **Multiple Issue**
        - What is Static multiple issue and how is it made possible?→Compiler groups instructions to be issued together. The compiler detects and avoids hazards
        - What is dynamic multiple issue and how is it made possible→The CPU examines the instructions stream and chooses which to execute - compiler can help but mostly the CPU detects and avoids hazards at runtime
-  _**Lecture 8:**_   Memory Hierarchy - ^^ _UNFINISHED_ ^^ 
    - **Simplified Hierarchy** 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/KMlCQdiT80SX9-YDPVhi43hFkqREInuvawwt35m0RWISHmhoBvx-GN05A8P6YbHWOiu3EG5SJs2zL__r3QpUNFrs0dTlsI5b0UDUjooKhA07DSVlEXB0W8afVN16hh4k.png) 
    - **Memory technology ** 
-  _**Lecture 9:**_   OS Support
    - **Virtual Memory**
        - Describe what virtual memory is, and give three benefits of it ↓ 
            - Virtual memory is the OS & the CPU giving processes the illusion they have their own address space and storage. This is done using pages (4 KiB) or superpages (4MiB)
            - Aids memory allocation
            - Improves memory security (can check that a process can access a piece of memory during translation)
            - Allows lesser used pages to be moved to HDD - giving the illusion of having more storage that reality. 
        - What error results from trying to access a piece of memory not in your page?→A page fault!
        - **Address Translation**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Mll1jb30EmTDbe4jOm2FimwPS13y5-P0bJEOKlTXzXJgp16eRKfQUSwnG_gLsocTI8OFx323HyUXKJB2v7QYdg6N_Gae6GzRlQRoze4phFyCOmcr_zSPEFI2EK8KetR8.png) 
            - What changes in a 64 bit address after translation→First note that in 64 bit addresses (as it currently stands) only the first 48 bits are currently used - the rest is sign-extension. So in translation the first 12 bits is the page offset that stays constant - the next 28 bits are the translated physical page number:
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/StpnR4tGLibsuNTvjL5iyWlZ5f7L8tAPG-1XZisUixnPB4gUUN-T6QMUDL9qTjdla3ig9GBcCEGFELaabQyvbhgHMRKBIF-tnIa37hmk8cXORs-MOupIHPBvJPWC2HkU.png) 
 _**NOTE: THIS IS IN 64 BIT - MOST OF THE COURSE USES RISC V 32 bit**_  
        - **Page Tables**
            - What is a page table, and what happens if I query it (and how would I even know how to find it in memory)? ↓ 
                - The page table stores the physical addresses of pages, indexed by virtual page numbers.
                - The address of the page table in memory is stored in the page table register in the CPU.
                - If you query with and the page is present, the physical page number will be returned - it also stores certain metadata like referenced or dirty...
                - If the page is not present, it may have the location on disk - whether it does or doesn't, the **Page fault handler** will be invoked. 
            - What steps must the Page Fault Handler take to get a Page Table on Disk? ↓ 
                - First choose a page table to remove, if it's dirty it must be stored on disk 
                - Then load the desire page from disk and into memory - and update the page table!
                - Then restart from the offending instruction
            - Describe what it means for the page table to be **fully associative**, and give the replacement policy in use ↓ 
                - Fully associative means any physical address can go into any virtual address spot - this is possible because we're using a map **not** calculating the virtual address from the physical.
This means we will never have conflicts for a single spot in the page table. 
                - The policy is Least Recently Used. 
        - **Translation Look-Aside Buffer (TLB)**
            - What is the TLB→The TLB is a cache of page table entries, this is used because translating normally is low latency - as me first have to access the page table, then get the specific page table entry (on DRAM, slow ); ) 
            - Why are TLBs effective→Page tables have good locality!
            - What happens on a TLB miss and how soon must the miss be detected? ↓ 
                - If the page table is in memory, fetch the page table entry and retry. This can be handled in hardware (complex for large page table hierarchies) or in software (by raising some special exception)
                - If a page is not in memory, normal page fault.
                - The miss **must be** detected before the destination address is overwritten 
        - **Hardware page table walker  **
            - What does the hardware page table walker do?→Searches for a PTE on TLB miss, if it finds it the entry gets put in the TLB - otherwise exception baby.
        - **Page table structure**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3qaWcOMCeWbIG6jLM6Zpq4B9MEQRl9_z0qynqCpwjcK6I85TumTyCxrfArQfMs9Zhox0seP2L8UGtsnQIWr9HIT3wqvKePlsJgFcEzUyb7h6hYkAnEb8jmOLbiyYTcX5.png) 
            - Describe the structure of a RISC V virtual address→32 bits, last 20 are the two sections of the VPN, the first 12 is the page offset
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zholROCQwqqhQ7U5VrZqu3G6B2gID6nb1NOjFI4zptI2xEJtiFtLdkXK-gBe3K0h5DnySO-pYC5e0CWvoNAhJxgWr3etgVvbHEGLVxxQzJ3o2PI7IflOC2_8eyrkEpNh.png) 
            - What are multilevel page tables, and why do we need them?→
    - 
- 
- 
-  _**Lecture 15:**_   CUDA and OpenGL
    - GPU Memory:
        - Different hierarchies of memory, various levels of sharing. Isolation vs sharing for individual threads and warps composed of threads.
        - Why do Modern GPUs also use caches, even though multithreading hides DRAM latency?↔Caches reduce DRAM bandwidth requirements (Would need larger buses).
        - What are the GPU Memory Types ↓ 
            1. Threads allocated private local memory. Stack Frame, spilling registers.
            2. Shared Memory on each multithreaded processor (streaming multiprocessors):
                - Not shared between processors 
                - Dynamically allocated to thread blocks on creation
                - Can be used for communication between threads
            3. Global GPU memory available across GPU, also available to the host/system processor. **This is GDDR VRAM if the GPU has it, else** **external RAM.**
            4. Also constant and texture memories 
        - GPU Memory Locations:
            - Local memory - in external DRAM; Can be large
            - Shared Memory - within each multithreaded processor; high bandwidth
            - Global memory - In external DRAM; can be cached
            - Constant and texture memories - In external DRAM; cached in specialised caches.
            - **How are thread accesses of values different in a GPU to a CPU **→** Accesses by one thread is broadcasted to all other - don't need 32 accesses for a single value.**
        - Example - Kepler Memory:
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/XuzblUh_rrlMLk8o-CPXl4Rw7Hjsp0HIfwgeOevS6YsNjBev9u3lAXwXPQ77Cg8sIS57ijCwg3fcPgtWE5wzKHu-ltUTmoxfomsFz8W1B26CPtf6i4BOuhcvjPl8DIq_.png) 
            - Configurable, can set up a split between amount of shared memory and cache. E.g. 16/48kb split.
            - ECC (Error correction Codes) on registers, caches and DRAM, protect from errors from things like particle strikes.
    - Programming with CUDA:
        - Why use a GPU programming language?↔We can use High-Level languages, make things **portable across GPUS. **To **abstract away from GPU internals.**
        - CUDA widely used and mature.
        - Compute Unified Device Architecture overview: 
            - Its a C like language but allows C++ constructs too. 
            - What does the programmer need to specify about CUDA code?→Programmer identifies the code to run on the CPU and that for the GPU.
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dbmGAZxgLYhjIY9qKOOKtFehp2duKks1M9KvhVIZ8qGP3rH_8j3ZFrfwKvIgEaCBq2jOImcvNFHRsExCVfjqAsUD1uCtrSUpFx1kq6Y0vy2xxCRBsFo7TQ3LxrLETxKf.png) 
        - In CUDA what is the **kernel? **↔A Program or function, designed to be executed in parallel.
        - In CUDA, what is a **thread? **↔A single stream of instructions from a computation kernel
        - In CUDA, what is a **Warp? **↔A group of threads that are executed together
        - In CUDA, what is a **Thread Block? **↔A set of threads (usually a set of warps) that execute the same kernel and can cooperate
        - In CUDA, what is a **Grid? **↔A set of **thread blocks** that execute the same kernel
        - The 128 forms the **THREAD BLOCKS **within the **GRID. **Contained within the Thread blocks are **WARPS**. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/IOpN_f2w7U97udVrPrApTVX3kF50t4vhMTdOHOIfpfFaCbTbe3SpkPBmt4vq47OWje2XY4Uee77ULJh7FJSLx-sIvb4GYv3lSqzlQkdXiGXKo602PG-3Yq9gjV1bNum_.png) 
        - ```csharp
__device__ or __global__ mean on the GPU.
__host__ means on the CPU
``` Must call GPU functions with code dimensions:
        - What does this specify in cuda: ```csharp
func<<<128, 8>>>(params)
```↔These specify the number of blocks within a grid, AND the number of threads within a block. In this case, 8 blocks with 128 threads for each block. Note in CUDA this will result in 128/32 = 4 warps for each block.
        - ```csharp
func<<<dimGrid, dimBlock>>>(params)
In the above case:
func<<<128, 8>>>(params)
``` 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/IV-BieGOCBrUPR1f1WfLxLAxTszfR145eY_YKGy6PUT58Cez6N2otQQygd5YmlzTzqVo6sdf9kkTILbMntewX-mi3FT19NTryACLaUcemLRyXt3Q6gJk81Jk6trgQf3t.png) This is replaced with: 
        - Explain this ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Mge8HfaS1Wte6Kp2rLWLoeKXEMlPkYyTEXjOskuf7-lRgHMPpunbIMoP_g09Dp2D3RyvUfD1ulqyB1crfvIveWJYrFJmm3Fl1Mg6lk0g2yC5mlsHeDOYPVCQUjhG2I_Z.png)→ __Each thread is one iteration of the for loop!__   i<n is used **because we could call it with more threads than needed, as there are 32 threads in a warp.**
        - Called using:
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/fEpPAxd5Adxm1gbu5o48waHRg8Yxt0gtDGWLkfS9yGG8Jv0zZoC4LWtuGndgcOhm9EcJTaqJhJ_hZ7TkS2UpMKYBig7Qu_MvpVUdkKiW8ugEl_TJRrqNhxm61IH2LTMN.png) 
    - **Programming with OpenCL**:
        - What types of systems is OpenCL designed for?↔Many types, including CPUs, GPUs, DSPs, FPGAs, etc
        - **Based around 4 models of Computation** ↓ 
            1. Platform model - Specifies one host and multiple devices
            2. Execution model - Defines how the host interacts with devices
            3. Kernel programming model - Defines how concurrency is mapped
            4. Memory Model - Defines the abstract memory that kernels use
        - **OpenCL Platform Model**:
            - **Give a high level overview of the OpenCL Platform model**→Host & 1+Devices where devices are divided into compute units and then divided into processing elements: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/foy6M1jue01yXLC_9O94FlbNKw1Rz3fHxllaYgi_isUxkQyhHD8T45bMRrfdRiCzZBKBQDkHLITYvoRTRFvdVravQx_dgMKWFf6lLrUAqLVHBVOgQq2J8hTfO3AHKzFF.png)
            - **On your PC, what would the high level parts of the OpenCL Platform model?**↔The Host would be main CPU for your computer, the GPU would be one device containing streaming multiprocessors (Compute unit) and each thread would be a Processing element.
            - How does OpenCL handle multiple platforms on a single system (e.g. Intel and AMD devices)↔Apps use **a rich API to determine devices and platforms and create and run computation.**
            - How does  ```csharp
clGetPlatformIDs(entries, *platforms, *num)
```work?↔Need to call twice, the first call gets the number of platformIds then allocate the memory for the platform array (now you can with the number) and call again to populate the array.
            - Do the same with ```csharp
 clGetDeviceIDs(platform, device_type, ...)
```
        - **OpenCL Execution Model**: 
            - This describes how execution is actually set up.
            - For which we need a context. What is contained within the OpenCL Execution model context? ↓ 
                - An abstract environment for the execution
                - Manages memory objects
                - Keeps track of programs and kernels on each device
                - Manages interaction between the host and devices
            - What are Command queues in OpenCL? ↓ 
                1. Command queues allow the host to communicate with the devices within the OpenCL Execution model
                2. For example data transfer or running a kernel
                3. One queue per device, host sends the commands
            - **What type of queues are used for OpenCL command queues**↔Queues can be in-order or out-of-order, in order = FIFO Queue. Out-of-order, commands can be rearranged for efficiency.
            - **How do we synchronise OpenCL command queues?**↔Barriers used to synchronise queues.
            - Describe Command Dependencies in the OpenCL execution model ↓ 
                1. A given command depends on others. Event objects specify these command dependencies.
                2. Each command has a wait list.
                3. Each command has its own event, to link dependent commands with this
                4. Events contain the state of the command: Queued, running, submitted, ended, ready, complete.![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/g5IxZIxS7kbLZkh4q50OMN6J0KveTEEgfwzVD_yBNJfcMjSDnH5CEJgWa8M4KMFeOlATwdk4J67xdlsd_bLA_53GlGQGpP9J8Pb3z-zz9Ft5R0mIlv-ggcPKyCJbahrV.png) 
            - Kernels is the **code that actually runs on the device.** 
                - Syntactically like a C function, each kernel contains the **body **of a loop. 
                - Kernels express parallelism at a fine granularity - allows efficient mapping to a wide range of hardware.
            - What are work items in OpenCL?↔Work items are the **basic unit of concurrency, **each work item executes one iteration of a loop. Corresponds to a CUDA thread.
            - What is an NDRange? ↓ 
                - Work items are given a index depending on the NDRange, for a 1d problem consider vector addition work item X computes the addition at index X. For a 2d problem, consider matrix multiplication where work-item (x,y) computes a multiplication (x,y). Work group space would also be the same number of dimensions.
                - Usually corresponds to input/output data 
                - Either 1 2 or 3 dims, called an index space.
            - Describe work groups ↓ 
                - Work items within an NDRange are grouped into smaller units called work-groups
                - Share a memory address space AND can synchronise with barriers.
                - **So**  _NDRange like multiprocessor, and work group like warps._ 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/YIcQUGPH3R_-VjyAdj7kTkf8DIabxxt09KamvGHs6zTC4mm1qgG_bR7FaodXWBWygh_LmlhTO6ZLlzLk7TcU74n8x182ThQtHUsOZoQBo6gSPZiTRmFFdY5dSKRl2cgx.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ByZZ8HnD4pWOMhL-gIvdDRe5GmBzERU4KHrrgdtesq-HdvOkuhp6Tll6ruD-BIxUuuGrq9vmfm7ig5BGEXQUwAITQSF9GUTpPxN7AQZ34pHceFFNr_koWHUL3qmflvOZ.png) 
            - Describe the benefits of compiling the kernel at runtime↔Allows for optimisation for a specific device - **otherwise would have to provide binaries for new devices. ** Allows easy development and execution on different systems. **This adds an overhead in startup time.** We start with kernel code as a char array in memory.
        - **OpenCL Memory Model**:
            - **What is the benefit of the OpenCL memory model?**↔Abstracts away differences between different devices, need to be able to map to something physical as vendors map their hardware to this model.
            - Defines what happens to each memory operation, i.e. what values to read and in what order the operations should occur.
            - **What are the 3 Memory objects in Open CL** ↓ 
                1. Buffers - equiv to C arrays
                2. Images - abstract storage that cannot be directly referenced, rather pixels can be selected. Just stores images mate, innit
                3. Pipes - ordered sequences of data as a FIFO
            - Memory is either host or device memory, host memory is **not worried about by openCL. **Device memory is accessible to kernels. 
            - **Describe how memory is structured in the OpenCL memory model?** ↓ 
                - Global memory visible to all work-items.
                - Constant memory visible to all for simultaneous access.
                - Local memory shared between work-items within a work group
                - Private memory only visible to each work-item
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/DyxW5z8yzG_0ws52kJDEee5y0NAr4d8jYSmzFcS94aip5zBnrvJCXtc1SldJS8_PcHcWFkcHnIXFN6E-16fB-ISxGATxacbBHZkXLftjvkdQa2nDWRT2-aOmmh8dhhAX.png) 
            - Running OpenCL code:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5w9hDVmdSIRGs7TDGAtayWCd-e7D4CWxIJ84aSMi1Wo_lFYQUkTL_VltlCzoRG9MuDh0_GjWFi-XqsqOxlKycy2ICDXGGpezzUn8h3M6eqoYPtaMVodyqTzHDEVc4Zb4.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rA3v0z1Eq08duWs10CRgOManH37EqCKMBY-BtWX7cAPLjleoKygO7meQgBbN98k8Q-IJZJkR5dX7VRAeFqH2sIZqOvA3HheT5dDzSaJN8N_2Knaifnp2Zz5ZHsz_5tWr.png) 
            - **Why do people sometimes choose CUDA over OpenCL** ↓ 
                - OpenCL **much more verbose **than CUDA
                - OpenCL gives start-up slowdown as kernel compiled
                - CUDA faster on Nvidia devices, better optimizations
                - Never know the exact commands that will be run with OpenCL, decided at runtime 
            - Platform discovery **and compilation** performed at runtime. **SO you can't actually know what's going to be executed, in terms of machine code.** Allows code to be changed at will depending on the generation of the gpu.
            - **CUDA **only targets NVIDIA's GPUs, so one platform and static compilation to PTX ISA. OpenCL targets much more than that.
            - Intel and ARM can't "retire" commands from their ISA as they require backwards compatibility, however NVIDIA can change by adding or removing instructions. For OpenCL **the ISA is only known at runtime.** 
        - 
    - 
-  _**Lecture 16:**_  Future directions in Computer Architecture
    - Industry Opinions
        - Industry quite conservative, only looking 5 years ahead max. 
        - Energy efficiency is the new fundamental limiter of processor performance, far beyond the number of processors. Miniaturization helping with energy efficiency. Compute very inexpensive.
        - Moore's law slowing, getting down to 7nm. Even if you don't make the transistors smaller over a period, you can improve your process of working with that node. Smaller transistors more expensive, used to be a complete win of smaller and cheaper. 
    - Challenges:
        - Energy efficiency - moral obligation to keep power down.
        - Reliability - keep things working correctly.
        - Performance - how to make things go as fast as required.
        - Security - How to make things go as fast as required
        - Often these things are intertwined
        - Could get to a point where there's a backlash against computer systems, need to get roll out right.
    - Energy-Efficiency Challenge:
        - What change comes with multicore systems→Moving from complex single cores, to multiple simple cores.
        - Dial down clock frequency to save power. 
        - Problem: Neither CPU like or GPU like multicore designs are sufficient to meet speedup and efficiency wanted.
        - Simply adding cores not solution. 
        - Need to fundamentally alter the cores themselves. 500x more energy efficient on ASIC than on general processor.
        - One option to specialise our multicore chips. Heterogenous cores. Problem, locks in to using a specific algorithm. 
        - Often optimizing around software designed for specific hardware. 
        - Google's TPU uses custom ASIC for neural network training - locks yourself into a particular style of machine learning. Could be better solutions designed in the future. 
        - Use reconfigurable FPGAs that can be changed. But can't get clock speed up very high.
    - Performance Challenge:
        - Performance **must **come from parallelism, can we beat Amdahl's law? Research and change in culture takes a long time! Only mid 2000s multicores became mainstream. 
        - Speeding Sequential Code:
            - Temporarily exceed power budget (sprinting) allow some cores to run faster and hotter based on dynamic voltage/frequency scaling. 
        - Processing-In-Memory: Data movement uses energy, some computations can be done in memory such as **Zeroing blocks of memory** don't need CPU to be involved. Lot's of different systems try and zero memory as don't trust other things to do it.  
        - New Memory Technologies:
            - Phase change memory is **non-volatile **but with slower writes than DRAM. 
            - 3D XPoint - SSD caches could be alongside DRAM within the year. Latency of 10s of nanoseconds, slower than DRAM but **far faster than flash.** 
    - Reliability Challenge:
        - Reliability is also becoming a significant issue.
        - Process variation is a concern, doping has some random elements. Meaning some transistors operate slower than others.
        - How to get less variability with transistors?↔Use bigger transistors.
        - Why do failures occur over a processors lifetime?→Transistors wear out quickly and Permanent faults develop that must be addressed.
        - Dual-Core lockstep:
            - Two seperate processors running the same code, for safety critical application. Logic ensures results are the same, mandated by standards for some sectors. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4fQL9HpquKHetGG8iCV-SW96EfhFJPWdBMSLSWkS2cd416xjxAEgeWtBflEsVDK_-B_iEqPnwBkjXOO4XrPmeycG7zLIIzZB_y1q2MP9oDy6fr8aSFIiYSq7rOb3bSc1.png) 
        - Can Embrace the poor reliability: 
            - Many applications don't require 100% accuracy. Such as graphics, video, audio, sensor analysis, games, etc.
    - Security Challenges:
        - Why do systems increasingly need to be secure ↓ 
            - May be running on unstrusted servers (cloud).
            - May be computing with sensitive data
        - Programming languages can help, but lots of legacy code out there!
        - Spectre: 
            - An attack that relies on speculative execution, tricking victims into loading secret data by **training the branch predictor**. Cache side channels to leak information via timing - see if the load hit in the cache or not. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JX1bFVt_kKvC56tPoPSUzeAdbKGPd8Ffb-GrW-TeSnFavGYQ7emHM4a8RD4_m0po810-ISomhkeXccel9A4bFeLmapustEXEQscVl6ZCy_cu5sJtNP4K3gYZzYgF3jZC.png) 
            - While the execution is rolled back, the cache is still perturbed.
            - Mitigation:
                - Filter Cache preventing things in speculation affecting the cache
        - Generally want to prevent leakage of secret information, ensure no unaurthosised modification either.
        - Must protect against existing attacks, we can protect against whole classes of attacks (CHERRI). We can also make systems resilient to future attacks, allow for patching in the field.
    - 
    - 
    - 
- 
