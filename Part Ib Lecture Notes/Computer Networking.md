- 
- **Lecture 1**
    - The abstract definition of a network is―a system of "links" that inteconnect "nodes" in order to move information between nodes 
    - **Defining Characteristics of the Internet**
        - A federated system―is a system of many networks, **coupled together by a single common interface. **
In terms of the internet, all tied together by IP, a single common interface between users and the network **and between networks.** 
        - Single common interface good for interoperability, but tricky for business. Why?―Consider should Netflix pay IPSs for giving users the opportunity to buy a subscription - or should the ISPs pay Netflix as users may buy the ISP simply to use Netflix. 
I.e. interoperability allows for using the ISP to use another service, where does the money go?
This business problem is important, because business incentives drive a lot of network advances.
        - Enormous diversity and dynamic range - varying communication latency, bandwidth, packet loss, technology (optical wireless etc.). Varying **Applications, **varying **users. etc.**
        - **Constant evolution.**
        - **Asynchronous operation**
            - **Speed of light slow**, server receives my operation after my CPU has gone through millions of instructions. So, **Communication feedback is always dated.** 
        - Why is the internet **Prone to failure? ** ↓ 
            - All components along a path must work flawlessly, including error prone humans. 
            - Large scale ⇒ Lots of components. 
            - Asynchrony ⇒ Long time to detect problems. 
            - Federation ⇒ Hard to assign blame.
        - The internet is an engineered system, and thus is constrained by what technology is practical - **Cost. Cost is important, lower cost ⇒ more people ⇒ more useful network.** 
    - Channels = Links. Peer entities = Nodes. 
    - Bandwidth, latency and BDP are  ↓ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/68cshaTQsHYS7T08GVb4HL1DsAaPweAVF0lTy6EqYOHNrxcPyYFhms_6d18JimR4zox1lc3pfggbpcMI26hlHg0juxUYqg97NaOOB-JHHxr18BSQuDfkfNwehLux0VwX.png) 
        - **Bandwidth - **number of bits per unit time 
        - **Latency - **Propagation time for data to travel along links
        - **BDP -** Bandwidth-delay product, the amount of data that can be "in flight" at any time. 
    - **Packet Delay**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iwVYDBNZeqP2raNkJpBPysGimipgCK6SonUfviFO-ej1ad2J86qvvNNnyN8NH1zRC_M9xO9Gn1rkK6B8UwV5TCFRPX-bpjEZwOOqbECBe8Qj5K-qsP1gAAd0Crnnb0Fm.png) 
        - Includes time it takes to "load" the bit into the pipe. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tQ-o34-sieQG09HZLZRPCImnstnJdY5IHi2bw4gpy247wZrXaRR25--WveOEdZuUljQ8kQbx8f4FyI1CWm_nXt11Qk-yAHxI5fbfwTSiDYUuvn9GprmuD_glu9aebyeg.png) 
        - Different term dominates.
        - Can have networks with same BDP, but very different characteristics.
    - 
    - 
- **Lecture 2**
    - What problem do **Switched Networks solve?**―Switched networks are an alternative to having data lines between each node. They solve the **scaling problem **of such a solution. 
    - **Switched network** 
        - What are **switched networks**―A method of **scaling interconnecting nodes**, where network links are a **shared resource. **The problem is ensuring sharing is done safely, might not want interleaving/interference between messages.**
**![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/B3FXY8lP2qYLEuS5lOsmdEFie0uFkzIVtxLVOHiNGqvTPiQWdTPWxGZ7BM6-QiyTzmVqSGruqeMOZfymQihBxutymlp4tXHWlnJ9cAifP1RxLAn_YtBtfe40XCnsyPgu.png) 
        - **The two forms of switched networks are** ↓ 
            - Circuit switching - used in the POTS (plain old telephone system) - with switches controlled by people or mechanically. Physically connecting wires. 
            - Packet Switching 
        - **Circuit Switching**
            - Source reserves network capacity along a path, repeating that establishes a connection. Only then can A start sending data. After message end, you send a ""teardown circuit message
            - The **4** steps of** circuit switching **are ↓ 
                - A node sends a reservation request - desiring to communicate with another node 
                - Interior switches establish a connection, i.e. a circuit 
                - The node sends the data
                - The node sends a "teardown circuit" message 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2hk3X2advrBVh0hfQHDmLgoKDaCO0sNeDaQMcfN4A4UCMiZ4tn72g3oNtM54K3BiQyUS5Kcdtwv3hdOxZlmqeoH4JjEFPU1u2AFIRc_UuI_KqfEx_iMPrtokeZ58CCm_.png) 
            - What are the main 4 problems of Circuit switching? ↓ 
                - **Set up time is slow** - may need to reserve dozens of connections. Get worse the fewer the connection lines. 
                - **Failure prone, **could be dozens of machines you're relying on to work.
                - **Slow recovery from failure, **as they don't route around failure.
                - **Waste bandwidth if traffic is bursty **(intermittent),** **as no other switches can use the line during that period.  
            - What are the **pro's **of **circuit switching**?―Garuanteed performance & fast circuit after establishment 
            - **Circuit switching Pros and Cons**   ↓ 
                - Pros: 
        Garuanteed performance & fast circuit after establishment
                - Cons: 
           Waste bandwidth if traffic is bursty. **Connection establishment is overhead.** For each connection we **rely upon many machines being reliable! **Recovery from failure **is slow - **Generally circuit switching doesn't "route around failure". 
        - **Multiplexing**
            - What is the foundational idea behind multiplexing?―**Sharing **makes things **more efficient** and **cost less**. Having **many telephone wires** along the same route is more efficient and the cost is less than having individual poles for each line. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Y6Y848Wq2KCORgadL4hP7heIUbFkx8LhtlKUcGSnCyGyTl1ybB5ztuQcKZ-R6djOClrZZxwg109FqfpMAh51P1bVKT4ZrkancHbzoZBgzRphVxaWZ0oPugwAg8FpTe7W.png) 
            - Sharing makes things more efficient and cost less, 
            - Old time multiplexing, many wires along the same route, pole/wire is being multiplexed. No other way to give people a wire per telephone.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Y6Y848Wq2KCORgadL4hP7heIUbFkx8LhtlKUcGSnCyGyTl1ybB5ztuQcKZ-R6djOClrZZxwg109FqfpMAh51P1bVKT4ZrkancHbzoZBgzRphVxaWZ0oPugwAg8FpTe7W.png) 
        - **Circuit switching: FDM and TDM**  x
            - **Frequency division multiplexing**. Consider tv stations broadcasting to different frequency bands. People are given pieces of the available channel - decreases the maximum amount of data sent, but data can be sent simultaneously.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UKj4XaR01npEZh8o4zx_jybJ2x5BWoxiscC3R0VPFgJJoraeHyek-eL9XI4I4KstK-AG8aTW2-HfbbBFdQSm2smNFvPCSZu5V6LWHo4oqSzkW5A9FYCaSUEJVeLhnJ7m.png) 
            - **Time division Multiplexing. **People can take up the whole capacity, but for a certain timeslot (consider a lecture theatre). Radio used to be News⇒Sports⇒Weather⇒Local⇒News⇒...
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Cowjx_Xu9MV8BraHdFpcfbf9tfZ3z5-N-E5BV_uvalnEw103LUWplG2zDPFHCB170m-xQr3ga73FRPNK0QL2UszFpZx4PYtuNps8jEJJIkJJv3uM8Y0Tc9bbEDiCLBIr.png) 
            - **How is time division Multiplexing achieved**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QYstAMPLEKh6uKL2EJKgfd0DvlDCrn96VlcMwx9iU0Itp5792CFlrBg3XKZ0fpZGgUoHuXP_ebXzLl7fxOa9obssTkKyfBtzlZVWfpXLwceNkpi0VEetx7-KRVTlUEPW.png) 
                - Six simultaneouos slots, where frams are loaded onto (Think how crosstalk could occur if data wasn't lined up right). **NOT FRAMES LIKE YOUR THINKING** 
                - Relative slot position inside a fram determines which conversation each bit of data goes to. Slots are reserved during circuit setup and teardown occurs afterwards. Capacity will be taken up even if no data sent.
            - **Timing in circuit switching**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6kEPJfPobG6ODpKponTQCDZ76L62k-AYmizKiSAIkOHuOLKAZ5rpB-g8Bf8d1qDoq4WtDUwM5lBXJ5QNWECzdOLvzsXFWl1eQWrDPFQLvpHbozaf9VeT_lZssx9pCDhn.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b5PoGvWPGCw1PF5HNmnpU_rEVBPLoGz-lC1AFMeIg8E6jYXOa1Xnbe3XMhPUumTA_y_ldpuI4GkC6fommFUnkmec4TkGFJe3oTgQXgRMSYphgsxEYBKGItOI2zkHJQqU.png) 
            - If I have a **640,000 **bit file, sent over a circuit switched network. Where **links are 1.536 Mbps, **Each link uses **TDM with 24 slots/sec. **And it takes **500 msec to establish an end-to-end circuit.**―$$0.5 + \frac{0.64 \cdot 24}{1.536} = 10.5$$  
        - **Packet switching**
            - Data sent as chunks of formatted bits (Packets). 
            - Packets consist of a {{**header **}}and a {{**payload**}}. Headers as an API describing things like {{destination address}}, {{length of packet}} etc.etc.etc.
            - Switches forward the packet to other switches or to the destination. Need a forwarding table to know where to send it. **Each switch operates independently.**
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yGX72IaZwju2Ai-Odsn2TA499Zk1sas8UMBv_PIM1kz96Obi7rkD7UC1wG5NUpYiXNMJAUupWBin0Y7TJlVC5tcBC8oJpJOaThPJ-Xsk7O36vpZf3BzIeyMKvTZG1ZKb.png) 
            - Each packet travels independently, **no concept of a circuit.** 
            - No link resources are reserved in advance. This Packet switching leverages statistical multiplexing, and the result is we can have repeated/reordered messages. 
            - **Timing in Packet switching**
                - This method of waiting for the entire packet before delivering is called "Store and forward"
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7SD0WybrxjxXWruZ201la_zA3f4u6RrSKG2OSjHuFtWbmGjLMbmQIoa21cWRVG2_ldYBubPVQ6PJIHSfK6AtNfOdvUelI9kcx3mSEVdZ6BGYwNhMCuq_3IUzH_d0ePob.png) 
                - We can even start transmitting as soon as we've processed the header - using a cut-through switch:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jUdN2RNWsMfZLz1Ah_lHLpTXGzsb68Zje_mkmLhs97N3KHV3khQrAzMe_tEai8WDkTwk7NFD0lNviQfhDTsjPp8sDvT9s__tlxwUWun-FlF9es5iLmYRULyo7lULa9NL.png) 
            - **Flows sharing total capacity**
                - Statistical multiplexing relies on―the assumption that not all flows burst at the same time. Very similar to insurance (literal insurance, if an earthquake occurs everyone who had earthquake insurance needs to be paid), and has the same failure case..
                - Get diagrams form ppt 
            - **Statistical multiplexing: pipe view**
                - **Queue does not increase capacity - adds time!**
                - Works fine if messages aren't simultaneous. However in the case of transient overload we must do the following:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dKFgFY-J1msyqWUJv456QmQUEAHUPPS-5zO4JcuRCbS76Y_Yn4Y8mmNis3xMRLKOLbFzoVaE4W9CRPMg5m_tz-MBqqpnbtWzfrHgrk6DVdbI6ZF23JrOaBe28yx9WAHI.png)
Queue will cause some delay.  
                - However, if there is more input than our output capacity we'll eventually drop packets:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2BhAKrrdOo6JdBTvh5AotbXXN0uloZjqShw6W6z-kSSb_fqM0sCw9BIpMbyUQM0eEwtL_4JaRT1tIcWXUQZb4feH9-Xyp3cEkb5Govt092vsFYqGm8geQVLj1r6_UKIG.png) 
                - **Queuing Delay**
                    - packet delay = transmission delay + propagation delay + **queuing delay** 
                    - Caused by packet interference
                    - Made worse at high load - no idle time where the queue would have drained out. Traffic jams at rush hour.
- **Lecture 3** 
    - **Multiplexing** **Disadvantages** 
        - Might have to **wait** 
        - Might **not know how long** you have to wait 
        - Might **never get served** 
    - Multiplexing is the action of sharing of common resources. 
    - **Queuing Delay Extremes**
        - $$\text{Traffic Intensity} = \frac{\text{Average Packets} \times \text{packet length}}{\text{Link Bandwidth}}$$ 
        - Describe the three cases of traffic intensity and their effect on the queue and the delay ↓ 
            - Traffic Intensity $\approx$ 0. Queue is empty and the average delay is low
            - Traffic Intensity $\approx$ 1. Queue contains some items and the delay becomes large 
            - Traffic Intensity > 1. Queue is always full, average delay infinite - or data is dropped.
        - We need idle times for the queue to drain. Queue supposed to be during panic times.
        - A large reason for delay when sending a message is not because the line isn't straight, or because fibre optics travel at ~2/3 the speed of light. It's because all routers inbetween have queues that add delay
    - **Internet structure: Network of networks** 
        - Packet passing through many networks!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/P_BPuCNYkMCi_mR4m9fZqqUstd6x9GdmhavxKZ21TzbC951rorQ0J_uUnldimaX_WjrAoJI9EbKj4CmB56GCM6xXJQlpPGvn4CsmKIRVK78YRr4MxChVJAw-PaBqIvPo.png) 
        - Tier 1 ISPs:
            - Have a complete knowledge of where everything is, if they don't know how to get somewhere you don't get there.
            - They exchange traffic with each other via Peering links.
            - Most extensive operations team, most expensive routing kit. 
        - Tier 2 ISPs:
            - Pay for the privilege to access tier 1 ISPs
            - Can have peering links to other Tier 2 ISPs
        - Tier 3 ISPs:
            - Similar - pay for privilege to access tier 2 ISPs
        - Local ISPs - last stage
        - **Internet exchange points** **(****IXPs)** 
            - Allow everyone to connect to everyone else 
            - Companies that aren't tier 1 ISPs like this - means they don't have to pay tier 1 ISPs to access their service.
        - What happens if an ISP tells Netflix to pay them, otherwise they won't route their service to you? Netflix will pay 
        - **POP - **point of presence is a connection point of a network. That could be between ISP and users, ISPs and other ISPs, users and other users etc. Particularly large ones are from ISPs to other ISPs.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9zJ4OJK892aZif6rH7L_gtrdKaU8Jx4jpD7mX_oNhrDrsJPSFvYN84mI6E0Xi7m8IC52nuoyzETfH-Gg0Zq25o37l3cOWX2P7tP56GIFJapNGsbr_gsQsdSeqq4BvpbY.png) 
    - **Packet switching vs circuit switching**
        - Packet switching may (does!) allow more users to use network
        - If we have a 1Mb/s link and each user uses 100kb/s when active, **and they're active 10% of the time. ** 
            - With circuit switching, we can have 10 users 
            - With packet switching and 35 users, the probability that >10 are active at the same time is less than 0.0004$$1- \sum_{n=0}^{10}{{n \choose {35}} (0.1^n)(0.9)^{35-n}}$$ 
            - However, under the binomial assumptions - these assumptions may not be valid. 
    - **Packet switching Pros and cons**
        - Cons:
            - No garuanteed performance 
            - Header overhead per packet
            - Queues and queueing delays
        - Pros
            - Efficient use of bandwidth (stat mux)
            - No connection setup overhead
            - Resilient (can route around trouble) 
    - 
    - 
- **Lecture 4**  
    - **Abstraction concept**  
        - Breaking down a problem.
        - What not how - 
            - Specification vs implementation
            - Modules in programs
        - Vertical vs Horizontal
            - "Vertical" what happens in a box - "how does it attach to the network". Vertical monopolies: Consider Texas Instruments DSP processing chips.
            - "Horizontal" the communications paths running through the system. 
        - Partition systems into modules & abstractions
            - Well defined interfaces give flexibility! **Hides implementation. Extend functionality of system by adding new modules.** 
            - E.g. libraries encapsulating set of functionality
            - E.g. programming language + compiler abstracts away how particular CPU works 
        - Well-defined interfaces hide information
            - Isolate assumptions??? What this mean!
            - Present high-level abstractions
            - However not showing your code - **can impair performance. **Missing knowledge etc. 
            - Ease of implementation vs worse  performance  
        - Implementation is distributed across many machines (routers and hosts)
        - You must decide:
            - Layering : How to break systems into modules 
            - End-to-End Principle : Where modules are implemented 
            - Fate-sharing : Where state is stored (connection oriented network, if a node fails inbetween we lose our connection).
    - **Layering Concept**
        - System functions divided into layers built upon each other.
    - **Layers and Communication**
        - Interaction **only between adjacent layers** 
        - layer n uses services from layer n-1, and provides services to n+1
        - Botto mlayer is physical media.
        - **Top layer is application.**
    - **Entities and Peers**
        - Entity is a thing...
        - Entities interact with the layers above and below.
        - Entities communicate with peer
        - 
        - Entities usually do something useful:
            - Encryption - Error Correction - reliable delivery
            - Can do nothing at all
        - Not 
    - **Layering and Embedding**
        - Higher layer information embedded within lower layer info - consider repeatedly wrapping/boxing up :![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XP9YQ0M5kcFGCxEtez0evlz8d1-jW_B_IUjtAWl5v9CLLP_-Y_jKwXRON-3cww6kd_uuKJpa0iliSytt_zfDOpgXNC_WFKqiKwPW7crFRTQStVttlNLWMx9Yron_NC5x.png) 
        - **Embedding is not the only form of layering** 
        - Encapsulation 
    - **IP stack vs OSI stack**  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HrftcK6my4vZZPgZkHTAItcbef7Q_nfPeEJ-qez1xJ0uxhC9K-H0rqR6o58WtZYkmsYXEWyfszQUjpELMG0fgkPDbNv801uaWIdY7i0zIcaUwl3WySaFIO_l6yzUR9aJ.png) 
        - OSI had extra layers that were left to software - next slide 
        - Can have repeated layers
    - **So many Standards Problem** 
        - Many different packet switching networks with **their own protocols **(system for organizing communication - e.g. English language protocol) only nodes on the **same network can communicate.** 
        - The solution is adding **Gateways **between networks:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tZGlX-KY2tNvLPa653K5c78LYl_GtphzGCBikJSaVcWq6fGIyWKG7tpqAe8Y9BPgfo5KDcAAwaPuGXyyjPuiJ_8dkRH8ImFawwYdRAMcY0K0TjSpPJR4pPtyYJxaZvcp.png) 
    - **Internet Design Goals - **retrospective, made after internet was going
        - Connect existing networks 
        - Robust in face of failures
        - Support multiple types of delivery services
        - Accommodate a variety of networks
        - Allow distributed management (I'll look after my stuff - you look after yours)
        - Easy host attachment (Want to make it easy for people to join a network)
        - Cost effective
        - Allow resource accountability (contradicts distributed management - also do we deserve resource accountability? We aren't paying the people who's switches we're using)
    - **Multitude of Apps Problem**
        - We don't want to write code for our app, for every different communication medium - e.g. Coaxial Fiber optic etc. 
        - Solution: Add an intermediate layer that we write the code to talk to. The intermediate layer then speaks to everything else.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oyuNaGmMChbuko44ZmoOxF1LFVqQrFFwNXdbAEHEvCxL50sIijqYA0KwzRZgxzXL7IBO1D0EfTtsRVtaGenQ5wJFJ63Bxip1n2CClJgbp_nIlaM4iNzuWyST_WZzFUw8.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Kq6eyK7F-WPoCFxckOGexwl295R2fuowNMZDKxpkglLTeeP4BI08Nw9nA9q4Q5OyceqC5MUiZxzVEhYm5hitPgknoC9AjNX9MfUrspKc29zIDBJe2IHHjIfniWIiW-WO.png) 
    - 
- **Lecture 5**
    - **Why use vertical stacks?**
        - Make it very efficient
        - Own internet property
        - Own the system
    - **Layering crucial to Internets success**
        - Layering is―the separation of a task into many separate functional components that communicate in a hierarchical manner.  
        - **Layering allows **for  ↓ 
            - **Reuse **of code - whatever application is being run, the code to communicate to ethernet doesn't need to change
            - Hiding **unnecessarily details** 
            - **Innovations **at each level can **proceed in parallel** and be pursued by **different communities.** 
        - What are the **drawbacks of layering? ** ↓ 
            - Can have **duplication of functionality** - e.g. error recovery to retransmit lost data
            - **Information hiding** can **hurt performance, **- e.g. we don't know if we have packet loss due to corruption vs congestion (info not stored in IP)
            - **Headers start to get really big** - e.g. TCP+IP+Ethernet is ~54 bytes
            - Layer violations still occur when the gains too great to resist - e.g. wireless peering into data they shouldn't see **or **when the network doesn't trust ends - e.g. firewalls examine packets 
            - Layer violations when network doesn't trust ends - e.g. firewalls, need to examine the packet
            - Layer N may duplicate lower layer functionality - e.g. error recovery to retansmit lost data
        - Persued by different communities 
    - **End-to-End Principle** 
        - Some application requirements can only be correctly implemented end-to-end - no other elements should access the data. - reliability, security...
            - Implementing these in the network is hard - every component must be fail proof 
        - Hosts
            - Cant rely on networks help, so must be able to satisfy requirements
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Pm4jhvVZqAgYWYdTvep-otuqAdgLnKtRJA5GfTLIJYU068rsmWWIho_0zaVxUMM5fNOoXCaciWNZ9ksSTNWNu_NCvyxcZ13VycOq2A_HRqMwxhm7zTuFltOT11SgXqGC.png) 
        - Solution 2: end-to-end **check if the sending worked, **and retry if it didn't 
        - Solution 1 is incomplete
            - What if any network element fails? You need to do the check anyway!
        - Solution 2 is ... 
        - • Implementing functionality (e.g., reliability) in the network  – Doesn’t reduce host implementation complexity  – Does increase network complexity  – Probably increases delay and overhead on all applications even  if they don’t need the functionality (e.g. VoIP) • However, implementing in the network can improve  performance in some cases  – e.g., consider a very lossy link  
        - Only if Sufficient Interpretation
            - Dont implement a function at the lower levels, unless it can be completely implemented at this level
            - Unless you can relive the burden from hosts, don't bother -
        - Only if Necessary Interpretation
            - Dont implement anything in the network, that can be implemented correctly by the hosts
            - Make network layer albolutely minimal
                - improves performance
                - lower layers more flexibl
        - Only if Useful interpretation
            - If hosts can implement functionality  correctly, implement it in a lower layer only as a performance enhancement • 
            - But do so only if it does not impose burden on applications that do not require that  functionality  
        - Distributing Layers across network
            - 
        - What gets implemented on a host 
        - 
        - What gets implemented on a host
            - Physical layer  - 
            - Datalink layer 
            - Network layer
            - Transport layer NOT SUPPORTED
        - What gets implemented on a switch:
            - Same, but no Network layer - just local delivery. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vjr4ZaxAgWVNqv2GfEGdv49-r23QR5WyeZhUMwEZqsmi-bLF_EIZPvrvdPlQBZr8Bchhu-YRRVNeN_uRfcJqA35cfdBYLWuFZK3Qx7mDtYBt_7BxraRO3I7B4TQ2oM4a.png) 
        - IPV4 and IPV6 not directly compatible
    - **Alternative to Standardization?**
        - Have one implementation used by everyone
        - Open source projects -
        - Or sole-sourced implementation, only their code will work with their own
    - 
    - Skype, FaceTime, Signal ETC OK ETC EtC CETC ETC etc C!!ETC 
    - **The physical layer**
        - The copper glass or wifi - Comes with the fundamental limits, that of light. Coaxial cables and twisted pair cables are bidirectional - as opposed to fiber optics.
        - Capacity, delay, fidelity (signal to noise ratio) all limits provided by physical layer
        - Bandwidth is BETWEEN to things, e.g. 1.0 and 1.1 MHz = Bandwidth of 100 KHz
        - Some frequencies area **supported **by media better than others, for example the atmosphere doesn't support the transmission of infrared light well - it get's absorbed.
        - **Radio physical media**: 
            - Bidirectional and multiple access.
            - Propagation environment effects like reflection, interference and obstruction by objects.
        - Fidelity is the **signal to noise ratio.** 
        - **Analog meets Digita****l** 
            - Need to make transform between analogue and digital world. As the **world is analogue.** 
            - Infinity of frequencies to form a square wave. 
- **Lecture 6**
    - **Analog meet Digital**  
        - Square waves have high frequency components, resulting in random super peaks as below: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Df2mRJBJKr-Esgexa-4bOE-JzqC9WnT9t8wFHJCV_AFoEuMuusiHFNJIBy2uh6YFiyG1Qzo5clVKADknt0nxwk2Kje9NURYrFyGHd4IVZGsoVHFWa5vFaT7jNu6a9vUi.png) 
        - $$\text{Received Signal} \approx \text{transmitted signal + noise}$$ 
        - Noise can be systematic or random - e.g. systematic noise from equipment or random noise from thermal vibration. 
        - Noise increases in distance, so larger systems can be less reliable.
    - Bandwidth vs Signal to Noise 
        - What's better: High bandwidth or low signal to noise ratio?
        - Information capacity is measured in bits per second, of a channel. $\frac{S}{N}$ is the signal to noise ratio.
        - $$C = B \log_2(1+\frac{S}{N})$$ 
        - Channels with no noise have infinite information capacity. Channels with a Signal to Noise ratio of 1 have information capacity in bits per second, equal to the bandwidth in hertz.
    - **Digital channels**
        - **Symbols **are the voltage levels on the wire, 5V 0V may map to bits. 
        - Baud rate is―the rate that symbols can be transmitted. I.e. the number of times we can change between different voltage levels in a second.  
I.e. The number of indivisible units of information sent per second.
        - Why are bit rate and baud rate different?―Our bit rate can be higher than our baud rate if we have multiple voltage levels to represent more than 1 bit. E.g. if we have:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j38PlNezW40gwwE00P_6yI5Ci6OgGUXH2l-o-wcSF01RKLjilt-2J-_9Z46sFEHl3ecnjhlhR07XyQProaa0_ing3an2T6XOVW4tKvN-dJzfctCvisgQ0pD_KIoFzhEk.png) 
The bit rate has doubled as we can now send 2 bits per second, but the baud rate remains the same.
    - **Modulation**
        - What is modulation?―Transforming an information signal into one more appropriate for transmission on a physical channel. Could be converting data to light in a fibre-optic cable.
        - Can have conversion errors in both directions, noise leads to incorrect digitization and insufficinect digitization leads to information loss.
    - **Bit boundaries** 
        - Where and when are the bits? Need to know what the boundaries are
        - **Synchronous**
            - Shared clock - bit transitions inform clock?
            - Transmission is continuous
            - Receiver continually adjusts its frequency 
        - **Asynchronous** 
            - Transmission sporadic, divided into frames
            - Receiver and transmitter have oscillators who are close in frequency - producing tx clock and rx clock (transmittor and receiver).
            - Receiver first synchronises its clock by examining 1+ bit transitions
            - Receiver clock drifts, but only a fraction of the time over the course of the frame 
            - Transmission time limited by accuracy of oscillators
    - **Coding**
        - Changing the representation of data so it can be sent on the physical layer 
        - Might have system where 1 = transition and 0 = no transition. Or if we flip the output whenever we write a 1 ⇒ 011001001 becomes 010001110
        - **Manchester encoding**
            - If our clock is greater than our data rate, we can align our data on the clock pulses. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H-luNVF1rwYTgUgTZCwfjXFlVx9UwUCTmy45Bas1mPByf-hCB3lPgEA9o92ym2jQas0PFuKMAaE65vYZQSsNr-kGUEt2RZcOm4k8cganpIN1w4mERO173Mtyy5bqDklc.png) 
            - Change our representation of 0 to the transition from 5v to 0v, and vice versa. Means we don't need the clock as we can just examine the transitions. Removes long periods of 1 or 0s
        - **Quad level code**
            - Have 4 discrete levels (0v, 1v, 2v,3v) to represent sets of binary numbers We can pack more data in but the sender and receiver have to be more sophisticated
        - **Line coding**
            - If the clock rate is greater than the data rate (5 to 4 in this case) have strings of 5 bits that decode to strings of 4 bits. Has an overhead, but is easy to decode with a lookup table.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KFX4U0jK6toNq9vRLBPfnwvxxGpZuj9GYiPzb0cydJFHeyX6MQk8nLvEcq0o0HrRZweHCJayQSuwlHyYHUJ795OtS4_WicckWFMZfNDaaA0rvlceNnqvY-06IIWvUzUu.png) 
        - **Line coding scrambling**
            - Generate a random sequence and distribute it securely to the receiving end - then take your message XOR the sequence and send it on the wire, doing the same on the other end will result in the original message.
            - Assure you a lot of transitions.
            - No overheads
            - **Self synchronizing** 
                - Takes the previous n digits and uses them as the scrambling pad.
                - Downside - startup cost need to wait for the first n bits.
            - **Hybrid coder**
                - Adds 01s as our scrambler could result in long strings of 0s /1s probablistically.
                - Mark start of frames using a "01" string, know it occurs every 6.4ns so know to look for it. Means we can always extract the frame reliably
        - **Multiple Access Mechanisms**
            - Many people can use a shared channel, so needs to be divided - Freq Division Mult or Time Division Mult and code division multiplexing -** note these can all be combined and used at once** 
            - **Code division multiplexing** (CDMA)
                - Apply different codes to a signal and get different outputs. Unique code assigned to each user
                - All users share the channel, but user has own sequence (chipping sequence) to encode data
                - Encoded signal = (original data) XOR (chipping sequence)
                - decoding - apply xor again
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WCEyWZ0iogtJbVTjsRoZzK10jiQka6ALN05NF8ENmOIB7AwwGuftUtEWfBg2E9s--Qv2TVjwGsJIPnU3W1ZZtKwQ_t-gL230j58JrDxNrXcYTAXkYnOwvNI9qFx5lT1b.png) 
        - **Error detection and correction**
            - Problems of transmission: 
                - Attenuation: loss of energy
                - Distortion: signal changes shape/form - caused in composite signals
                - Noise - thermal noise, induced noise, cross talk, impulse noise
            - **Basic idea**
                - Add additional redundant information to a message, so we can detect the error
            - Error detection code: **Parity** 
                - Add one bit so that **there are an even number of 1s** 
                - Cannot detect even number of errors
            - **Error detection code** 
                - Generate a "checkbit" and send with data, other end can also generate and checks if theyre equivalent
    - 
- **Lecture 7**
    - **Error Detection Code : CRC (Cyclic redundancy check)**
        - Sequence of redundant bits added to the end of data.
        - CRC = data MOD divisor
        - Check if the data mod divisor equals this set of redundant bits. Easy to build in hardware!
        - More powerful than parity, can detect various kinds of errors - including 2 bit errors
        - Choosing a good divisor is crucial
        - He says you can add the rem on the end and the entier mod will be 0
    - **Forward Error Correction (FEC)**
        - What if errors occur in the same way each time
        - Replace erroneous data by its "closest" error-free data - E.G. Send copies and majority vote
    - **Detection vs Correction** 
        - Detection uses less check bits - but need to resend
        - Correction uses more check bits - dont need to resend
        - Both can be used together
    - 
    - Data Link Layer 
        - Data-link layer has responsibility for sending data from one node to another over a link.
        - **Channel services** 
            - Encapsulate datagram into frame, adding header and trailer - MAC addresses used to frame headers
            - **Reliable delivery between adjacent nodes** 
        - **Where is the Link layer implemented?**
            - In every host - implemented in the network interface card. Attaches into host systems buses - combination of hardware, software and firmware
        - **Multiple access links and protocols**
            - Point-to-point vs Broadcast. 
            - Need to handle interference in broadcast - collisions can occur if a node receives two or more signals at the same time.
            - **Multiple access protocols **determine when nodes can transmit over a shared channel. Communication about channel sharing must use the channel!
        - **Multiple access control (MAC) protocols**
            - Three main types:
                - Take turns - nodes take turns, but nodes with more to send get longer turns
                - Random access
                - Channel partitioning
            - **Taking Turns**
                - Polling 
                    - Primary nodes invites other nodes to transmit in turns
                    - Need to decide on primary 
                    - Concerns: Polling overhead, latency, **single point of failure** 
                - Token Passing
                    - Control token passed around sequentially
                    - Can only send when you have the token
                - ATM (asynchronous transfer mode)
                    - Sender transmits labeled cells whenever necessary
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DOymKJFTYZNPgN8UnU-i0ABVrZ_NNrdWBTFIPD0ULvHfejeipIRDWnTmlgQeRfhkwbjqcGu_adFtAZqxh_Siugi3xVdDJpZfC5ewS2NyQfgdmM8FVaRS9XXZH2Oq-fCk.png) 
            - **Random access**
                - No communication needed
                - Collisions and data loss can occur
                - Specifies how to detect and recover from collisions 
                - **Carrier Sense** 
                    - Listen before speaking and dont interrupt
                    - Check if other nodes are using the channel
                - **Collision detection**
                    - If someone starts talking at the same time, stop
                    - Detect by seeing the data on the wire is garbled
                - **Randomness**
                    - Don't start talking again right away - Wait a random amount of time
        - **CSMA (Carrier Sense Multiple Access)**
            - Listen before transmitting - if idle transmit entire frame, otherwise defer transmission
            - Doesn't eliminate all collisions due to propagation delay.
    - 
    - 
- 
- **Supervision 1** 
    - Revision: How does a network distributed system compare to one running solely on one cpu?
Network distributed systems are more complicated to design around as you can make less assumptions. For example, it's far rarer for a CPU core to fail, than for a single server in a massive server farm to go offline.
Thus you must consider such failure states and build to "route-around-failure", through redundancy or protocols allowing continued communications despite losing nodes.
Additionally, network distributed systems face far greater latency between nodes than CPUs do with memory and with a lower bandwidth.
Furthermore, you cannot guarantee that nodes will not disobey the protocol defined for communication (or act in a byzantine manner) while we can generally assume the RAM will not be trying to trick the CPU.
    - **Define The following:**
        - Node - A node is a single actor in the network, who is connected to other such nodes through links. Nodes can communicate with other nodes using links, but can crash (permanently or temporarily).
        - Link - A connection between nodes in a network. Considered only partially reliable, can fail.
        - Router―Routers are devices that send and receive data on a computer network, they do this by examining the packets they receive (specifically the Physical , Datalink and network layers are required for examination) and sending the packet to either another router or to the destination computer (routing tables are used to decide where to send each packet).
        - Bandwidth - bandwidth is the maximum amount of data that can be sent across a link (by a given node) in a second. This could be due to a limitation of the link (e.g. copper wires have a lower bandwidth than fibre optics) or the node (i.e. one node can have a faster network card than another). ^^Can also refer to the frequency bandwidth^^ 
        - Bursty-ness - Periods of very high network activity, means network is bursty. ^^Kettles at half time^^ 
        - Latency - latency is the time between the sending of a signal and it's arrival. ^^The time taken to do something.^^ 
        - Jitter―Jitter is the variation in latency. A network with high jitter may have some messages that are sent in milliseconds and some that take up to a second. This is usually due to high network traffic resulting in congestion as buffers are populated. 
        - Buffer - A buffer is a list like structure where incoming messages can be stored while waiting for the network to be free enough such that the buffer can be drained and the messages sent. It is usually only used in times of great signal load.
        - Protocol - A protocol is a set of rules governing communication over a network. For example, the English language protocol has grammatical and syntactical rules about how the English language can be used for communication via sound, text, etc.
        - Multiplexing―multiplexing is the action of sharing a certain resource between multiple users. Wherein different users are granted access to a resource at different time.
        - Federated system―a federated system is formed when a group of distinct compute or network providers decide on a united set of rules and guidelines to follow. For example ISPs agree on a set of guidelines for internet data. ^^Allows you to get more users - bad if you want to change the protocol, need to get everyone to change. Protects against bad actors.^^ 
        - Horizontal abstraction - considers the breadth of the problem, i.e. the communications paths running between many complex individual systems. ^^Not 100% sure on this^^ 
        - Vertical abstraction - Considers a single piece of the system with high complexity. E.g. how exactly a component attaches to the network. ^^Not 100% sure on this^^ 
        - Layering in protocol design - layering protocols means multiple protocols are in effect at once, allowing the use of multiple different mediums at the cost of increased space taken up by headers.
        - Bursty-ness - A system is bursty if it has lots of periods of very high activity/network traffic, contrasted with periods of lower activity. ^^During half time lots of kettles get turned on^^ 
    - **What is multiplexing? Define and give a non-networking (non-lecture) example of:**
        - Multiplexing is the practise of sharing a connection for increased efficiency. Rather than having thousands of telephone wires from every persons home to all their friends, we form a network which everyone uses for discrete slices to time.
        - Time division multiplexing - time division multiplexing is a system in which users gets a set amount of time (a slot within a frame) in which to use a given resource. For example in a network, we might arrange packets from specific users as slots into frames. The receiving end of this data-stream must know the order of slots within the frame to route the correct messages to the correct destinations. An example of time division multiplexing is when as a child you are told you are only allowed to use a toy for given (miserly) number of hours, after which time you must turn over the toy to your sibling. Even if that sibling fails to appreciate that toy during their allotted time.
        - Frequency division multiplexing (hint: use something analogous to frequency) - frequency division multiplexing is where a resource is divided into frequencies, which individual users are given access to. Thus dividing up the resource and allowing for shared usage. An example would be in a jazz band, if a guitar player is soloing over a bass backing track they are encouraged to inhabit the higher frequencies (notes) - as any lower frequency playing will be inaudible over the sound of the bass.
        - Statistical multiplexing―statistical multiplexing is where users can use a resource at any time, under the assumption that the probability of many users (more than the system is capable of handling ) accessing the resource at the same time is so low that it will not cause a problem in the average case. For example, gym booking slots in a University assume that because there are many hours throughout the day for users to book - the gym won't be overrun at a specific hour (neglecting to consider the two main camps are morning and night users). ^^Not good when you have coordination. Good because you don't need complex organization. Demand for internet spread out in time and space.^^ 
    - Outline how to implement time division multiplexing?―One way is to divide time into frames and assert a certain number of frames per second, then those frames are divided into slots. Users are then given slots in which they have sole ownership of the resource (this can be a permanent time slot, or the time slots may be temporarily allocated to users with a Queue storing waiting requests for timeslots.). The code of which slot corresponding to which user (and how the frames are organised) must be understood by all parties (including parties receiving a message using time division multiplexing) in order for the system to work. 
    - Why can't we just connect every computer to every other?
Because the result would be that every computer would have $n-1$ connections (where n is the total number of computers) and there would be $\frac{n}{2} (n+1)$ total connections on this network (~$1.35\times10^{31}$ according to estimates on internet connected computers). This would mean we would have to have a system allowing billions of connections to (even though a given computer only communicates with a tiny minority of these)  which would be impossible (too expensive to do for all billions of computers and likely there are not enough raw resources on Earth to accomplish the task) - even if each connection had a bandwidth of 1 bit. Additionally, monitoring all of these connections for waiting for a signal would take a huge amount of time.
        - How do we bypass this problem (big O estimation would be a good idea here :) )
We bypass this problem by using packet-switching, instead of connecting all computers - groups of computers connect to switches, which then connect to routers to share the internet network. The total number of connections decreases from $\frac{n}{2} (n+1)$, to the order of $n$ - each computer need only have a connection to a router which will communicate with the wider network. This system only works because computers only communicate with a small subset of the total computers in the network and not all the time, meaning the router doesn't work to capacity at all times and the wider network is not required to always work at full capacity.
    - What are the two types of described switching networks and what is the main unit of transfer in each?
Packet switched networks and Circuit switched networks.
Packet switched networks use statistical multiplexing and send discrete packets of data on the network that are routed by routers and resent if lost. The main Unit of transfer is packet.
Circuit switched networks first establish a complete connection through a network before transmitting data, then tear down that connection when communication is completed. The main unit of transfer is an entire message.
        - Give a use case where each is optimal 
Circuit switched networks are ideal when a connection needs to be very stable, but the time to establish the connection is not as important. For example a surgeons connection to their remote surgery robot.
Packet switched networks are ideal when you have many users communicating intermittently, with a few network bridges which cannot be locked up - for example if using a messaging platform, you don't want your message to have to wait for other people to stop sending messages before your message can be sent.
        - Give a use case where each is highly suboptimal 
Circuit switching is suboptimal when you have nodes likely to fail, as your teardown message cannot be sent and recovery from failure can take a long time.
Packet switching is suboptimal when a secure connection with guaranteed low jitter is required - as packets can be lost/ routed different ways/ delayed by queueing.
    - Why would a p2p file sharing protocol like bittorrent not work well in a circuit switching network? (Hint think about the costs involved in each network flow and how long each flow exists for)
Bittorrent works by sending small packets of data between "seeders" depending on the data the "leeches" require - this means leeches receive small pieces of data from many different seeders. In a circuit switched system, the overhead of creating a connection to each of these seeders (only to send a small amount of data) would be too high for the system to be viable.
    - Discuss the Internet networking stack
        - What is it - The internet networking stack is a way of dividing up the stages of internet networking to provide abstractions. This means that not every app need implement the code to communicate over different types of mediums, instead the code is written to interface to the application layer and the message filters down through the layers.
        - Why does this make it simpler to build each part of the system?
Unnecessary details unrelated to the target domain is hidden. Also systems implemented elsewhere can be reused. Also innovation at each level can proceed in parallel, meaning interfacing with these other improved levels becomes easier.
    - Why when transporting a box of diy electronic parts from China to the UK is it likely that it makes most of the journey inside a ISO container?
ISO containers are a form of multiplexing, where many different packages share space to reduce the cost of transporting items on a tanker - this way the cost of operating the tanker is shared. The bulk of the journey from China to the UK is the shipping over water, meaning most of the time is spent in an ISO.
        - Does a similar reason apply to why IP is used as a common transport layer in networking?
You could draw the parallel that packets spend most of their time in transit in WAN's rather than LAN's, as there is much less distance to travel in a LAN than in a WAN. Thus the IP transport layer (which transports over WANs, i.e. using the network layer) is the most common transport layer.
        - Can you imagine a scenario where IP would not be a good fit? 
If most of your data was being sent locally (perhaps internet communication with between virtual machines) where the added headers would not be necessary.
    - Outline the internet :)
The internet is a large amount of LAN's, connected by routers. The connections are possible (and routed) due to ISPs, these ISPs contain the way to contact every computer (that you can reach) in routing tables. 
        - What kinds of organisations does a packet traverse travelling from Cambridge University to MIT?
Travels first through Cambridge's switch, to a router and then through an ISP to a MIT server within the UK. If it did connect with MIT it would likely travel through an undersea network connection.
        - Discuss the how traffic may differ within these organisations and if it may be possible to exploit that. 
MIT may expect more traffic than Cambridge, meaning Cambridge could be vulnerable to a DDOS attack if very large traffic was inflicted on it's servers.
    - What is the bandwidth delay product and why is it a useful measure for system design? 
The bandwidth delay product is the product of the bandwidth and the latency of a system. It tells you the amount of data in the "pipe" at any given time, and thus the maximum amount of data that can be sent without receiving an acknowledgement. This is useful as it helps describes the use cases for a given connection. ^^Not 100% sure^^ 
    - 
    - 
    - 
- **Supervision 2**
    - 
    - Protocols 
        - Come from RFCs, they get comments and send it to the IETF after changes. The protocol is then formalised
        - How do they get standardized? When a good protocol starts being used, there is a desire from customers to be able to use the facilities of this new protocol and to be able to communicate with people using this protocol - this drives the generation of new technologies using this protocol (the protocol can even be hardwired into the board) and the usage becomes so widespread that switching protocol becomes almost impossible (especially for small performance boosts) as the web of people using such a new standard would be so small it would be useless.  
        - Layering
            - Downside of layering:―Headers start to get large as different layers add their own.
Information hiding results in some useful information being lost that we might want, e.g. we can't know if a packet was lost due to corruption or congestion. Performance overhead at each layer - results in performance drop.
Higher layers might replicate functionality of lower levels, i.e. error recovery.
The layering philosophy often gets violated anyway as certain layers might peek at data their not supposed to if the performance gain is large enough, or if the packet poses a security risk (firewalls)
            - What is a cross layer violation―This is when a layer accesses data it's not supposed to, this can be for a speedup or for greater security. For example in header compression the link layer accesses header data of a different layer to it, but the speedup gain is large enough that this goes unpunished.
        - What are end to end guarantees
End to end guarantees are guarantees about certain features of your communication over a network, e.g. max latency, privacy, reliability etc. These can be implemented multiple ways, we can have the network implement these guarantees - meaning every connection would have to ensure packets are reliably sent. Or we can push this responsibility to the user program, make them ensure reliability by checking if the message got through or sending multiple messages.
            - Why might multiple interpretations of this principle be negative?
It makes the term almost meaningless, as different people use it in almost opposite ways. Additionally it means people can back up their arguments using end-to-end guarantees as a term even if their definition is different to yours. 
    - 
    - Physical Layer
        - What is it?―The lowest layer, along which the data is physically sent (potentially) long distances over copper wires, fiber optic cables, radio waves and more!
        - What is analogue and digital
Digital signals are signals that alternate between a few discrete values - e.g. binary signals alternate between 0 and 1 (often represented by <0.8V and 0.8V < x < 2V).
Analogue signals do not have discrete options for values, and can be a continuous range of values over the real numbers.
            - How can we convert from one to the other? (don't go too deep on this)
We could convert from analogue to digital by taking samples (at a set frequency) and putting the value of the signal at that time as the closest digital value (e.g. 7.43 might be rounded to 7).
We could convert from digital to analogue using Fourier analysis, if we carry the data required (the combination of waves) in the digital signal.  
        - Define bandwidth in the context of analogue signals 
We could define bandwidth to be the highest frequency signal we can send across our link. As the higher the frequency the more information we can encode (while wavelength could simply be scaled up and down so higher wavelength doesn't necessarily imply more information being transferred).
NYQUIST LIMIT
        - What is noise in analogue signals, and where does it come from?―Noise is when an unwanted signal is superimposed on top of our desired signal, it can result in information in the original signal being masked and thus lost. It can come from interference along the wire (e.g. copper wires might face electrical interference from magnets or similar, radio waves might combine with other signals on the same frequency) or at either end.
        - ^^Dont really understand self scrambling signal - can we go through?^^  
$$y_n = x_n \oplus y_{n-3}$$
xor incoming signal (x_n) with a delayed 
        - What is a self clocking signal?―A self clocking signal is a signal that can be decoded without some other means of synchronizing the sender and the receiver (by sending the clock on another wire for example).
        - Define manchester coding―Manchester coding replaces the coding of low and high voltage for 0s and 1s with a transition. 1 is now represented as a transition from a low signal to a high signal, and vice versa for 0.  
^^NEED PREAMBLE - If we just get 010101... can't know clock period^^ 
            - Why is it useful?―This transition can always be detected, even if a stream of 0s or 1s is being sent - meaning we can always detect where the clock pulses are and where new signals are being sent. This is an example of a self-clocking signal.
        - What does interference look like for example on the signal: [1,-1,1,1,-1,-1,-1] and [-1,1,1,-1,1,-1,-1]:
[0.7,-1.2,1.1,0.3,-0.2,-0.1,-1.2] and [-1.4,0.1,1.6,-0.1,0.45,-1.41,-0.41]
        - How do we use Code Division Multiple Access to allow multiple signals to be transmitted on the same wire/airwaves―Each user is given a chipping sequence to apply to the data, when they apply their sequence they either get the original data or some garbled mess - depending on if the data was intended for them - if it was they can decode the signal using their chipping sequence, if not then decoding would require a different chipping sequence to access the coded data.
^^Think of this as taking the dot product of the combined signal with the two chipping sequences -  so you get the component along your chipping sequence "vector".^^ 
        - What is error detection
Error detection is a method testing for certain types of errors in a signal, upon detection the message can be resent.
            - Outline parity checks―Check if the message has an even number of 1s, if not then append a 1 otherwise append a zero. The receiver can then check if the entire message (including the appended value) has an even number of 1s - if not we have an error.
            - Outline CRC codes―We take the modulus of our data to be sent (modulo some number p) and append this remainder to the data. Then at the other end, we take the modulus again of the **data portion** (using the same p) and check if the computed remainder is the same as the appended value.
            - ^^I have some confusion about CRC where he says you can simply append the remainder and the entire remainder should then be zero - but wouldn't you have to add the value to get this result? Because you're multiplying the data by 2^(size of modulus) which could change the remainder.^^  This works apparently, dunno how ask Yash.
        - What is forward error correction?―A method of replacing erroneous data with the closest error free data, i.e. **guessing the minimum number of bit flips** that would make the data correct with your error detection protocol. This could be majority voting where each bit is sent 3 (an odd number in general) times and the majority bit is selected as the value. E.g. 011 ⇒ 111.
Can send 7 bits for every 3 and that's resilient to any 2 bits change. Then you should only have 8 possible incoming signals - check which signal it's closes to and take that.
        - AM vs FM - amplitude hard to change quickly, so FM encode data in frequencies. High frequency 1, low frequency = 0. **Noise doesn't affect the frequency, only the amplitude**. AM varies amplitude not frequency 
    - 
    - Data Link Layer
        - What is it?―The data link layer is in charge of reliably transmitting datagrams between two nodes over a link.
        - Define Broadcast links 
Broadcast links are links where multiple nodes receive the message and possibly rebroadcast or deliver the message to the application layer. You always send your message to all connected nodes. Single shared broadcast channel
        - Define Point to Point links
Point to point links are between two nodes, no other node accesses the data and you don't rely on rebroadcasting by other nodes.
        - What is a collision?
A collision is when the data from two nodes is received at the same time - interference can have occured.
        - Channel Partitioning
            - Discuss TDMA, FDMA―TDMA is done by partitioning the channel into frames, within which each node has a slot they can put their data into. This provides an upper bound on the capacity of the channel and helps eliminate collisions (if nodes obey the TDMA protocol in action)
FDMA is done by partitioning the channel into frequency bands, nodes are then given a frequency band that they can communicate on - as waves of different frequency have little to no interference this helps reduce garbled signals.
FDMA and TDMA can be used in tandem.
        - Taking turns
            - Discuss: Polling, Token rings―Polling is a method of reducing interference. A single node is elected the primary node, and that node invites other nodes (in order) to speak on the channel - other nodes wait until they're asked to speak before speaking. If the primary node fails, we need a method of detecting this and electing another leader otherwise no node can communicate.
Token rings work by having a token which is passed between nodes, nodes can only communicate on the channel when they have this token and nodes pass the token on once they've finished talking. This also has the problem of a single failure point.
        - Random Access
            - Discuss: CSMA, CSMA/CD―CSMA is a method of reducing interference. Before a node transmits data on a channel, it checks if another node is talking, If another node is talking then it waits a random amount of time before checking again - if the channel was quiet the node transmits its whole frame. Interference can still occur because there is a slight propagation delay.
CSMA/CD adds collision detection to the CSMA stack - we detect garbled communication due to collisions and stop transmitting to stop blocking others from using the channel. 
If you're receiving a garbled signal - then send a jamming signal to get them to randomly back off.
            - Discuss Random exponential backoff―Random exponential backoff defines the amount of time to wait after a collision, before trying to transmit your message again. After our mth collision we **randomly** choose k s.t : $$k \in \{2^0, 2^1, ..., 2^{m-1} \}$$
we then wait for the k * 512th packet to be sent before attempting to send our message again. If a node is broadcasting when we're set to send, wait for that broadcast to end before transmitting.
We need different seeds for pseudo random number generators to ensure our k is not the same every time between nodes!
        - Outline Ethernet―Ethernet uses a CSMA/CD protocol with exponential random backoff when a collision is detected. Collisions are easier to detect over ethernet than wireless signals (as wireless can't listen and broadcast at the same time) meaning less time is wasted during collisions.
Ethernet is easy to maintain, fast and inexpensive - it has also evolved and improved over time. 
        - Outline 802.11 AKA WiFi―Designed for limited area, Access Points are set to specific channel. Broadcast beacon messages with SSID (Service Set Identifier) and MAC Address periodically. Hosts scan all the channels to discover the AP’ s – Host associates with a AP
        - What is the problem with:
            - hidden terminals?―If two nodes can't detect each other, carrier sensing doesn't work and they will communicate at the same time - meaning any node that can detect both of them will have collisions and the messages will be garbled.
            - exposed terminals―Exposed terminals are terminals who wait for a given node to stop transmitting when they don't need to, this can occur if the node they think they would collide with is out of their range while their intended recipient is in range.
        - What is rts and cts?―RTS is a request to send, CTS is a clear to send message. 
A node sends an RTS request (containing the length of the transmission), and waits for a CTS message from the receiver before transmitting. If one is not received there is assumed to have been a collision. 
After a transmission has been sent an ACK (acknowledgement) message is sent.
        - What is a MAC address?
A MAC address is a unique code given to every computer, it allows for identifying which machine is sending a given message.
        - What is a self learning switch?―A self learning switch learns which nodes can be reached through which interfaces – when a frame is received, the switch “learns” location of sender – records sender/location pair in  switch table.
        - What is flooding (and what is the problem?)―Flooding is the process of making sure that all the nodes participating in the routing protocol get a copy of the link-state information from all the other nodes. Each node sends its link-state information out on all of its directly connected links, each node that receives this information then forwards it out on all of its links. This process continues until the information has reached all the nodes in the network.  
Flooding can lead to loops where nodes are sending flooding data to each other forever.
            - How do we fix this?―Ensure the network topology has no cycles. We build a spanning tree (a graph without cycles) and edges **not **in the spanning tree do not forward results. 
- **Supervision 3**
    - 
    -  _**Network Layer**_ 
    -  _What is the purpose of this layer_ ?―The network layer manages communication over IP and handles routing around a network. I.e. the physical path a packet will take
    -  _Define simplex and duplex_ :―A simplex connection is when nodes can only send or receive data along a line, the can't do both. A duplex connection is when nodes can send and receive data simultaneously along a line.
    -  _What is the difference between the data plane and the control plane: _ ― _
_ The data plane simply pipes incoming data to a port, where it is then shipped along a connection - it does this using the routing table supplied by the control plane. The control plane handles this routing table and makes decisions at a larger time scale. Handling the routing means updating shortest paths using various algorithms.
    -  _Why is this separation also useful in other contexts (for example distributed databases)? _ For distributed databases, this separates concerns between simply storing data and also synchronising and maintaining databases - for example synchronising fragmented databases.
    -  _What is the line rate of a switch?_ ―The line rate is the number of bits per second that can be sent from a port, e.g. the speed of each port.
    -  _What is a border or edge router?  _ ―A border or edge router is a router between two Autonomous systems, e.g. clouds.
    -  _**Routing table**_ 
        - What is this:―A routing table is a grouped table of networks, for each network we have a next hop ip address to send the packet to, a "cost" associated with that route and the interface to send it along - e.g. port.
        - Why does this allow the router to make fast forwarding decisions?―The router can make a quick lookup in the routing table based on longest prefix matching of the IP, then we can quickly manage the header and transmit the packet.
        - Why is address fragmentation problematic for this table?―^^Address fragmentation is when one company get 1000 ips, they grow and need more - but the next set has been bought. But the next contiguous chunk is gone - then will have to get another section.^^ 
        - How does IPv6 address this? 
    -  _What is an autonomous System_ ―An autonomous system is a system in which a routing algorithm is run on the switches within that system, calculating the fastest routes within the system. Usually owned by a single entity, think clouds.
    -  _What famous general problem is calculating routes equivalent to?_  There are similarities to be found between calculating routes and the Byzantine generals problem - wherein unless all generals synchronize, the task fails. Similarly, if routers have differing routing information loops and slowdown can occur.
    -  _Outline and compare Distance Vector and Link State routing_  ↓ 
        - Distance vector routing: 
First each node communicates to all it's **neighbouring nodes** the shortest "cost" of travelling from it to all other routers along it's provisional shortest paths. Then each node examines the distances, and improves upon it's own list of shortest paths. Every node does this, and over time a optimum solution is reached. Need additive metric, otherwise could have an infinite loop as an equally good shortest path.
        - Link state routing:
Each node communicates it's local link state (list of directly attached links and their costs) table to it's neighbours - and they flood the table to all of their neighbours etc. Until every node in the network has received it, then every node can build a graph of the entire network and subsequently run Dijkstra's algorithm to calculate the distance from it to every other node. Then build a forwarding table, which link to use when sending a message somewhere.
        - Distance vector routing sends less messages on the network.
Distance vector routing has a lower complexity for it's underlying algorithm.
Distance vector routing iteratively arrives at the correct solution, while Link state routing get's the correct solution as soon as the processing of Dijkstra's algorithm completes for all the routers.
    -  _Under what condition is Link State routing better?_ ―Link state routing is better at recovering from loops caused by incorrect link costs.
    -  _Why does the Distance Vector routing break down_ ?―If a router malfunctions and advertises incorrect routing data, that error get's propagated to every other router and they all end up having incorrect routing data.
LOOPS - (consider triangle loop) if someone in a loop crashes, one node might just send to A how sends back to B etc.
    -  _Find an example of BGP route advertisement resulting in a large proportion of internet traffic being routed via a single AS_  - Couldn't find BGP route advertisement in the lecture notes
    -  _Describe a packets traversal through a router_ :―First the packet arrives in the port (the router then looks up the outgoing port on the routing table), it then has it's header updated (TTL decremented and checksum updated accordingly), finally it is sent to the output port where it is buffered, finally it is sent out the corresponding outgoing link. __
Just to check my understanding, the Control unit doesn't communicate with the ports sending them the routing table? It only updates the routing table the ports use periodically.__  
    -  _What is longest prefix matching and why does that result in 'optimal' delivery_ :―Longest prefix match matches a given destination IP with the destination IP in the routing table with the longest subnet mask. Longest prefix matching works on the fact that we may send many packets to a given network (to different hosts on that network) - so even if we don't know the exact route to a given computer, longest prefix match will find the address of the network (or less specifically, route it to the country/region or simply a default address) that computer is on and route it to there. 
 __Don't really understand the grouping of entries in the routing table - seems to say that ports get assigned by IP no by actual routing: __ ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QC4iKPENrlqT9O170cdiicsa4T9KuLvRbdkbZI5srFJfw2r9qhmvjY2hU3Q0kuAnR7zrh9hwXE5rdrZ7Lu80Htv5IjLD6YDmg0ZUZumcCMUUmfMQ8XTSE9IcQUuZ2116.png) 
    -  _Describe each part of an IPv4 packet:  
_ Version Number - the IP version number, 4 in this case.
Header Length - the length of the header in 32 bit words.
TOS - Allows packets to be handled differently depending on use, e.g. low delay for audio.
Total length - the total length of the packet including the payload in bytes
Identification - Number associated with a set of fragments to recompile them into a single packet.
Flags - Indicates fragmentation possibilities, do not fragment or more fragments on the way.
Fragment Offset - Offset of the fragment from the start of the datagram in bytes.
TTL - Number of hops left before the packet is dropped, useful for preventing loops.
Protocol - information about the type of connection e.g. UDP or TCP
Header Checksum - a unique number that can be calculated from the header binary, used to detect corruption of the packet. 
Source IP - IP of the original source computer
Destination IP - IP of the destination computer
Options - Number of optional header settings, for tracing or testing.
    -  _Why is the protocol specified within the packet header_ ?―Different protocols have different underlying headers below the IP header, knowing the type of header to examine allows for quick and easy demultiplexing.
    -  _Why is ip fragmentation required?_ ―Because not all links have the same capacity, if a router needs to send a 1500 byte packet along a link with a capacity of 1000 bytes - fragmentation is necessary.
    -  _Outline how to fragment a packet_ : ↓ 
        - The packet is split into multiple fragments that will all meet the MTU requirements for the link (the less fragments the better, as less chance of packet loss).
        - These are all given the same identification number (if a packet is already a fragment, the id number is unchanged) and are given an offset from the first datagram (only the payload counted, first packet has 0 offset). 
        - Finally, all packets except the last have their MF (More fragments) set to 1 and all the packets are sent.
    - What addresses are in the following subnet: 192.168.16.0/23
192.168.16.0 - 192.168.17.255
    -  _**DHCP**_ 
        - What is it meant to do? Meant to provide a method of dynamically giving hosts unique IP addresses and renew the lease on said IP address.
        - Outline the protocol -―Host pings DHCP server requesting an IP
DHCP responds with an IP
Host responds with that same IP
DHCP sends an ACK
Host then adopts this IP.

 __Bit confused about the src and dest ip's in the diagram - are these reserved so the DHCP server knows what to respond to? Also does my hub at home have a DHCP server or would it contact ISP?__ 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dyAIgnOJEZa5z3RtotRC9v-8j1ocoFTeUKByRZdBOXCcoqqwPyaJ7nvAiiTsrNMaTVvy9XQhQ3r7CmilYDSaultTwtwq-7Kdm6UhJLCqqQAUTVkUbj31n4qSdfNA1Inn.png) 
        - What is a NAT:―A Network address translation takes a private IP address and port, and maps it to a public IP address and port - then when a packet with the same public IP and port comes in, route it to the correct private IP and port.

This means multiple computers on a network can seem to share the same IP to the outside world - then when a response comes to a specific port, the router knows which computer to send the response to. 
^^NEED TO UNDERSTAND NAT PUNCHTHROUGH^^ 
        - Why are NATs required for legacy IPv4 networks?―Because there are more computers needing IP addresses than available IP addresses, this means 2^16 computers can share the same IP on a network.
        - Why might some say that it improves the security of the system?―Because a webserver cannot tell which computer within a network sent a given request.
        - Why does it pose difficulty with for example self hosted services (like game servers, or email servers)
Is it because for such a service, a given port has a specific purpose - and all data needs to be routed through this port. But here we have repurposed ports for computer identification?
        - What are ICMP messages?―ICMP messages are messages sent after receipt of a packet (sent back to the originating address) in the event of a failure or problem with the transmission of that packet. That could be that the TTL was exceeded, the packet is larger than the MTU etc. 
        - What is IPv4 ARP, what happens if an IP can't be found―IPv4 ARP is a method of determining the MAC address of a host, given it's IP address. This is useful for layer 2 communication which is done using MAC addresses and physical wires.
In ARP, hosts keep track of a table of IP and MAC address pairs. If a host wants to know the MAC address for an IP, the host broadcasts that they have an IP x and they want to know the corresponding MAC address - the host with that IP address will then respond with it's MAC Address.
        - Why does soft state result in robustness?
IPv4 being prepared for hosts to lost their IP or change their IP builds robustness against hosts  hogging an IP address without using it or changing IP in an attempt to spoof the system.
    -  _**IPv6**_ 
        - Outline an IPv6 header
Version - Same as IPv4, will be 6 for IPv6
Traffic Class - Contains the differentiated service field which classifies the type of packet (e.g. low latency sound packets) and two bits for ECN, which can indicate congestion is coming in packets (as opposed to just dropping packets).
Flow label - Groups a sequence of packets into a flow, signalling to routers they need special handling (Like sending all the packets along the same path, useful if packets are fragmented and we want them to arrive at the same time). Flow label can be any number, but all packets in the flow must have the same number.
Payload length - Same as IPv4
Next Header - Indicates where the next header is where we can add the equivalent of the options in IPv4
Hop limit - Same as TTL
Source and destination - address equivalent to IPv4 (in terms of usage)
        - Outline IPv6 packet fragmentation―- IPv6 packets can only be fragmented at the host sending the packet, intervening routers cannot fragment them.
        - Outline an IPv6 address structure:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9ocBmzW-Gq8oO09K_H5c5CQZamlwWRWvanVvjjViWmDrwFYZ5Y3qPmD8n_u6etqqInjkyS_1iBo9zuw1etAATcUOyRJQ7mDRtpCLBcavKtsZJRiAYB4cl4irI24Ki66M.png) 
 __This is the only slide, don't really know what it's on about - can we go through?__  
        - Why does this make routing easier? 
More space - very hierarchical
        - What do the following addresses mean:
Note that **Your computer will have multiple addresses, 1 for global unicast, 1 for site local.** 
            - fe80`::`/10 - ranges from fc00`::` - ffff:ffff:ffff:ffff. Used for link-local connections
            - : : 1 - all zeroes and then 1, like localhost in IPv4. 
            - fc00`::` /7 - ranges from e000`::` to ffff:ffff:ffff:ffff. Site local connections. Not globally routable, would have one for the computer lab.
            - 2000`::`/3 - ranges from 2000`::` to 3fff:ffff:ffff:ffff. Used for global unicast - If Yash wanted to send to me and Marc, he'd register a global unicast address - then me and Marc would subscribe and receive the messages broadcast from there.
            - ff00`::` / 8 - ranges from f000`::` to ffff:ffff:ffff:ffff. Used for multicast - send to the router first, which forwards to everyone else that's subscribed to listen.
        - What is IPv6 neighbour discovery - It's a method for IPv6 hosts to discover other hosts and routers on the network using ICMPv6 packets.
        - Outline SLAAC―SLAAC is a method of generating and testing IP addresses automatically, without the need of a DHCP server. First the host generates an IP address (generally using it's MAC address, although this has privacy concerns), it then pings the network with packets testing if that IP is in use, if no other hosts reply then that IP is assumed to be unique and is assigned to the interface.
Note that it only generates the last 64 bits (otherwise we wouldn't get the hierarchy of IPs) the first 64 bits are eight fe80 for link local addresses, or wait for a router advertisement.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yt6C0pLDaTVm4ClKEY5IupCYi6ZSEWIqD8-xWIZuhPT_OeNBoyvO3wfxP5FXpuwgzC-MRemF5-K5rm_xvzIAMdNpZ0dlVWdJjvgolth2smYdDuQaD3mrunbLKDH-T8hR.png) 
        - What is its purpose
SLAAC is a method of generating and testing IP addresses automatically, without the need of a DHCP server. 
        - What are router advertisements?―This is where a router occasionally advertises it's presence on the network in the form of a special packet supplying it's IP and other information. It tells the host where to derive it's network state using two flags R and O - R says to use a DHCPv6 server and ignore O. O says other configurations are available over DHCPv6 such as DNS.
        - Discuss 6to4 tunnels -―6 to 4 tunnels operate like an IPv6 VPN service, wherein a host using IPv6 can communicate with a different server - which will forward all it's packets using IPv4 (after translating the IPv6 packets). The server will then send the responses back to you in IPv6 format
- **Supervision 4**
    -  _**Transport layer**_ 
    -  _What is the transport layer? _ ― _
_ The transport layer is the interface between applications and a stream of IP packets. We need to decide which packets go to which applications. It can also provide reliable connections over best-effort IP (using TCP) or faster (but less reliable) connections like UDP, where implementation of these details in every application would be tedious. 
    -  _What are ports at the transport layer?_   
These are the transport layer identifiers, using a mapping from ports to sockets (stored by the OS) we can decide which port maps to which application (each application must open a socket).  
    -  _Why does this make running duplicate services from the same ip address difficult?_  
Need to ensure we don't have port conflicts, where multiple services are trying to use the same port. 
    -  _Why does the transport layer need to mux/demultiplex IP streams?_ ―Because multiple processes can be sending IP streams from different **ports**, and we need to examine the header **below **the IP header to find out which port the packets need to go to. The ports are the method of multiplexing, sharing the network resources between different applications.
    -  _**UDP**_ 
    -  _Outline UDP _ ― _
_ UDP is a lightweight delivery system, simply providing de-mux and anti-corruption capabilities. Packets are simply created and then send, without waiting for an ACK at the sender. 
Headers contain the source and destination port (for demultiplexing), a length and a checksum - followed by the data. 
    -  _What guarantees does this provide?_   
The checksum provides some guarantees for testing for corruption, and the source and destination ports allow for demultiplexing - however this is not a reliable connection. Packets can be lost or reordered as no packet sequence is provided.
    -  _Outline some C/pseudocode (but valid POSIX commands) code for a basic echo server_   ```c
#define BUFSIZE 512

int main(int argc, char *argv[]) {
    int sockfd;
    struct sockaddr_in servaddr;

    if (argc != 2) {
        puts("Usage: client <port>");
        return 1;
    }

    if ((sockfd = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0) {
        perror("Cannot create socket");
        return 2;
    }
    // Set server to all zeroes
    memset(&servaddr, 0, sizeof(servaddr));
    servaddr.sin_family = AF_INET;
    servaddr.sin_addr.s_addr = htonl(INADDR_ANY);
    servaddr.sin_port = htons(atoi(argv[1]));

    listen(sockfd, 100);
    {
        int n;
        char bytes[BUFSIZE - 1];
        while ((n = read(sockfd, bytes, BUFSIZE)) > 0) {
            // Output the results to stdout
            fwrite(bytes, n, sizeof(char), stdout);
        }
    }

    return 1;
}
```
    -  _**TCP**_ 
    -  _What is the purpose of TCP _ ― _
_ TCP is designed to provide a reliable, correctly ordered and uncorrupted delivery of ^^a stream of ^^packets over an unreliable connection.
    -  _How does it provide reliable delivery?_ ―Via retransmission and acknowledgements, as well as an initial three way handshake to establish a connection.
    -  _Outline sequence numbers for reliable delivery_ ―Sequence numbers are used to order the sequence of packets in a sequence. A packets sequence number is equal to it's offset as a TCP segment from the start of the entire TCP flow.
    - In TCP what are the sequence and ACK numbers?  ↓ 
        - The sequence numbers are the byte position of the 1st byte in the segment. E.g. ISN + k:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xtdqBigCdYYHvUABNnffIo3SkGA0jM1MkzijlgGeack7W5RvxoV69_33jAT26SF0KBBztYvPwfPrc-hicC4y2TVFRl14iUW2JEfWU3z1fij_jos_7i42f_MubfXCp_ya.png) 
        - The ACK numbers are the byte position of the next expected segment.
    -  _Outline cumulative and selective acknowledgements_  **IN TCP**  ↓ 
        -  _Cumulative Acknowledgements:_ 
Packets are not dropped when received out of order, they are buffered. Every time a packet is received (packets out of order are buffered), an ACK is sent with the SN indicating the bit position of the next packet to be received. If the received packet was the next expected packet, the SN would be the bit position of the end of the last in order buffered packet. If the SN received was not for the next expected packet, the receiver sends the SN of the next expected packet + 1.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2alRg9cxu3jFsEulJf3TG8aRlb1pKdz-qMAr0gMMXx4K_sexOr1ZHmJOHXeERsChscJ7Oj_Vdkv4ekmLHlri_K4sDGQXY3NGtHh4v3RvC1wuL8iAd1NT9oFcET7eO-u8.png)
The sender only resends a packet if 3 consecutive ACKs with the same SN are received (indicating isolated loss) or no ACKs are sent after a certain amount of time - in which case the sender retransmits the relevant packet.
        -  _Selective Acknowledgements- TCP DOESNT ACTUALLY DO THIS_ 
Similar to cumulative acknowledgements, except an indication of which packets are being buffered is sent in ACKs - meaning during repeated ACKs the sender can choose to retransmit multiple packets at once.
    -  _Outline CWND, advertised and Sender side sliding windows_ ―**CWND **- how many bits can we send without overloading routers along our route.
**Advertised window** - how many bits can we send without overflowing our receivers input speed. With **Flow control **this window will vary as the buffer of the receiver fills, and the amount of space left will be signalled in ACKs. Additionally, the window size at the sender will grow as ACKs are received, as speed is gradually ramped up.
The **Sender side window** is then the minimum of CWND and the Advertised window.
    - What does TCP do if it doesn't receive any ACK's? How does it measure RTT? ↓ 
        - Retransmits after a certain timeout - we don't want the timeout to be too long (inefficient) or too short (duplicate ACKS). So we seek to make the timeout proportional to the RTT.
        - Can use exponential averaging to measure RTT:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6Hb-4bX3Nq-srt6nvRJ9avrctNSTXXh6Q5s6APtmKdX1lzEGuDcRhg8eJsNS7XumsmZ3HV4fVzJqAkNk2mwmSUOQtqVrp6rA_P11b91Wfi7x1HGQlpTH0u0JN7si_-4w.png) 
But can't measure RTT if we can't tell between ACK of original packet and ACK of retransmitted packet. Thus don't include retransmitted ACKs into RTT calculation. Set the timeout to $2 \times \text{EstimatedRTT}$. 
        - When we timeout, double the timeout. Collapse back to $2 \times \text{EstimatedRTT}$ when we receive a new ACK. 
        - Can model better by measuring the deviation:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2FKFwuJl2lOmfwNjZGez6axk0zdRuTEqiA_Xb1ab3veJ07MsUox0E93jpfvePpCYa_Oa2JGfC-_LBQ8L9RoQoIn6uxVsIIws0xzxP6vKhe7X3a5tnTon4U1t9WRwTYwA.png) 
    -  _Outline TCP :)_ ―First a three way handshake is initiated to synchronize an initial sequence number, this sequence number cannot be zero for security and reliability concerns - if we always start at 0, we could have cases where packet with sequence number 100 was lost before and now gets replaced with a completely unrelated packet as the receiver thinks a resend has occurred.
In the three way handshake, Host A sends a message flagged SYN (Synchronize sequence number) containing a proposed sequence number. Host B then replies with that same sequence number + 1, a proposed sequence number for B and an ACK. Host A then responds with their sequence number, B's sequence number + 1 and an ACK and the connection can be started.

Both the sender and receiver maintain a sliding window, where receivers send cumulative acknowledgements. Packets are not dropped when received out of order, they are buffered. Every time a packet is received (packets out of order are buffered), an ACK is sent with the SN indicating the bit position of the next packet to be received. If the received packet was the next expected packet, the SN would be the bit position of the end of the last in order buffered packet. If the SN received was not for the next expected packet, the receiver sends the SN of the next expected packet.
The sender only resends a packet if 3 consecutive ACKs with the same SN are received (indicating isolated loss) or no ACKs are sent after a certain amount of time - in which case the sender retransmits the first packet in the window.
The aforementioned packet window must be carefully managed to keep congestion low, and not exceed the maximum window size - this window size being whichever is smaller, the advertised window size of the receiver or a congestion window set to help prevent router overflow.

When tearing down the connection, host A sends a packet flagged FIN to B - then B must send an ACK to A, followed by a FIN packet from B. This ensures that both hosts have the opportunity to receive all packets in flight, and potentially request retransmission.
In the case of abrupt termination (for example due to a process crashing) the terminating host sends a packet flagged RST.   
    -  _Discuss the abstraction_   
Don't really understand what this question means.
The abstraction of TCP is that applications can now directly interface with a reliable connection, even though in reality all the messaging is done over a best effort connection.
    -  _Discuss segmentation - Why is it required - How does it work_  
Segmentation is how bits are loaded into IP packets from a stream of input data (TCP is a stream of bytes service) , before being sent over the network, a given segment either fills up before sending or times out and is sent without being completely full.
The IP packets contain an IP header, followed by a TCP header followed by the data - the entire packet must not exceed the MTU (maximum transfer unit) while the part below the IP header must not exceed the MSS (maximum segment size).
These segments are useful for two reasons, 1 they can be used to provide an ordering mechanism for packets i.e. the sequence number, 2 they allow for flow control as you can vary the MSS.
    -  _What are TCP sequence numbers?_   
Described above. Outline TCP quite a general question, didn't know what I should/shouldn't include.
    -  _Outline what happens when packets are lost inTCP_    ↓ 
        - If a data packet is lost: 
Consider a packet with sequence number X is lost. The receiving host A will continually send an ACK containing X whenever it receives a new packet - then when sending host B receives a certain number of repeated ACKs it will employ **fast retransmit **and resend the missing packet before resuming normal sending (with a reduced sending window).
        - If an ACK packet is lost: 
If an ACK packet isn't received in a certain amount of time, the receiver times out and resends the first packet in the window. If one ACK packet is lost but a later ACK arrives then we know the first packet must have been acknowledged and can keep sending as normal.
    -  _How does TCP choose a retransmission timeout?_   
The retransmission timeout is a multiple of the RTT (round trip time) between hosts, this is because the RTT is the minimum amount of time necessary for communication between the hosts . Many times the RTT is a waste of time.
The RTT is then calculated via the following two formulae:
$$\text{Measured RTT} = ACK_t \ - \ SEND_t$$ 
$$\text{Estimated RTT} = (1-\alpha) \text{(Measured RTT)} + \alpha( \text{Estimated RTT})$$
This averaging formulae allows for adaption of the estimated RTT to network changes (the estimated RTT would change accordingly) while not changing the estimated RTT suddenly in the event of temporary network speedup/slowdown (jiggle).
    -  _How a connection is established_ ―First a three way handshake is initiated to synchronize an initial sequence number, this sequence number cannot be zero for security and reliability concerns - if we always start at 0, we could have cases where packet with sequence number 100 was lost before and now gets replaced with a completely unrelated packet as the receiver thinks a resend has occurred.
In the three way handshake, Host A sends a message flagged SYN (Synchronize sequence number) containing a proposed sequence number. Host B then replies with that same sequence number + 1, a proposed sequence number for B and an ACK. Host A then responds with their sequence number, B's sequence number + 1 and an ACK and the connection can be started.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2dwl7uUhBdSRe8KzoROzqZ1xuVl3HIJNkS7gO9_LX1EI-AhI4FWUjW7qTvibd6KKh8vNRqhO-jjusseI1TnjAW_x11Lmq_8P2YaXXQqrswyhkKG-qDDGfAt75N5-xL6h.jpeg) 
    - How a connection is torn down under normal circumstances, describe both one at a time and both together ↓ 
        - **One at a a time**: When tearing down the connection, host A sends a packet flagged FIN to B - then B must send an ACK to A, followed by a FIN packet from B and finally an ACK from A. This ensures that both hosts have the opportunity to receive all packets in flight, and potentially request retransmission.
        - **Both together**: Host A sends FIN, B sends FIN + ACK (fin in ACK of A's FIN), C sends ACK
        - In the case of abrupt termination (for example due to a process crashing) the terminating host sends a packet flagged RST ^^once they've received a packet they don't recognise^^.
    -  _What is the purpose of RST_ ―RST is sent if an application crashes or otherwise closes suddenly, it is to signal that the host can no longer engage in the communication and typically signals an error- a RST will then be sent by the OS in the case of a packets sent to a closed socket OR during resource clean-up if the process didn't close the socket properly.
    -  _Flow control - Why is this needed for the receiver_ ―Necessary as we don't want to overwhelm a slow receiver, this could be due to high network load, CPU reception thread slowdown, buffers filling up etc.
^^Also consider that the receiver might want to keep data in it's buffer for a bit while it processes is - so need to communicate current amount of space in the buffer.^^^^```^^ 
    -  _Congestion control - Why is this needed? - At a high level how does it achieve this (in terms of what is it estimating, and what additional considerations apply) - Discuss approaches and why all of them are terrible :)_   

Congestion control is a way of managing global internet resources, to ensure the best connection for all hosts. As the internet works under statistical multiplexing, if many users are blasting the network routers will need to buffer packets and congestion will occur. If no congestion control were in place, no one would be able to use internet resources.
At a high level, congestion control works by adjusting resources in response to high congestion - whether that be host bandwidth or the number of packets the router drops. Congestion can be estimated by the end hosts measuring packet loss, or the routers themselves advertising their congestion levels. 
        -  _Don't care_   
In this approach we simply don't think about congestion control, while this does reduce some processing and packet size overhead this will result in many packet losses as the internet is a jittery network.
        -  _Explicit reservation
_ Explicit reservation first requires users to negotiate with routers along their route and arrange the maximum bandwidth they can use - this converts a packet-switching network into a proxy circuit-switched network and comes with all the problems a circuit-switched network has, including high start-up overhead (need to talk to every router on your path), slow recovery from failure and possible hogging of network resources.
However, it does provide a solid maximum bandwidth and a reliable connection (if no routers drop out or need to change your bandwidth allocation).
        -  _Pricing_   
Routers drop packets of lower tier customers, and buffer higher tier customers packets in times of congestion. This requires a payment model, carries ethical considerations and faces the problem of what happens if a large proportion of people become higher tier customers (back to square 1).
        - Describe Slow Start―Initially CWND is set to one, and we double the CWND for every complete RTT without any loss. This can be accomplished by increasing the CWND by one at every ACK. $$\text{CWND += 1}$$ 
        - Describe AIMD ↓ 
            - Grow the window by 1 for every complete RTT without loss, this can be implemented incrementing CWND by 1/CWND at every ACK$$\text{CWND += } \frac{1}{\text{CWND}}$$ 
            - One losing a packet, set CWND = CWND / 2 $$\text{CWND} = \frac{\text{CWND}}{2}$$ 
        - When does a sender stop slow start?―Set a slow start threshold ssthresh set to some large value. On timeout ssthresh = cwnd / 2 - when CWND = ssthresh then start AIMD.  
        - Describe fast recovery ↓ 
            - Method of dealing with isolated loss by taking duplicated to be ACKs real ACKs.
            - After 3 duplicate ACK's, ssthresh = CWND/2 
CWND = ssthresh+3
E.g. we're accounting for the 3 duplicated ACK's
            - While in fast recorver, CWND = CWND+1 for each duplicate ACK
            - After we receive a new ACK, CWND = ssthresh = CWND_old/2
            - Note that CWND_OLD / 2 is chosen as a good mid point, we don't want to go back to the old value as that resulted in loss - and starting at 1 is inefficient.
        -  _Dynamic adjustments - Why does dynamic adjustment require cooperation (and why might a company like google cause a tragedy of the commons by 'optimising' their TCP congestion control) - What signal is used to backoff? - Where does the sawtooth come from? - What phases are there to the standard algorithm - What is Fast Recovery_   

Under dynamic adjustments, hosts probe the network (routers respond with a congestion level or hosts detect dropped packets), hosts then adjust their sending window accordingly. 
In TCP we begin with a slow start up to some threshold to poll the network speed, that is a small Congestion window (often 1 TCP packet) is chosen and you add one on every ack ( Means doubling by the time the whole window is sent). 
Next we move to AIMD after reaching an ssthresh (slow start threshold) - if an ACK is not received and a packet is assumed to be lost, halve the congestion window otherwise increase the window by some constant amount. This introduces a sawtooth pattern as the network usage linearly increases, the exponentially decreases in the case of network congestion.
Fast recovery deals with the problem of TCP being too sensitive to reordering/isolated loss, the first repeated ACK message received is still counted as credit for a correctly sent packet (but ssthresh is set to half the cwnd) (e.g. the congestion window is incremented as normal). Then after a set number of repeated ACKs, if a new ACK is received set the CWND to ssthresh. 
When you halve the next time wait a bit.
    -  _What are TCP's flavors_   
TCP-Tahoe - cwnd = 1 on triple duplicate ACK. Set ssthresh back to the $\frac{\text{cwnd}}{2}$.
TCP-Reno - cwnd = 1 on time-out & $\text{cwnd} = \frac{\text{cwnd}}{2}$ on triple duplicate ACK. SSthresh also halved.
TCP-newReno - TCP-Reno and improved fast recovery (default). ":) by Yash"
TCP-SACK - incorporates selective acknowledgements
    -  _How can routers help TCP congestion problems?_   
Routers could inform endpoints if they were congested, they could tell endpoints what rate to send at and they could enforce fairness. 
        -  _Outline Max-Min Fairness_ ―Given a set of bandwidth demands $r_i$ and a max bandwidth C, max-min finds **the **unique value f such that $\sum_i \min(r_i, f) = C.$ This means that for small enough bandwidth demands, no limit would be placed on the bandwidth allocation to such a flow. For larger flows they would be curtailed to the max value f. 
This method strikes a balance between accommodating high bandwidth flows, while not letting them take over the network at the detriment to smaller flows.
        -  _Outline fair queuing _ ―
Routers try and estimate when the last bit of a packet departed a router, and packets queue where the first sent from the host are first sent from the router (the idea being they've been waiting longest). 
^^In the slides he says:
^^![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PSqP_aPoVLNSzNY9PzAIjg71nWHz6F4TFs1H3v-FcQhxJr6itBqtanTpWNiU5FkJx0wUYPfKaqFVsHNxp9AP-bTXSIYZSUWm0AQP8McvEV550zI4GJvvyodbJ0Zk8H1v.png)^^ 
What does "deadlines" refer to?^^ 
        -  _Outline some general 'fairness' qualities and discuss under what circumstances each might be optimal_   
FIFO - first to arrive should be sent first, works in situations where the time taken to reach the router is approximately equal for differing hosts.
Small packets first - works when very large packets are common, and thus won't be permanently buffered while small packets are dealt with.
Critical packets first - packets marked important should be sent first. Works while hosts don't game the system by marking all packets critical
    - 
- **Supervision 5** 
    - Discuss DNS―The Domain Name System is a system which provides an IP given a domain name. This is required as associated IP addresses to servers can change, we may want to contact a different fragment of the server at the same domain name but a different IP. Additionally, no one host can have a complete lists of domain IP pairs - so we would like to fragment and spread that data around the web. 
        - Outline its structure
The top layer is the root DNS, this is replicated around the world by any-cast. The next level is top level domain servers, this includes country domains (.uk .ca .cn etc.) and generic domains (.com .gov etc.) these are maintained professionally. Then authoritative DNS servers can be maintained locally or by service providers (.cam .ucl etc.) which will provide the actual IP address of the host.
For example if I enter www.cl.cam.ac.uk/teaching/2122/part1b.html,
The chain would go ROOT ⇒ country specific (.uk) ⇒ Authoritative name server (,.ac)
^^Does my host machine strip the page locating part of the URL when I make a DNS query? 
Also what is the name for the servers between the TLD and the authoritative name server. As in Between .uk and .cl - or would the TLD pass straight to an authoritative which would resolve the rest. Slides seem to say there can be servers between, but googling seems to say if the first ANS fails there will be an error thrown.^^ 
        - Outline iterated queries―First you query your local DSP resolver located at your ISP, the address could come bundled with your OS or you could get it via a DHCP server (^^can we still contact DHCP servers on ipv6?^^). That DNS resolver then progresses up the hierarchy, querying first the root server for the IP which responds with an IP of the next DNS server to contact - this continues until the DSP resolver contacts a authoritative DNS server which responds with the IP. That IP is then sent back to you.
        - Outline recursive queries―In a recursive query, each DNS server is given responsibility for handling the request and a "call stack" of DNS servers is built up. E.g. your DNS resolver contacts the root DNS server who contacts the TLD etc. Finally when an authoritative server which knows the IP receives the query it responds with the IP, and the IP flows back down all the servers that queried before finally ending up back with you. This can be detrimental during heavy loads (either at heavily used servers like root, or smaller, lower level servers less used to the load).
        - Why might it being organised by an American company be negative for the world?
They could throttle/block domain name requests to competitors.
They could require payment for improved DNS request speeds.
They could strongarm businesses/countries into using their product/associated products by doing the above.
More attention might be payed to American infrastructure than elsewhere.
        - Given that DNS queries take > 500ms in most cases and each outgoing connection will requires one, how do we improve the speed of this? ↓ 
            - We can fragment DNS data across multiple locations, meaning a DNS server might be closer and faster to contact.
            - We can have caching at the server level and at the host level, so servers aren't wasting time re-fetching data and users can skip DNS requests if they already have the data.
            - Can implement negative caching, store common misspellings of domains that we know to be false so not to waste bandwidth.
            - With both types of caching, data needs to have a TTL - as the IP could change or a supposedly incorrect domain could be registered.
            - We can use UDP connections and compress headers for smaller packets sizes.
        - How can we ensure that failed queries fail fast?
Negative caching. As explained above.
        - How can DNS servers be use for an amplified DDoS
Because there's no way to verify the results of a standard DNS query, man in the middle/spoofing attacks can be used. A widespread attack could be used which provides an incorrect IP for a domain (could be done over a common shared network, like eduroam for example) meaning the website could not be reached/an incorrect website would be reached.
        - Outline the format of URLs
protocol / hostname [:port] / directory path / resource
Where the protocol is http/https/ftp etc. I.e. the request-response protocol.
The hostname is the DNS or the IP.
The port is optional.
The directory path is the path to the directory containing the resource.
The resource identifies the desired resource, e.g. image.jpg.
    - HTTP
        - Outline how connections are setup―First the client must initiate a TCP connection, this requires the usual 3 way handshake used in TCP.
        - What are the three most common types of HTTP request?
GET - requests a specified resource.
PUT - replaces the current resource with a specified resource. 
POST - submits an entity to the specifies resource.
        - Why is the statelessness of HTTP difficult to work with and how do servers fix this? 
The statelessness means every connection TCP connection and request is unique and lasts for the length of the request. That means that you cannot get data about the user to serve specific data over a series of requests (i.e. username, password etc.). To solve this issue, users store a small amount of server side data on the client side (in cookies) which they send with the HTTP request. These cookies must be encrypted properly to ensure privacy. 
        - How do modern web browsers improve the performance of loading a web page?―Through caching. Much of a websites content (stylesheets, pages, javascript scripts etc.) will be cached so they can be quickly retrieved without having to retrieve the whole content from the server - instead the server will simply inform the browser if the content has changed since it has been cached (if it has then the new site must be sent).  
    - Discuss content delivery networks
A content delivery network refers to a geographically distributed group of servers which work together to provide fast delivery of Internet content (they also makes DDOS attacks harder). This is done by distributing load, and pairint hosts with their closest server which can serve them data.
    - What is a reverse proxy―A reverse proxy is a cache of documents stored close to the server, this reduces server load so common documents aren't repeatedly causing server usage. Instead servers can be used to generate dynamic changing content. Reverse proxys work best for static content.
Also load balancing and firewalls
    - What is a forward proxy―Forward proxies are caches of documents (stored by your ISP), meaning the server doesn't need to waste bandwidth supplying the data and the data is close and can be retrieved quickly.  Again they work best for static content. 
    - How do we host multiple sites within a single machine? (consolidation)
Need multiple server processes mapped to different ports on the machine (through sockets). Then the HTTP request must include the site name in the header (the host address) which is required in HTTP/1.1.
    - Can we use the same approach to host multiple services (for example games servers) behind a NAT?
Yes, as long as the NAT stored the corresponding (IP, port) to (NAT IP, new port) pair so that the incoming request could be routed to the correct machine and the correct port in the machine. This would only be the case if that machine had made a request from that port previously.
    - How do we host a single site over multiple machines? (scalability and reliability)
Need to direct clients to particular replicas of a website to pair them to nearby replicas or balance load across multiple servers. This can be done by:
**Single location, Multiple machines**: Have one IP address and run a load balancer at that location with multiple servers available. 
**Several Locations**: Configure DNS servers to reply with the closest IP to the requesting host. 
    - Discuss QUIC
        - What is it?―QUIC stands for Quick UDP Internet Connection, it is a protocol that seeks to offer the speed of UDP with some of the reliability of TCP. 
It offers reliable transport, FEC, security through cryptography (a connection is started with a 3 way handshake to establish identities), better multiplexing and restartable connections. It's downside is that there is no absolute guarantee on ordering of packets.
        - Why is it implemented over UDP―Because TCP is so deeply ingrained that it is near impossible to change it, thus it's much easier to implement a new protocol on top of UDP. Additionally, no real change needs to be made to UDP - features just need to be built on top of it.
        - Who uses it?
The majority of Google's web traffic is in QUIC - aditionally over 75% of Facebooks web traffic is over QUIC. Many large companies that can afford to migrate all their services to QUIC and can benefit from the speed increase.
    - Discuss Bittorrent―Bittorrent is a peer to peer network. Peer to peer networks have no central server, instead a variety of hosts store parts of the database and share that with other hosts on request. These hosts can be distributed around the world, are intermittently connected and change IP frequently
        - Why is it useful for replicating 'linux ISOs'
Because bittorrent can facilitate higher download speeds than via a central server.
        - How does it function
BitTorrent functions by having many users send 256kb "chunks" of data to each other periodically. 
When a new user first joins a torrent, they must ping a tracker server storing a list of peers. They then contact a subset (their neighbours) to join the torrent.
When a user is sending chunks, they pick the top 4 hosts sending them data and send them back chunks. There is also the procedure of "optimistically unblocking", where every 30 seconds a host not in the top 4 is sent chunks in an attempt to make them part of your top 4. This is how new hosts start sharing chunks on the network.
When a user is receiving chunks, they periodically poll other hosts and request the rarest chunks first. When a user downloads their entire file, they can altruistically stay and continue sharing chunks or they can leave.
            - Outline the operation of a distributed hash table
A distributed hash table is effectively a distributed peer-to-peer database. 
Each peer is given an identifier represented by n bits. These are hashes to ensure all keys are in the same range. We assign a key to a peer which has the closest ID to the key.
Each peer is only aware of it's immediate successor/predecessor (and second successor to handle peer churn), thus queries take O(n) time.
When a peer wants to find who holds a certain key, they forward the request to their successor who checks their table and forwards it on if the value's not in their table. Once the peer with the value is found they respond straight to the original requesting peer.
^^Still not sure what the key/values actually represent - also in the bittorrent slides apparently a new peer contacts it's neighbours and requests what chunks they have, does bittorrent not use DHT's then?^^ 
- 
- **Assorted Flashcards**
    - What is the difference between a domain name and a URL?―A domain name will simply be the name of the website (e.g. www.google.com) while the URL will also specify a page within that website (e.g. www.google.com/images).
    - What is an application attack?―Send requests to a DNS server (having changed the source IP to your victims IP) requesting all subdomains (anything that sends loads of messages).
- 
