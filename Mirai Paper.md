- Page 02
    - The Mirai botnet, composed primarily of embedded and IoT devices, took the Internet by storm in late 2016 when it overwhelmed several high-profile targets with massive distributed denial-of-service (DDoS) attacks. In this paper, we provide a seven-month retrospective anal- ysis of Mirai’s growth to a peak of 600k infections and a history of its DDoS victims
    - Starting in September 2016, a spree of massive distributed denial-of-service (DDoS) attacks temporarily crippled Krebs on Security [46], OVH [43], and Dyn [36]. The ini- tial attack on Krebs exceeded 600 Gbps in volume [46] 
    - We track the outbreak of Mirai and find the botnet infected nearly 65,000 IoT devices in its first 20 hours before reaching a steady state population of 200,000– 300,000 infections.
- Page 03
    - While DDoS was Mirai’s flavor of abuse, future strains of IoT malware could leverage access to compromised routers for ad fraud, cameras for extortion, network attached storage for bitcoin mining,
    - Mirai is a worm-like family of malware that infected IoT devices and corralled them into a DDoS botnet.
    - Mirai spread by first entering a rapid scanning phase ( ̈) where it asynchronously and “statelessly” sent TCP SYN probes to pseudorandom IPv4 addresses, excluding those in a hard-coded IP blacklist, on Telnet TCP ports 23 and 2323 (hereafter denoted TCP/23 and TCP/2323). If Mirai identifies a potential victim, it en- tered into a brute-force login phase in which it attempted to establish a Telnet connection using 10 username and password pairs selected randomly from a pre-configured list of 62 credentials. At the first successful login, Mirai sent the victim IP and associated credentials to a hard- coded report server (≠)
    - A separate loader program (Æ) asynchronously in- fected these vulnerable devices by logging in, determining the underlying system environment, and finally, down- loading and executing architecture-specific malware 
    - Mirai attempted to conceal its presence by deleting the downloaded binary and ob- fuscating its process name in a pseudorandom alphanu- meric string. 
    - n order to fortify itself, the malware additionally killed other processes bound to TCP/22 or TCP/23, as well as processes associated with competing infections, 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EkhH1kkHo6j55g_m0YzdXlUvRfK4cui73PQcF7KVebsatxUmLe9BYXqyF_GuIVbCMe9zwR9LcD6UoSZupcEgCzqtiJV1qEYpNM9Mu-JKvoMJpVkhYX7wgdaXsB9HAb1G.png)
- Page 04
    - o distinguish Mirai traffic from background radiation [94] and other scanning ac- tivity, we uniquely fingerprinted Mirai probes based on an artifact of Mirai’s stateless scanning whereby every probe has a TCP sequence number — normally a random 32-bit integer — equal to the destination IP address. The likelihood of this occurring incidentally is 1/232
    - would expect to see roughly 86 packets demonstrating this pattern in our entire dataset. In stark contrast, we observed 116.2 billion Mirai probes from 55.4 million IP addresse
    -  A number of challenges make accurate device labeling difficult. First, Mirai immediately disables common out- ward facing services (e.g., HTTP) upon infection, which prevents infected devices from being scanned.
- Page 05
    - To track the evolution of Mirai’s capabilities, we collected binaries installed on a set of Telnet honeypots that mas- queraded as vulnerable IoT devices.
    - We logged 80K connection attempts from 54K IP ad- dresses between November 2, 2016 and February 28, 2017, collecting a total 151 unique binaries. We filtered out executables unrelated to Mirai based on a YARA sig- nature that matched any of the strings from the original source code release, leaving us with 141 Mirai binaries.
- Page 06
    - e analyzed the binaries for the three most common ar- chitectures — MIPS 32-bit, ARM 32-bit, and x86 32-bit — which account for 74% of our samples. We extracted the set of logins and passwords, IP blacklists, and C2 do- mains from these binaries, identifying 67 C2 domains and 48 distinct username/password dictionaries (containing a total 371 unique passwords).
- Page 07
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ef_s_W1z4cOGy0E6a2-UR9Kl1zpF9Z_SnH8OyiaYfdrffYuY8CMy5LL_HIAsXlH2krSfiIHAAzacTmqMq4USloMZ19dT1lk2EoAFwqwFiuFTkDN8OhS9sEYq3PVvt2wX.png) 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qlP_m-ICbjThGaKMeq__K9q44eFeiWdZZm6BMbqoNUT39WD_17tb92nvRHWY3g3eNoIio7Bm-Bz1riu7AOrKRGqdggSI22SaTqnBO56mhvF7_dTISKAamlIP0VwcQI1a.png) 
    - We observed multiple phases in Mirai’s life: an initial steady state of 200,000–300,000 infections in September 2016; a peak of 600,000 infections at the end of Novem- ber 2016; and a collapse to roughly 100,000 infections at the end of our observation window in late February 2017
    - The decay that followed may be explained best by Deutsche Telekom patching routers soon after the attack [21]. The non-immediate decay may have been due to the devices requiring a reboot for the patch to take effect.
- Page 08
    - Mirai largely infected regions the black market considers to be low-quality hosts used for proxies and DDoS [88] and may have limited potential avenues for monetization
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-1WQcinVLe1hj0fU_Vz7M5K3qHy5QxfoplAEJUTKnOjKxuq68IGxlZAEecJPRXOdZA0CjZ629yzXcFe0AwoSRnAGc3DGeIzworuLh_GqmvcJDOQy6oL-oPAhdkX_Uo9U.png) 
- Page 09
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5) 
    - Our results across all five protocols indicate that security cameras, DVRs, and consumer routers represent the majority of Mirai infections (
- Page 10
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/h_weEA9cMlyd735fWbW1eZpQ0GjqBreBHC4ApcuUqfkpdZmSqlnXbpU60qWS_n5ZJuqnJRRbkDh1MY8Pqnw0kJ8xn-U1wGuQN_ARObQncXAypHtetNhuDEKtwBCuFERd.png) 
    - We further note that the majority of bots scanned at an estimated rate below 250 bytes per second. We note however this is a strict underestimate, as Mirai may have interrupted scanning to process C2 commands and to conduct brute force login attempts. 
    - e used to cluster C2 IPs and domains based on shared network infrastructure. 
- Page 11
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hb7JvhpmjPgOpXshmedgiizTHi65begn6oeMrwwuOwsEWhcjJebtRXphcFnhmXc0pTIBuUHfWKDsz4_ajYEL32XlYttp24wYZEpw_om_3QxhVak5yAsalaPfwc4XPBeB.png)
- Page 13
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gT-K1dj36UfLH8GLAWkDc_UhTRSTRDlTSd9A6TiS5pKjbpd0YehyRKgj5eN-4gvmnLZC_pBF5rEvf22N3mzkMcRx5P1-WOJ4p0SBkcSrxayj_2kensqgW1Zfw7fkR0D0.png) 
    - hese victims ranged from game servers, telecoms, and anti-DDoS providers, to political websites and relatively obscure Russian site
    - The Mirai source code supports targeting of IPv4 sub- nets, which spreads the botnet’s DDoS firepower across an entire network range.
    - The three most frequently targeted victims were Liberia’s Lonestar Cell (4.1%), Sky Network (2.1%), and 1.1.1.1 (1.6%). We examine Lonestar Cell in depth in Section 6.3. Sky Network is a Brazilian company that operates servers for Minecraft (a popular game), which is hosted by Psychz Networks. 
    - Interestingly, the 7th most common attack target was an IP address hosted by Voxility that was associated with one of the Mirai C2 servers, and we note that 47 of 484 Mirai C2 IPs were themselves the target of a Mirai DDoS attack.
- Page 14
    - Dyn On October 21, 2016, Dyn, a popular DNS provider suffered a series of DDoS attacks that disrupted name resolution for their clients, including high-traffic sites such as Amazon, Github, Netflix, PayPal, Reddit, and Twitter 
- Page 15
    - We note a 71% intersec- tion between the 107K IPs that attacked Dyn and Mirai scanning in our network telescope. 
    - Lonestar Cell Attacks on Lonestar Cell, a large tele- com operator in Liberia and the most targeted victim of Mirai (by attack account), have received significant attention due to speculation that Mirai substantially de- teriorated Liberia’s overall Internet connectivity
    - Fur- thermore, the juxtaposition of attacker geography (largely Southeast Asia and South America) and victim geography (majority in the U.S.) places a spotlight on the importance of global solutions, both technical and non-technical, to prevent the rise of similar botnets. Otherwise, adversaries will continue to abuse the most fragile hosts to disrupt the overall Internet ecosystem
