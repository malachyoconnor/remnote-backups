- Lecture 1 - 3-Address code and flow-graphs
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-fA56Za1tbM7MZFyb775uaOYAe9bFP8G-8kVCs7vLc2UXru7c4n9kZ2ImP8XuOZgCsx-X-Prcgx-PFDvkjLq6eceWmOgf0xYsWWjjRoo7ja34I8585GeGRFRHOrinOBt.png) 
    - Good programmers write maintainable and **general **code - compilers remove this **unused generality**, and hence make the code smaller faster & cheaper.

    - Optimisation is analysis + transformation - transformation is doing something dangerous, the analysis step determines whether it's safe.
    - Analysis shows your program has some property, the transformation checks if your code has that property and then applies it.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CAPe9nnWaMG1fg9gOcvjWVIKJvk7n4hwdNKGBi-66cyVqoLlwebiOuY02bRWgJmJ_UWOyOe_CG4wJrVod3x16UseeY1psmRlzfNu7p3DgItce3Uj7xfeTKQeX-FO08Jw.png)
We can't simply move k out of the loop here (to not recompute k*2) - but we can't do that here because we have a cross iteration dependency.
    - Stack-oriented code
        - Code heavily using the stack...
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KxKrYbcJfOn2Ug9NaUKYwwJhnJAEz_zLpnnbIVmbvPtXBi52F7L2-kzMlVIxEeb0at-hAvBX4mqjm_CjPavJ8eHjO-N2MO_WmWGyqaEGL2Di5meQ0PKVWEsk7a9ieGkt.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kXzBui0-Chc1PxdqUxwJ1CHS5WV7GPKNcuzdYf3izM50epAS9y5XC75JlzaTfZk3mGgN25jvqPIV_T3kraar_SUilRwrdheAMUgIquKvvdW7A5JGCQs2xxSm0mpaqmM_.png)
**Not easy to see what's going of from the start.** Dependencies between different instructions is implicit - this makes analysis  _**hard.**_  It also makes adding code very difficult.
    - 3-address code
        - Convert the **stack code **to machine code - e.g. a load becomes a move, an add is an add and a multiply chooses registers not from the top of a stack. Temporary variables are used as temporary locations to store things in - e.g. t34. ArgX is the arguments to the function.** The compiler can create as many temporary variable as it likes.**
Res1 is the result.
        - The links between variables is **explicit**, we can see how t32 flows through the code. Additionally, you can slap things into the code and not affect anything.  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ktYCiLi5pPih7Bz1WIQQ06vWq5ux-PUTukIIEO62QHWJqh7qeaG_IdeBuzU6h9YUlG59ennVRaDoKSlHQAChT_F5XbTDoTdwsW7P8LDrCubjsoJ3xGXkdL-ly4R42fWj.png) 
        - 
        - 3-Address code commands
            - What does `MOV t32, arg1` do?
            - What does `CMPEQ t32, #0, lab1` do?
            - What does `SUB arg1, t32, #1` do?
            - What does `CALL fact` do?
            - What does `MUL res1, t32, res1` do?
            - What does `MOV t32, arg1` do?
    - Flowgraphs
        - We still don't have our program in a form that's very easy to analyse - we want a graph representation of a program where **each node stores 3-address instructions**. Each edge then represents **potential** control flow - all of the control flow that could possibly happen:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tiSdMuYSO3b2nqyJ0_sw7uNtFTC0yek-cqvlukU1XKOTK977MmI-sfrrdvJk6Nmq2Uz2_dZrSr3CKkoLngolujHLWHm3axLIYN9JfR38gnEMk5xFKSFlqWj70_TovrpF.png)
        - Flow graph for factorial:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sM1jXGbIhzFotsTXQ5EXA_EPZFzgX_n3hixlxYaw0S0TxdQ_QLn4HY4Q1bq6BIJVGyk15Rmix8ngy38AyDU2ChV8nWqFXZWMHcYtuGL9LbtWxb2L0HVRGqspqStPkqVx.png)
Note the graphs flow from entry to exit.
Also note that CALL fact **does not return to the top. **We don't use conditionals.
        - Basic blocks
            - Form a sequence of instructions which form a function. These are grouping of instructions where there is **no **interesting control flow between them - no jumping, we **have **to compute the items in the block.  
            - So **every basic block has one predecessor and one successor **(Perhaps other than the start & end). 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2Xs7HsYqRCUxPBupQsgww_RSuU6KEPwGaWm0FQbQr2cxiAMEUtAPdO8wsqWwzXC6_BasG9rwKFqyIjVX5fLD_1vE0O1LVGugiv7kfA5LecmeLA-wYtof5A95_5SC3MLs.png) 
Do we stop basic blocks at a call instruction? Varies, can be useful to know that control is given up.
            - We then separate out the entry and the exit:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jflCTNZ0gnog6qwc99lJmCk4KAgGPe7LjDisHtkrVFTUs2mV1aj1xRgIHCLP2sNmx6WAvKU5j1v3NdYsyPanHnl7lMUZy5JylYTCXjM7AmCF-2XuyrvGWPVtXyYIb2Gt.png)
            - Why do we use basic blocks?→Reduce time and space requirements for analysis algorithms by calculating and storing data flow information once per block, **instead of once per instruction!
**If we need to we can go in later & examine the basic blocks. 
        - Analysis types
            - Peephole optimsations are→within basic blocks 
            - Global optimisations are→between basic blocks -  
            - Inter-procedural optimisations are→over the whole program. E.g. unreachable function detection.
            - Peephole optimisation example:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Pu2kQb9r2IEkCzmoqqvutQBHzuT1QptYmsMx0QQ41XnSe6G5hBQQxKJsMOR3bzAaTG9MX6rL71OlzydIBMzvLV24LFbs-IM_BpqNcmfV7NSJfAeSJCerXJFzHO9Fx5HL.png)
            - Control flow analysis is→discovering the control flow 
            - Data flow analysis is→finding the data flow structure - (variable use etc.) 
        - Finding basic blocks
            - Find all instructions which are leaders - e.g. the first instruction in a block ,the target of any branch and any instruction immediately following a branch.
            - For each leader, it's basic block consists of all instructions up to the next leader.
- Lecture 2 - Unreachable code & procedure elimination
    - Intra-procedural analysis
        - Analysing a single procedure on its own, do this for every procedure.
        - What's the difference between dead and unreachable code→Dead code computes **unused **values.
Unreachable code cannot ever possibly be executed.
        - Deadness is a  __data-flow__  property - will a value ever be read?
        - Unreachable is a  __control-flow __ property, is there any path to reach this point? 
        - What does the safety of an analysis mean?→We're **sure **we aren't affecting the program. Many interesting properties are undecidable, so they must be approximated. 
        - Overestimate reachability so we are sure removing it is safe.
I.e. if we can't 100% tell if code is reachable, assume it is.
Assume that loops always terminate and both branches of an if are reachable!
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BWszlJH7wfmLFjmU_0dSI0zajacMUzZeUJOzZHjbWaR4wtIrrGCVp86cVtXC_jwc6WZX2mWWDmQB--5FFrAA8MQ_ufgIL6khHEOsl58IV6lblNVAaX1INfwDdh4OMOiT.png)
It's not safe to just assume things about JMPS! Could go to the same label or a different one each time. 
So, to stay safe we assume we can go to any of the three!:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HgBc_1jBLviqLHghuElBoFwX_SoATtDawMu9FPevivJtkDM-cS3P3H8Qg4tE64v3ju-lfD5Twhm_SGSsautSowU99TCXaHUuzMDCXRFO9VAl8sKyqXH3SV875bJxJl0Z.png) 
    - Naive reachability analysis
        - Mark the procedures entry node as reachable, move to successors and mark all of those as reachable until we run out of nodes.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CvEJDshtZ-_8PqpfONV1pnsjOiipqFAmjGvQSKsbM_yrZg0Bt22D_nGz2vKGroWhvSI3fcqTxxLLVEmqi1sNENzwHA5R4VG152uO-Rqf7KribY1rmVgCETwzY1CgiQvs.png)
        - Results in a simplified flow graph.
        - Why do we bother with the unreachability analysis? Surely, programmers would never write code like this→Naively unreachable code may be introduced by the compiler itself!
Something like this caused by copy propagation:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/phVVVVU5joOEGK_HTjean_ugFjo4Sji_bbIoRTUCCa-nYB5gudBW2NxzMyxsFnuIr6lO3mFtdiXnQb1hFBmoW_sZh6LCr8k96ZAtCYY7yTeZleKImJud2-06K1JKKydf.png) 
    - Less Naive analysis
        - We're now analysing the code itself - rather than iterating the flow graph we instead make a **decision **about the path. 
Checking for things like: 

        - if (false && ...)...
if (x != x) ...
if (!true) ...
while (true) {..} ...
        - Unreachable code eliminations not only make the program smaller, they can make it faster if other optimisations are allowed to run.
        - What is code  __straightening?__ →Eliminate jumps between blocks by coalescing them:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JMnqHmgtoLD0gCvARON7Gpm9n5Wt0CGmVjtFbPWo75ipRSHo3xjBH3OzUF19ZUH3mStfNQNMHpF0LZCxifNFSb-Ja1cZDdnnVdXUSMsTVO1OlHBr6VUQOMnKyqlcgZsq.png)
Here we can remove the above blocks and coalesce some blocks:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R9vAIy9Cz13KeBese_4FRlCa0_t4VTFUbNnWNItsvDi_rKA2pLvKjM_cX3x-eUQfzIRlpbaIABslBaIgqoU8kgFcb2EvbyJcQZwhNuUAnr8E6c9W7VhFtLHaRVkbk-wx.png)

    - Inter-procedural analysis
        - Collects information about an entire program - propagate information from inside procedures to outside. E.g. take information about the callee to the caller.
        - What are call graphs→Stores which functions calls which other functions. Just examine the call instructions.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7T8DW1KPSAQ_4Kz3CoPDkHxeRiX_imqfAL8RS0Id18clJbYrD5mGRtJ5s7v5yII7-wyfWj0ObZoWXPmLQfbHsBiC4CSABeloklZiYLJSJz2Dp3MsdGKf_cttXr9imCzm.png)
Note we have indirect calls - if we're passing functions around we might not know which function is being called.
        - A problem with the indirect calls is we'd need to just connect that function to **every **function... 
        - We can then mark and sweep again, mark every successors of marked nodes until we find functions that are never called:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mOtMxJ7IMvfXRaImqrAfCyttXcfn6VWgLc8f2knG3kAKEPWyxp2Yrv5Ad4wDzPrxzZs_fceIOV5u273W8UyWu9YgAx_iW2eSi1TALMLCM_Y2imFb1UXdThKA29W6JDTd.png)
    - If simplification
        - If we've got an empty if then - we can remove the if...
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CVjbiVpgTB0P2HxSuZB3e_gSl25wg-WsZFhf_ZUFsmKIczsYvHUEyNmqoP3jizp8ws2NddvMag0ho1_Qa-KgyA8YslgoFaSPNkL-zzXDhnyQToCpxVg3FKXv25KRKkx1.png)
Can remove empty elses.
        - Removing them have benefits for simplifying the control flow graph:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YsaON2k--EhRFbJcVkFji68O5W-0tEj7w9vQc0du3MTLKabk4QFV0NZk0ycA2G1n6temLdDEyxnrQans1lURg3HHEMAHbzNLVlTh_yxKIBt5h7_jqM_UjSRN_JNPutgf.png) 
        - Nested if simplification:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GxGm9ocdgiyL2wz5MPqiSFPYu_cRhnGeI7a_2dYvdClmN7YSdxpZ3pPFzCAznO8T0Cr5n6kgmsIIRDFnK49jWkpezBHkqQYSvlIVsxSFC1D6yKvXRtTK7wS9aoOBVq4G.png) 
        - What is loop unrolling?→Taking a simple loop, converting that to repeating the body code x times - then examining that code to simplify with constants if possible:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HBrfRndAuE88l7CmjFbXlm1_cbVi5rrGWv8SFeTJpBGp6sAAuOHzyaJLl9rs0NdOaKj8Az8r5soJtF99uh0jXqU_-le1xz6UJhPiXmTzlV4AFb9NiuhMwyU3fqqK6y7L.png)⇒![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sBfCtI1ljtJBCqYqFiF4NDY1UciiGYbuyiN93hLT7PVE2qDSV9fhqfCyxF6IFCzjH6zykUvptlX6fWqQnWCbfZdfqxHayviyqYmO9ZZ8A3R6UwP0h_TaRHrkqUrdhXjU.png)⇒![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ppDxw4KZ_Np4bz50n4BmgPkyCDYMJluV1zZHU0tvA7F4JxjkCSDkBlJNkSSDeIVNi1RA0BCqy7ia75ddr6IsR7ZOnFgpPpbp0uSxZKZzo-fcWGwmImVKVYIHqyyX6wdW.png)

    - 
- Lecture 3 - Live variable analysis
    - Make notes on the first 2 slides
    - Liveness
        - Liveness is a data-flow property of variables - is the value of the variable needed?
Are there no possible paths through the code where the variable is used.
        - We thus consider liveness from each instruction's perspective - each instruction has an associated set of live variables.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7LhpQ0vfVgo73hPYfYMrqSIgCu253poqVRFytJt-sQB5O16ji_72p1HYOACyfbiKbmTzGQJQnpMG_dQE99o4c3R_aK79lpcez25Meynl2OtmWbL39LyvNW028JNq1ImA.png)
        - Semantic liveness vs syntactic liveness
            - When is a variable semantically live at node n?→If there is some execution sequence starting at n whose behaviour can be affected by changing the value of x. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TrEeQ3JVX4ks8LeeV7HS71OTxNsuyjrTFy6tTKIfF2c5dKZMieBpxQO_v86xDgcitTHGLXxC0CJwY48K-QhVUsPWFl3BLatSdMuzj7CSkn_5hDc5W_OkLmoMa2qzfgKh.png) 
            - Semantic liveness is concerned with the __ execution behaviour __ of the program - this is **undecidable **in the general case. 
            - When is a variable syntactically live?→If there is a path to the exit of the flow-graph along which it's value may be used before it is redefined. 
            - The **path to the flow-graph **is different from saying **some execution sequence **- because not all paths through the flow-graph are real, overestimation. 
            - **Semantically**, we would know one of these two values will be true and $t$ is dead:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MIOEFGxkdMeVM1KX8fDJu8ThOuNq_UROkOfWf-TGCpuzEfxc3SRpQ3GP1ujYh7twImFuoRdmy-TGDWNbwrmqguH6eLNfBhf1Svq1yx_pVOToqVYIHbTjIvg_RQ2khmO1.png) 
However, it is still **syntactically **live:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2XuyBm--YfAy9rIOVCkjfjPHTAkZGPwJvuWvFe3bF38n1-OV_mRiOtizprYYBfXfBdFXRyVwH2xA5ID-pcSg4bwDFcXMBA46Eh-azUoYAMJ_131QPwsS82EJROKikTPA.png)
Even though this path isn't possible.
            - $$\text{sem-live}(n) \subseteq \text{syn-live}(n)$$
We  __safely overestimate liveness.__  
        - Live variable analysis 
            - LVA is a backwards data-flow algorithm - usage information from future instructions is propagated backwards to find which variables are live.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ESw3qfm-G0QNo24emEt-4N5PM2u3uzDk6xcT36Ty10pFU30KIBF340gZrZlBOuVfk201flgciJJ_srTMDMVC-PwhKoGULKiTle29xuan8wk9c00PuChY0dtQVk9CCp0b.png)
            - An instruction makes a variable live when it **references **it - i.e. uses it. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6vs52I90FDZ1Ve8CUNEXZcV-WEqjWik1lPTpkyVOoVHZ1042oUjXBSDhMj7r8hZc6lPZiEsij9Nt4ic6pYRvUrB-uH2lAyUisKGXDJ3rK8vvy7YN8-elYry_vJgb58R7.png)
            - An instruction makes a variable dead when it **assigns **to that variable.
            - Define functions ref and def which gives the set of variables referenced and defined (respectively) by an instruction at node n.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hOD7B-30TjHtR9b4DxRB2wjRcVLVfwCNOawsu1f4wjq4UDOBVS0iVESW7cEYaEMS4J59iUZLNLC1L50897eNeLEZF4_D706DYw4614GpW44fp8_nvh7Ug5Try9wQH0KI.png)
            - As liveness flows backwards, we modify the reference sets by adding any referenced variables and remove any defined variables. We have to remove those defined **before **adding those referenced. Otherwise x=x+y would only leave y as live. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/57E6K0T-1jHjh1VsFcpKxhKnFMNp5oeIbqiW--NFiod-eMmCSeDsb1iqfdIwywXeYgEiUMYuvpvNz8tsGOaKpcZNMMpeDLlk8Dw7cXAeTd6V6WAhdDdI3Sw8v55-BMSh.png) 
            - Note that in straight-lint code: **out-live(n) **is just in-live(n+1) - however not all code is a straight line. So we need to combine separate paths when there's a junction.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3_DKSBlIIjMw5dkUD89fnpjklZgPTkGzm1x30hiU6qj7XuX7viUwZQMNES0OsLHYOh-lD1gQG0s24sbcOb02M1fhBO8V9fmLMIYJQ8AztR5t50j_-gP5VRymkymeK2BN.png) 
            - We take the union of the in-live sets to get the out live sets - we only care [**if a variable can be used **](https://remnote-user-data.s3.amazonaws.com/5n8Wx3mESanhcO9AWIpVy41ZBjKGbsMesHYEBerBbtQ58aK1W3xCBuZ6yp9MeKPgq1o6-fhZ7CKkjD1IUPA7ZWpW0UjEoBzSObfLMqP5uDN7Gla9D3ZKXDCErJ6uEk04.png)not where it can be used.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5n8Wx3mESanhcO9AWIpVy41ZBjKGbsMesHYEBerBbtQ58aK1W3xCBuZ6yp9MeKPgq1o6-fhZ7CKkjD1IUPA7ZWpW0UjEoBzSObfLMqP5uDN7Gla9D3ZKXDCErJ6uEk04.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1ucGWUorOVwcPNfg_TS9wTbAwPn-vsMU4s9KvnBrLS3SoB2ZyvkOuvGTXbEUCINU4YgZ4fGH_Zof063de7zz_cjoBdFACu480XH1enMLErlaP4vCmPoJGE--w48ug_Wn.png) 
            - So, we have the data flow equations which we can combine:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i_d-GcLW1LHIp8GHSeLBkTchUCbSAFIXaUdk9CBg5kXPAE2CRznuHF9QLAWYL7cMd-EkIKJH4Uvxjbkss_FFoT5-GmwNfDIYTjk6a6CIi0Z_t235MmnlkuF4tloUmnTl.png) 
            - What are in-live and out-live sets?→The set of live variables right before and right after an instruction executes 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NqcYMFtMCjge1VDFdYafndxA7QkKm2iNGoAb_SULeZtoQ9z6w0tZlPzlUs7XOicTNLT2tIlzAi6ZGASWWkf7eji5X7p4cbQ1SHjHaqU8m11n_6RZ8xZfAD38W9vzjung.png) 
            - An algorithm to compute this is to iterate over the flow-graph and find live(n) for each variable. Adopt an iterative approach. You **keep doing it until nothing changes.** 
            - What's wrong with this example of a liveness algorithm? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NydHgY-fQf5j2a_1QFeEcpXjmchhXY93NRh53CYxxnwFvvxE3JbbLJcnx-G9voCV2CNFIjjDAFOUX7JYfxTp6_fhUy6st3zh9D8CUAtapEKerzOCcujzUUdCrMYHz7Bm.png)→We've calculated this using {y,z} = {z} U {} (as the out-set for def z would have been empty on our first pass). What we need to do is do our first pass, then find that the correct our-set for def z is {x,y} - then we have **both **out sets for ref y and can combine them. I.e. {x,y} U {z} = {x,y,z}
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fD1mmwN2WGY8kXLH4RWSwfu-_yAvMOnrCkIOTU-yd4cExegnUpPS5-RUbStotjEVMT3FWkjXq4gL3pc3ldsdPyNy6Ns3gDnqlnhRb7fPWfb8Xe7XrdqHBf5zF7VPM_6q.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yqJa_NlHUvt9LHZ6om3GdzmQ-PdUq_XIp9dxHyOfckcpeyRWGQfhVxhBMugoZoH33wTly32hVmSvmPQs-7Vc9WBSc3IrUqYV0uKggNeR5nrQKzjmWHZ1LEyZQ3JR_4aZ.png) 
            - Algorithm is guaranteed to terminate since there are a finite number of variables and the effect of one iteration is monotonic.
            - Furthermore, this algo is guaranteed to find the smallest solution.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/k45z2rYxh3tsOeJ9PtGmHyh314UK8JMRnZrLtLi_CmJ6NSp2NhHvPEUROQzlwXcbQ_scA7CaOY93dxonnc3Yc6w2BLdvEGyiNh7WYB89l-_qRS1aypr38sQ_sTB2A41u.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/k-gXVVH5afXkibQb7VByb8W7yypBPUCudAK7NordQ-gRerJDRrZnpAgTQPaJ9BepGWkdiX3LbAAAbS46ViiiH8_ZjJitJZtl60Hb4CK19RVprY4V-A47Bc2nY_zHIAYR.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R5HslkkDSs_r_Ki6fdYcIKxWI5McUkWy1JYgPhtGbBBYWqp5WR24vkNXf8B9rsGSwCI_61aC0bW0WH-yKjbH5kD6rdbXITr5agLgO0clLKnD9F3HczTkvORqrHQNrXjK.png) 
    - 
- Lecture 4 - Available expression analysis 
    - Programs can contain code where a calculation is needed, but it's been done before ⇒ Redundancy in the code. The concept of  __expression availability __ is useful in this situation. 
    - Expressions
        - Any given program contains a finite number of expressions (computations which produce values) - so we talk about  __ the set of all expressions __ in the program. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oXUjYeF4ETtWsc0Y5Jug33khfGkpkkvgTLjwWPjlAS5etC9btLDfOIbIhCNV0crlmpN6qBJO100TDF8b4cW0eMWMCLo_UIrtbACirMHDwexc-OCH7WceNuxplQCGCCPG.png) 
        - What is **availability**?―A data-flow property of expressions, has the value of this expression been calculated previously:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vPo-ziw1fDnmYh--wZNxz931gAD8_Aj-tqX-X3yKqtfdEgLdmKPJ7Qm9eEXZ4I_a5IxmntxGY6Kw17z7iCak8l7F5-43ybbJWmHVYo0mzNSGSG9GmFA14FD3lsBa2Hs-.png)
We examine the set of expressions available to from each instructions perspective, we look at the set of available expressions before and after an instruction. Very similar to liveness analysis.
    - Semantic vs syntactic
        - Availability differs from earlier examples in a subtle way - we want to know which expressions are  __definitely __ available (i.e. have already been computed) at an instruction, not which ones  __may __ be available. 
        - We need to consider the difference between  __semantics __ and  __syntactic __ to find the differenceL 
        - When is an expressions **semantically** available→If at node n its value gets computed along (and not subsequently invalidated) **every execution sequence ending at n.** 
        - When is an expression **syntactically **available→If its value gets computed through every path from the entry of the flow-graph to n. This is a computable approximation of the semantic availability. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i2T_Z_aFznDWFeVJFezKiUFmkIVJeupUM5JyZeu37nYuX04eniTcnj5ktsALMgCyfBVD6XpihMGJZ5pTB8wBsMUNgroumeL5sXd8RSSGFbySYO9jDstnDG8YIADU3hEl.png)
Semantically available but syntactically not. 
Note that the $(x+y)^2$ will not be available **either **- we don't know their the same things 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/phW3d2mb2HuUNgJ1RpdTZxcImhoYrelTMENrI7qO6F8u0iNkrCa-yX2Vh5Ef70Uc2aa5hGyadcYTsF4RA2IvFSuATy9tC2fxVzSN8XtcwtHuhO_ZQ5yJUj4vedoIGVhk.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/L1pf2Lg2PIs7KieFAu-GY85A-FEjZuWQXy3oEzcxxNNrJrOWdFuiyMtp-hJHSrZ8t6vDqyLwtejZyYtTvBU3BY2eCIetvh7VvdT-76i6lwawFbh8TEkVmmyz5jShVcwk.png) 
    - Available expression analysis
        - Forwards data-flow analysis - propagate facts forward.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/C69vC-La2dpVakbTwcn3x38bHhRY968zt2xg-oDh8iU6AQ5QgfGND2Q4hfk9w0zf_rDxqneHUbm3IT2Nq1fXtOSX4zkx0W02Jyhd7MFzu9Qnpe-wN5UC7aAHZ5TUEthj.png) 
        - When is an expression made invalid?→When it is **killed **i.e. when we rewrite or invalidate a value in the expression. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WrqglLEEMmrc4cLNKithEOEJa7POFUImHWt3H_CkXUXYj90pf-kaAjtXdAZHWDDJXfOJvGcszmcP4fFVziLyCSqGPtINAFz01elI7GD3LFP1vQQYwW9zsAzMq-Y9E45A.png)
        - We device  __gen(n) __ and  __kill(n)__  - which give the set of generated expressions, and killed by an exression at step n. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-W2rAMovsvQo16Pn_bBk_aICgX_AG-_LBPSrodiHFscdCkBLWT5Op8wNX1yZ9nLp_euWZC78LNSC4DNliEF5_I422fM__siZz7pRHL0hZXh2EgIxpK8H7MnnvwXYmp_E.png) 
        - In available expression analysis, what do you do if an instruction both generates and kills expressions?→Generate first, then kill. I.e. **x = x + y** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HH2heGxoUTzFK5_VrFEA07SeWm6Qac_e9swju4x0m3vJcplyJDuaAP9SsMhQiHVP46YwkBZ3HRSkHzshN8it_mVBrSgGEHOetfxyjZ68MX8ozZdji6L1oSxkVhwEtbj1.png) 
        - When a node has a single predecessor, then in-avail(n) = out-avail(m). However, when a node has multiple predecessors - you need to unions the available expressions. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UghWeHbwgBiWnw8KkXoibJs8CUpIkbBjQIu180Mz3s25THg3fvgmDSH-qe23wl44dMN_MhZB7YX6VD5H2S62ZKQGhQ5_16RwJvuAswqL2PGctQPSZJivInsDK-RZ6SpF.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OyOFsIRaAJx0SffAveLK4J-c6RRdUf5UHu7LsDcp-zoeR_cHsHOpTAytziKKbCRqZi7khf0QI0V2N5zuePgxiL-mVe4fOa9pSrFwTmNmRej0xJLFDncmHijlSNGGci0x.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/y0p_KXwvYI_OsT9GmjAkdWy0Ma1KwW6Fj8itxKmI9aTrXAbWlPbFxOtnZU0kPiY6TJ_copL1sgt3YT1-CgHLrn05e4ArE7dh1xQ7B_a_yWUfdTiQn4nkaujmATZQbFBx.png) 
        - We must make a special case for the **entry point **to the procedure.  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9K4X41Ue8n9Ysa3zypJr-NdAt2DiT7HOgoIQmkll2-tkQwSWsp6En8lCnm9RgnTykq_BgqlgdgDnVUfg2ynyw9TX9gSKUyx8fKfAaJWYBiPyQSv_MUDd-2pp79hJ3XdL.png)
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eNg0z5RhdbFWEMr_fqKmVRX7Z9Zq2slc6S-RLm_ufXzzKrNkBMUyExup4zWJ1rZxS3hVX0TtuO4ucmH6g3HsjAy50750Y5XSXaQ9gP9JFOHwO-Zz1ZKdZiXiNx9TrxWI.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pzdv9ItxfTtBP8cDtA7eKERHZU7r-GNmAkn8GvY5eE8AAnjQ9KdMu8EDaxSG4i9KD6U3VWGYai1kAmt8ggX2xYnqTy8trFdO03NLtyfClbcDe1hh3raSRqqFVaitoVa-.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D_C6JSIPHltWLGrLOZ-wrK6XWVjTH9yiFqpRWutDPi1awmGbUQdw5i-utdO2Hr1M4gkE51kFeU2cfH5BfTbGbWmpVoV-GWHDhktsg41Z04o7RzVpatJs_v0TKYVILr5h.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ym_ywoBbW4z_c6CGlsw8ScpavIgUxR1HjHjyO2hvcfi5Th_AdbZRE457U4BsNV-WxT8QJ_H6l9rNO_83yGpiRuov9t6Gpy2402FAiIEx5wFuuq4si1k9ij9xDUKHiNtc.png) 
    - Algorithm
        - We use an array to store the available expressions for each node - initially make all expressions available - iterate over the flowgraph until no new items change.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UukpZiIbVLNn5WeU41DUijWnjhINWoyYsuAaiBezMaPSypqS7o0hi9p6lujZ3fQoagXLfKiDAEeJys4kMkWOUkKEeypf3HQ8RMXxoHbLMLH7YxTM1r-jFTJ8Fu3tkirg.png)
Why do we start from 1?→Something because of the first initial variable. 
        - As with LVA, this algorithm is guaranteed to terminate  since the effect of one iteration is monotonic (it only  removes expressions from availability sets) and an  empty availability set cannot get any smaller. Any solution to the data-flow equations is safe, but  this algorithm is guaranteed to give the largest (and  therefore most precise) solution.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/K3mIT3Fp6ntQyPLb6wTF3Ee5VW87igajdKLzmXJianSg5q6hSi1lOYdpa8CTlBHo2R7-EWlLs9XAjvs1KLrBrtWYYI3xlki5eDE76FuwPEiJ0objfmUN7abjw-ka5Gkc.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R9TfCo2Y3cScr8TVrF4HaokRJDu9cZC-TFsOn1cHvPLmwjH_BrFLu9T-B9mpw7tv1s_G--INsj_ECQksCC2cnTb1lzlcCwIvvg_K7uvCfNy1EY4B5RaSnWYUORvJEABb.png) 
    - Safety of analysis
        - Syntactic availability safely under-approximates semantic availability. 
        - Address-taken vars are a problem.
            - we must underestimate ambiguous generated (assume no expressions are generated)
            - Overestimate ambiguous killing (assume all expressions containing address-take variables are killed).
        - Reaching definition - finding how far a value reaches down the flow graph.
        - Very busy expressions - calculating if an expressions is **going **to be used later one. (Along every path). 
- Lecture 5 - Clash Graphs + Liveness
    - Data-flow anomalies, these are where the program is worse, in some sense, than intended.
    - Optimisation vs debugging
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fymqpfeYC21uosGYeThKhgVLiEfDSKT7GdSBcDj7tHG7B9WvPMPUZXvu5ca2laULW7Z2kNpp5hLRalmCh-UhMp69QjnaVNPy3L-P0Ry8iRid_MI5Ii6yM027g-1W7SSO.png) 
        - The compiler needs to able to report a broken program (compiler warnings). Allows for optimisation **and **bug elimination. 
        - Dead code is a simply example of a data-flow anomaly, and LVA allows us to identify it.
    - Dead Code
        - If an instruction is written into, but is not live when after it's written into - then it's redundant.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d6Bugzi-qeUoBHH8GPLnLSQ8zVOupNq0Ak7AN9nnqXZsJLB65p2yum-neDT9Wwu5EXt99Mt96C_sLXTZqzEI32vlMdHSSoQSoYT8UQQCJI5E5aNa9HvIbuTQuQwwRPep.png) 
        - Dead code with **no live side effects **is useless and may be removed. If it's dead immediately after being assigned to - we can get rid of it.
        - Once we remove a line of dead code, other code might also turn out to be dead.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tnyO4B7UQWCGDkbw8TOMpAYY0ua4HzrE7FWMJRbxhTm_ZRmOBnJc8W29GEk06Y-9Ey6hgz6WQxvWAA6LsSE1ZoGilARB4CuSfkmeraFacD0FvEAowCd5xLXNdngzWVYm.png) Here b is dead too. Then a & b.
        - This transformation will keep the semantics the same, but the resulting code will be **smaller **and **faster**. 
    - Uninitialised variables
        - In some languages, it is syntactically legitimate for a program to **read **from a variable **before **it has definitely been initialised with a value. 
        - We would like to detect and warn of this situation.
        - How do we use live variable analysis to find uninitialised variables?→In a healthy program, at the start of the program, all variables should be dead (Remember we flow from the bottom to the top in Live variable analysis). I.e. they should have all been assigned a value.
If there are any live variable, they represent potentially undefined behaviour.
Note: This won't catch every case.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YYbyNiiuMgcOnQ8ELekVKBQCJrtXabS4s7mzU7QMV2IYOs1fNpbDsj_pc6C-sdgU9FUVV1ahRzVdZb01htODBDobA3hBQIXxvER04fHqyq8LEyWCFQo12cfI8mT_7nIu.png)
        - What would be the problem when detecting uninitialised variables here?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0EK9n9lyVZkAugR4_D8nyYExEbUkXp3XtmlUmxNp28nD1mxY9uLjJ9UUdQutktbQ_di0Q3ZKffDLf47TrgIf5Tqr7vMR-t0kpagRWjSYqX8bF1camP_hBo5ZklWRZNRl.png)→When we have an if, we **union **the two possible paths. So we have (from bottom to top):
{x} U {} = {x}  - Bottom if block
({x}\x) U {x} = {x} - Top if. The {x} comes from the path where we DON'T follow the if.
If p doesn't change in the ... we should **not **be flagging this at all. 
        - The compiler can't do anything automatic here - the programmer needs to fix unitialised variables.
        - How do we adjust our analysis of uninitialised variables for **scopes**?→We would say that at the beginning of any scope, any of the variables **defined **in that scope should be **dead**. 
    - Write-write anomalies
        - What is a write-write anomaly?→When a variable is written to, then written to again without being read in-between. First write is unnecessary.
        - What analysis do we do to detect write-write anomalies?→Step through the program **forwards - **at each expression remove all variables who are **referenced **and add any that are defined.

x=11 {x}
y=13 {x,y}
x = x+y {x} - This is why we check the referenced first, reassigning y **after **it's used makes sense here.
y=11 {y}
y=12 {y!!}

E.g. x = x + y ⇒ ({x} \ x) U {x} = {x}
        - Just finding variables that have been **written **but not yet read from. 
        - This can cause problems like:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WvpwXhm1wWm55r8kGFzlNJ1e1hcny-04I8Hm3QfGl1kTC3wi9Etm__wKR3mJCEnnnsFUHMPdxE4I585C3kufftIWR-HcUEDSKXMkedDZu0k61Yc5k-2sqUgsThmEVYty.png)
x **will **be written to twice, but that isn't so bad.
    - Clash graphs
        - We need to map from our temporaries to the underlying architecture.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZRLJvG3w5_fnBBDbJXAZK5BiNKbt-EOuA9r5tHQ3hdRtm7O5yIPML5ufk67XfqNO7VadJ5h84ycnPfBwScKavc77d9FSbjiK4fv-t3HHJ8B2RWo4v6hFWxbYcBBuRRCM.png) 
        - Why is LVA useful for generating clash graphs?→Because it tells us which variables are **simultaneously live. **I.e. Which variables are going to be used in the future so we **cannot **keep them in the same register and overwrite one. 
        - How do we form a clash graph?→We run LVA on our three-address code. Then every virtual register is a node on the graph, and if they are ever live at the same time there's an edge between them:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2ESWYXiE51TTeSaePj_rFQRkw1hud6vjGZbdt3HDeeZH_GJm_-iMoUzLFeBejWCvr8xHsmVemftrag1X1SeWYr-MBBgXlKrIp9AVki0X3d8txqBjFNdYuyMpI10t996N.png)
So we couldn't use the same register for a & z, but we could for z and y for example, because they are **never live at the same time**. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MPYI3iw7pVG3r64oMC7zhl5E37v247RqADlOJgyAngLG3OJMrGB5incFWKPWClRCrdLG4CUyKP53_cukzLjAJuBUzxZfoU94ky4gUuUk-nFH5Ell5PRWLHwYFGJ8vtSE.png) 
    - 
    - 
    - 
    - 
    - 
- Lecture 6 - Register Allocation
    - Motivation
        - Normal form is convenient for intermediate code **but **it's very wasteful. Additionally, real machines have a finite number of register - at some point we need to transform the intermediate representation to the **real **registers. 
        - This task is called **register allocation.** 
    - Graph colouring
        - Colour in a graph with X colours where no connected nodes have the same colour.
        - For arbitrary graphs - we may need a colour for each node. For 2D maps, you can do it with 4 colours. 
        - This is essentially the  __same problem __ that we wish to solve for clash graphs. 
            - We want to know how many colours we need so no **two simulteneously live variables are stored in the same register.** 
            - And what colour each vertex should be.
    - Allocation by colouring
        - We first pick a colour - and try and spread it as far as possible (we decide x is red).:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tpkbFJoV-7IVog1IWJ3CRfIzCu3rkrI4Udh6bnMlMh1AzNBI8Ovl8_xWXYRPbh_M_D2ZRtm3djpISyDdrzrczl1eRd2kQa7FIBMQilKVAUPBxtiYM1FcveiE6VHhVj7f.png)
        - Do the same for as many colours as necessary:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4M-4ma6KZ5eGPD1KBFBEug7jP1vdS7j855MnEbKEaelUZE3OSeVj0ZU--hpw7X5MhqvAXll6qiA-Cna8YuGwPSS_43rvkTiINjviMh3ibn5sxQG4CjblC9p7OHjXrohK.png) 
        - We then assign colours to registers!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XGNT1ClJFJASrrbf4CjvPgKPdHVI8BUIESJzsi8nQ8bSrGhWbSZL_ydHwBpR9GfQE5WMKuy0yDnHw_TV33ohkHRAdFOVfjaZBtCr0pkTGs5_QVUReAQVoE7xb_sb_KJS.png)
    - Algorithm
        - Finding the **minimum **solution is **NP-Hard.** We use a heuristic which yields satisfactory results. 
        - Describe the heuristic algorithm for finding a minimal graph colouring ↓ 
            1. Choose a vertex with the least number of incident edges (clashes).
            2. Remove the vertex and its edges from the graph, and bush the vertex onto a stack
            3. Repeat 1 & 2 until the graph is empty.
            4. Pop items of the stack, and choose a colour that **doesn't clash **with any of it's already coloured neighbours. We will try to take an existing colour before creating a new one.
    - Spilling
        - This algorithm tries to find an approximately minimal colouring, but it assumes new colours are always available when required.
        - How should the algorithm cope when it runs out of colours?
        - What is spilling?→If we have simultaneously live values exceeding the number of architecture register, we have spill them to memory - these have to be loaded into a register before it can be used. 
        - How do we adjust our minimal colouring algorithm?→If we look at an node and it has **more ** __**or equal**__ ** edges than we have colours **(colours = architectural registers) choose a vertex to spill! (Usually **least accessed **variable chosen) E.g. remove it's vertex and edges.
We then look at the vertex again to see if it still has too many edges.
Continue this until the graph is empty, then perform normal algorithm.
        - What's the problem with spilling variables based on the minimum accesses?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/w7JQ5qnFE7rAr00sCQqHU__H3cZ5VJbZYLq8SaC9sk5NEQ9_E-bIK4F7CjDEvb7ZLyDoDZdiol0S_Dp-fe5sNpRg1Yo7e3MTocjVAdiYfg1Wc2eMn-hXU4mfNJChpMrF.png) 
Remember, we need to load the spilled variables into a real register - so simultaneous liveness matters!
        - Spilled registers obviously need to be loaded from memory  __into a register. __ How do we solve this problem?→Start the process giving the compiler a lower number of colours than we actually have. Then the extra registers can hold the spillover. Generally we only need one or two fewer architectural registers, as most instructions operate on a max of 2 variables at once.
        - What is a preference graph used for?→If we have a `MOV a,b`in our code - we can simply store b in the a arch register and cut out a MOV instruction.
We construct a  __preference graph __ to show the pairs of registers that appear together in MOV instructions - this is then used to guide colouring.
    - Non-orthogonal registers
        - What is the problem with non-orthogonal registers?→On some architectures, certain instructions **require **certain output/input to be in certain registers. So we can't decide for ourselves where things have to go:
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lyj-EDeCZqJu--thdK7hZR8Oac3_DxP4L-dNyNkmusGpEOcDMvxdExVjAyN-N1rZsgOuR-uxzG7zUGeRe0VHvT_Ug-lbYwE1TLz4QfCv1vtQ5Ja7GpoCmwHCMc5SHXQ0.png) 
        - How do we handle non-orthogonal registers?→We pre-allocate a set of virtual registers to be used as swap-in locations for the **all** architectural registers.
We then adjust our intermediate code by putting in mov instructions:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HuXwZiEUeh4R7sRuFLO2y2xGh1c23y0IK1JDqjQPR8BGWObSauABmWYprbXuTWBDHX9gUrirCLHfUdUJYTI0gUM4X8E17oND7CTXHfd7PcFhbkBBPT7-bXIF0DOWh3ML.png)
Many of these MOV instructions will be eliminated during register allocation. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DtIccQ7qL8Gs0sNgPpZJT9hqsiwJmeXIkj33H50iQPXNfWXJ8mL4XR4EdZF4We0Jifl0ZoWAznZ4vF06A4kSkUZOIOCaeSYjkw0z_qSJ4iCtNc_4goFaE9jcHUJRp6Ci.png)
        - What do we do about instructions that corrupt the contents of an architectural register? I.e. calling a function could change v0, v1, v3→We can insert an edge on the clash graph between the corrupted register and **all other live values **- so the compiler doesn't store any live values in there which would have been corrupted. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/P_ZT50O7zRReuMts8wqxxJyfpwgK-XQtD4K20hqKG7zexxh6G8F4Lco6jS_A50rAyZmrWgJQ_z8vfNm7nXN3zvQM85zCdZ22bDKFF7VOEJT_Ow9snc94a2k6shlJ2fE1.png) 
    - Procedure calling standards
        - The final technique of synthesising edges on the clash graph can be used for procedure calling standards - e.g. where a function can expect to find it's arguments.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zlPSzlJB7Jp5WYL6gpcPIGECBzDHCsPRtkN5nRvHO1HMC4QXmRyAGWb2uVU_LXtPVK7i4ywB3iHb7gYU-w-VtpnQpRgXX9zukLKE7wjCD5w4wtQdHXy4o8AQambL7k65.png) 
        - **So, **procedure calls may corrupt some of the registers. r0-r3 and possibly r9. 
So we add edges to our clash graph and add colouring preferences to do the right thing.

We also need to add MOV instructions to move the required variables into r0-r3.
        - 
    - 
- Lecture 7 - Redundancy elimination
    - 
- 
- Lecture 9 - Abstract Interpretation
    - Motivation
        - We want to reason about how a program will behave **when it actually executes. **At a particular part of the flowgraph, we don't fully know what's going to happen and which paths we are going to take. To figure this out, we examine this behaviour directly.
        - We find things out by a running smaller simplified version of the program. I.e. execute within the program or  __interpret.__  iplication
    - Abstract interpretation
        - The key idea is to use an  __abstraction: __ I.e. a model of the otherwise unmanageable reality whie: 
            - Discards enough detail that the model is manageable
            - Retains enough detail to provide useful insight into the real world
        - Similar to a map, it discard unnecessary detail while having enough to comfortably accomplish its purpose. Looking at a full 3D model would take too long, maintains too much useless information.
        - Our plan from our abstraction **needs to hold back in reality.** 
    - Multiplying integers
        - If we want to know if $-1515 \times 37$ is positive there are two ways to find out: 
            - Do the calculation.
            - Note that a positive times a negative is always negative. ⇐ this costs less and gives us the same amount of information.
        - We form an abstract world using an  __abstract interpretation __ of multiplication - call it $\otimes$. 
        - The magnitudes of numbers are **insignificant;** we care only about their signs. Discarding the complexity of all those infinite integers, leaving **3 values**. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kzdxBEhK3ydmiWOPx8zz1Sz9CJuLpO_Dg37lAk5HwSY3WJBDIgQcteTymrPdxqF7Y9FWmpWzisM3PVTA_BUf0qExccF3Mv5J7HHHVEBQGK1L_z0DW3U_Lvor4xbFzIuc.png) 
        - We then define our abstract operators:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FpPAEvh6t6-3rHTt1DbwA2U9tLlSStg_qaunPjS-TvuGwrZ0LEtISpqjwSzEB3HEnLTIXJcecfTQGEyh0RKBi_iVf1HIIKp8AJK4GmZEQvAuLGqY5s7-jWwHkc3bsbg0.png) 
        - In general the process is 
            1. Define the problem
            2. Devise an abstraction that retains the characteristics of the problem
            3. Solve the problem in the abstract world
            4. Interpret the solution back in the concrete world
    - Safety
        - An abstraction discards detail, you need to ensure that the imprecise results are **safe.** 
    - Adding
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yBJ_LXPEchpfif3eUP5DoGgAqXFqwPysOpMhuNr2X5GVwGunnkFPQpBrup3dPTkUNcJIWGwNGl4Pyq2W2AH-tUOm1s9eNZu8whiYLgSkEI3_Wuve2Xd5F3TfT-6-R-8G.png) 
        - When adding integers, their relative magnitudes **are important **in determining the sign of the result - but our abstraction discarded this information. 
        - We add the **I don't fucking know **operator $(?)$ - this could be **any **of the other abstract values. Because we want the abstraction to be **safe **above all, we must put up with this weakness. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/t6pCEV5mhy9kVJLzAcf7fHTUCTmhUuuOMfLKQXwYD2VdvOn8wUwnbEGgdADhfrQNiK-8NBqZy-fSlJm4D_mtwVQNSl8NQuQ04_gJuGMHxgJWb6_1swQDmkzgNUNGirJo.png) We don't know how to handle this !
        - Safety
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VB1WSl3cWgJwZMVN0WDZKyNd4LA6oi6b5puNS-xb0uYOcCyne_-vt_ZKF9mo2AjEpYDH7S4lBKvG6CVx0xh5QX5TIqeXVXV2y-G2INdBSf0oHJibosn-D971vHdGj7mn.png) 
    - Abstraction overall
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/96xZpthDjwJSTiSvxo4NamJOhNCqeYsYTtsjGL-pudxhnoWdbbGaf8vziUebMkW1XomTNiHr8cFTomSWCsSs-9u-Ug_yrW5o6hbARJ2hCuqN5LV_2Py1EbT6RrRqgMEX.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uo9z0oZaEKaOU6927P0zmN8NNonjMb-BK-RLKAOW_-QO6DSCNeA8AF6ktl3g-GHsV5FjC_9HFRzYDmEUUNK9PEWzMbFA_V0wygYf0KMnoOqmOzA_US5KOvBMB8aWB7q_.png) 
        - 
    - 
