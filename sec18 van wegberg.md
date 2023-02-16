- Page 02
    - Researchers have observed the increasing commoditiza- tion of cybercrime, that is, the offering of capabilities, services, and resources as commodities by specialized suppliers in the underground economy.
    - Commoditiza- tion enables outsourcing, thus lowering entry barriers for aspiring criminals, and potentially driving further growth in cybercrime.
    - We use longitudinal data from eight online anonymous marketplaces over six years, from the original Silk Road to AlphaBay, and track the evolution of commoditiza- tion on these markets.
    - We conservatively estimate the overall rev- enue for cybercrime commodities on online anonymous markets to be at least US $15M between 2011-2017. While there is growth, commoditization is a spottier phe- nomenon than previously assumed.
    - The idea is that specialized suppliers in the underground economy cater to criminal entrepreneurs in need of certain capabilities, services, and resources
    - Commoditization substantially low- ers entry barriers for criminals, which is hypothesized to accelerate the growth of cybercrime
    -  do so, we turn to transaction cost economics (TCE). We argue that the characteristics of commodities are highly congruent with the characteris- tics of online anonymous marketplaces. More precisely, the one-shot, anonymous purchases these markets sup- port require suppliers to offer highly commoditized of- ferings.
    - While data from online anonymous marketplaces pro-vides a unique opportunity to track the evolution ofUSENIX Association 27th USENIX Security Symposium 1009commoditization, we are not arguing that these market-places provide a complete picture. They do not have amonopoly, of course.
- Page 03
    - e analyze longitudinal data on the offerings and transactions from eight online anonymous marketplaces, collected between 2011 and 2017. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3ykPx24BPivIKJjeuyOsZlUBObZh1ryP44DpD8ONXA6zLu8_3ggirE7D4fjdz3mxpahKB566FktbBMH_LaijIHVk7WpeHj37I1iSOVQq5Cc-GU92LFDXxYNq-Tg3lSjp.png) 
    - Williamson [47] distinguishes several asset character- istics that determine if and how outsourcing will occur, as shown in Figure 1. A, B, and C are various forms of outsourcing and D is vertical integration
    - k is a measure of as- set specificity, referring to the degree to which a product or service is specific to e.g., a vendor, location, control over resources, et
    - “fungible”, meaning that different offer- ings of it are mutually interchangeable (k = 0
    -  The more specific an asset is (k > 0), the more investments are specialized to a particular transaction.
    - The second factor, s, refers to contractual safeguards.Transactions where investments are exposed to unre-lieved contractual hazards (s = 0) will not be traded pub-1010 27th USENIX Security Symposium USENIX Associationlicly (i.e., anonymous online marketplaces such as SilkRoad or AlphaBay are a poor fit), but on smaller, “invite-only” markets
- Page 04
    - When s > 0, con- tracts with transaction-specific safeguards are in place.
    - The efficiency gains also work in the other di- rection: those who offer goods or services that can be commoditized would use these markets to sell them and benefit from the wide reach and high frequency of trans- actions, without being exposed to risky direct interaction and coordination with buyers.
    - Similar to the prominent drugs-trade on anonymous online markets, we expect two type of commodities on these markets: business-to-business (B2B), e.g., whole- sale quantities of credit card details, and business-to- consumer (B2C), e.g., a handful of Netflix accounts. We are primarily interested in B2B, as that is the form of commoditization that is the most worrying and specu- lated to cause a massive growth in cybercrime, though we will also report the main findings for B2C. To assess the degree to which B2B services are commoditized, the next section develops a framework to identify the differ- ent value chains where there is demand for commodi- tized cybercrime.
    - First, we look into the value chain behind spamvertis- ing, which is driven by three resources: a) advertisement distribution b) hosting and click support and c) realiza- tion and cash-ou
    - Second, extortion schemes, for instance ransomware or fake anti-virus [17] have a value chain that consists of four distinctive resources: a) development of malware b) distribution, by either exploits or (spear)phishing e- mails, c) take-over and “customer service” and d) cash- out [30, 42].
    - hird, click fraud is supported by four similar, gen- eral resources: a) development of a website, malware or a JavaScript, b) distribution through botnets, c) take- over by either malware or JavaScript and d) cash-out [32, 42].
    - Fourth, the criminal business model in social engi- neering scams, such as tech support scams [35], or one- click fraud [16] leans on: a) (optional) development of malware or a malicious app, b) distribution by phish- ing e-mail or website, or through social engineering, c) take-over and setting-up “customer service,” and d) cash- out [35, 42]. 
    - Fifth, cybercriminal fraud schemes, e.g. those enabled by financial malware, build on four general, main re- sources: a) development and b) distribution of malware or a malicious app, c) take-over, for instance by using web-injects or a RAT,1 and d) cash-out
    - Sixth, cryptocurrency mining relies on near-similar re- sources as click fraud: a) the development of malware or JavaScript, b) distribution of malware by botnets or the injection of a JavaScript in a compromised websites, c) the take-over, i.e. mining, and d) cash-out
- Page 05
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a2aJFbUsR8pFYRQFhQXtZ5QHJZ8gj1f6w7X7cr7SohgvDcYjcZ2MktGvwjk_Yx8S1l_5_VaV55BHVlyIopJ7QTAsItY9RD1aHO5h_38DqVI3qBR3GqiCaufiRfHma1fF.png) 
    - 1) collect- ing and parsing data on listings, prices and buyer feed- back from eight prominent online anonymous markets, 2) implementing and applying a classifier to the listings to map them to cybercrime components from our con- ceptual model of value chains (Figure 2) as well as to additional categories of B2C cybercrime, and 3) using Latent Dirichlet Allocation (LDA, [10]) to identify the best-selling clusters of listings 
    - We first leveraged the parsed and analyzed dataset of Soska and Christin [40] to obtain information about item listings and reviews on several prominent online anony- mous marketplaces. For each of the over 230,000 item listings, the data include (but are not limited to) ti- tles, descriptions, advertised prices, item-vendor map- ping, category classification, shipping restrictions and various timestamps. Additionally, each item listing con- tains feedback that has been proven to be a reasonable proxy for sales [15, 40]. Each piece of feedback contains a message, a numerical score, and a timestamp.
    - AlphaBay is important since, according to the FBI [4], by the time of its closure, it had featured over 100,000 listings for stolen and fraudulent documents, counterfeits, and mal- ware in particular. The US Department of Justice (DoJ) also claims that AlphaBay was the largest single online anonymous marketplace ever taken dow
- Page 06
    - Next, we implemented a Linear Support Vector Ma- chine (SVM) classifier. Manual inspection confirmed our suspicion that the markets also contain retail (B2C) cy- bercrime offerings, next to wholesale cybercrime offer- ings. For this reason, we added six product categories to distinguish supply in that part of the market: accounts, custom requests, fake documents, guides and tutorials, pirated goods, and vouchers. A final category, namely, “other”, captures the listings that did not fit anywhere else (e.g., scanned legal documents). The classifier is initially trained and evaluated on a sample of listings (n = 1, 500) from all the markets, where ground truth is created via manual labeling.
    - First, we identified listings that contain more than one cybercrime component, e.g., offering both a piece of malware and (access to) a botnet. Second, we identified package listings, such as complete cryptocur- rency mining schemes. Third, we observed that some vendors add unrelated keywords to their listings, pre- sumably in a marketing effort similar to search engine optimization. Fourth and last, we observed custom list- ings, i.e., listings that are specifically created to be sold only once to one specific buyer. Custom listings con- tain bespoke products or services ranging from custom quantities to a completely custom-made product such as pre-booked plane tickets.
    - we excluded three cate- gories of cybercrime components from the classification: JavaScript malware, webinjects, and customer support. For these, we found no listings in our random sample
    - (i) data cleaning, (ii) tokenizing, (iii) training and evalu- ation of the ground-truth samples which are the concate- nation of the title and description of the item listings
- Page 07
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Q9_vkgaR_4qpaEIB6cxux_KATsM6cbB8KgqQ0i5ojYljxVU0rWLewxvgOZvBlkydUFzZvZ2EAfeBsKaP9bGmMmY7x4FlPcqoee-cNe8ZI5wMud6st8DPOWJeWrMp4BGU.png) 
    - o calculate the tf-idf, we used a max-df (maximum document frequency) equal to 0.7 – this dis- cards words appearing in more than 70% of the listings. In the classification phase we then used these values as an input for an L2-Penalized SVM under L2-Loss. We im- plemented this classifier using Python and scikit-learn.
    - Because of the nature of listings that cover multiple categories, e.g. bundled goods, we anticipate some clas- sification errors. It is however important to distinguish between errors where the item listing is classified as “other” (false negative) from acceptable approximations
    - Our main goal is therefore to prevent cy- bercrime component listings, like malware, from ending up in “other” and vice versa.
    - he average precision is 0.78 and the average recall is 0.76, denoting some confusion be- tween cybercrime components categories
- Page 08
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/v7vy23r0fUCTEiWI1fibs4bgTw86S83gN3vyFrgx2PNIZ-Scd7vG1OxGelEAwNK55iEzMuUWSSSasLFXFpa3EsYymsFUNWR0fwt-O_6_MFMCijG4HBfq2O96bSEQQ9-h.png) 
    - Cash-out stands out: In terms of the num- ber of listings, active vendors, and in total revenue, this category is by far the larges
    - We see, again, that the cash-out category contains the most expensive set of offerings with very diverse pricing.
    - Like an ecstasy tablet, a RAT will hold its value over time in terms of being a functional solution. In contrast, stolen credentials “go bad” after some time. The first buyer who uses these cre- dentials will in all likelihood set off red flags at the credit card company for irregular spending,
    - Cu- riously, the median lifespan of cash-out listings is above average, which could be due to vendors updating the spe- cific product listed, or persistently selling unusable credit card details, or to a slower-than-expected detection of suspicious transactions by credit card companies.
- Page 09
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MeBo-6Z5QFmlPY4fkX0DSjAHGFzLBlbCMD176J56NczV49ojCdttbSL6ZOFbNWAB-7Zp_d2TbukyGuwFb-OHNd2-eK50V5rf_s672TW8FXzgbssVuBtEx-leerDDbKrj.png) 
    - Figure 4 shows a growth in listings, amount of feed- back and revenue for cybercrime components between 2012 and 2017. The drop at the end of 2013 and the be- ginning of 2014 is partly due to the take-down of Silk Road 1 and Black Market Reloaded
    - Right after this volatility, the AlphaBay market emerged, and subsequently became the largest
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_FmzP9XbAwG923XXhHVGSyEniickpc1QSTWJ6agTriWwueNdtXv35V7TplowrWLMuNWB21cN1QVD6d746s9lmvzvQZXCzb6TP_qE_SsOk0XudbXx_kjdwOuWfk0KthAZ.png) 
    - Figure 5 shows that the upward trend in feedback in- stances is not only caused by an increase in listings, but also to the increase of amount of feedback per listing. In 2011, a listing on average received around five pieces of feedback per month. Over time, this ascended to around eight pieces of feedback per listing in 2017
- Page 10
    - More specif- ically, one listing offering “US CVVs” received nearly 700 feedbacks in the first quarter of 2014. From the beginning of 2015 onwards we see a steady growth in revenue alongside the growth of AlphaBay market as a whole. In the early days of the ecosystem we see an in- crease in cash-out revenue which was primarily driven by a listing offering “10,000 USD CASH,” which can be seen as typical money laundering – the customer pays in bitcoin and receives cash.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5ZP3iPNqcDAdR65si_34Yc4Xx8-I3kd_balcZzNL67BKXzFZioGBCfasnvVeg-Ws5I7sDqstdzoCLBzyGFhblODrIPOymyNIRQ59ifMbmzOgnjAvkdep9EkhyOq7RRI_.png) 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KUvjauDgoilMcsaVeehJLVUwsFxm2lovKNN5N_jzUnw_TGxCBcGILR0RBRIvoZSh3G4RRXfaQHaXwTkkVIrch-sOvu4hCCuWKjx3cyZl1hewaBtT1JI0HhFeYyoNoKjD.png) 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iSakBy8wyKMTbKjv9w-TpNxdVXZcNdopNmnxEsQw1wusxtPPk4xq1e_2iqy2-M1JvSZY4pebQn20WX_BZckJ4o4UJmkAdku3l9r19EEtp5W3gE7mEpiYh3uMNATGcfaT.png) 
    - Similarly, we see a spike in botnet-related sales driven by a mysterious listing ti- tled “source,” receiving 10 – rather negative – feedbacks in the summer of 2014. 
- Page 11
    - Listings and revenue are not distributed normally across vendors. As in many markets, there are big play- ers and small players. Figure 10 plots the cumulative percentage of listings and revenue of cybercrime compo- nents over vendors. A small portion of vendors are re- sponsible for a large fraction of the listings. To be more precise, around 30% of vendors are responsible for 80% of all listings. More interestingly, just under 10% of ven- dors are responsible for generating 80% of the total rev- enue. That means that around 174 vendors have sold for nearly $7 million worth of cybercrime components. This translates into an average revenue per vendor of around $40,000, but the distribution is wide and skewed. The 174 vendors range from a minimum revenue of $7,355 to a maximum of $1,148,403.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vLGiugxhZInAn8eHpxmP8pnB7Q6bucUq5IJGxkpk1WcdOqsA-Ol3VGQDBEXmaogmofJ_7XcsBwdOqDEchN4Bj28hVir2J7mBcErm-1UgzFw2qFoAWG6yhjZmE2pVaYW4.png) 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/87QUb337kWZvdCcABtwKMhkKzAzV43RJflxmAzo9Iq-H_5eJyiJM1AN3KBEz4pjpSZNRNwnKo9dJ8mMw0OY5egn4aE5xMA_oTNce6eFEu9oXjfKgkBTompeNS7gqPgcO.png) 
- Page 12
    - The large portion of retail cybercrime is in line with what has been observed on the drugs side of these mar- kets; B2C transactions for consumers of drugs, along with more modest amounts of B2B transactions with larger quantities for lower-level dealers
    - We identified the three best-selling clusters per category by summing the number of feedbacks of all listings in a specific cluster. We then compute the total revenue gen- erated by the item listings in each cluster
    - For all cate- gories, the three best-selling clusters contain more than 46% of all feedbacks, and in many cases more than 60% of all feedbacks.
    - The categories “botnet,” “website,” and “RAT” show lower revenue numbers. Upon manual in- spection, we could identify a very small cluster with only a few feedback that was dominated by a few very expen- sive items.
- Page 13
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dXDQrHFsLp-fq4Eq-r10ZGS6-m9WSnETjvtSYuIj0I4EgYJnqkAY3P82osQ7zAnlfoWNFV2bswFxnT0nOwRSQ5DE-ZmjOP50tqfOjFErh5DtcrxKfb7IYv6oTT3CU5uz.png) 
    - e observe clusters with distinct offer- ings in 4) carding tutorials, 5) PayPal accounts, 6) Visa and Mastercard card details4 , 7) “bitcoin deals,” 8) bank account credentials, 9) Amazon refund guides and 10) Bitcoin exchange
    - App. Prominent clusters of the App category include of- fers for Android loggers, i.e., malicious keylogger apps, Android bank apps, i.e., malicious banking apps, and Dendroid, a RAT for Android.
    - Botnet. Prominent clusters of botnet listings fea- ture products and services revolving around Zeus bot- nets, varying from tutorials, to source-code, to “turn key” setups. We also identified offers on C&C servers and 4This cluster ressembles 1) and 2) but with a focus on Visa and Mastercard brands. It could a priori also include gift cards. DDoS services
    - E-mail. The prominent clusters in the e-mail category contain two types of spam lists, namely basic lists of e- mail addresses, as well as complete databases, including personal details to create personalized (spear) phishing mails. In addition we find a cluster of offerings on spam- related services. Exploit. Within the exploit category, the two main themes are 1) Microsoft Office exploits, e.g., malicious macros, and 2) browser exploits. We also recorded a non- trivial set of sales for Mac exploits. Hosting. The prominent “hosting” clusters include host- ing through VPS or CPanel-listings. We also find a prominent cluster on hosting of Tor-based websites. Malware. Within the malware category, ransomware stands out by featuring two prominent clusters. One clus- ter revolves around the Stampado ransomware, the other on Philadelphia ransomware. We also observed a promi- nent cluster on miscellaneous (assistive) software tools such as keyloggers or portscanners. Phone. In the category of phone listings, one prominent cluster comprises listings on bypassing security features on phones. The other two prominent clusters offer re- spectively hacked Vodafone accounts and lists of usable phone numbers. RAT. Two out of three prominent clusters in RAT list- ings contain generic RATs. The third cluster specifically deals with Mac OS RATs. Website. The website category is composed of three distinct, prominent clusters. One cluster contains web- site development listings. The second is predominantly VPN-connections and/or SOCKS proxies. The third cluster consists of compromised RDP-servers/hosts list- ings.
    - Our analysis suggests that nearly all prolific clusters supply a component that matches B2B demand, but that this supply is incomplete, in that the observed supply ful- fills only a niche demand in each category
    - For instance, we see ransomware dominating the malware category, whereas domain expertise suggests there are, in general, other types of malware in demand. This demand remains mostly unfulfilled in online anonymous marketplaces.
    - Yet, the supply is only ori- ented towards setting-up the necessary phone lines. We observed that guides and tutorials are among the promi- nent clusters in the botnet and cash-out categories. We however note that selling a guide is not the same as out- sourcing a cybercrime component.
- Page 14
    - In this section we briefly present the prominent clusters in the B2C categories – i.e., retail cybercrime. Account. In listings that sell accounts, we observed two main clusters that revolve around offerings for single ac- counts to pornography websites. Next, we see a cluster of listings selling Netflix and Spotify accounts, in quan- tities between two and ten per listing. Fake. The three prominent clusters are respectively of- fering fake passports, fake IDs and counterfeit money. Guide. The clustering process revealed guides in a) bit- coin (“deals”), b) “making money” or starting a business, and c) “scamming.” Pirated. Miscellaneous pirated software, like the entire Adobe software suite or pirated adult videos, and pirated Microsoft software, e.g. Windows 7, are the prominent clusters in pirated products. Voucher. In the category of voucher-related listings, we see offers for: a) Tesco vouchers, b) lottery tickets and c) “free” pizzas, of which most are indeed discount vouch- ers or gift cards for various pizza chains, but a few are in fact credit card offerings, where “slices” refer to groups of accounts. 
- Page 15
    - hey investigated the market for exploits - which turned out to be moderate in size - and the cybercrime-as-a-service market, where growing numbers of new services types were discovered.
- Page 16
    - In three of them (“javascript,” “customer service,” and “web in- ject”), we found no offerings in the large random sam- ple for the ground truth, not even when we searched the whole data with specific keywords. We assume this means there is very little, if any, commoditization of these value-chain components
    - n line with what other researchers have observed for the drugs trade on these markets, we see both B2B and B2C transactions in the cybercrime categories. B2B and B2C, a.k.a. retail cybercrime, turns out to be compara- ble in revenue. Between 2011 and 2017 the revenue of B2C cybercrime was around US $7 million, where B2B cybercrime generated US $8 million in revenue.
    - In terms of generalizability of our findings, we have measured and explained the trends in commoditization of cybercrime on online anonymous markets. Beyond this, our findings only speculatively suggest that the trend to- ward commoditization might not be as comprehensive as has been claimed elsewher
    - Still, this casts an interesting perspective on the “the- ory of the commoditization of cybercrime.” There is a huge discrepancy between the reported profitabil- ity of criminal business models like ransomware (over $1 billion in 2016, according to the FBI [20]) or DDoS-services (one youngster making $385,000 with his booter-service according to local British polic
    - The lack of strong growth suggests that there are still bottlenecks in outsourcing critical parts of criminal value chains. En- try barriers for would-be criminal entrepreneurs remain. The services that are highly commoditized, like booters, seem to draw in mostly B2C activities – i.e., consumers going after other consumers, as was the dominant finding in a victimization study of commoditized DDoS [37]. A recent takedown of a RAT operation also suggested con- sumer consumption, rather than B2B transactions [6].
    - B2B services that require ongoing coordination among the criminals fall short of full-fledged commodi- tization. In other words, the scarcity of supply suggests less-scalable and potentially vulnerable components in criminal value chains. These might be targeted by inter- ventions
    - Contrast this approach to the series of police actions aimed at the shutdown of whole markets: from our data, these operations seemed to have had only relatively modest effects on the overall trading of com- moditized cybercrime. 
- 