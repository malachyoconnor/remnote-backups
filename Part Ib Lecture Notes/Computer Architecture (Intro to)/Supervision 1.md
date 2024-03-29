- 
1. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2UQdpnQ1FkPkFUL4c5t1kWXX8y3CADrCFDn91MYJHDc14YPQZRJNraIwCbbIp89K4lKp_c4rP_kIcGIvHYGgzPMxlPie8s-mfFv3OwXYC4kPYjfGX5OrK1qSldMXblyW.png) 
    - Moore's law states that the density of transistors on integrated circuits, doubles (about) once every two years. This continues to apply for the time being, however we are approaching the limit in size of transistors - given that the smallest transistor we could produce lithographically would consist of a single atom in size, it stands to reason that Moore's law cannot continue forever (although we cannot predict future discoveries). However, for the time being the doubling of transistor density every two years is still being upheld. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xYXHCdBxVEZ6SpLlP-ayz2XFjwCy7rNKi_33h8Ft17-nd85USY418aMCx8u1LRpktHyZtvLU8yMgvokFrZkmRMFDkL0vk1EJmqRIId_2caDaXUokQUVpOl0smC6Vz0Ut.png) 
        - While the density of transistors continues to rise, the computing power you can leverage from said transistors is not increasing at the rate it used to. This is due to the breakdown of Dennard Scaling, Dennard scaling is the idea that the decreasing transistor size results in higher clock frequencies at the same power. However, this has broken down as transistors require more static power to run and the working voltage of the system cannot be scaled down at the rate Dennard scaling requires - this means relying more on specialised chips (accelerators) and improving processor architecture rather than continuing to miniaturize it.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Q4ZZGTuw-9knew4SIejsy_O4NY5MIENMPj9WtraKgVUfPcSKFU4XeS2GoYszaS6keQ62ydV4udorTU2XdJ9BwbPsD6FykSnC-dIDlRpqDT5no4GOWHQdqm53hiHH5EYz.png) 
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
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Fw_FBajQEF-Q1GHz6GAARODE3VXBhH3R0LRSkqdRZBXYmxqRgG7vn8gy-EfmFUvKbVD4PG8R6E4mtm2ATTTyn4E3hlZyrRlAn8ZcsIpWvWI84T60DpyNFqGCSomlzvtp.png) 
        - The breakdown in Dennard scaling requires a changing in approach in the design of high performance general purpose chips, the 1.4x frequency increase every generation can no longer be relied upon to bring hardware improvements. Alternative strategies to improving performance must be employed including:
            - Domain specific FPGA chips known as accelerators
            - Limiting the number of transistors active at any one time - in that vein is race-to-dark, turning of cores when not in use
            - Improvements to chip architecture & ISA
            - Employment of different chips for different workflows, e.g. a more powerful CPU (or a GPU) being employed when doing rendering work
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rEOnDKh22cKdx73dq-PcN_vOV8Cxn89SGxibA9BzJ7xQI8S8uQLf6rULEmAM-eaeTDB4Ug_Uer2MECtP2NkXhQ72OTzE_UTYrbJTWJwoOjKvDbK3WuAUaRsHuiK6WyxQ.png) 
        - Dark silicon is the amount of chip area in a integrated circuit that cannot be powered on while maintaining suitable working temperatures. As described above, the efficiency of transistors has not increased as Dennard scaling would have it - so if all transistors were supplied with power in increasingly dense chips, the resulting increase in temperature could damage the chip or cause a fire.  
2. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IT2dql__fLGqf4GVNEhdRVjR6-BnrpjXNiugp6PTQvw_I9j5k69Tv1Ks--Ykd6G55c_eFnSdr0NXF0Bnfq2S51OWqpezgQTjtNyZgIA6LYsNC6ur2O8y0tNYxfYTKSUa.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p6oneUwYrLCGTrHJs9vTxCUgjN_tN_NPdlHLiLcZ2R31Mlpdau-G6wEKpokuFnXG7JYy8TBo0PPh_tqb-dvSq4DmiVNA-T1lLxeiegE0vgor63iFn6gkmX20JkzBeyQZ.png) 
        - ```c
module seven_bit_nor(
    input [6:0] a,
  
    output [0:0] b);
  
  assign b = !((a[0])||(a[1])||(a[2])||(a[3])||(a[4])||(a[5])||(a[6]));
endmodule
``` 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hvLJ8_w-jNwTuRhid60ORFMQI6QKJZXkC8LH76ZnP4iZ2IE4w0g0eVxf3OW6r5RkQ5ioCwFNi-he9qQbhhPmCi0M9x7sdqXKWkrrkduxhT2DJdtzGg8MmwysRT1TuKr3.png) 
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
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cIXgZzNJHK2WR6WlPb5Xa5O2WJKh45GL9qCrPopl3SFPcaCG-s-u1w9WGvjhgCbyIFpB6r2kDBj2h2Wab-OzxI5hjcdWEk1dr9jAQXL6Hcg3EMaZL8Whr8K88mR2V78B.png) 
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
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6K7crCiuD-NaTWO5HDkgVM6FkAe0Of2_sqJQvWVP3upsUajztlz2m-KGH70D7eVV_cRR_H2gri3BqPGzELahOpgmJNKlqGC3AkLtPehk75w1wo19H5XEy5BjYc71zyOa.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BUjnDkUsxRvCapdfbOZPBKiFsYzgeUIhACSbI38k3SkiAJHDSdGse8ICaWWLaDhY1QPEzayhsBQazHEWL8mEiPFuKe6xKYh2ACD0Ay86olZl4U2_cY3jZ_Q8vlc3HAPC.png) 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rOhjWwznStNn4uT7WgYJKTEYQY4qRLbaELNgyfAg_NM3wpopMfnPgCTJQjnNMs_sWeE2SDwzHA8sfu83f4BRt2tp23FdJE-wgyPDlw-hZDFfbhuxHmg4VccfcEJn3ofm.png) 
        - Whenever Ain is 0 & Bin is non-zero, 
3. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/62jYcXcvp5-K-KT9jGUFLq0G8ymM7zsMMkrns5IvjLMBDOFIj_hYmDl0Uu-FPw3unnSyFYHrkKInj3tYN7P7WcJIENoO7_UWgxJx9CieJwrKeJ72aOLVsCwi4GZLAmri.png) 
    - The mystery module behaves like a stack. 'head' is the index of the head of the stack and mem is the equivalent of an array (that head points into) that stores that items in the stack. The opIn command puts the value in dataIn onto the top of the stack and opOut simply moves the head of the stack back one (allowing that value to be overwritten in the future). When the module is full, if we try and add an item error will be set to 1, meaning we will not be able to add another item. Similarly, when we are empty and we try and take an item out error will be set to true and we will be stopped from doing so. When we are empty we have the additional side effect of outputting -1 in dataOut. op decides whether we are inputting data or outputting data or neither.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hUkjVm7UBOSGw-ABIHcSOtftvD9mLbfGtF8VIgib2ETzsgFn_3vwsXGxUFPyBesxk70KJMVN-DGsja5FjlBTelQFspG3eQMSnM_LpRYyv_H9nyR77FhX4LWjKMsxofik.png) 
        - Production tests are used when the chip comes off the production line, it tests whether the correctness of the board is maintained throughout the manufacture process. Functional tests are done before production, and ensure the correctness of your HDL code.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ufaK7X_Tg3kA8QzEtneISxNOefoDhJE0V6Bwh8EMdc0lNl24lQDjdz45KY_jSQnZ3BoMOUZaiGkFQh7PHbsB_cERPZb1pGLlXTkJ7_H-wzYumQeY3U19dJK9j7kMQG_s.png)
        - The mystery module is parameterized by the width & depth variables, thus there are a huge amount of permutations of those values that would need to be tested. The opIn, opOut & opNeutral values would all need to be tested - and varying ordering of the commands would  to be tested, resulting in thousands of possible permutations. Additionally the correctness of the outputs of the stack would need to be tested according to varying inputs.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/61sohsSD65S5uRDO7M5mmOgV9Cl-ttxt3bT7agOqJCBQKBffyOlE7wriUFv-K7DgJEA2Ypjvj8YJOmEqUlqVRJrugPn9eJvIEfwbDq9tse1AiMDeUsoDqHjZyftziDRh.png) 
        - Similarly, the correctness of opIn, opOut & opNeutral and permutations thereof would have to be examined as well as the effects of varying width and depth - however less permutations need to be tested, as we have concluded the logic is correct and are now testing the physical board where any problems would appear with less nuance than a small logic error. However, this process is made more difficult as we are using a physical board - it becomes more difficult for testing in parallel, and physical factors like temperature and humidity need to be considered. So individual tests may take longer, and we must ensure the board is kept at the conditions it was designed to be used in by users.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/L9w2S79jAzPJe-B5MEgJrZ03BGSBkt6ryzB0yvzSWy6YJnEalCGKflbVuEEnCT8EnxOGZGmphXuvmJHHIgbQbo5e1g2J3nlZ3sSZhNL8s3thrK64Ai1YlI9irxlIGCQq.png) 
        - SystemVerilog is a hardware description & verification language used to build logical models of hardware that can then be simulated & tested before finally being implemented in silicon.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/s_dGIjzu1_bYbflvHG1GqIQhDr3wBoOryD0wRVWVCyiN6pAc-21l-DmB-dHReBb1K4qy7jBN09IW3LXdZ_Er7L0PsQNeynZaSeNrZK5awAt4wP1JLQnjySt3ubgF1bHM.png)
        - Meta-stability is when the output of the flip-flop takes a value with voltage between that of a high & low signal. It occurs when the input to the flip flop changes during it's setup or hold time, and the flip flop captures the value of the input as it's changing.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rljtTxKhNSKzEPi1Q5loesdd1fpx_6hXt-vg42OuntEKsxFmYR8YCUiuM_cGTjeV4PMnY7az-5OR-AB6gUor50g7dvs4gHpRrUzmsOADWhjf35daaVoLOl9YYuVEt_5U.png)
        - FPGAs comprise a sea of interconnected logic blocks & IO units. These logic blocks can contain complex features like flip flops and lookup tables, and can be programmed to implement a variety of functions. They benefit from being directly programmable by the user, that is one needn't invest in a chip negative for millions and produce your design in silicon - this means programming one is much cheaper than the alternative. Because of the vast array of logic blocks, FPGAs can take advantage of massive parallelism resulting in quick computations. However, FPGAs are much slower per gate so this parallelism is necessary to reap a performance benefit.  
4. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9JfvfQNG88PPatL-LGthmAf1ekA6VqJBTBChY92IumRxKw24x0ntjkLvUzM3ZV_UObXKGqhdW8oZCKDv9HvetY8ptV4R6SvHMBd1ReiQGfLE3VqcKcrEsKWXtP0KCHIi.png) 
    - In C's case first pre-processing is done where the plaintext elements of the code is changed. Then the compiler compiles the C code to assembly code, this is ISA dependent as different instructions will be deployed in different architectures. The compiler will employ tricks to improve performance while keeping the semantics of the code the same. The assembler then converts this assembly code to object code and finally the linker combines various .obj files into a single executable file containing machine code.
5. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Sdh8cPzeyLI-XzDa6wMfkiZYUB6H_Zki2pKhO_YN3Ns3c_Cd1JHwxAtAhDZ1pu1Ami8Tl67xRH55V6FFll45UCaBIp_jWUQ7AO4j4wtkLEoRCqk4knF7CI_GcEe-lMhw.png)
    - Clock Speed - The number of times per second the CPU clock flips, equal to: $f \leq \frac{1}{\text{Time taken to traverse critical path}}$ . Operations can be segmented based on the number of clock cycles they take to complete, and all are sped up by increasing the clock speed.
    - Number of cores - more cores allows for greater parallelism and thus a potential speedup, this does require software to be written to take advantage of parallelism.
    - Cache size - as fetching from memory is such a slow task, having a cache large enough to minimize those expensive calls is very important when trying to improve CPU performance.
6. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/g0pdH_L0Ima0pUXs9OKScuB2D6KMgpQBOK8bRQXVNuGGd4YUOCHTjIuTOuDn4mbe9YjsJu96F3uCt8T5d5g8-3koJVb3dsY5T-P1_ZtOeXm0cm2F_khcU2PV50yInyY_.png)
    - An ISA is the set of primitive instructions the CPU can perform, ISA matters for a number of reasons:
        - Ease of programming - One can design ISA instructions that couple multiple commonly combined instructions together to make the life of assembly programmers easier. In RISC such instructions could be left as subroutines.
        - Making the general case fast - Including certain operations into the ISA can result in speed ups in specific operations that will rarely be used (e.g. supporting integer operations) due to pipelining. Thus choosing which instructions to leave out, or how to use non-special-purpose components for a given instruction requires careful thought.
        - Some parts of the modern software stack is ISA dependent, meaning porting those sections to modern systems would be incredibly expensive. 
7. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hSiQu5PlT8ACwIkSvrP7QR59BevxaMb9YVZOVrd72gcmD7ONRE87Qq0XY_iUHb-sZke0qV9Mo3060_YtFMjL3kjOJu2x8zQoyUG6we5DDRM8kYSGECzgwqA61IXsyqee.png)
        - Moore's law makes predictions about the density of transistors on the CMOS chip (namely that it will double once every ~2 years) while Dennard scaling makes the prediction that clock frequency will increase by 40% every 2 years while keeping power the same. While Dennard scaling is based on the assumption that Moore's law is true, it goes further and assumes increasing transistor efficiency. Dennard scaling broke down in 2006 as transistors required too much energy even when not switching, however Moore's law still holds today.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UY0yfJpN6phy-eB9hvgQ8zb-XyGz1uy9gljT2bTMYvVfdOY_EehHgKuHVUtdm-aK4iLXdRS_gJN8kk9kNvtfh5QBu_Ks21NuUw_QuEqCXalCgUT-Su4MqvY2lq6OPKZp.png) 
        - The critical path is the longest path that data can travel in the circuit - an exhaustive search could be carried out by testing every input for every state & measuring the time taken to finish computation. Alternatively, we could model the circuit as a type of graph and compute a breadth first search - recording the largest number of steps in the search. The critical path directly impacts the maximum clock frequency, in that the clock frequency is:
        - $$f \leq \frac{1}{\text{Time taken to traverse critical path}}$$
        - Thus, decreasing the length of the critical path would allow you to increase the clock frequency.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sZU5STJY-guUdE3BQKXz05R38ufvi96_JuO8__Gyvy-s_Q1IZ9jQ2FMe83wU57ZB1AyOmj6Q6vhwYopP9mIrqF_gwdK52wpZVyQFbII2GpcxT6E7JRL7sJiwee9hg3wq.png) 
        - A calling convention is a low level scheme for how functions receive parameters from their caller and where they do with results, for example MV r0 r1 moves the value stored in r0 into r1. It can impact the design in a big way, calling conventions imply certain big decisions such as:
            - Max instruction length, decides the total number of instructions possible
            - Max number of immediate parameters to a function, e.g. parameters that don't need to be fetched
            - Where return addresses are saved
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BlFcoIXChRxj-7sJ7kp-w1qtgRgmJVcwHgNY9niWjD3TvdTtUvetXCboQ-cPtmM99T17rV38pCr_s6_zcGGjV1gQjSxxBDzzPhZrcLgC062aMOSSTZ4l6eEFqpLRvye4.png) 
            - Section A: This section checks if we need to do another round of the function or if we're finished. If a1 ≠ 0 then jump to .L7 otherwise jump to ra (this will either be to the initial function caller or to another instance of gcd)
            - Section B: This section allocates space in the stack, and saves registers so we can make our way back up the stack frame to the initial caller. Allocate 4 spaces on the stack, store the current return address in the first segment of the stack.
            - Section C: This section computes the modulus and recalls the function with these new values. Set temp = n2, n2 = n1 % temp and finally n1 = temp. Then jump and link to gcd (storing the current instruction location into ra).
            - Section D: We'll reach here if we've previously completed section C and section A finds $a1 = 0$. Here we retrieve a previously store return address from the stack, free up the stack and jump to the return address. This starts the process of unravelling the stack frame.
8. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sBPoSMEcGwfeclHCQG5umDhvhCzuEURc3ZFKjKlKxZWrAqVUb05SDX2eaWMJOC8QpkfIjBRGoNxhcRdC4XDdaIiJtDvfcRC-5S02rkInpNg2NzzkCnvWZBbX9yoCyJl0.png) 
    - Von Neumann style processors are not the be all and end all of general purpose processing, the incurred Turing tax results in slowdown & massive power use. As the golden age of silicon is over, we need to consider accelerators & other methods of improving performance that our outside the Von Neumann box. 
9. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xzHKmOBmsp5VTUoRYJqnaeoGLIMjg6wfYAlFayAT7WDYyE3UH1rDsBABqCNr8M6_ZfUR7SyD0-tUrPiXdfiXuO3t1uuT3vqOiMDug6FC-Z0X_z9Z_q2JxwWc_W0nGfvb.png)
    - Clocked digital designs are used everywhere, propagating the clock signal is very hard and requires careful thought & design. Designers need to ensure that their system meets timing requirements and handles asynchronous inputs safely.
10. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KnuI9ow0ir_IgodEqmPCY7IHvLAA5uGz_W4OqIwyGOIrbGVgtUaub1gRxD2OMrQg2JLYTmNUH5OKJLuUMoJLFzyHknqz358TnMcq-rMQVSx21tmKPfKUcYzwonBnDHlT.png)
    - There are many possible elements to optimize in processor design, and while one optimization could help a given workflow it may hinder another - thus there's no perfect CPU architecture only compromises. The Von Neumann model doesn't help with improvements, most transistors are used moving & storing data rather than performing computation. 
11. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/M6Mcdr232g4ok7gXv5Jnt0aBIXo-zv-LY1wfcfH3O-o8qTWJ_IbgZSIJJN-ma2PeMKIeiC8JlpD4XwHqS3srsVvlCk8lnU8OBJjeMph6pjP8HqEP4LLLL_GZ1rw1InkS.png)
    - RISC processors are often simpler and lower power, but CISC still dominates the PC industry (ostensibly due to backwards compatibility issues). RISC is used in the phone & microprocessor space and also in the research & teaching space as it is open-source and (relatively) easy to understand. 
