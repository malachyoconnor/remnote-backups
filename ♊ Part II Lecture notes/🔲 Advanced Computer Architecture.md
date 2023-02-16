- Lecture 1 - History + design choices
    - Best design varies over time and depending on use case - which direction do we take in trade-offs.
    - **Architecture** - set of specifications that describe a computers. Includes the instruction set
        - Architecture specifications: A contract between the hardware and software. Many different compatible processors may be implemented to achieve different goals.
    - **Micro-architecture - **The logical organisation of the inner structure of the computer. 
    - **Hardware or implementation** - The realisation of the physical structure, i.e. logic design & chip packaging.
    - The  __Stack
__ ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DT0kJDxW54nNUfu948kOdM66RVtAUaEFV7QokCPWZuEvVkXtZWUPJGVW9gMTU60zP166KP-znmVebVFsLLjZ4qow2SJgmFOeGQFw5Bsvclxbr0bNB5Zuz6pVF5sSgNOW.png) 
        - Each level imposes different requirements & constraints.
    - Design Goals
        - **Functional **- We want the thing to work and  __be correct__ . This is hard to fix, verification is the highest single cost in the design process. We then need to **test **chips once they've been manufactured - coverage, cost, testing etc. 
        - **Performance - **what does this mean? No single best answer, depends on the workload/use-case. 
        - **Power **- keep power consumption down. Limits the performance. 
        - **Security **- control access to sensitive data 
        - **Cost **- Design cost (complexity) and die cost (the size/area of the chip - the bigger the more expensive) + packaging. Packaging means you break a chip into **smaller dies **and the combine! 
        - **Reliability **- Do we need to detect or tolerate faults during operation. 
    - Markets and features
        - Each target market requires a different trade-off in terms of power consumption, cost, area, performance, etc.
    - Historical performance gains
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CXdyjj0EMGKXThbSDj9PUm-h-4noF6GEQ_88ZXY3asOSsQfwEcCpJuBRyrp-U5wtdwKBtDvPmEdNNeQIu3qe3jUhE-qGf6NavQcRxmbQ8dzkQRP8rMU87cyDtbovQuFV.png) numbers of fas
Note: 52% improvement year on year for ~20 years. 
        - From 1985-2002 performance improved by ~800 times. Over time technology scaling made transistors faster and lower powert.
        - Time = instructions executed * clocks per instruction * clock period
    - A shorter critical path
        - Why might we want a short critical path?→The critical path is what limites our clock frequency - the shorter the faster 
        - Can be done by inserting additional registers to split into separate pipelines.
        - Length of critical paths decreased **10x** 
    - Instruction Count 
        - Increased datapath width!
        - Larger register files so fewer loads/store instructions
        - More complex instructions? ARM vs RISCV
        - Single instruction, multiple data - data level parallelism can help
    - Clocks per instruction (CPI)
        - Earlier machines transistor limits meant multiple clock cycles required for one instruction.
        - As transistor increase we couold aim to get closer to a CPI of 1 (without our clock frequency being **low!**) A longer pipeline makes getting **cpi & clock frequency down very hard.** 
        - Instruction level parallelism? 
    - Note: Of the 800x improvement, 100x is from frequency and 8x was from other improvements!
    - 
- Lecture 2 - Core performance + Dennard
    - Better fabrication technologies lead to more markets ⇒ Moving from the room sized computers to smaller microprocessors or higher performance processors or low power processors etc. 
    - Transistor number increase was not the only cause - increasing die size also contributed.
    - Limits to single core performance
        - Limited pipelining - trade-off of frequency vs instructions per branch. Flush loads of instructions when hitting a branch.
        - **Cost of interruptions grow** - higher impact of cache misses and mispredicted branches 
        - Some components v difficult or expensive to pipeline
        - Practical limits for very high freq clocks (we have to distribute the clock + has to arrive at every register at the same time. POWER usage) - registers represent a finite delay?
        - Limits of instruction level parallelism
        - Difficult to discover and exploit instruction level parallelism 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oZLLhbC5hMcGbZnW5zvDOIgQ-YP1Acve9N4-Lj1azmVDwokBMz7t1IGzejcw13ZBVk6I46bJMsdVhDl5_aaOz5_tmBMXD25K8EK7Fk1BtmwmE8BLeqmmdw6jX2DS_PCy.png) 
        - Dennard and Post-Dennard Scaling
            - Dennard scaling allowed power to remain constant - transistors were made smaller, the number of transistors doubles & the capacitance decrease to 1/s.
This works because we can push the supply voltage down, causing the threshold voltage to fall 
            - Post Dennard scaling, continuing to push threshold voltage means the transistors **leak voltage. **This leakage voltage grows **exponentially **as we push down the threshold voltage... 
            - 
        - On chip wiring
            - Smaller wires do stuff...
            - Wire delays scale poorly compared to logic delays.
            - This limits the amount of state reachable in one clock cycle - bad for large complex processors.
        - As a result of all these problems, gains slowed from 52% to 21% per year for the highest performance processors in ~2004
    - Multi-core processors
        - Increased performance from multi-cores was cheaper than via single core frequency or instruction level parallelism. Lead to shorter pipelines and more power efficient processors.
        - Power consumption may limit performance.
        - Need to write parallel programs.
        - On-chip and off-chip communication will **limit performance gains. **Off-chip bandwidth is limited and may throttle our many cores. 
Cores **need to communicate **to maintain a coherent view of memory.
    - Specialisation
        - Look beyond general purpose and trade flexibility for efficiency.
        - Rather than the ability to run all programs, design for a narrow workload (could even be a single algo).
        - These **accelerators **can be 10-1000x better than a general-purpose solution in terms of power & performance. 
        - What does specialisation allow?
            - Remove infrequently used parts of the processor!
            - Tune instruction set for common operations
            - Exploit forms of parallelism abundant in the application! Specilise for your target area!
            - Instantiate specialised memory and tune widths + size
            - Provide specialised interconnects between components.
            - Optimise data-use patterns
        - Note that for an add instruction, only a very small proportion **is the actual add **:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kcGtrhz3NxkJoQPWq58DNVu8DkoLfwcdJdwMgpgt5jdLopYLGkxAPhPanprPg6fopFZeMoi5AHBcBlQi_eOjiDCrNyO7O3DFhbTHM2RcAju_aeFkkXfIqvqnmAl2SYwH.png) 
We could specialise for a specific domain we could reduce this power usage.
        - Limits to specialisation
            - Costs when designing a new accelerator
            - Chip may only be competitive in a small target market, reducing profitability
            - Specialisation reduces flexibility
            - Specialisation is also subject to diminishing returns - can't just keep pushing down.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JlU_AJXZMjFJHLFgR1C9ZxU_6MWR7fmyLFwReSz1mvj0Jr7LzZqucepLao7cgf0YCC9-si3hyhoQvXPNXcT5ib-mP0xDc9DjsAwE4eVfgTcg4weCx35o_OgK7uTzg51a.png) 
- Lecture 3  - ISA + Pipelines
    - Fundamentals of Computer Design
        - Speedup of a part of the system is limited by the amount of the time that system is used - Amdahl's law.
        - Complexity - seek simple elegant solutions. Complexity adds to design and verification costs.
We want to  __understand what we have built __  __**and **__  __predict how it will behave.__  
        - When you add an idea - you don't initially have an appreciation of how it will interact with the rest of the system. What are the costs.
    - Instruction set architecture
        - Acts as the interface between hardware and software. You can decide where to put that line, you could give the processor high level code **or **tailor the instruction set to allow for a high performance implementation. Co-optimize the instruction set and the pipeline. 
        - You could also provide explicit information about how instructions are dependent on each other - makes it easier to make parallel.
        - AArch addressing modes:
Pre-index means that the source register is changed **before **load
Post-index means afterwards:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wXYDk-SPulhgczXF-oTVQrrW6VgaD1l6cALYlOIMFOL6Ff7HwKkxQr45u_W3wPQ6XGCDAbaZ6CemP0iY81oMcFDJ8F0FE6gTXKm75ZQwFupflplO7seVTzfZkeuGUaGr.png)
    - Advanced Pipelining
        - A simple processor:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gDqzpjHPJc0gq8OU46Cd4SefkU9dCvB1SPjq4enECC5RA8zsJiz-liD-UZnHzB3V6tg-p_oFbrGnaEQHPoIVjMCn47C5GKNKQFrlozRSTO0ElF_3qMLyUrdSWO_N29Yu.png)
Instructions per cycle is one here. 
        - Minimum clock period wil be the worst case delay between two registers shown - this does vary with Process, Voltage, Temperature etc.
        - What does pipelining do to latency and throughput?→Latency will increase (it takes longer to execute each instruction) but throughput also increases.
We don't care about latency, we care about **throughput.** 
        - Why does pipelining improve the clock frequency?→During pipelining we add pipelining registers in the middle of the combinational logic - this reduces the worst case delay between two registers and so we can increase our frequency: Half the worst case, double the throughput.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rzW2j5TZIwaPK5a01AKe3Hv6VlXxZp1AMxjYXAlMIOeZZtO5J0w7-eZH_9ocyDxgLr1F-acdvzGdkdM37rV3lutVRVwNMTyf5vHafGGwDLmqnZG7Tmq_Ksn6OP_SDD8k.png) 
Note, this does add a pipelining overhead due to the register! Means the gains are not linear.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UYclCaCWZg7coWo4mbFoLzSN3vO4fLT4WydRon-mRZ6zYJ8xdWOH_5_vzHyirfwKpMbxSYamuYQHM4-QVW9y6pZMRR_CTe7Y-7CYvPZiMmYrmAY54u3PhTd-_m7hbL8M.png)
The control information about each instruction needs to move down the pipeline. E.g. we need to remember what register to write back to.
        - An ideal pipeline
            - Ideally our CPI would equal 1, but in real life our pipeline will stall and the CPI will increase.
        - Stalling to access memory
            - The latency of accessing off-chip memory is typically 10-100 times higher than the clock period. We must use on-chip caches.
            - Why would we want a separate instruction memory?→On every clock cycles we need an instruction and on 30% we'll be accessing data memory. We'd stall every fucking time [😩](../😩.md) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iy_TF4v_Z3CVCRahVyJOgpxFeUuGbdE7CgjWewfZknb6t1wDJhV0Yk0sVZ3P6djV30eXTOQ4IWJtVC3hqBYVWSFBMbRtWZs52_4AJMtvCDTlxY4p4vnCe6SnX575EFyB.png) 
        - Maintaining correctness
            - We need to ensure results from our pipelined processor would be identical to an un-pipelined one.
            - Structural hazards
                - Arise from resource conflicts. I.e. instructions may bneed to stall to wait for access to a shared resoucrce - i.e. a register file read port. The registers may be full!
            - Data hazard - need to respect inter-instruction data dependencies
            - Control hazard - caused by instructions that change the PC
            - Data dependencies:

                - True data dependence (read-after-write) can be solved by data forwarding. Two adds - output from ALU to the input of the ALU. Second instruction is data dependent on the first.
                - Load-use delays are always going to be slow...
                - What are name dependencies?→When two instructions refer to the same register 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2uYpf_NDpb3iUj-9OZh5UJv7k6kiVFxOuyqcZvRfdi6HIQ2wPy7Uv0wRv9GUpUA_VwzX91H8xii3MqginM53MzmjpGvrjzhsFke7TomqpeY52eAVNTIkHWD2MARB1yrP.png)
We can't reorder lines 3 or 4 - we'd get a writer after read error.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tJZmQP1VtHRtQTaynnmMfLDgYnU_tXZmhZmg7zLliLMe5j3-dMYC0GVYhySvO7xXexyBan8PXmQRF96pkkN6pNBXgmbAofOtlCaiW8Rt_XtFVvXQMdrdoMjcfpeVvdg1.png)
We usually get around this by **renaming variables**. I.e. the instruction set has 32 available registers but we have 256 to work with.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aCwuvR_O7_lr8Nao7WGjxMbSMXjtGyWwNGyHIL5lr_v8ICtPmN7_L7O67vtuKGTYtsZX6g8Ikc9QvpUA96X2AxRy1sS5aqdcWaMg2rw5j48sOrl3bQWuaVFnxnRKa__t.png) 
        - Control Hazards
            - If we don't evaluate the branch in the decode state - we'll have to wait till the execute stage till we know we have a branch. Then we'll have to flush two instructions.
        - Pipeline Control
            - Hazards often require us to stall our pipeline - but this stall logic **could add to the processor's clock period. **One solution to this is to design pipeline sections that **cannot stall!** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rvaE7shneYFDzqCLgfLpW8i4ohNx39V_xvglzykkn74LsSimvjae2EfMDrIFAGfB9_JTMjtptkf3j8wCTDCXOeYvSLqBHErk9wLqgaeThjkZro2uHXe44t1_kBlVA5S-.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Rln8Wa7M6kdWSWxc_JPQyPnzUdybSiakIDom5dWS7QdNA1841gwNTsLpwwFsVrVCkqjHHS_3n8j0egDyWsMRDHP62p3FlWrBUZiYti93SNeFJfeQn0FBsd5313Qlq_yB.png) 
- Lecture 4 - Multiple execution pipelines
    - Multiple execution pipelines
        - It's impractical to require that all instructions execute in a single cycle
        - Instead we form different **length **pipelines. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T73H_deXyIqJvsBphb0FLxxDVH9nTt5mhCPju5J4u03F0aw8UlsX-ANIAEz8v5o1jtHKLSzj3yrqhPotyizUNz8_ZItF0Evv8Cn--4TtnQOWE_uWqicVmvGUsUi5sQM1.png) 
            - 3 instruction fetch stages!
            - We need to know as soon as we get an instruction that it's a branch
            - One small branch predictor and another larger branch predictor that's available **next **cycle. 
            - Different operations that are pipe-lined - notice that the output are fed into an output pipeline, this ensures results come out **in program order**. Otherwise shorter pipelines would finish first. 
    - Diversified pipelines
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BXnTD_LvZGID8TYJSEcKLss1fFeRXfZvlHvQ_tkLbaNaMWhcPoQH24lGTARe0MD-kewq5mtVam2jJvA50ib5blFhlhugICdIMVjuH9yPotsH_dTlOpPrDrs0t75vWhqZ.png) 
        - We can sometimes allow pipelines to overtake each other. I.e write back out of order.
            - We need to make sure that contentions for the register write ports are queued. (If two instructions writing to the same destination register happen at the same point)
            - Careful about Write-after-write hazards
            - Out of order completion can cause problems for **exceptions **too 
    - Example ARM10 pipeline (1999) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qqYvNxLGoy5fznuL8Z6LxFZLgT2-xlHHAc6Is7sjwCZB1sdWECWco9yeiRVQPWs_DIbpugayIND8IxuB4yh2obkgUvvgORlZKcF6zN_bBz-mYWoJSbdwis13xI1s3JQH.png)
Stored in the Data cache before put into the register file. 
        - Data Hazards
            - Cannot allow all ALU instructions to bypass memory instructions - must respect dependencies
            - RAW or WAW hazards
    - Pipeline CPI
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/O3xt3KZbi-GDlAkp1O63f8-fHeFzDVUHausFeOqRjASLHk8l7MRtzhDiiAyUVnIw1BTLmtREm590ZmmiebOtcEtb8joEM7JJm6QcC4Z36a-FxguRqOYNoKRGidrhoBAd.png) 
        - What's the tradeoffs for creating a deeper pipeline→A deeper pipeline can have more things going on at once, so the CPI goes down.
However, the longer the pipeline, the higher the cost of exceptions.
Additionally, longer pipelines mean smaller distinct sections - these sections are fast to compute and allow for a higher clock speed. For higher clock speeds, stall times due for memory cost more cycles.
    - An analytical model of performance
        - Examine a critical path of delay T, divide that into S stages f delay $\frac{T}S$. Then add the clocking overhead, the delay of the register:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RBLqwudzLZusiRhtl_54BS716NypPtMqwaLOmgSGQjnmeQjoFchqD6qkvJQEBWnL6U6DOZk9o4_BVMOnf_TbhIe7aPGo-JK8t95GYqw5ejYLHknk60nCAp1ZIFgYSLj2.png)
        - Using this, we know:
            - Pipeline CPI = ideal pipeline CPI + pipeline stalls **per instruction** 
            - Freq = 1/ (clock period) = 1 / ($\frac TS + C$) 
            - Throughput = Freq / CPI
            - Lets assume stalls occur at frequency b, and their cost is proportional to pipeline depth (say S-1) so:
$$Throughput = \frac{1}{1+(S-1)b} \cdot \frac{1}{\frac TS + C}$$
        - We can plot the number of pipeline stages against the performance:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MG3MIj_tgYSSBylHPWo0FKEfwhFRCoU8IA4sLo9fBD9z3XHshx3YpeEv7fONTUejNffaAqk_4Vn7dYN0qE0GJB7caYhIe3QEe02qGxebKwne2JH9oCJ37yWGQjBj6gla.png) 
    - Typical pipeline lengths
        - Area optimised cores may have 2-3 stages. 
        - Simple efficient scalar pipelines usually have 5-7 stages
        - Higher performance stages could have 8-16 stages.
        - **Becoming shorter in general, we've moved to more multicore, energy efficient cores.** 
    - Control hazards
        - What would we need to do to reduce control hazards, when we fetch a branch? ↓ 
            - Figure out that the instruction **is **a branch 
            - Compute the target address and branch there.
        - We would like to calculate the next value of the PC in parallel with reading our instruction memory. This is **hard,** as a branch may be decoded/evaluated later in the pipeline. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Pt40cCic1v04u6kGc5-SwLi5gditF0YUbbzuIn64ZEoE5liFff-nmo-WWEopZjFpiUcYW91KVBL6T67hCm3kqA4OvEq9L0TjduSq6lVNQfCJY-59fa_mGGS-vjv7uFG9.png)
The two instructions after become NOPs - wasting two cycles. 
        - Option 1: Assume the branch is  _not_  taken 
            - If we evaluate the branch in the execute stage and 60% are taken (and 20% of instructions are branches) we get:
CPI contribution from branches = 0.2 * 2 * 0.6 
New CPI = 1 + 0.24 = 1.24
        - Option 2: Evaluate the branch  _earlier_  
            - If we bring the test into the decode stage, we can check for a branch (with some simple test) to save 1 cycle.
            - Need to be careful with data hazards - may need to stall when calculating values **used **by the branch. 
        - Option 3: A delayed branch
            - Rearrange the code (with a branch delay slot) so the first instruction after the branch **can be executed:
**![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nx3FqQH4WMwBjNuVlAgOEWjMGc_q_euFUQdBBEiSCerhaKukWxV3CYgqV76pkpdr6JGgVayhAfQty7ATtup_KXjKr7rYiEvN7UVkffJNHoYaJgRMdQjiwVOUwm9_SYp3.png) 
            - A compiler can usually fill it 60-70% of the time.
            - Could add more, but the idea doesn't scale and quickly becomes a burden.
        - Option 4: Branch prediction
            - For high-performance processors with deep pipelines, why are branches more costly? ↓ 
                - Branches are decoded later. 
                - 4 instructions are fetched at once, and 3 are decoded at a time. So we've wasted more time.
                - Due to these -we may discard > 40 instructions if we flush due to a mispredicted branch.
    - Static branch prediction
        - Exploit that branch instructions are more likely **to go backwards than forwards. **I.e. loops.
Assume it's taken if it goes before the PC. 
        - Accuracy around 65%
    - Example: ARM10 processor
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ByknHhpUnbNJgc4GtuCIeS-2YJENgq21ebQiGpS_Jcu6LgPr7rLOJizJYHZKV2_afaDino9EjfypHBuytlbpkFluZBpmPsajz8X-3AdDggW-mkjN6BccqO6DZVFbmx4p.png) 
        - Could dual issue branches and the first instruction of the branch.
    - 
- Lecture 5  - Branch prediction & Exceptions
    - A simple one-level dynamic branch predictor
        - Predict a branch was taken only if it was last time. We use a simple table of 1-bit entries to store our predictions. How many incorrect predictions would we get per loop?→2, one going in and one going out. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gf5QGucpdrMYrM-JgHk3xtM3mcBax0q2rDUFCI049aGh55fv6ORJgK-vYR5bQMN2RD7kuGMQbX-vjVWrqqky1oRmj2hxewszu7yHvPg951VNqVOLGQ9h0fBdKCuYG8Wc.png) 
    - One-level branch predictor
        - Describe 2-bit saturating counters for branch predictors→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/v5RIgNL8l2QT8DB_qdnsDR_Znmt3QV3AgqdIJEeAQVT5apsJn2nN5d9ZznVCxjBL_n7fHC7V_tfnzHXdXupGyiH0RkE4YAAgoxpk3mufUuLOikxhn1TSRY920KNtwUqi.png)
Taking the branch increases the counter, not taking it decreases it.
If the counter is at 2 or 3 we branch otherwise we don't.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IZnq1jeGkHSp3lNZ5_GAVy8HgyK2tEQEnX_bdXAd-1AYdwE3DzTjtf_QUyuIIciascyhCIMG-Uoq_YP0C_yTukF3gMczige0KwNIZPYF_i9JUK1zSNyjQvubnpkDSu9M.png) 
        - This means we only get **one **miss every loop at the end rather than 2. Basically, we only change switch from predicting a positive branch after 3 incorrect guesses. 
        - 2-bit saturating counters are as good as any more bits.
    - Correlating predictors
        - How can we improve on simple bimodal predictors?
        - We take advantage of the branch being correlated with the past outcomes of itself (local history) **and with the past outcomes of other branches **(global history). 
        - Local history
            - Look at what **a particular **branch has done.  10101011011010010110
            - Two-level predictor
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/syPcAZAtF-GsJtE1Ui-VICLaG-YIb2nNorYAqzYWz4DVIfiLSJV4844rN38O8oRvBA8cU0S5QBsOQQtd7u2ETkrd2a7sW8z7es7Byk4inaRSY2ApdwGlVLOEH4osGqMG.png)
What does this two-level predictor do?→First we look in the branch history table, this gives us a record of what this branch has done - e.g. not taken | taken | not taken. 
We use this to index into the pattern history table, this is a collection of 2-bit saturation counters **for each possible history. **I.e. If an if then branch only executes every second time - 010 will lead to a branch, while 101 will not. 
                - We have two memories - the branch history table and the pattern history table.
        - Exploiting global branch history
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QgQ_kU0nzmOAnzLXyoC9xSQK5iW5sNOcz6DOeaFeFNTtqwOZv6Y84nks9Vc4da4XIm5_50tE4gXEv87Fi_VluoAVvYqlX9Z_L1992SbSWQ_c7K6ZMPw88T7X4AxFf_Hh.png)
Branches will be correlated! 
            - Explain how global history two-level predictors work→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sJXU0Pm0h-noX4lHyZHpgCIdG2ktB5wh7T9BuUbeNhkKjWoylI-lyv9KtX7dAmStvF6q01i-rJOSZnWGyaSDt5xye_aIVvvbynGEzkqhBnHwn9X4L4yw1NVvi6VoJ9DZ.png)
We examine the global history of all recent branches - then hash that in some way with the branch address and look up in the Pattern History Table.
This just stores a 2-bit saturation counter which we use as normal.
        - Optimisations
            - Tournament Predictors ‒ More advanced schemes employ both local **and **global history predictors. Another predictor then chooses whether the **global **or **local **predictor should be used. 
            - Aliasing problems ‒ Many branches will end up **aliasing **into the same place in the pattern history table. You could put problematic branches in a small tagged cache.
        - Dynamic branch predictors
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b9dri_FQgZPa-iKiCSSSFTAk-j0N3py23a7NId1ChG4MSBfN-rGa7eChBd97PEjTPLVmKAGKjyntXgtWlnbYSOENdKumGbIlPru7Fz188gPOPCipYUpymCw9oCXPmwDi.png) 
    - Limits to dynamic  branch prediction
        - Give 4 limits to dynamic branch prediction ↓ 
            - Some branches are systematically hard to predict
            - These all need training, so there are going to be some problems
            - Some branches are going to rarely be encountered
            - Predictor accuracy will be limited by the hardware, cycle time, hardware area
            - Aliasing + interference.
    - ARM Cortex A-15
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/m5zUSkfuH8siUywt2WjrgyjRkfs4KQi6J5TQywEJss1stuQWy6Tj7gP9w6aljJLH7ELGQ1RREO4tWo17huXh7wFprL3vFHCx5T3NBVCELWn1jN7aNZ1PYvUXLwl2smw7.png) 
        - The branch predictor consumes ~15% of the core power !
        - Bi-mode predictor
            - To combat the aliasing problem, separate the normally taken branches and normally not taken into two two-level predictors.
The choice predictor decides which one to use.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xjq36ZNTKpnU7puNt3JdVKOKwnEUHQR4qkYj9h391SJD1NvwYqx7DUCR22o22k4Vldj_EjveBt8rEVHO4y4P1c2skQNV4ygbyqoG45vicYtyHHqRUNQsj5qHaW7c3Rwo.png) 
    - Is branch prediction a solved problem?
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qzTjzqJwC4cNgsQBPlZhTS_BTLLkAo9tYJv-W5ognhNwcBCkW--YPi0T8ABupwCgAlwv6C6rwOpWK4anztz2pGRMwe6RSTLRplbf_we1H9j4SxHNnrfGRTpOS9vZeq50.png) 
What is this graph telling us?→Branch predictors limit how complicated we can build our pipeline, we get diminishing returns. (Note: the X axis is exponential and Y is linear) 
        - What does IPC stand for→Instructions per cycle. 
    - Branching without stalls
        - What do we need to know to **completely avoid **stalling on a branch 
            - Need to know the current instruction is a branch
            - Need to predict if it's taken or not-taken
            - If the branch is predicted as taken, we need to know the branch's target address.
        - What is a Branch Target Buffer?→Cache of recent branches with the target address - tells you if a instruction **is a branch **and where to branch to if it is (also what type of branch):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n2QjD2s13QD8tQ6xfWmdwroG7lMgi3lw-p94RitaFRrK6njTqDVURmnUCMU_pRdYomDwD9JxcnonibLWNuttqCLxMjLjBA42bVevVvs97zKA2ybDnSYF61jYkDRfjghj.png) 
        - Explain what's happening here when the PC is incremented
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c_N2Uot2og3jcqdvwjNN40NUzlBHUwxif1mWGKv220G6vIJsn4dxq3eCbXaXx4MK-hMuNYOAZRsBwaVbUUh77jBPo4eLxtePPFpM-ND1CdmNazA96yeFh2wLHqy8368J.png) ↓ 
            - The next PC is given the next instruction in order - i.e. PC+4. 
            - The branch target buffer passes if the instruction **is a branch **and where its target address is. 
            - The Branch predictor says whether we are to branch or not, this is anded with whether or not the instruction is a branch. If both of those are true, the next PC will be the output of the branch target buffer.
    - Other BTB tricks
        - We could store the **next instruction **in the target address in the branch target buffer - this means we don't need to fetch it, just start decoding immediately. 
        - We could also create a seperate structure to cache these
    - Return address predictors
        - What are indirect branches?→When the target address changes - we could have multiple entries per branch in a BTB.
        - Functions may be called from multiple places in the program, why does this present a problem for branch predictors and what is the solution? ↓ 
            - Near impossible to predict where a function is going to return **to ** 
            - We produce a **return-address-stack **storing locations for called were called from. 
    - Exceptions
        - We need to interrupt a program's execution, pass control over to the **exception handler.** 
        - Synchronous exceptions ‒ caused by a particular instruction. These are precise, can let all previous instructions have executed
        - Describe synchronous vs asynchronous exceptions↓ ↓ 
            - Synchronous ‒ these are caused by a single instruction and can be handled precisely. I.e. we can wait for previous instructions to trickle through the pipeline, then save the processor state and defer to the exception handler.
            - Asynchronous ‒ These are generated externally, i.e. unexpected memory error, interrupt from the hardware/peripherals.
        - Describe the process of handling an exception ↓ 
            1. Save the processor state.
            2. Save the return address PC.
            3. Get the exception handler address from vector register and jump there.
            4. Save the registers state, execute the exception handler then restore the register state.
            5. Return from the exception handler (ERET command)
        - Precise exceptions and pipelining
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oqwEgbApEQPkUw2o3RjrbJfeLHtK_rLH1si7-kkwCaXslzINGlrNrywnzTrwfrcYnfbIYrGKCap22d5sYEh2CjLq_SEE8TeXr6zrmm0sOgwHlwhATUVaMZQDEv3-gAyF.png) 
            - We can't immediately jump to the exception handler, need to handle in program order.
Wait until writeback and then flush everything before
            - How do we maintain program order when handling precise exceptions?→Ensure other instruction shave finished by **only handling exceptions in the writeback stage.** 
    - Limits of pipelining
        - If we pipeline our execute stage, we will need to find successive independent instructions to keep our instructions from stalling.
        - Need to pipeline our ALU.
        - Registers and clocking overheads are non-zero! Can't have 100 stages, these will dominate.
        - Need to balance logic between pipeline stages, clock period is determined by worst case-delay.
        - Limits on the number of pipelining registers
- Lecture 6 - Superscalar processors
    - Instruction level parallelism
        - Generally there is a lot of instruction level parallelism.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d-sGDcty6K41OGNk63og93OqCFGSle1X9ffexcvWpRwDmpxRxoYGsjP2311Ir66aIoI3tpgU_fAKgm6W540cjgEYbxdzvr9QCylkOkKl_XEcflvCjUltysaSq_Z36Lxa.png)
        - The question is, how much can we capitalise from.
    - Super-pipelined and superscalar processors
        - What is a super-pipelined processor?→When the pipeline stages are further divided into M substages - e.g. an ALU execution split into some number of smaller operations
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YNiu1gjPCZYVp7ZsCNlwFDTFLSdPBrynJNLgcD4q1dQ3A0RGDGsI5WDbn2_uIUO3VHB1PmETiwUROYC1LmxzqCzqBTzsHwbzI4fXxOA7zFYVUXSrjjakMkyY6thKku1y.png)
Clock can be made M times faster 
        - What is a superscalar processor→Multiple instructions are processed in each pipeline stage - meaning the IPC $\le$ P.
Fetch 4 instructions, decode them etc:
  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FWeDvcKaVEqKnfCSxQfDQr3IFHn3VjgLTh13EUx7pyhIP1v-t-1NYUq0bPR8pQ88e-Xaz60wjeeZvkfuldofK8QfXiujUAVm7_Rq1yXpjJ2kUVHyrPqy5Ui-CZmOlo_0.png) 
    - 
    - 
    - 
