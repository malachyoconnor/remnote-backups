- **Lecture 1**
    - The abstract definition of a network is→a system of "links" that inteconnect "nodes" in order to move information between nodes 
    - **Defining Characteristics of the Internet**
        - A federated system→coupling of many different networks - ~20000 ISP networks. All tied together by IP, a single common interface between users and the network **and between networks.** 
        - Single common interface good for interoperability, but tricky for business. Why?→Consider should Netflix pay IPSs for giving users the opportunity to buy a subscription. This business problem is important, because business incentives drive a lot of network advances.
        - Enormous diversity and dynamic range - varying communication latency, bandwidth, packet loss, technology (optical wireless etc.). Varying **Applications, **varying **users. etc.**
        - **Constant evolution.**
        - **Asynchronous operation**
            - **Speed of light slow**, server receives my operation after my CPU has gone through millions of instructions. So, **Communication feedback is always dated.** 
        - Why is the internet **Prone to failure? **→All components along a path must work flawlessly, including error prone humans. Large scale ⇒ Lots of components. Asynchrony ⇒ Long time to detect problem. Federation ⇒ Hard to assign blame.
        - The internet is an engineered system, and thus is constrained by what technology is practical - **Cost. Cost is important, lower cost ⇒ more people ⇒ more useful network.** 
    - Channels = Links. Peer entities = Nodes. 
    - Bandwidth, latency and BDP are  ↓ 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/68cshaTQsHYS7T08GVb4HL1DsAaPweAVF0lTy6EqYOHNrxcPyYFhms_6d18JimR4zox1lc3pfggbpcMI26hlHg0juxUYqg97NaOOB-JHHxr18BSQuDfkfNwehLux0VwX.png) 
        - **Bandwidth - **number of bits per unit time 
        - **Latency - **Propagation time for data to travel along links
        - **BDP -** Bandwidth-delay product, the amount of data that can be "in flight" at any time. 
    - **Packet Delay**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/iwVYDBNZeqP2raNkJpBPysGimipgCK6SonUfviFO-ej1ad2J86qvvNNnyN8NH1zRC_M9xO9Gn1rkK6B8UwV5TCFRPX-bpjEZwOOqbECBe8Qj5K-qsP1gAAd0Crnnb0Fm.png) 
        - Includes time it takes to "load" the bit into the pipe. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tQ-o34-sieQG09HZLZRPCImnstnJdY5IHi2bw4gpy247wZrXaRR25--WveOEdZuUljQ8kQbx8f4FyI1CWm_nXt11Qk-yAHxI5fbfwTSiDYUuvn9GprmuD_glu9aebyeg.png) 
        - Different term dominates.
        - Can have networks with same BDP, but very different characteristics.
    - 
    - 
- **Lecture 2**
    - If we have a small number of nodes, interconnecting lines inbetween each node is possible. However, in general we need a **scalable **way to interconnect nodes. 
    - **Switched network** 
        - What are switched networks→One way of scaling interconnecting nodes, where network links are a **shared resource. **The problem is ensuring sharing is done safely, might not want interleaving/interference between messages.**
**![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/B3FXY8lP2qYLEuS5lOsmdEFie0uFkzIVtxLVOHiNGqvTPiQWdTPWxGZ7BM6-QiyTzmVqSGruqeMOZfymQihBxutymlp4tXHWlnJ9cAifP1RxLAn_YtBtfe40XCnsyPgu.png) 
        - **The two forms of switched networks are** ↓ 
            - Circuit switching - used in the POTS (plain old telephone system) - with switches controlled by people or mechanically. Physically connecting wires. 
            - Packet Switching
        - **Circuit Switching**
            - Source reserves network capacity along a path, repeating that establishes a connection. Only then can A start sending data. After message end, you send a ""teardown circuit message
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/2hk3X2advrBVh0hfQHDmLgoKDaCO0sNeDaQMcfN4A4UCMiZ4tn72g3oNtM54K3BiQyUS5Kcdtwv3hdOxZlmqeoH4JjEFPU1u2AFIRc_UuI_KqfEx_iMPrtokeZ58CCm_.png) 
            - This can be quite slow and failure prone, as we may need to reserve dozens of connections. Consider that if a single connection fails/is released you cannot send a message.
            - **Circuit switching Pros and Cons**   ↓ 
                - Pros: 
        Garuanteed performance & fast circuit after establishment
                - Cons: 
           Waste bandwidth if traffic is bursty. **Connection establishment is overhead.** For each connection we **rely upon many machines being reliable! **Recovery from failure **is slow - **Generally circuit switching doesn't "route around failure". 
        - **Multiplexing**
            - Sharing makes things more efficient and cost less, 
            - Old time multiplexing, many wires along the same route, pole/wire is being multiplexed. No other way to give people a wire per telephone.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Y6Y848Wq2KCORgadL4hP7heIUbFkx8LhtlKUcGSnCyGyTl1ybB5ztuQcKZ-R6djOClrZZxwg109FqfpMAh51P1bVKT4ZrkancHbzoZBgzRphVxaWZ0oPugwAg8FpTe7W.png) 
        - **Circuit switching: FDM and TDM**
            - **Frequency division multiplexing**. Consider tv stations broadcasting to different frequency bands. People are given pieces of the available channel - decreases the maximum amount of data sent, but data can be sent simultaneously.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/UKj4XaR01npEZh8o4zx_jybJ2x5BWoxiscC3R0VPFgJJoraeHyek-eL9XI4I4KstK-AG8aTW2-HfbbBFdQSm2smNFvPCSZu5V6LWHo4oqSzkW5A9FYCaSUEJVeLhnJ7m.png) 
            - **Time division Multiplexing. **People can take up the whole capacity, but for a certain timeslot (consider a lecture theatre). Radio used to be News⇒Sports⇒Weather⇒Local⇒News⇒...
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Cowjx_Xu9MV8BraHdFpcfbf9tfZ3z5-N-E5BV_uvalnEw103LUWplG2zDPFHCB170m-xQr3ga73FRPNK0QL2UszFpZx4PYtuNps8jEJJIkJJv3uM8Y0Tc9bbEDiCLBIr.png) 
            - **How is time division Multiplexing achieved**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/QYstAMPLEKh6uKL2EJKgfd0DvlDCrn96VlcMwx9iU0Itp5792CFlrBg3XKZ0fpZGgUoHuXP_ebXzLl7fxOa9obssTkKyfBtzlZVWfpXLwceNkpi0VEetx7-KRVTlUEPW.png) 
                - Six simultaneouos slots, where frams are loaded onto (Think how crosstalk could occur if data wasn't lined up right). **NOT FRAMES LIKE YOUR THINKING** 
                - Relative slot position inside a fram determines which conversation each bit of data goes to. Slots are reserved during circuit setup and teardown occurs afterwards. Capacity will be taken up even if no data sent.
            - **Timing in circuit switching**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/6kEPJfPobG6ODpKponTQCDZ76L62k-AYmizKiSAIkOHuOLKAZ5rpB-g8Bf8d1qDoq4WtDUwM5lBXJ5QNWECzdOLvzsXFWl1eQWrDPFQLvpHbozaf9VeT_lZssx9pCDhn.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/b5PoGvWPGCw1PF5HNmnpU_rEVBPLoGz-lC1AFMeIg8E6jYXOa1Xnbe3XMhPUumTA_y_ldpuI4GkC6fommFUnkmec4TkGFJe3oTgQXgRMSYphgsxEYBKGItOI2zkHJQqU.png) 
        - **Packet switching**
            - Data sent as chunks of formatted bits (Packets). 
            - Packets consist of a **header **and a **payload**. Headers as an API describing things like destination address, length of packet etc.etc.etc.
            - Switches forward the packet to other switches or to the destination. Need a forwarding table to know where to send it. **Each switch operates independently.**
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/yGX72IaZwju2Ai-Odsn2TA499Zk1sas8UMBv_PIM1kz96Obi7rkD7UC1wG5NUpYiXNMJAUupWBin0Y7TJlVC5tcBC8oJpJOaThPJ-Xsk7O36vpZf3BzIeyMKvTZG1ZKb.png) 
            - Each packet travels independently, **no concept of a circuit.** 
            - No link resources are reserved in advance. This Packet switching leverages statistical multiplexing, and the result is we can have repeated/reordered messages. 
            - **Timing in Packet switching**
                - This method of waiting for the entire packet before delivering is called "Store and forward"
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7SD0WybrxjxXWruZ201la_zA3f4u6RrSKG2OSjHuFtWbmGjLMbmQIoa21cWRVG2_ldYBubPVQ6PJIHSfK6AtNfOdvUelI9kcx3mSEVdZ6BGYwNhMCuq_3IUzH_d0ePob.png) 
                - We can even start transmitting as soon as we've processed the header - using a cut-through switch:
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jUdN2RNWsMfZLz1Ah_lHLpTXGzsb68Zje_mkmLhs97N3KHV3khQrAzMe_tEai8WDkTwk7NFD0lNviQfhDTsjPp8sDvT9s__tlxwUWun-FlF9es5iLmYRULyo7lULa9NL.png) 
            - **Flows sharing total capacity**
                - Statistical multiplexing relies on→the assumption that not all flows burst at the same time. Very similar to insurance (literal insurance, if an earthquake occurs everyone who had earthquake insurance needs to be paid), and has the same failure case..
                - Get diagrams form ppt 
            - **Statistical multiplexing: pipe view**
                - Works fine if messages aren't simultaneous. However in the case of transient overload we must do the following:
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dKFgFY-J1msyqWUJv456QmQUEAHUPPS-5zO4JcuRCbS76Y_Yn4Y8mmNis3xMRLKOLbFzoVaE4W9CRPMg5m_tz-MBqqpnbtWzfrHgrk6DVdbI6ZF23JrOaBe28yx9WAHI.png)
Queue will cause some delay.  
                - However, if there is more input than our output capacity we'll eventually drop packets:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/2BhAKrrdOo6JdBTvh5AotbXXN0uloZjqShw6W6z-kSSb_fqM0sCw9BIpMbyUQM0eEwtL_4JaRT1tIcWXUQZb4feH9-Xyp3cEkb5Govt092vsFYqGm8geQVLj1r6_UKIG.png) 
                - **Queuing Delay**
                    - packet delay = transmission delay + propagation delay + **queuing delay** 
                    - Made worse at high load - no idle time where the queue would have drained out. Traffic jams at rush hour.
