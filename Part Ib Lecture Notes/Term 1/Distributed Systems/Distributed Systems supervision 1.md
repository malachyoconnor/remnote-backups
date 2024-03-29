-  _**Exercise 1**_ . A TCP connection allows two nodes to send each other arbitrarily long sequences of bytes. You decide that you want to send multiple requests and responses over the same TCP connection. What do you need to do in order to implement such a request-response protocol using TCP?
    - You could **wrap each request and response with a header** which would encode the length of the message (among other possible pieces of information), the header would have to accord to a set code that both nodes understood (e.g. it could have the first 4 bytes specifying the length of the header, the next 4 specifying the length of the whole packet perhaps more data specifying the type of the request). Then when a node receives a stream of bytes, it can find the length of each individual message by examining the header - then if there are more bytes after the header they can know that is another message (whose header will be examined).
-  _**Exercise 2**_ . How is RPC different from a local function call? Is location transparency achievable?
    - An RPC call is different in a few ways ↓ 
        - The function is not executed on your local machine
        - The arguments of an RPC must first be marshalled to be sent over the network
        - RPCs make use of an API to facilitate their use
    - Location transparency (the idea that the location of a resource (whether it be on our local computer or on another node) is achievable under perfect conditions (impossibly fast WiFi or having local resources slowed down to achieve such transparency) however in reality the lag between forging and communicating over a network connection is detectable and is much greater than the lag of local file being opened is large. So the very quick loading of a file would indicate a local file.
-  _**Exercise 3.**_   Say you have a client-server RPC system in which a client repeats an RPC request until it receives a response. How could the server deduplicate the requests?
    - One solution would be to attach a request number and a repeat number to each request. So if I a request "GET : "img:coolpic.png"", it could be sent multiple times like this:
            "req:1, rep:1, GET : "img:coolpic.png""      "req:1, rep:2, GET : "img:coolpic.png"" ...
Then a second request "STORE : "img:coolerpic.jpeg"", could be sent like:
   "req:2, rep:1, STORE : "img:coolerpic.jpeg""        "req:2, rep:2, STORE : "img:coolerpic.jpeg""

This would allow for easy deduplicating in order of req then rep
-  _**Exercise 4**_ . Reliable network links allow messages to be reordered. Give pseudocode for an algorithm that strengthens the properties of a reliable point-to-point link such that messages are received in the order they were sent (this is called a FIFO link), assuming an asynchronous crash-stop system model. 
    - ```python
buffer = []
received, messages_incoming = 0, 0
time = time.monotonic()
# read_message() blocks while waiting for a message
# Wait a max of 10 seconds before exiting the while loop
while (time.monotonic()-time < 10000 and msg = read_message()):
	time = time.monotonic()
    received += 1
    messages_incoming = msg.messages_incoming
    buffer.append(msg)

    if received == messages_incoming:
        break

if time.monotonic() - time > 10000:
	send_failure_message()
	return []
else:
	# Sort based on the message number
	buffer.sort(lambda x : x.number)
	return buffer 
```
-  _**Exercise 5**_ . How do we need to change the algorithm from Exercise 4 if we assume a crash-recovery model instead of a crash-stop model?  
    - We would need to implement a mechanism for informing the receiver/sender that we have crashed and lost the data stored in our memory, in the two cases: 
    - **Sender node crashes: **We don't know how long the period of unresponsiveness will last, so we can't simply keep waiting until the node comes back online. Instead the receiver should cache the messages received so far in some non-volatile memory. Then when the sender wakes up again, a unique ID of the message should be sent, the recipient can then indicate how many (if any) messages were received and the sender can resume sending where they left off. 
    - **Recipient node crashes: **Once the recipient wakes up, it will need to signal the resending of the entire incoming message - on the senders side a non-volatile storage of outgoing messages will need to be held or a method of backtracking execution so the message can be sent again.
-  _**Exercise 6**_ . Describe some problems that may arise from leap second smearing.
    - Floating point accuracy: The smearing of 1/86400 in binary form will introduce a very small error, and that error will be repeated 86400 times every time this update is done - if a small low bit floating point representation is used, the error introduced will defeat the purpose of the whole exercise. 
    - This is more reason for software vendors to simply ignore the problem. While this is not a problem  now, bugs mirroring Y2K could start to appear in the (far) future which go undetected.
    - This makes bugs harder to detect, as desync occurs over many hours rather than at one instant - while the latter would be noticeable in logs, the former would be very difficult to sus out.
    - Desync problems can arise if one node is doing smearing and another isn't. 
-  _**Exercise 7.**_  What is the maximum possible error in the NTP client’s estimate of skew with regard to one particular server, assuming that both nodes correctly follow the protocol?
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qpQ_ydxHmeLCcJOH6RsYAsXfSQmhKyB1tFdamdF6Ap_bDPQSH3D9yXDiDWlMRhPCDIbkBbsV34oweAqelXOk2YakrBsEOBexbuDNPmUFzd2RpaSGhmlB3zKHzVrmj3e5.png) 
    - delta = (t4 - t1) - (t3 - t2) = total network delay
    - skew = (t3 + delta/2) - t4 ^^ Question: should the skew not be the absolute value of this?^^ 
    - This estimate is worst, when the estimate of the time taken for the second response is worst - i.e. when request 2 took the minimum time (according to the speed of light & the distance) $\tau$ and the response took  (t4 - t1) - (t3 - t2) - $\tau$, resulting in a true value of: $$(t_3 + \tau) - t_4  = (t_3 - t_4) + \tau$$ 
    - and an estimated value of:
    - $$(t_3 + ((t_4 - t_1) - (t_3 - t_1))/2) \ = \ \frac{t_2 - t_1 + t_3 - t_4}{2}$$ 
    - Resulting in an error of:
    - $$\frac{t_2 - t_1 + t_3 - t_4}{2}  - ((t_3 - t_4) + \tau)$$ 
    - 
    - $$\text{error} = \frac{t_2-t_1-t_3+t_4}{2} - \tau = \delta/2 - \tau$$ 
-  _**Exercise 8:**_   ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5S3daW4zY8nipJDU9bb6QDZFwpAKv76GLWXklLBsLwNMaHVyXCyqi6beHbSePSUh2wUUqfIM089PwNg7KdgKAG393iZn0TG3vKoFUqd6uZlbpIj28GT5HfxMznzEsjyk.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JZ0cqETpk4kB-8uo8RsxSXte3C9NVDfOw4vemdbEKxinYe3CqfOPdSUNb_Fpyd4-ye6MCznEIu-9sZu06atSqyFY7bbC1aTgvSUTUTXT9mFmE5HTbSF5PSAVbnrb2wkH.png) 
-  _**Exercise 9.**_  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yjzPiqfzh56oOnjdrWniK1-rmUzLvrJVHdmIi3wGYvHrNK61hUGjfCo6hw7JQp6f_L5YYwSlqfsN8hscm798IJxxy9ynwJuNREyNIPIdegj_vVikP0lJGqiVY31FzpHB.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ob9D3CB9suoCvYxZxqxdjPsKhfoPPSYm6DlccDXCh0NtAPdvEKZA7Lly3ra6n6EQ8nrb-eQAqp-ly0gw__HevRFKuj9ebM1cP9wxXqeeExDvTyWgi-ry8nKXL0kJ1kY9.png) 
- **Exercise 10.** Given the sequence of messages in the following execution, show the Lamport timestamps at each send or receive event   
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4atqIBUEAzm7OncyN5qB3j5Z5XjQtc_OHDZgMdXZh6kXNeqKApIIRpARrwbyAHUyX7k7ndM-H0MBpStyrugFtkC4DMVZEVYv2pTPR9uWBOaXYXUGmwbk1reIC3dx1sE2.png) 
- ^^ _**Exercise 11**_ ^^^^. Not really sure what im doing in this Q^^ 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OLpHgGNm5MfltmNel8M5Q5lLaLiOvEi-XeYkJSwWR2d7kXOaSbkgkSRhko_Iat92Wrqx24q4XCLZlBOuaCfxNSdmG60OZoL9OyAZd8aFGEzVQs2X26dJVDRGVZhjhzk1.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oBARg9P1D24HOK5JpsjKfxt9BYToaiGQaEFssa4ymDfFEdCvwPFRyS1POKECnRvToCUUSUDiGleDPpD1--KUBhU6sgaQqXCITyKlJIKliumPf_oMLkMtWVPrL2PwqsPV.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_yytoqeaDujPLnHDbTmbdQ8mL45y-VCzC7OtvC2qnqKA8ofMwyZq15n7C4nYTpYnzbyjKVGghpq51wFQGApk_Zsmi4sMKo7jf3lGLupIBvMobBOH_MVgEeECiIBzpoqp.png) 
-  _**Exercise 12**_ . Given the same sequence of messages as in Exercise 10, show the vector clocks at each send or receive event.  
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9jwOOpv8Z8WqVwxq7ynfW03XwQFEn7ipkP88FMsmB5DkrGrmrNBuwEUhIDojkOzdAeBx17jEOVmlWrU2whx6-qnXAjz4jqukHzSSGc3F-r53v3Rg82YAzsXevXp8Bh-Z.png) 
- 
- 
- 
- 
- 
