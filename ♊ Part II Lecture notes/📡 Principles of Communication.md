- To ask Supervisor
- 
- Lecture 1
    - What is Routing
        - What is routing?→The process of finding a path from sources to every destination in the network. Can be one to one, one to many, many to many etc.
What route should you take to connect to Antarctica from your laptop? 
Routing handles what routes you should take, are there faster routes and what happens if a link goes down along the way.
        - What is a routing protocol→A routing protocol builds a routing table for routers and switches to route packets in a network. Node then make  __local __ decisions (next hop location) that are based on  __global __ topological information (the shape of the graph). 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mn1cSkfQdXfaa-1x-KpBukDxqmqkoPCVRAC7e1ixecOQIIc6gsXZgg8c7XfEoQxikP5eHrVga7C1Q17bCFaKN3-uf65HCD2iwVYz_E4_iTqfmpAZcEtf6_j1Nv3reOBV.png) 

        - What are the differences between local and global decisions? ↓ 
            - Given that global decisions rely on global state, this state can be dynamic (a link going down or one path being found to be faster) and changing - where as the routers contents will not change on their own. Additionally, global state can be **hard to collect **as a system can crash without your knowledge. 
            - One difference is in the **timescale **of these events. Local decisions involve deciding where a packet should be routed with < 1 millisecond to make that decision (using a routing table). However, global decisions require data from around the network - this information is bounded by the speed of light. Thus, by the time we've found out a link has failed many packets might already have been sent.


        - What is route **oscillation **and what are the problems with it?→Route oscillation is when the listed route oscillates from one path to another from minute to minute (or whatever timescale,  more impactful when it happens more often). 
Consider if the route to Facebook was oscillating. The traffic along those routes would vary wildly from minute to minute, this would impact the users (the traffic load along those routes would vary enormously, thus capacity would vary enormously) along that route and the load balancing algorithms would perform poorly if the latency was changing wildly from minute to minute.
        - What are the requirements for routers? ↓ 
            - Minimize routing table space to make them fast to use and ensure there's less information to exchange when it is exchanged.
            - Routers should be robust to not allow black holes (information silently disappears into a defective router), oscillations or looping (A ⇒ B ⇒ C ⇒ A - work is being done but the packet will never arrive at it's destination). 
            - Should use an Optimal path (for some measure of optimal)
            - Minimize number & frequency of control messages - we don't want to flood the network, and we would like the system to be resistant to a lack of such messages.
    - Features of Internet Routing
        - Internet routing varies from the traditional circuits in a number of ways
        - Packets not circuits, meaning timescales can be much {{shorter}}. As we need not create an expensive connection. 
        - Topology is complicated and heterogeneous (diverse in character) - as opposed to telephone lines which were very much tied to businesses and were painstakingly designed. 
        - Tens of thousands of internet providers (contributes to the complicated nature) **and **many different types of connections. Fibre, radio, cable etc. (these affect capacity **and reliability**)
        - Traffic source is bursty! With a huge range of source behaviours
        - The traffic matrix is unpredictable, what does this mean?→The matrix of sources to destination cannot be predicted. We can't tell what websites a user is going to visit (messaging protocol might change). Far less predictable than who we're going to call.
        - Goal: Maximise throughput, subject to minimum delay, cost and energy.
    - Internet Routing Model
        - Describe the 2 key features of internet routing→Dynamic and distributed. Meaning it's dynamically routed, and distributed (rather than centralised).
        - Describe Intra and Inter-AS routing↓ ↓ 
            - AS means autonomous systems, for example Facebooks interconnected set of local networks.
            - Interior Gateway Protocols are used within a autonomous system. Generally optimizes for shortest path, whether that be shortest stop count, lowest delay or highest throughput.
            - Exterior Gateway Protocols are used for AS to AS routing.
        - Describe the requirements of Intra domain routing for high and low end AS's↓ ↓ 
            - **Convergence time** (the speed at which changes to the network are propagated throughout the network.). For smaller entities this may be less important, as the change in latency may be smaller for short routes and some connectivity disruptions will be tolerated. 
For larger entities (especially for whom speed is a requirement, e.g. trading) the convergence time is crucial.
            - **Should scale for the size of the AS**, low end AS's may only have 10s of routers while higher end AS's may have up to 1000s.
            - **Operational/Admin/Management complexity**. For low end AS's this will be simple and self configuring. Don't want too much human intervention.
For higher end AS's this will be complex and require operator hooks for control.
            - **Traffic engineering capabilities** (high end only) - for large networks you may create some boutique intra domain traffic engineering to optimize the system based on knowledge of the topology. I.e. you might want maximum throughput in one place, and minimum latency in another - (streaming one path and gaming another)
        - Describe the requirements of Inter domain routing↓ ↓ 
            - **Scale for size of the Global Internet **- focus on **reachability **not optimality (e.g. we don't want google.com to suddenly fall off the map). Sometimes we cant optimize, because different networks can be designed for  __different things.__  (For optimization, Google, Netflix etc. will put a server  __in __ (or very near)  __every ISP)__  
            - Should use IP aggregation techniques minimize the size of the core routing table.
            - Allow **policy-based routing **between autonomous systems! Business relationships (which forge the connections between AS's) are arbitrary! I may only allow a certain number of connections, a given speed etc.  __Qualitative relationships that get turned into routing decisions__ 
Needs to be extensible to meet demands for newer policies.
        - Explain this image and how it relates to routing:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MLv_NefWOyKGcX9aR1BBUiszy9PCshxAspmDsNt5HqMRXYmmWjqqqfSFpaKlXevfY8-YZmIS_8zNmLzPo6DliwG6-8prhMBLOvCoUIXZg8YAN-J7M4TTHwGitHazFy9q.png)→This image shows how an AS's are linked via Inter-domain connections. These ISPs (A, B and C) have users within them, and certain users are connected to other domains ( __**border routers**__ ). Thus a higher level topology forms  __between AS's __ - the inter domain level. The **Gateways ** will perform both inter AS routing with the other gateways and intra domain routing with nodes within their AS. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/93ln84Qx3G1SIZ0oC-zbLezY011WO-WSywyCB5f3JoHEY0OX2UgA9BDgsZrwsjSaAeB0iwfHiDpQYyqU9gyO-vZLA6hcg9jxERW2O8i1NkTQfzmOFVGHELVEavuGCIXi.png)
Layering:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-RcIB2Yym-PJiE_gGx6gvYMV5q4-S15VKW--0mh0iAj-y8jkO-hI_ieZWBhCb-H8oqqkwR31ZETOYzniHjWDlabVw7dDfcS4IDnFc5e8sUk233HrO_ucRTOvTu6-ZEZ6.png) 
    - Basic Dynamic Routing Methods
        - There are other ways to do routing than how the internet mostly does it, by→forwarding on IP network prefixes. Each network has a unique IP  and each router that the packet traverses will examine this IP destination address and look for a match in its routing table to figure the next hop of the journey.
        - What is **Source based** routing?→Source based routing means the entire path is computed at the source (based on a stored topology) and it then communicates that path to the routers who will obey. This can be done be encoding the route into packets (can be large & inefficient). This can be used to recover from outages or avoid certain paths. Could possibly be used as an attack vector
        - What is **Link state** routing?→Per-link information is known to routers, and periodically routers flood the network with their link information to get a map of the network. This map will be the same for **all routers.** Need to do Dijkstra. Fast convergence
        - What is **Distance vector** routing?→Per-node information - at every node store distances to destination nodes in a vector. Set this up by peeking **only at your neighbours signposts! **This can be better as you need not flood the network and share your entire network with competitors. (will converge to same) 
        - Give a reason for choosing either Centralized vs distributed routing→Centralized is simpler (and can be optimized better), but is prone to failure and congestion.  
        - Give a reason for choosing either Source-based vs hop-hop→Source based allows for easier network engineering, as it allows for specified routes. But you have to encode a lot of data in the packet header.
        - Give a reason for choosing either stochastic vs deterministic routing→Stochastic routing adds randomness to the route. This can spread network load and avoid oscillations **however **results in misordering. 
        - Give a reason for choosing either state-dependent vs state-independent→State-dependent can allow for recovery from failure. However, state-signals are always going to be a little bit stale and it means more communication & complexity is required. 
- Lecture 2
    - Central routing
        - Within a single network, assume all nodes involved are part of a single security domain.
        - Describe SDN→SDN (Software defined network) is based on antithetical architecture where you can reprogram the operations of the network. Switches and routers have an open API, allowing adding and removal of entries to the routing information.
        - Describe where traditional routing wins and where SDN wins in manageability, flexibility, scalability and robustness ↓ 
            - Manageability: Clearly SDN is more manageable. We can route gamers traffic one way etc.
            - Flexibility: SDN is much more flexible. Trade off queues and delay to get an improvement.
            - Scalability: Traditional networks are scalable by design. Scalability of SDN depends on the network.
            - Robustness: Traditional networks are very robust, SDN's are **not **robust - if the central node crashes, you're screwed.
    - Fibbing
        - Describe briefly what the  __Fibbing __ protocol is?→Fibbing is an attempt at a middle-ground between traditional routing and SDN's. Wherein you have some control over link-state IGP's.
Want high manageability, flexibility and robustness.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sEDR9MH1qVaN5XxBD_QnwLfaKy0OPC2jJ9-ZnIc0Gbc-FZxNj5aGH5LMV25Zo3nZ4resT-yn0jWvdnv1R7gEPT4To5XxFk2OgVgjK51EFIJwtpU6F8lBXQgxDtz0Yl72.png) 
        - How does the  __Fibbing __ protocol work?→Instead of replacing the normal routing protocol, we instead  __lie __ to it (using carefully-computed information) to provide alternate routes. 
So if a route is going unused (because it's not the shortest path), Fib first inverts the shortest path computation to figure out what needs changing. 
Then it invents a virtual node V1, and tell your source node that the path to the destination via V1 is the same or better than the shortest path. Note that FIB pretends to be one or multiple routers, and shares routing information.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ViINGwGcNzO58xtLjE8fMu3fs2ONsX6bFbNSVHzsat9vw1dovFYRV_uYgsntuDqWpIGXy92cZVuEC00bpMw2GMI0W6zSBihWI71RES3P1BHJJZyBkAZwP8-7Dr5Qm853.png) 
Note that the virtual link  __still physically goes via A.__  
        - In some cases, you might require multiple virtual nodes. But you  __can __ merge multiple virtual nodes. 
        - How many nodes would need a virtual node attached in order to get this to work? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CB3mFUFi_GAk577TTQxjKj2k47UW6l9OKkHtJpHSW7O1oJflvdx0bqmwYZ01o_9J4rutLYwfaGuKJsjdlW9NX4ipOX_x5JbnuLld3yhXul1xgiNWCoWqdIR34jqW2MBC.png)→In the simple algorithm every node except F would need one
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j-Tfy6chlaMbVod2qP5Ky1ctSQ9j8ASZaNby3fhwrA0sNVp9g-taXza04DoddNr3G5PZvGWsRlD21DHGn6X6xNabSIpna8x-DZ05ATPsT7D5SQ5YqGrAUzjicUPbNpz4.png) 
However, we don't need the nodes at D or E - because once you're on that route there won't be a reason to double back. And you don't need them at C or A because  __we only need to lie about the link from B to F__ ! 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bKIgBBJUwpx7lbBmN_vZf1G3Ic_MIss4XYr7msLDw_BS19VL_8BebHannSj9z1KvcKwQEcxIFX-FzPpQrt2tD-hIPznYq8FIbRBIkLKH7jeASN4Yuvdxv1bvhkEVHx-a.png)
        - How does the Fibbing protocol achieve robustness?→It can distribute fibbing controllers, having multiple on the network in case one or more fail. 
Also, if a real network link breaks and you're left holding a link that's lying - that's fine! The distributed network protocol will realize its broken and act accordingly - finding the real shortest path.
- Lecture 3
    - More on Fibbing
        - Note that fibbing has a very low impact on routers - meaning it scales well.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hlgAjXuHRH__9RLioNFteZC0iRuhH8kdRoGjT0f3DNcO17GaS9At7cbsmCP8zeIRyvItSpcNtJM1olz2q5i8mOyBSTB5rsz5ZVUsduPdaw1esbDOJCAb06_ZTRIUz2w8.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/joXnjEnbWpmXyzgwlX3pZfVDcyaWsN18Tt9Dlio3sEttxedC_w9MV0biF0e8L2x67_dj97SdEn3maZwIs9P5XC2ELUpCxaw1WWn8Ssci3O7INVBYz7JSrmc60iPda1ua.png)
Here the failure occurs at the end when the controller cannot be reached at all. This is only the case if the red flow was a special case which the controller was controlling -  meaning once the controller goes down, we don't know handle the red traffic.
    - Multi-Protocol Label Switching (MPLS)
        - What are port fields?→A field stored in the packet which defines the destination process. 
        - What is MPLS→Multi protocol label switching. This is a forwarding scheme designed to speed up IP packet forwarding. 
The idea of MPLS is to use a fixed length label in the packet header to **decide packet forwarding **(As opposed to longest prefix matching - which is complicated and isn't just a hash table)**.** 
Instead use a 24 bit label that maps to an output port & that's it!
Note that labels  __only have significance in a given switch.__  
        - Called a shim layer, stands between the link layer and the network layer
        - Describe the MPLS Header format ↓ 
            - 20-bit label value
            - Exp: experimental use - can indicate the class of the service
            - S: bottom of stack indicator, 1 for bottom, 0 otherwise. This is used because you can stack MPLS headers.
            - TTL: Time to live:
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_vFZAA3XzWc21ULJIoHrlN7BP1RIU3cViA9PgE0WUR1S7fdorm5x3A-1Bscl8vtBEO3ttoxKN3ILg1gZCzI6mwucC0TOLwWahXdyD9KOV1aUFSFfOw9SesSSixquyKTf.png) 
        - Forwarding Equivalence class
            - MPLS capable routers are called  __label switching routers (LSR)__  
            - What is a forwarding equivalence class?→A subset of packets that are all treated the same way by LSRs (label switching routers) - for example if I don't know anything about a packet destination, just send it to switch X. It's just a group to bundle a class of packets that will have similar network behaviours.
A packet is assigned to an FEC when it enters a MPLS domain.
            - What can determine a packet's FEC? ↓ 
                - Source/destination IP 
                - Source/destination Port number
                - The protocol ID
                - The Incoming interface
                - Differentiated services code point (bits in the headers that will tell you we want high bandwidth not low latency or vice versa)
            - Different {{scheduling and discard}} policies can be defined for a given FEC.
        - MPLS Operation
            - Describe what will happen to a typical MPLS packet starting at the ingress to an MPLS network ↓ 
                - First it get's strapped with an MPLS header, with a FEC class encoded which depends on feature of the packet.
                - At subsequent LSRs: The label is used as a key into the forwarding table, the value will have both  __the next hop __  __**and **__  __the new label to wrap the packet in.__  
The old is replaced by the new and the packet is forwarded to the next hop.
                - Egress LSRs strips the label and forwards the packet to the final destination based on the IP packet header.
        - Label Switched Path
            - What is a label switched path?→For each FEC, a specific path is needed. This is the LSP which is assigned and **unidirectional **(goes in one direction).
            - To set up an LSP, what must each LSR do? ↓ 
                - Assign a label for packets along the LSP (label switched path) depending on the FEC (forwarding equivalence class).
                - Inform the **previous** LSR upstream of the label we've set.
                - Learn the label from the next LSR so we know where to send a packet next.
            - To propagate the labels we've set, we need a label distribution protocol - the forwarding table is then created as a result of the protocol.
            - LSP Route Selection
                - What options do we have to decide on a route ↓ 
                    - Hop-by-hop routing: Use the route determined by the dynamic routing protocol (shortest path).
                    - Explicit routing (ER): The sender LSR can specify an  __explicit route __ for the LSP. This can be selected ahead of time, or done dynamically.
                - Explicit routing allows for establishing LSP's based on policy, QoS, etc. Additionally, we can have pre-established LSP's that can be used in the case of failure.
        - Diffserv-Aware MPLS
            - What is Diffserv-Aware MPLS?→Switches and routers have special case scheduling, where different users get a different share of the network. Differentiated service! 
You can then bill people for their different service and collect $200 as you pass go.
            - How is Diffserv-Aware MPLS done?→At ingress, packets are given their standard MPLS packet but also an extra one which defines what type of service they will receiv.
Core routers then process the packets based on the labels and Exp fields and the networks will do different things with queueing and scheduling etc.
            - Bandwidth brokers then buy and sell bandwidth, higher bandwidth and lower latency.
        - MPLS Protection
            - Link-state routing has a restoration epoch time of seconds.
            - How does MPLS enable fast failure restoration?→Compute the next best route, then if a path breaks we can immediately shuttle the new start label to the ingress point. This path would have to be link or node disjoint, so if any link/node fails, we're still okay.
The timescale would then be RTT - rather then whenever the next epoch occurs in link-state routing.
        - Label stacking
            - A packet can carry multiple labels, organized as a stack. Processing is always done on the top label.
            - What is the purpose of label stacking?→Using label stacking we can group multiple LSPs into a single route, called a tunnel. 
This new path get's pushed on top of the stack and will get popped off at the end of the tunnel point. 
- Lecture 4
    - Segment Routing
        - What is segment routing?→Segment routing is a loose type of source routing where instead of every hop changing the routing behaviour, the routing behaviour changes from segment to segment - i.e. initially a stack of segment header is pushed on, then at each segment node the top segment is popped off and the packet is forwarded to the next segment.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sMzM0xK8qxQ_1_ik9BIF-wNlyhpjJ6pQkxaEgPgTJSUrqQtIWAYGtG0XKfTIg2FdJH589o7MYrsxxAXcGUAkfnqfGwhmGhrw6sQw4hUBVFYXzIfr_Hgxr7pymj6jeuFT.png)
        - Operates on the IP layer (kind of) - treat packets differently not just based no shortest path forwarding, but note that you may not have to do something special on every hop.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XaJjvuPAK9tNWHbnE_N7mXsyd4XfWKbWpxMmzvOlr3pFyyfKCpEy6H0IyTjouV5VRSOFuI2QIn9J6l2WpeYtmaJ6Ikjkghg6vAkvB7L1k7MvpTAG8yKfFNBD1oLTO-gL.png)
        - What benefits does segment routing give you? ↓ 
            - You can do the traffic engineering, send a packet along one segment if it's low latency and another segment otherwise.
            - It means your paths are more resilient: You have distinct routing along segments that share no nodes, and segment routing can facilitate fast recovery (don't need to wait for router advertising).
            - Easy to expand to IGP (inter-gateway protocol), as you can advertise the segment in the Link-state advertisement state)
        - Describe the synergy between IPv6 and segment routing→Segment routing headers can be implemented using IPv6 headers set to forward to the next header (You store the list of segments in the segment routing header then adjust the IP header when you reach a segment node).
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FvjFDiR8jaANTYPaK4SPcbehWIOnWs2UiwJMqMvuX-qSaFUD47KIiYaNt-OnDyl66o05kSPAuihDV3byMWlalnQAuBJ_yq8ctu5CH5OF3k74YnTOn29yWBRZreKxdg43.png)
This means routers that support IPv6 can support segment routing out of the box - they don't need to learn the segment routing header language.
    - BGP
        - Customers & providers - running costs and initial investment costs need to be offset by charging people. 
        - If I need to connect my West Dorset ISP to a network in Canada, I have no choice but to talk to a bigger network like British Telecom - they will then be connected to people with fibre under the pacific, through this packets can be forwarded.
        - Peering
            - Describe the "peering" relationship?→Peers are backbone providers that talk to other backbone providers - providing transit between their respective customers. Note that peers do **not **provide transit  __between peers! __ Because they would be acting as a provider for another peer:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/N72Ff8PHN17313wDaX66Di07dMu82CmGhyMRKZsOOdNjoOQWaMpvh2rTvnBmCwi1MDrZ5qyG8Dol7nsrESn4s8Pxx4yP61t9xYdk8FZqJOgZOynLZBSwkg5aocIvQCH6.png) 
Traffic is not allowed along the dotted line!
Note that peers do not exchange $$$$$ - they seek for traffic to be equal from and to them, meaning both can provide a service.

            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CWFJn9fk0GrNw4BqKDAQof0Oag8uFBRlrumDyDBEsq-Es5Uyhbcj49X9Ziqle-n0O4ORZKXihnPAUk_6ZLBQmjeEwvt1ZpcljpBFo5NNCnXAQQUNZrEm29MgQu1DCTWD.png)What does this image show?→Demonstrates the hierarchy of providers, providers can have providers - meaning you go up the chain and then back down 
            - What are the reasons to peer or not peer (3 pro, 3 con)?↓ ↓ 
                - Pro: Reduces upstream transit cost
                - Pro: Might be the only way to connect your customers to Tier 1 internet providers

                - Pro: Can increase end-to-end performance
                - Con: You would rather have customers - you would like someone to pay you to connect to your users, not pass over connections for free
                - Con: Peers are usually your competition who you will be benefiting by giving more users.
                - Con: Peering relationships will need to be renegotiated periodically
        - Forwarding
            - What is the difference between routing & forwarding?→Routing defines end-to-end paths, forwarding defines the next hop. 
            - Border routing gives you interconnectivity between AS's, however you don't have enough information (ISPs don't publish all internal topology) to form full routes. 
            - Why wouldn't an AS publish it's internal topology to allow for better inter-domain routing?→You would have to flood the world with all your router information, this would kill the network and does not scale.
Additionally, a given ISP has customers it's optimized for - if you knew how and where they've done that you could steal their customers.
            - In what two ways are forwarding tables populated→Statically and dynamically 
            - Describe static forwarding table population→Administrator manually configures forwarding table entries. Giving more control, allows for not just destination-based forwarding. 
But obviously it doesn't scale and is slow to adapt to network failure.
            - Describe dynamic forwarding table population→Routers exchange network reachability information using routing protocols - routers then use that to compare the best routes.  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r8mspHPETYebvtI-S20A96ZqDWyIHB-ibanVzHtqZ3_yn2bbuba5CoMM2WTO8T08IJ7d1mSpcImpnguKBqq_M8ct525nIE7wLIUxKVTCDNb52rMqSsgu9rn4x9zQx5nL.png)
        - Architecture of Dynamic Routing
            - How do edge routers learn and share routing data?→The edge router hears the internal and external routing - it then takes information from the outside world and maps it into the inside world in the forwarding tables. I.e. it will share that data so other routers can figure out where to forward so the correct edge router receives a packet going to a different AS.
            - BGP is a {{vectoring}} protocol. Meaning each router knows a little about {{network topology}}, only {{best-next}} hops are chosen by each router for each destination network. The convergence focuses on {{connectivity}}, not optimizing some metric - then the network {{converges}} on the best paths.
            - Routing computation is distributed among routers within a routing domain, routing messages are usually not routed - but exchanged between physically connected routers. 
Note that shared routing data can be stale.
            - A border router opens {{TCP connections}} to all it's neighbour routers! Even though those neighbour routers, may not be {{one hop away.}} This is because you could have disjoint bits of the network connected by multi-IP hop bits of network - e.g. the same AS can be in different places around the world. Here, the turquoise bit is all one AS, as is the white: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ShM4LqdcI6HsFR6ucrjwWYxS2GqQ7uAbaxugD6V5ZQ5B1jfMuV_Ydm7E2HPsRPuk5XDVAybH_GjlqAuMh7B1Ug70RhFFwQV0SNgXAFWuoP440Sk-NA7AQkk480-2LStH.png) 
            - Autonomous systems are given numbers, these are centrally allocated.
            - In this case, BGP will not be needed - the network will simply find the shortest path to one of the border routers.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hBw3yxm--Nz7ELIBjovG_Bcd9q9BdRdt-mWPRQbVihqrPM2nDGUkRKBD_7EjUlpYnamJ5TCmvLwRQav6az37k7JjlDFhX8aIK6VnLPwGNTw9O17Crhi8IV7X55mfCvs1.png) 
            - How can ASNs be shared?→Paths in BGP will be computed using the IP prefixes NOT simply the AS number.  
            - Autonomous Routing domains are not the same as autonomous systems because→ARDs can share the same ASN, or can have multiple ASNs.  
- Lecture 5 - BGP inter-domain routing
    - BGP - Border Gateway Protocol
        - A policy-based routing protocol which is the de facto EGP of today's global internet. It's a relatively simple protocol, but configuration is **very complex** and the entire world can see and be impacted by your mistakes. This has been done in reality, when an AS in China advertised itself as the best route - meaning they received all internet traffic for a time.
        - Describe the process that occurs when a border rooted is turn on under BGP?↓ ↓ 
            - The router first sees it's neighbours and connects to them via TCP to learn about the world through the BGP protocol. 
            - It then starts to exchange information like what are the IP prefixes that are **in their AS ** __or__  __** **__ **Reachable across their AS**. I.e. Exchanging all active routes.
            - They will continue to exchange incremental updates over time.
        - What is iBGP and what is the problem with the mesh configuration→The router also needs to learn about other border routers **within their domain**. This is needed so the other border routers within the AS can share routes and IP prefixes with each other.
iBGP (internal BGP) is used to communicate using IGP (internal gateway protocol). So all the border routers have TCP connects to each other! 
Under the mesh configuration, we have bad quadratic scaling: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FkaUTMKaac7MDJIEu1uA7ZrCwDBTtzsJkJ7j3hB7dI6fcMDv6i9HrPV0Lts7Qy6r8cpozIaFxZHOyVOPPR4FZ8Rg6VTdAFQoQW8LwYFb6831Tmd3WUOP0eMXgD0D-ilu.png)  
        - What are the fours solutions for the iGBP mesh problem? ↓ 
            - Buy bigger routers
            - Break AS into smaller ASes - adds complexity and operational costs.
            - Route reflectors are used to build a star network rather than a mesh: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GXtPR0JYW3hWwmrHd4N_8f7IrCDYXoSBnm0nCR9SKbpYzFlXxQKRz-sRn_Z6h7aE78NE6pwC9Z5WEbABygdZWqppGXrC2D8KvkL7ymJf4Lxm09nbTw2x6fwnZRlmoyLu.png)
These reflectors past iBGP updates to clients and perform some filtering - only allowing the best routes.
            - BGP confederations -
        - What are the four types of BGP message? ↓ 
            - Open: Establish a peering session
            - Keep-alive: Periodically handshake again to make sure everyone's still alive
            - Notification: Close a peering session
            - Update/Announcements: Announce new routes or withdrawing previously announced routes. 
        - What are BGO announcements?→Messages that announce new routes are withdraw previously announced routes - they are **prefixes** + **attributes**. 
        - What are BGP attributes?→These are pieces of data/configuration used to decide the best route. 
If a router is advertised the same prefix from multiple places, we need to be able to make a decision.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bht_ewP9ucARLh2St1E7Rjg3OulPllzqdTYFm729eWQP1Zd5x4e_eBC3RK7jqBAbGCg-_3fYI7QMwZCKt0gxin_ToxotUb8zJ9oefL-044jVEnwdVtVgI9HUko8HK1Xq.png)
        - BGP Attributes
            - What is the AS_PATH attribute→Whenever a route passes an AS, the router adds the AS number of the AS it is travelling through - if the path of the AS was previously in the AS_PATH then the route is ropped.
            - What is the NEXT_HOP attribute→This stores the IP of the router that ADVERTISED THE ROUTE (**NOT **the next hop along the route):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kPTkXDyyi76XmWVjKZvNomqykeXJMdmK76-f85iVr5iVDsy7Ytdcwsw1GJFEMWpPHpNkn0fhA5fE6EtcvUw9QVoWqjkN2Dmt1om4LZd4HScSO3gTgn-nFjpjp7x8gYSr.png) 
            - What is the MULTI_EXIT_DISC attribute?→Multi exit discriminator - if there's multiple choices to enter a AS, we use this attribute to decide which border router to enter via. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b8uGkALXRWS5edF16UKt8CbwX1MPPHQTCjYldof5VIddAdr1g9wvHyp-r-7eVhaDtN7BfLLKBjZ3h_OExUjB1WOOkNNz8flIUGTeYHRwV_C6gydVl0qBwOFXiINBj2EU.png)
I.e. here the top AS notes that the bottom AS prefers to receive traffic via the left router, so it chooses a border router appropriately.
            - LOCAL_PREF: Used to choose external BGP paths - i.e. choose the border router to **exit via.** 
            - What is the COMMUNITY attribute?→Way of aggregating routes together. Useful for differentiating customers, providers and peer routes. 32 bit way to group things with no predefined values.
            - ORIGINATOR_ID:
            - CLUSTER_LIST:
        - How is route selection done in BGP?→You work down an ordering of attributes, and try to break ties as you go.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ik1k-KSpgsxOsRQSsOP-r4vF3VCEUcBF9mS4pMR9suWpODZ2FXw09UB1FiHYqWgS3FSkqgJebYNq8a-PXnj0oeXEuzJSt6GykFyub3K120kilJggjquY_Ks1NbaV5J_5.png)
        - BGP Route Processing
            - Describe the 6 stages of BGP route processing↓ ↓ 
                - First we **receive **a BGP update 
                - Then we apply our import policies. The policies are specifically written code that control things like route filtering and tweaking attributes.
                - Best Route selection is decided based on attribute values
                - Create the Best Route table, and install forwarding entries for the best routes in an IP forwarding table
                - Apply export policies, more route filtering and attribute tweaking. Also open ended programming like import policies. You filter the information you've learnt over the process because you might not want to tell everyone what you've learnt (for traffic reasons, business reasons etc.)
                - Send a BGP update
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/s1Lwilw8VUYzAvFcdgRMkfRUwbsvMpcDTjiBXrgEJFe3eL0DLw3FOKxRyqf7WQNqPHfg3OUP3SfvYzpCOdrP-SzfCvjwCHqDuLhFymvRrJtsxx4_vjSMAY6yh3BCPyTs.png)
        - Combining EGP and IGP
            - What will the following combination of forwarding table and EGP result in and why (For the router pointed at by the pink arrow):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lvgRxidvsFdIzh4RCXCuGyau4XJBUCuHyaS3TT9X3mgF4-Ze95QbnzKDCE53D3a7eAsIPFbCxex_wMyWrBR1dyNU7GqZBoicIj7_UOD1UuzlPCxd2QZeAteXLw-G9exg.png)![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/s-2ZBFH8x4jaT5BQaVxI7krJwjgwGXs91N5znnmnl_F2X-U9a1rXJYR4qHEpa0M51X5id8_vtDmiXKdw2SX7EZNYPczEDj2ChGt2qwZsMXfeTfxYUL3axTNemNq7kmc6.png)→This results in:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2W-fOBhbNRlXR1YqE0OJVN3m4cTbP765TY5Owcss_45hGLBO1PJJsMkHBROJrRi-y0WXnTnKlLjxDlKja5XuyakKw-L3Mle43fItrdGWaCuKYh78wpQiyFUeKB3WfYuy.png) 
For 135.207.0.0/16 We know we received a message from AS2 at this address - and to send there we can find the best next hop address.
Similiarly, for the connection 192.0.2.0/30
        - Implementing Customer/Provider and Peer to Peer relationships 
            - What do we filter out when we export routes to providers and peers? How about customers?↓ ↓ 
                - We filter out the routes gathered from other peers and other providers. Only providing customer and ISP routes.
The ISP routes are the ones we know about already.
                - We do no filtering for customer, we love them. 
            - First we import routes from peers, from customers and from providers into a database - note we also store ISP routes that we know ourselves!. 
When we send to  __providers and peers __ we  filter out any data from peers and providers, only sending customer and ISP routes. 
We give everything to customers.
            - How would it be decided which route to choose?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Z3IOiRjZpK03quUpnbE_ZJhEU7VrGwgRnGkvdkyKK0qvM1A657WHMcsLE48yBxMpdJ2pTRtXDft36OnIycq1TPu9JoV7Qlvb-yLIPyh22eD1-SauxP6MO4y_WujchuOo.png)→This would be based on local preference - iBGP is used and decides it's local preference for each route, it will then choose the highest one. 
This still allows for recovery from failure, once we know that a connection/route has failed along the way - we go the next highest local preference.
Incoming announcements are tagged with a local preference.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IvDN3ogn79I_OoIziS9WGTPxMPwfMaAE-hLUNvnmyjDsfmBubJxuYCFZEPnm2XIV3ThJmmSW601wFqfhYlB2Q4WJz3N7KYLd_xAYhLPLrlan7yd4TQ38dtW1aMzBkkAD.png) 
In this case it will go via AS 2.
            - Why don't we just run a ping application via different AS's and decide local preference based on the fastest one?→Because we are routing via whole AS's - it could be 1 router hop one day and 27 the next. The internal and external routing worlds may differ a lot.
Note that shortest AS path is not necessarily the best choice either:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5TwB6Mxy3GsK90satISoo3U9b_gbFA2KBdWYCAjGEgVsteXYYH3JoIzlV_x88izgOIffbV-xKLUv2kekXssihgQY6j4-gtOTzxtV5ssSUiKjTDRL-zevRK6ZCiHUfoMD.png) 
        - Traffic Engineering with BGP
            - How can you do traffic engineering inside and outside an AS?↓ ↓ 
                - Within an AS, you can tweak metrics on the link state protocol to change the routes however we like. 
                - At the BGP level it's much more course grained, and we don't get to tell people about real performance metrics (other than AS hops). We **can **tweak attributes for outbound routes to get other people to do things we want. 
            - How is BGP route advertising different from link state flooding?→In BGP route advertisements, not everyone receives the same information and the information is not sent in a timely manner (necessarily). 
Routers may filter out AS's that they communicate routes to AND routers may wait while they perform some computation before forwarding a route. We don't want other providers to steal our customers.
            - Does traffic always follow the ASPATH? Why or why not?→No, an AS along the path may decide to filter routes with a destination with a specific prefix or for too specific subnets (to not pollute the world with a very specific prefix and increase routing table size) - in which case the route will go another way 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0Uh_AlU3hFGmw-FdWs_gR5fSQyDgpG_xNIyCfGD_Z0eFEezFQcMSoz2oIOQJbNyDkIQsmlNuDzDeVVB9AfUF1P_5RgssQ1-n_88LQJ8-kzwGzruTbb7gvi6ranH8qcOY.png)
- Lecture 6 - More BGP
    - AS Graphs depend on Point of View
        - Peers don't transit for other peers - they transit for other peers **customers **into their customer base or upstream into a higher tier network - but they don't transit for transits sake.
        - What would the network look like for router 4 here and why?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FtRKtTZVNoZMs_oP8vfpPcc0dPMRky42qSvc0IOk9meqtGXUyM0YASq2hDG6b2VX4JZqHFOLa9hBVwS8gygb8wBprB2SJJiRQuseATVbiFlGYeRkiCKDr6i9fPAta0IT.png)→It would look like this: 
You can figure this out by simply following the routes to each node. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gFWR4jkTpYwdEGb6qyONemLOaYKxEWSzS4-kwNso_4GzpiUMRqJJ6Lo3uQSpxHCOuJ2dNZmP5hUczAq8wB7d3eAfLUZla8fTEKqleVXfsugDziIjBmxS79IQJkO2SR4A.png)  __**
Because **__ peers don't transit to another peer, **unless **that message is going  __directly __ to one of that peers customers! So 4 could never have a message go from 1⇒2⇒3, because 2 would be a peer who's customers we **aren't** directly accessing! 
    - Implementing Backup Links with Local Preference
        - ISPs want **high redundancy** to allow for **high availability**, especially to higher up networks. So you will have backup links. You would like to control such that all traffic goes by the primary link unless it's broken - we can do that with **outbound** traffic, using local preference.
        - How can you manage inbound traffic in BGP?→Note that the ASPATH is a tie breaker between two equivalent routes, so at the backup link - we add the AS number multiple times to the AS_PATH. This is called ASPATH Padding and it's a ridiculous hack.
So for an AS 2, the primary link ASPATH = 2 and the secondary link ASPATH = 2 2 2
        - When does AS_PATH padding not work? What is the hacky solution to this problem?↓ ↓ 
            - If the path via the primary link is via a peer, while the path to the secondary link is a customer - the AS will prefer to send the traffic via the customer than the peer!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bD70GK60HIpe3RiSnDQlpaX3kOaRhy9NhPWmFO4vrS3CM4wjDKp0PJ3aGLyaQqroU3_0VwxG667CcqVKnbarwkO3Mk4Iu1M7G_Kvuo4SGfd2Ab7bgk5fHbAvs5tS0i7i.png) 
            - The hacky solution is to call up someone at the other AS, and agree on the meaning of certain COMMUNITY attribute numbers - you agree on a mapping from community numbers to preference, then paths along the backup link will be given a community number representing a low preference. 
This is up to the other AS though...
        - What is hot potato routing and what's the problem with it?→Choose your egress point based on the IGP distance to the two border routers. This could be bandwidth based, latency etc.
                          ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qrBwh17_QZz0_DDmRV6mgmMontTE-mzYW4vytrzTDsOKFuQZEX-r9aQ2uA3CRNJ5MSRW8hABfK3HTG3XjxMrT5GrgMIYUNuKdHAczITfUJaXxGEsUDmRtHawUtARWMzT.png)
The problem is - that border router could be much further from your end user:
                       ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vABVW7E1OB_-C1jdFKityitQcp8v-PWqKg9b0lRgnGJnk3BKIkLiYxHbmEtM6z9mtzCtg5qPB0_Ygc6xr_AO7YnrY7BpbR2As5pAt-nIa6WJe8newQYQLQzdexdElVyg.png)

 
        - How do you control for making sure messages are symmetric AND why might an AS not pay attention to this control?↓ ↓ 
            - You can alter the MULTI_EXIT_DISC attribute and make the router your sending via have a lower value. It would make sense to link the MED to the IGP distance, but it's not always done that way. 
            - The AS now needs to consider the MED you've set **before **they consider the IGP distance - but that might be too slow or inconvenient for them, in which case they'll ignore your dumb ass. 
        - What is route pinning? What's the problem with route pinning?→When you have a primary and a backup link, if the primary link breaks and then recovers - some traffic will be pinned to the backup.
You could have a contract in which you say **you'll only use** backup link if the primary link fails, which you'd now be breaking. 
        - BGP is not guaranteed to converge to stable routing, it can {{livelock }}and oscillate. Furthermore, BGP **is not guaranteed **to recover from {{network failures}}. 
        - Describe the stable paths problem→The stable paths problem seeks to ensure that every node on the network has **one **path to some root node, while maintaining reachability. For example, here we have multiple routes to the root node - and we make a decision on routes that maintains reachability.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yGh-m5LwaOJ8MacaGodWIFYZr9A_fc-Mzptt2cEFzuIarOfANsmKIJ-LZ6RzYnZTPVXQnkHOpiA-VDIEQB2d33CqsLtAB4X4pWwSxd7H_ObH7uLONaEfd81qd9f0sr5K.png) 
The SPP can have paths that disagree, and you'd better choose the solutions that agree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5McD2tw6zfMlBE6O8BU24xZJDrJdhZLtLLMH0YQKcM6Mc38UUhmGm-qOQANSP_C2FNMfJzX2wnuN35GdC0Eo0ie0o1Z2m6C4qpoBZ6WxD2kidTe14nOdJakNlNAYdCaw.png)
        - What is route triggering in the SPP?→When the primary link fails, paths along the secondary link are called upon and then both paths are in use when the primary link recovers: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hCOztBEzTdw4oMTuaoNftVcU8bdT-7ZlQed2-V1w-Oh-vrMQ5Ggt7W-vD47KRKpFxWGoC7Y1d4b2YBlhbEYeE5cgoManN05JD1KLtUDoQVIwMrpSVKKZc-Ls0Bg-RiyL.png)
        - What is the bad gadget, and what do ISPs do to avoid that problem?→The bad gadget is a topology in BGP in which **no stable paths are possible**. I.e. no path where everyone has a set path **and **all nodes are reachable:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TJF-iIF_I0DHY6K7bzqoRAmOEYimDZE9njD3m0IHMebRahb5IlcEy7I_bStqJ-ThG6O1-HVfXAtkFmstG9ZTX8-VU_hvpvdxBD4wHKC3uZi4Fd2-wU8yp_9BYVRBcjDd.png)
This topology can happen in the real world, and to combat that ISPs communicate extra information about BGP. The problem with BGP is that it's information hiding, so ISP's don't see this topology until it's too late - so they communicate extracurricularly (for this and security reasons)
    - Current Internet Growth Trends
        - Why does the growth of the internet affect routers in BGP? What could solve these problems?↓ ↓ 
            - Routers must store best routes and alternative routes. 
As the internet grows the becomes increasingly cumbersome to store and access quickly, especially for things like reflector routers - for iBGP you can form some hierarchy wherein you aggregate IPs together, but you cant do that in BGP.
            - If the routers die, a large CPU load is then required when calculating alternate routes - and that takes time, time in which certain IPs can't be reached.

            - Fingers crossed on Moore's law for the CPU and memory growing for large routing tables.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1S9Je7BJWMUfClZO_23nZKQ2Hc2-MdbzhpAQKrYYaGbH4UG5IuKlGaw4VBImdDAFD4f15AZhIoB_-1eWn0JnWSZ_DFGDFcbWJ6pg2JkNyCXNGhTqwcJsEwDmLsdTPHHw.png)→TODO 
        - What is route flapping, how do you solve it in BGP and what's the problem with the solution?↓ ↓ 
            - When a route is advertised and then removed constantly - could be due to a flaky cable at a router.
            - You could Rate limit on sending updates - send a batch of updates every 30 seconds, a router might change it's mind many times in that time. Similar to keyboard key de-bouncing. This can really slow things down, because the 30 seconds is not synchronized between ASs meaning the update can take a long time to propagate
OR, route flat dampening - punish routes for misbehaving and dampen them more because of that - i.e. ignore them more and don't listen to their foolish updates.
Penalise , and decay the penalty exponentially - when the penalty score exceeds the suppress limit stop sending the advertisements.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5gJGPwwHzusO1wO5rfdsFBEDNmphDMpxvrXWrnq7O8KC0N1s1HsRtxTuJ888UGxUgfP0XS9EArxv-FbTFEoZUhDck5ZTNHUfyNOoiNdSZEQfmXEWOhgsGpRKNx9QG09c.png) 
            - 
    - 
- Lecture 7
    - How can IGP export internal instability to the world?→IGP tie breaking means ASPATHs can change when flapping is occurring (this could be due to faults, or due to internal rules). This changing ASPATH is then exported to the outside world.
             ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H5qwmeolhGBgs9BLbzkh9Wmva3vypWuEfcDxN3FakBHS2LQVA2UfK-2Cr4bdVJquJ72pL-iwqRJC2nrncGOqOaR0mialwcu_LCHUBnDCGUAxq5wdg4lf1BbT4linVhkJ.png) 
    - Multicast routing
        - What are unicast and multicast? And what are the uses of multicast ↓ 
            - Unicast: Single source sends to single destination, specific interface going to specific host
            - Multicast: Hosts are part of a multicast group, packets sent by any member of the group are received by everyone.
            - Useful for multiparty videoconferences, radio & TV over the internet, distance learning, resource location (send a message to all printers and get some answers) etc.
Consider, for a streamer with 10000 viewers sending 1000 to each person per second - you need to send 10,000,000 packets per second if we used unicast.
        - Multicast group
            - Associates a set of senders and receivers with each other. Senders do not need to know receivers' identities. 
            - You need to have a mechanism for advertising groups, joining groups etc.
        - Addressing
            - Multicast groups have their own Class D address, it looks like a host address but isn't and indicates part of receiver set.
            - Senders send to the address from their normal unicast source address. Receivers in the world request packets from that address.
            - **Need to solve:** 
                1. Find which groups are currently active
                2. How to join a group
                3. Discover the set of receivers in a group
                4. How do we deliver data to members of a group
        - Expanding Ring search
            - What is Expanding ring search?→A way to use multicast groups for resource discovery - you set a TTL and multicast which reaches all receivers <= TTL hops away. This allows you to discover local resources first, which helps you decide (for example) which printer to use.
                         ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ETGQ6ELLZFD5F7IA68eC3djmXY4oa0HHqSUiKQ88CGynQ-o9CW7DtdovwtyfFtpoK0233UxM9Q47p47JFIXskrQ4OJESOacLJ_UaVcO4ZykCPEsBoTA5xyjO1ikYOfad.png)
        - Multicast flavours
            - When would you want point to multipoint vs multipoint to multipoint? ↓ 
                - Point to multipoint - one sender with many recipients (Single source) is useful if you're trying to mimic broadcasting.
                - Multipoint to multipoint (Any source multicast) - conference calls etc, where anyone can send to everyone.
                - Note that you can simulate one with the other, but it's a matter of efficiency. If you're sending the same packet multiple times, then that scales with the number of messages. However, if routers can decide to duplicate a message then only some routers will receive and send multiple message - grows with $\log M$ .
        - Problems in wide-area multicast
            - Sources can leave or join dynamically - meaning we need to dynamically update our shortest path tree. We'd like receivers to be able to join or leave without explicitly notifying the sender, otherwise this won't scale as we have the unicast problem but with receiving rather than sending. 
What about leaf nodes of this sending tree makes this easier?→Usually those leaf nodes are broadcast Lans/ WiFi networks, these networks then blast the message out to their users who can then either accept of reject the message.
        - Multicast in a broadcast LAN
            - We can map between the multicast group and the physical layer - mapping from IP address to the{{ MAC address}} - Ethernet will multicast all packets with {{multicast bit }}set on a destination address. 
        - Group Management Protocol - IGMP
            - Describe IGMP Internet Group Management Protocol) ↓ 
                - Detects if a LAN has any members for a particular group - if not we tell our parent who can then prune the shortest path tree
                - Multicast capable routers periodically ping the local net, with a query message asking if they want to receive group messages.
                - Hosts reply with a list of groups they're interested in.
                - To suppress traffic, replies occur after a random timeout and are broadcasted - if someone else has expressed interest in a group, suppress your response.
                - Then to receive multicast packets - translate from class D to MAC and configure NIC/adaptor 
        - Wide area multicast
            - Assume each endpoint is a router that can use IGMP to discover each member in it's LAN that wants to subscribe.
            - Simplest solution
                - Flood the packets to the whole world. It's simple and always works, but routers receive duplicate packets and detecting if a packet is a duplicate requires storage which can be expensive for long multicast sessions.
            - What's the difference between flooding and broadcasting?→From my reading, it seems that broadcasting sets the MAC address to ff-ff-ff-ff meaning switches read that, check their lookup table and find it's not there - at that point the switch will send the packet to all it's ports. 
While in flooding the switch receives a MAC address it doesn't have in the lookup table, so it floods because it **doesn't know the destination**.  #[[To ask Supervisor]] 
            - Reverse path forwarding
                - What is reverse path forwarding? How can you extend it?↓ ↓ 
                    - Method of broadcasting where we check where the packet came from, if it came from the shortest path (we assume the network is symmetric) then we forward it to all other interfaces - this way we don't need to remember past packets
                    - Additionally, don't forward the packet if you're not along the shortest path from the downstream router to the source. This can cause confusion if the downstream router has a choice of shortest paths to the source.
            - Pruning
                - What is pruning, and how does it help RPF? ↓ 
                    - Each router tells its parent in the tree to stop forwarding messages for a certain group - i.e. after you flood, the information burden is split among many routers - as many routers are parents.
This trades router memory for selectivity.
                    - Reverse Path forwarding does not stop all routers receiving messages they don't need, consider:
                              ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6no7Jog66jmPaC3cSOIUYwQNfTDG7GG99QOb8UwvcKwhUIAdPF2SOp6oOkqHmNESX2F1WNASjdcEKw1JilGAPN_Bbgs9TzzhF6buew52O40EhW8JhoHHvPMbkR1yzX0o.png)
                - How can a host on C's network join a group after being pruned? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BsxSIXBqE1dVQzQCI5rjGrREyq61CI0acsCayy35YCI3D3zm68fe5zekJDvfUpUPoNrAFXf3psgfPca4kITBW5E12yhmySuyDhMYaSyMbyC-UXvbte6VlpDerno0Jn4k.png)→IGMP lets C know of the host's interest, C can either:
 ⇒ Send a join(group, A) message to B which propagates it to B
⇒ Periodically flood a message; C refrains from pruning
                - Need to decide how long to cache information for.
                - What do you do if a router does not support IP multicast?→Form virtual links between multicast-capable routers - meaning the shortest paths are via those virtual links/tunnels:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Sm9cxq3tqeKIAza6nKBZ5EeRIV6GfgjjoYI3o5C8Rv7WoePlksMAWEnvzAtROyW_-PUpDIyG7FGa9Z_6gNFMMc-THFb32vUzvFpf0G9rYKGbVvoVoORsfRkF7_Y8YULK.png) 
Routers need to calculate shortest paths, only taking multicast routers into account.
            - DVMRP - Distance Vector Multi-cast routing protocol
                - Rely on existing path computations, and look at them backwards. Look at the source, and forward on all which aren't the shortest path to the source. 
                - Only takes multicast capable routers into account. 
                - Uses flood-and-prune to determine membership, 
                - Uses RPF to decide where to send a packet, 
                - Uses explicit join messages to reduce join latency without source information, so flooding is still required.
            - MOSPF
                - How does MOSPF work, and why does it do what it does? ↓ 
                    - Router floods group membership information with the Link State Protocol advertisements. Then each router independently computes shortest-path trees that only includes multicast capable routers. 
                    - Routers then compute a shortest path from the source to all the recipient routers in a group. Run once for every group.
                    - This is done because we want complete knowledge of where the group members are. You don't know this with regular multicast and pruning.
            - Protocol independent multicast
                - People send join messages to a core. E.g. the IGMP traffic
                - Fault tolerance - multiple cores for the same group. 
                - Two modes of PIM: 
                    - Avoids the flooding problem, for dense groups we might as well flood and prune. 
                    - Sparse mode, Core Based Tree used.
                - Could still have issues with denial of service.
- Lecture 8
    - Mobile Routing
        - To main questions ⇒ How to find the mobile host? How do we get to it? i.e. location & routing
        - Mobile Cellular Routing
            - Describe how cellular routing works?↓ ↓ 
                - Base stations are arranged in cells, these cells work at different frequencies so not to interfere with one another:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/94cIy7_VJMWAzt5WuQhSWjq21rglQ5Gt-FYzEFCkvkl9EwDFVVhkDKEptUlL0Eas0nbj5z_VIhl_SbhKjX35dpDxQPywIbuv4MWwJLL06p00eeoRk0_CQp88iGN3Fn0-.png)
                - Each cell phone has a global ID that it tells it's remote MTSO (mobile telephone switching office) when turned on and periodically from then
                - The Remote MTSO tells the home MTSO - this home MTSO is the one your phone is initially registered to and is owned by your ISP
                - Calls  __to the phone __ are forwarded to the remote MTSO and then to the closest base station. 
                - Calls  __from the phone __ go from the closest base station to the remote MTSO and then to the home MTSO. 
        - Mobile routing in the Internet
            - Why do we have to create a tunnel when you move and change IP, why not just change your IP?→Because TCP carries a checksum which requires your IP. So if you change IP, the TCP connection will break. 
We can't just get HTTP to restart the connection, because it would require some endpoint/identifier that had stayed the same. (Note this can be achieved with HTTPS and TLS with an identifier)
            - Very similar to mobile telephony
                - but outgoing traffic does not go through home, need to use tunnels to forward data.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-N83Hduus8cCtDYmWbbJEZErIuEXUiAS0h9-f9Hm97xRLskepoXCk04kdTcdWSC6EE4dIoxrNyYd5kE0fLRXZ31j6QfeNMci5QPeuBnlRfJu--6PsetEo2aXrCrH5Iof.png) 
            - Security is tricky with this, mobile and home address agents share a common secret which is checked before we forward packets.
    - Routing in Telephone networks
        - Telephone network topology 
            - Describe telephone network topology↓ ↓ 
                - Telephone networks have a 3-level hierarchy with a **fully connected **core.  
                - Phones connect to central offices, these central offices are connected on a local exchange system which is connected to the core network (national phone network - connects every city to every other city).
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mywpM82a6lSQX93QOJC76wUk8ry2qbx2f6pHkhspilv_5vHkvpT3woJz61gpHf0YJwnnIk5uknss4kb69S8HG1vCZhxJdKwZah_3g0oHqyZOgJt2Scapox-aA_P9Nntm.png) 
            - ATnT used to set up telephone poles in the US, and as a result it was the biggest lumber company in ther world for a period.
        - Routing Algorithm
            - Describe how the telephone routing algorithm works for the different levels of the routing hierarchy? ↓ 
                - If calls are within the same Central office, directly connect the circuits.
                - If the calls are within the same local exchange, find a one hop path between central offices.
                - Otherwise we send the call to the core, we use two-hop paths if a direct connection is full. We decide on a two-hop path by 
            - Describe the features of a telephone network ↓ 
                - Stable load - we can predict the pairwise load throughout the day. Note that further longer calls cost more money, so short local calls are common.
                - Extremely reliable switches - downtime is minutes per day
                - Core is controlled by a single organization, so we can see all statistics of its use and use them to make predictions. (Not the case for international calls)
                - Calls require resources - but all calls require the same resources
                - Very highly connected network
            - Statistics used for telephone networks
                - Poisson call arrival for the {{Independence assumption}} 
                - Exponential call holding time, due to {{distance and time related billing}}. This is not the case for the internet. 
                - We seek to minimize call blocking probability, subject to minimise cost of the network. However, demand changes over time - e.g. on New years eve or mothers day.
            - The cost of simplicity
                - Simplicity of the routing was necessary for debugging, and because only 8 KB of memory was available.
                - We still require reliability in every component, and a logically fully connected core.
            - Dynamic Non-hierarchical routing (DNHR)
                - Describe DNHR and it's main problem↓ ↓ 
                    - Divide the day into ~10-periods
                    - In each period, each toll switch is assigned a primary one-hop path and a list of alternatives. These alternatives are calculated offline based on traffic predictions.
                    - Only overflow to the alternatives if the one-hop path is full.
                    - Drop only if all alternative paths are busy.
                    - Doesn't work well if the traffic differs from prediction.
                - What is metastability in DNHR?→If many calls are routed via the second-best route, when the calls on the one-hop route end we don't switch back to the one-hop path. 
We don't have the capacity to measure and do something clever.
                - How does TSMR improve on DNHR?→While DNHR measure traffic once a week to update secondary paths, TSMR updates once an hour - meaning the list of alternative paths is more up to date. 
            - Real-time network routing
                - Describe real-time network routing in the telephone network. Give an example of how it would work in this network to get to B.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xxTGfXbdokR7FNAtLzjeKKN81V4eAC4WRVlCky0Uw6O6eP6EnmBmosh4n2NaFbGqK7ILWzSvikXz5kpMdvpOPuk7OnQs__cXCppqVNOhpRHrqQoC9AEtTEawdLenEKR7.png)↓ ↓ 
                    - This system has no centralized control, instead each central office maintains a list of lightly loaded paths. It then communicates with other central offices to find their lightly loaded paths - the intersection of those paths gives the best routes.
                    - E.g. A has a list C D E of connected offices, it knows the AD and AC are lightly loaded. It communicates to them both, D says DB and DE are lightly loaded - we then find the intersection. AD DB ⇒ ADB lightly loaded and is a good alternative path.
            - Dynamic Alternative routing
                - Fully connected network with a relatively small number of nodes (e.g. 50 cities). Stochastic traffic, low variance when the link is nearly saturated.
                - Describe dynamic alternative routing:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/A8CYYeFqOB2dZ49if0VubQ3U9LDlF_objagZf4in4Wx4Td89pxwqIL9aVF0upDNd9CT92ok18OsZvu7Zywmd3vAkBYErYv-Hos0etiIVbj2FBcJspHoP1GkB5EXycfUE.png) ↓ 
                    - Whenever link (i,j) is saturated, choose a tandem to go via.
                    - We could do fixed tandems, but it is inflexible during breakdowns and unexpected traffic at tandem.
                    - Instead we use sticky random tandems - if there is no free circuit along ij - pick a tandem at random and keep that as the tandem as long as it does not fail. If k does fail, the call is lost and a new tandem is selected.
                    - Trunk reservation is also used, we bias against using the two hop path by penalizing two link calls when the lines are busy. A tandem k accepts to forward calls if it has free capacity more than R.
We don't want to block calls going from k to j because we're going ikj
                - Erlangs Bounds
                    - A node connected to C circuits with a poisson with mean v:
The expected value of the i-th call blocking is
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_5_6b-ItUo5qLY0pGC0uA0KvfRhFkIewp5FW6Lg5VAUNveZcQG5-3lceOFzTGZNMG62SgyPzoeKk3bj6-x-C-DGj9Td11gxKhYblOiXlFr4La3hlDSNRhGUWSmHpsRgv.png)
                    - We can bound the max-flow to find the capacity we get from the two-hop paths. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZlZk_38Ve87nGWLzsEP5NnDe2y1Bocu5ehR33LTUfYswOUQR4BFdZHW8FI2vHVY0k0tTVnJriRwv7gMPKWq39lUFi0HtlQlhtJMzh7ODYxQo5YqYSPRIYZMwQ4IjmAjf.png) 
                    - 
- Lecture 9 (Flow Control)
    - Flow Control
        - Senders and recipients have different capabilities, you want to match the rate at which the receiver and network can process data. 
        - Sending too slow wastes time, and too fast leads to buffer overflow. We seek the find the correct rate.
        - How do we find the correct rate?
        - Considerations 
            - Simplicity
            - Low overhead
            - Scaling
            - Fairness between different apps and users
            - Stability
            - Generally tradeoff overhead for stability or simplicity for unfairness.
        - Usually done at the transport layer, ocasionally in the datalink layer.
        - Our model is a source, sink, server, service rate, bottleneck and RTT
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vhFqZO6ZmqUKNbaP9zCwhqwQEK5LPkATaA6GylaMtvtCzVQo3YA2az9scqybeFi9NEAsWG76KAgvgk7HqfVCSO6d4FcPsXpSdaLOLGuim3TzuBa6tysTa-H-pkwCHEOT.png)
        - Classification
            - What is open loop flow control?→The source describes it's desired flow rate and the network decides if that's feasible and admits the flow
            - What is closed loop flow control?→The source measures the available service rate and sends at this rate. Due to speed of light delay, errors are bound to occur. 
            - What is hybrid flow control→Source asks for some minimum sending rate, which is admitted by the network. It can then send more if available. 
            - Describe first-generation vs second-generation flow control ↓ 
                - The first generation **only matches the receivers rate**. It's not responsive to the rest of the network. 
                - Second-generation polls the network somehow (whether explicitly or implicitly) to determine how it should adjust it's rate. It can be decided whether the controls are enforced on the endpoints or within the network.
            - Open-loop
                - Describe the two phases of open-loop flow control ↓ 
                    - Call setup: 
Network describes the parameters, the source chooses from those parameters and the network then admits or denies the call.
                    - Data transmission:
User sends within some parameter range, the network polices users and scheduling policies give users QoS. 
                - Descriptors of flow
                    - How is traffic described in open-loop flow control?→An envelope is created which describes the worst case behaviour. This envelope is used as a basis for your traffic contract, and as input to the sources regulator **and **as input to the network policer. 
                    - Descriptor should be:
                        - Representative - adequately describes the flow
                        - Verifiable - we should be able to verify that the descriptor holds
                        - Preservable - it doesn't change through the network in an arbitrary way (if buffering occurs etc. should still stay within the envelope). I.e. doesn't break due to some scheduling done within the network.
                        - Should be usable - easy to describe and use for admission control algos
                        - Time series of interarrival times is representative, verifiable - but it's not usable (too slow).
Peak rate is verifiable, preservable and usable but **not representative.** 
                    - Describe linear bounded arrival process. Where does it struggle?↓ ↓ 
                        - Source bounds the number of bits sent in any time interval by a linear function of time
                        - The number of bits transmitted in any active interval of length t is less than $\#b < rt+s$ ($s$ is a burst).
                        - $r$ is the long term rate and $s$ is the burst limit.
                        - Struggles in multiple time scale traffic -  basically means when the quality varies quite often. E.g. in a movie going from a a talking heads scene to an action scene. Either the quality dips or the connection ends. 
This can be helped by changing the renegotiation time, e.g. every 5 mins we change our r and s depending on what we're doing.
                    - Describe the leaky bucket regulator for a linear bounded arrival process→Tokens arrive periodically in a token bucket, and a leak in the bucket means the packets drip out periodically in small "bursts". Goes from periodic bursts to continuous predictable drips of packets. These packets are sent out at the mean rate.
If packets arrive at a rate that overwhelms the bucket, those packets are dropped.
                    - Choosing LBAP parameters 
                        - Tradeoff between $r$ and $s$. 
                        - We want to find the lowest loss rate as we adjust r and s, we choose the knee of the curve:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V1vR3HY1IvSFkbdtx3ATRugfragBFTDA-CAyryRhoW-ioJ3MSnU8A8pJP3nD2tTpMJjAXGAVn2BA9-v5vFYCuPU80dkxNNAWwnH8NAO7Ny6IVs60SyR0vA3dcNegMgoj.png)
            - Closed-loop
                - Useful when we can't describe the traffic or the network doesn't support reservation (e.g. internet)
                - Monitor the available bandwidth and adapt to it as we go.
                - If not done properly we can have too much loss or unneccesary delay.
            - Explicit and Implicit Flow Control
                - Describe Explicit flow control ↓ 
                    - The network tells the source it's current rate
                    - You get more control at the cost of more overhead
                - Describe Implicit flow control ↓ 
                    - The source measure the network to find it's current rate
                    - Less overhead than explicit but at the cost of accuracy/effectiveness
                - Flow Control Window
                    - Describe the flow control window ↓ 
                        - I can have this many packets in flight **before **I receive an ACC - adjust the window as we go. 
                        - If the window is full we slow down the rate. If a packet is missing that can tell us the network is congested.
                        - We note the missing packet, thus the window provides  __both __ error control and flow control. 
                    - What should the window size be?
                        - How do we figure out what the window size should be?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PsSV2Lp3kBtpvuIFOhsgYbmbSYErxWMcFthUEnRLK8Drya_z4W0c1ZcFTQvmJbrTuWZPz77ppC5LtbMLZvxdWlV7sBAHn195FS_vbhXwZ8iXD0oYZs5l2Pki6z3czlFD.png)
Basically computing how many packets we can send before we get a response with the bandwidth delay product. 
                    - Window vs rate
                        - What is adaptive rate and how does it measure up to using a window for flow control? ↓ 
                            - We directly control the rate, and we have a rate **per connection**. E.g. if the receiving connection gets congested we decrease the rate. 
                            - It requires a fine-grained timer (window control does not) and it's not self-limiting (as the window is).
                            - It does have better control than the window and it doesn't couple flow control and error control.
                        - Initially static windows were used, good if R and b are static.
                        - 
                        - What is an On-Off protocol and where would you use it? ↓ 
                            - Receiver gives ON and OFF signals, when the signal is on send at full speed otherwise stop.
                            - When the RTT is very small this is all you need, i.e. in a LAN or a serial line. We don't need complicated windows as the bursty signals will only build up for very a short amount of time.
                        - Stop and wait signal - send a packet and wait for an ack before sending the next packet
                        - Describe DECbit/ECN flow control→Every packet has a bit in the header which represents that a queue is building; routers set this bit when their buffer is starting to grow (doesn't have to be full). 
This is reflected in the ACK the sink sends, the source can then reduce it's window (and increase when the bit isn't set) to oscillate around the optimal size.
                        - How does the router decide when to set the bit in DECbit/ECN flow control? ↓ 
                            - Measure the demand and mean-queue length over some period for each source. 
                            - Then if the mean queue > 1 then set bits on that source.
                            - If the mean queue > 2 then set the bits on everyone because the queue is growing very quickly
                        - How does the source change it's window depending on bits in DECbit/ECN flow control?→Additive increase, multiplicative decrease. If more than 50% bits set then multiplicatively decrease the window (because we're hearing about this a RTT late, so more needs to be done now) - otherwise add some number of packets to the window size. 
                        - DECbit/ECN works with FIFO but **assumes cooperation! **Conservative window increase policy. 
                        - Describe how TCP congestion control works ↓ 
                            - The window starts at 1 then increases exponentially until we hit ssthresh, at which point we slow to linear increase. 
                            - The exponential portion (so called slow start) **increases by 1 at each acc**. You might think this is linear, but for each full window worth of packets sent the window will **double in size!** 
                            - The Linear portion increases the window by 1 whenever #acks = window size. This linear phase is called congestion avoidance
                            - If duplicate acks are received, we halve the window. If we get a timeout packet loss we set our window to be size 1.
                        - Describe the weaknesses of TCP↓ ↓ 
                            - Loss doesn't necessarily imply overload but TCP assumes it does - on wireless connections especially this assumption is flimsy.
                            - If the network is overloaded, TCP blames it's own connection and penalizes it heavily when other flows could be to blame. 
                            - Overload is **only **detected on a loss 
                            - Needs at least bR/3 buffers per connection
                    - Hop-by-hop vs end-to-end
                        - What are hop-by-hop and end-to-end flow control ↓ 
                            - Hop-by-hop: First generation flow control at each link, easy to implement. I.e. router to router the flow control is based on the sink rate.
                            - End-to-end: The sender matches its rate to all servers on the path
                        - Benefits of hop-by-hop flow control ↓ 
                            - Simpler
                            - Distributes overflow
                            - Better control
                        - Benefits of end-to-end flow control ↓ 
                            - Cheaper than hop-by-hop
                            - We know it works as it's in place currently
        - 
- Lecture 10
    - Traditional Queuing behaviour in routers
        - How did queueing traditionally work in routers? ↓ 
            - Most boxes use the most naïve method of scheduling possible, no recognition of flows. Nothing explicit to tell you one packet is more important than another initially - you could infer some data but thats it.
            - Forwarding did not examine the type of traffic for priority.
            - No examination of traffic patterns.
        - We'd like an alternative to FCFS - going through the same interfaces can cause queuing delays and delay variance (and packet loss at the extreme).
    - Scheduling
        - Service requests at server is the packet at router inputs. The service order is the order we handle service and schedulers decide the service order and manage the service (output) queues.
        - Scheduler decides which output queue is serviced next.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sY2-Dp8YzwYCC8Ag5U95Yt9eyhzy8dB5dGMtwPU6pW70i1AIIQCDaSgA5qj5bf-wOqKGcKUwSJRJKHj9t92l0W5fw4v-Cwv97JEjbJhjzFqIsLVZrhVRgXpQRd50alsk.png) 
        - FCFS Scheduling
            - What's the main problem with FCFS scheduling→No differentiation at all between packets. As a result **no notion of flows of packets, **but lots of the internet uses TCP flows. 
            - FCFS is a **work-conserving **scheduler. 
                - What is a work-conserving scheduler?→This is one that doesn't idle if there's something to send - if there's work to do do it. As opposed to hold a packet until some due date.
                - What is the benefit of a work-conserving scheduler→Means we **don't waste network capacity.** No artificial delay added, we can't give  __all __ flows a lower delay than they would get under FCFS.  
                - $$\sum_{n=1}^N \rho_n q_n = C$$ 
                - What is the law this equation represents? What would happen if change one flow some way?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zKc9xAlr96Iv9_nBbmWNzcw5VqjP8DWlfw1AjyVsYHjZ9SS5tKiHPNRum0CtWTFpB_IdTQ8jPIMLXQrEeBy1uI8ut6T6cX6KNjDHBzKjB94jDFLaj8gdaWEy0lqSIiSh.png) ↓ 
                    - Conservation law - n iterates over all the flows and the constant C remains the same.
                    - The conservation law says that changing the rate of one flow will keep C the same. The other flow will just slow down. You would need some clever scheduling trick. Trade-off delay and throughput.
            - Non-Work-conserving Scheduler
                - What is a non-work conserving scheduler?→Can be idle even if packets waiting - allows smoothing of packet flows.
                - How are non-work conserving schedulers created and what are 3 benefits and 2 downsides?↓ ↓ 
                    - We wait until a packet is eligible for transmission, eligibility is some fixed time per router or across the network.
                    - Less jitter
                    - Makes downstream traffic more predictable - less bursty
                    - Less buffer space - end-system de-jitters buffers
                    - But higher end-to-end delay
                    - And complex in practise - how do we synchronize time on these routers
            - Scheduling Requirements 
                - What are the 3 main requirements for schedulers ↓ 
                    - Ease of implementation
                        - simple ⇒ fast. Implementation in hardware. High speed networks
                    - Fairness and protection
                        - Local fairness max-min
                        - global fairness maybe
                        - Protect any flow from the misbehaviour of others.
                    - Performance bounds
                        - Can we determine the delay someone will get
                        - per-flow bounds
                        - Deterministic / probabilistic
            - Max-min fair share criteria
                - Describe max-min fair share criteria→Those who demand the least will get what they want - when there is not enough left to fully satisfy any flows, they all get a portion of what's left.
C=10, demands = 2, 2.6, 4, 5 - we give 2, 2.6, 2.7, 2.7 (sums to 10)
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZOCa2jScuez7-pSRd9vPM1Xzxt-ST7AnM0lzujXsedpWFQE8Uu7Ou9xWxJ234226yhaQ0tEI3CcsZBuxjih7yrnJBvdjWCjkEJbrvwk9L3zHkUCMTqKs1dJa9X2Z5li8.png) 
            - Scheduling Dimensions
                - Priority levels, higher priority queues serviced first.
                - Degree of aggregation, all of Cambridge get's this fraction of the capacity. Leaves it up to the organization that paid for this aggregation.
                - Work conserving or not
        - Simple Priority Queueing
            - Describe Simple priority queueing and 2 benefits and 2 problems ↓ 
                - K queues, queue k+1 has greater priority than queue k. Could be router to router control traffic most important
                - Very simple to implement
                - Low processing overhead, Just work down the queues and service
                - No deterministic performance bounds
                - Starvation of low priority queues
        - Generalised processor sharing
            - Describe Generalized processor sharing ↓ 
                - Basically visits **flows **round robin! This gives you a bound, minimum of $1/n$ of the share. Delay is bounded by $n-1$ packet delays. 
                - Provides max-min fair share and is work-conserving.
                - It's not implementable as it serves an infinitesimally small amount of data from each flow - we cant send one bit of a packet and we can't equal the amount of data sent from each flow as packets are variable length.
                - Provides an absolute fairness bound - fairness of scheduler compared to GPS for the same flow.
        - Weighted Round Robin
            - **Queues are per flow** 
            - What is weighted round robin→Simplest attempt at GPS - weight queues according to demands and mean packet size at each queue. Then use max-min fairness process to dole out capacity.
            - Service is fair over long timescales, as mean is unpredictable and possibly unfair over short timescales.
        - Deficit round-robin
            - DRR does not need to know mean packet size.
            - Describe Deficit round robin ↓ 
                - Each queue has deficit counter (dc) initially zero
                - If a packet is to be sent, we check if the dc is more than the length of the packet - if so then send and decrement dc by that packet size, if not then dc = quantum + dc.
Quantum is the schedulers attempt to serve one quantum of data from each non-empty queue
                - Quantum set to max expected packet size.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/q1Y7Wme0KZPPH1VaHe3lFni62fKW_2fjGH-BfQ4oagJ9YIsK4uE1djHwsH32RH-AcDkA85wQxOQrDZfXFMYaL518ubtMJFQrpdWmcdmR3NrObE9GIufUihrSAYn4eXCu.png)
Pretty fair. 
        - Weighted Fair Queueing
            - Describe weighted fair queueing ↓ 
                - Simulate GPS by serving packets bit-by-bit. Packets are tagged by a finish-number, we sort the queues (other data structures exist to prevent sorting) by the finish number and release those with the lowest finish number.
                - If a new flow start or an old flow finishes **you need to change your computation.** Other flows can be completed faster, these flows then finish faster so R needs to be changed again! In the worst case we evaluate R each time a packet arrives or leaves. 
                - Rate of change of flows could be pretty big, flows could be appearing and disappearing often. 
        - Class-Based Queueing
            - Describe class-based queueing.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1yUe_qeveUIT2QoNC642q2v1LPAtxNZKZJI0omqzQKCIwdmHJiQ9tfVsWOu3t3NzHePgKVDk8zQo7RermNyWpbg1hm66UdwUq3-dZ0bbjiV0knRovMt0tn_8c2_G-Z9c.png)↓ ↓ 
                - First into which link, then which organization, then if it's real time or not, then the application their using etc.
                - Assign a capacity/priority to each node.
                - Node can borrow any spare capacity from the parent
                - Allows for fine-grained flows.
                - Requires a scheduler.
    - 
- 
