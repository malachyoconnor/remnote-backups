- 
- Economics Law & Ethics
    - Supervision 2
        - **Exam Question 1**  
            - a.)  Explain the criminal offences created by the various sections of the Computer Misuse Act.  [100 words] 
                - Section 1 makes unauthorised access of computer systems a criminal offense, however you have to **know **that the access is unauthorised. This can carry a maximum 2 year sentence but intent can be difficult to prove leading to large obvious banners parroting legal access rules when you turn on certain computer systems. Section 2 appends the intent to commit another serious offence after unauthorised access, making logging on to someone's computer and reading off their credit card info in order to commit fraud an offence worthy of 5 years in prison. Finally, section 3 covers the modification of items after unauthorised access, meaning writing viruses can now carry a 10 year punishment. This covers DDOS and the creation of hacking tools. 
            - b.) What offences are likely to be committed in the following circumstances?
                - a.) Alice is clearly running a distributed denial of service attack, and furthermore she is doing it with the **intent **to harm - I.e. she knows this form of access to the system is unauthorised. Note that if the volunteers were informed of their part in the scheme, they could also be charged. For precedence for this case, we could examine the Wimbledon case where 5 million emails were sent to a company - rendering their email useless. This was classed as a Section 3 offence and carried a prison sentence, while Wimbledon's lawyers used the defence that this usage of the system is legal as if 1 or 2 emails were sent that would be fine (so why not 5,000,000), however the test of reasonable use of a system should be "what would the system owners say if you were to ask them if you could use the system in this way" - and of course the use would be disallowed in Alice's case. Furthermore, denial of service attacks were specifically added to the law in 2008 meaning her attack would definitely be a section 3 offence which could lead to jail time of up to 10 years. ^^Always discuss precedent - write notes on that.^^ 
                - b.) Bob has committed three (or possibly four) separate infractions of Section 3 of the computer misuse act. Firstly, illegally accessed a website and modified it without the permission of the owners. Secondly, he has distributed a virus to customers, e.g. software that uses the customers computers in a way they gave no permission for. Thirdly, he is running a Denial of service attack on the baking firm. And finally, he could be accused of distributing hacking tools to all that installed the software - but this would be more debateable, as the customers would have no idea of the tools existence.  Overall, this could result in a combined jail sentence of up to 40 years as Bob has committed multiple severe criminal offences.  ^^Apparently section 1 in there?^^ 
        - **Exam Question 2**
            - You have an opportunity to resell limited supplies of a discontinued model of printer at a good price.  You have doubts about how reliable the printers will be. You will sell them through a website, and want to avoid becoming committed to sell more.  
            - a.) How do you plan to set up your website and use the law of contract to achieve these results? [200 words]
                - I would have to make clear the difference between offering the printer, and "inviting the customer to treat" where the customer makes the offer for the printer (at the specified price) and I can choose to accept or decline the offer (meaning if I have no more to sell, I can decline the offer). This can be done by creating a Terms of Service document and linking to it clearly on the website, this should be done with the advice of a lawyer to ensure no loopholes exist. I should also draw up an electronic contract describing that the offer is an invitation to treat, and also iron out details about defective goods. Due to our limited stock, defective items should be repaired or refunded - we must make clear in the contract that the item will not be replaced. Then once they electronically accept the contract, it is legally binding. ^^Jurisdiction need to remember that it's handled through English/Welsh law. ^^ 
            - b.)  How effective will you be? [100 words]
                - My effectiveness would be in question if the lack of a replacement policy was taken to court, as the customer has the right to the repair or replacement of an item within 6 years if it was faulty. So if I am unable to repair the item (and all my printers have sold out) the customer could take me to court, and dispute the contract as being unfair to the consumer. In this case a legal battle would ensue, and the results would indicate my effectiveness. The "invitation to treat" is a well known practise, and would be effective.  
        - **Exam Question 3**
            - You are commissioned by a customer to design a toy robot that children will be able to control using a smartphone app. This app will also enable them to program the robot using a simple scripting language. To simplify the networking, all communications between the app and the robot flow over Wi-Fi via your server.  
            - a.) Discuss the ethical and legal implications. [200 words]
                - The legal implications include problems of ensuring intellectual property rights around the scripts that customers use, ensuring we are not liable for any harm caused by the robot (ensuring the correct usage is explained in the TOS) and ensuring correct functionality. Furthermore, because the communications are routed through our servers, precautions must be taken so we act as a mere conduit. This gives the legal defence that we are not liable for damage caused by the customers use of the robot. We must make it clear in the contract, that we are not liable for scripts written that cause harm (if the script executes correctly). We must ensure the parents sign for this contract in order for it to be legally binding. May have to employ a Data protection officer depending on the scale.
                - Ethically, we would like to ensure the robot cannot cause harm - and abort operation if triggers that predict harm are found. However, we have the simultaneous responsibility of respect for persons and our customer may use the tool without our meddling. We would like to uphold the law, but this could require inspection of the users code that could be viewed as a breach of privacy. Additionally, we must take into account that the users of the system are children - non-rational actors who do not have the sense to analyse a harmful use of the robot. One solution could be to make the robot very weak, so certain harmful manipulations of it are impossible.^^ Hardware, if it breaks shouldn't hurt the child^^ 
            - b.)  Your customer decides to incorporate a microphone so that the robot can also recognise  spoken commands. To save battery life, the speech recognition will be done in the server.  What effect does this have on the ethical and legal situation? [200 words]   
                - The legal situation now must include accordance to GDPR laws, as we are processing data about our customers. We must ensure the data is processed lawfully, used only for the stated purpose, the data is not kept after it is no longer needed and the processing of the data is secure enough to ensure no loss or damage to the data. We are also under obligations to keep internal records of the database as well as garner consent from our customers (must get permission from parents!). Finally, we must ensure that a process is in place so customers can retrieve any data stored about them - the simple solution being to very temporarily store the data while processing it, and promptly delete it afterwards. 
                - The ethical situation changes slightly as we now have more sensitive data, that could include information from parties **other than our client**. The ACM code of ethics would have us respect privacy and honour confidentiality, meaning very few people should have access to the data. Additionally, we should ensure the models we use for speech recognition are not discriminatory - although there are limits, as we should not be expected to provide a universal translator for all languages if the product is only sold in England. If vulnerabilities are found we have an ethical (and legal) obligation to disclose that to the government and to parents.
            - c.) What practical advice can you give your customer about mitigating the legal risks? [200  words]  
                - Ensure data is stored no longer than it is needed, ideally the data should be discarded immediately after processing, this protects against GDPR laws and removes the need for a data handover mechanism. Ensure the toy is not strong enough to commit harm in obvious ways like speeding into people, this protects them from liability. Collect the parents consent before the child is allowed to use the system. Hire security experts to decrease the likelihood of a data breach or hacking, they should then implement a bug bounty program to ensure problems are caught. Ensure no data is sent from the robot to the server when the user is not trying to use it, an initiation phrase akin to 'hey Siri' or 'ok google' should be implemented. ^^Needs to be distinct so not accidentally activated^^ 
            - d.) Your customer now wants to include a camera so that the robot can recognise gestures as  well. Does this create any further ethical or legal risks, and if so, what might be done about  them? [200 words]  
                - Some further legal risks are included around the photography of children, these data are far more sensitive than audio data and the punishment for failure to uphold GDPR could be much greater. One solution to this is to disregard battery life when this feature is used, and have all the processing done on the device; meaning the data is never held on our customers servers. This also ensures we are never in possession of any illegal data. It must be made very clear and the parents should have to give informed consent that the data is to be sent to our servers if this is not put in place. ^^Alternative is to send features like edges, no sensitive data held^^ 
                - Further ethical risks arise as this is information that can be used to identify the user and anyone in the scope of the camera, meaning the data should be kept with the upmost privacy. 
            - e.)  How might the situation be affected by Brexit? [200 words]  
                - While the UK is no longer a part of the EU and GDPR laws cover handling of EU based citizens, it is unlikely that GDPR will be discarded in the UK. This is because, significant altering of the GDPR laws could result in the EU deciding the UK is an unsafe place for data to be sent - vastly reducing the possible customers to UK businesses that handle data from EU citizens. However, slight altercations to the laws could occur post Brexit. E-commerce laws relating to running of the business are also unchanged after Brexit, and laws around when you need permission from parents always differed between the EU and Britain (and thus will be unchanged). ^^If gap between UK and EU laws, would need a dedicated EU server^^ 
        - **Exercise 1:**
            - (a) Describe three different philosophies of ethics. [300 words]   
                - Consequentialism states that actions should be decided right or wrong, dependent only on their consequences. Furthermore, more positive results leads to an act that is "more right" and the opposite for more negative results. We with to maximise $W = \sum U_i$. However, utilitarianism requires perfect knowledge of all situations in order to assess all the good and bad consequences of an action (knowledge that any actors within such a system cannot have) it additionally requires a method of deciding if an action is good or bad and how good or bad an action is. 
                - The veil of ignorance or Original position, this is a thought experiment where rule makers are given no knowledge of their family, wealth, race or creed before they are reincarnated into society - it harnesses peoples natural self interest and funnels it into the creation of a fair society. Clearly, this is because you would imagine people would want the best life possible for themselves regardless of where/to whom they are born. This could potentially suffer issues depending on the values of the rule makers, one could imagine someone who would rather die be poor who gives half the population all the resources and flips the coin to establish their life.
                - The Kantian theory of duty states that an action is morally correct, if it would be willed to be a universal law. Additionally, one should treat people as an end in themselves not simply a means to an end (this could be seem as an instantiation of the first law). This mimics ideas found in many religious texts, where one should treat others as you would wish to be treated. This does face problems of perspective, as while some people would wish things to be universal law, others may not - for example an exhibitionist could be thrilled at clothes being made illegal, to the dismay of everyone in cold climates.
            - b.) Which of these philosophies might be more, or less, attractive to a successful businessman  who made his money from coal or steel? Justify your answer. [200 words]
                - Clearly the Kantian philosophy does not hold, as to be truly successful in business one must often treat people as pawns - additionally, they may not the utilisation of fossil fuels to become a universal law. The veil of ignorance could be more appealing, as highly successful individuals are often benefited the best upbringing - however they may balk at their hard earned money being redistributed to allow for such a scheme to take effect. Consequentialism may be their best option as there are effects that are impossible to observe, for example while the employment of people within the business is obviously positive the effects of pollution are less obvious. Additionally, one brings ones own moral compass to Consequentialism when it is decided how virtuous an action is - and the businessman may attribute his own morals as he sees fit.
        - 
        - 
    - Supervision 1
        - **Exam Question 1** 
            - a.) ** Explain what economists mean by a lemons market. [150 words] **
                - A lemon market is a market where information on the products in asymmetric, and customers cannot differentiate the higher quality products from the lower quality. As sellers have a vested interest in selling their product for what its worth (they have the knowledge on its worth), and buyers are unwilling to risk buying at higher prices for fear of buying a 'lemon', this leads to sellers selling the low quality goods rather than selling the higher quality goods at a loss until only the low quality items are on the market at all.
            - b.) **What is the difference between hidden information and hidden action? Give examples of  each. [150 words] ** 
                - Hidden actions are actions taken by one side of an economic relationship that the other side cannot observe, while hidden information is information held by only one side of an economic relationship. For example when buying cars, the fact that you're a bad driver is hidden information, and making the decision to buy a safer car because you're a bad driver is a hidden action. Another example would be a worker deciding to slack off, this is a hidden action that can lead to a worse product - the employer has an incentive to associate a cost with this action, this could mean only paying the worker for good products or monitoring their work schedule.
            - c.)
                - a.)  **You form a trade association with several other anti-malware firms and promote a quality assurance mark, perhaps with assistance from the government. [200 words]** 
                    - This signals to the user that your item is of high quality, as the government and . While this doesn't eliminate competition (as other firms also have this quality-assurance mark) it results in poor-quality providers who can provide a cheap enough service to allow for massive undercutting of price to be less favourable by customers. This means a greater share of customers land inside the quality-assurance holding group, resulting in a larger share of the profit. However the asymmetric knowledge of the user could **include** the existence of this mark, and they could end up buying the cheap product they see without knowing about the mark. Additionally, the validity of quality-assurance marks (especially for anti-malware programs) can be difficult to validate by the user, as illegitimate companies could produce their own mark to trick users. There's also the problem that you may be further legitimizing your competition, where alternatives with better products where the legitimacy was previously in doubt can now be chosen safely in place of your product. ^^Signal is good if cost high for low quality but low for high quality - to the point where lying about lemons is not profitable. Assumption being that ^^ 
                - b.)  **You approach the UK banks with a proposal that they certify your product for use along with their banking app products, in the sense that a customer using your  system will have exercised due diligence. [200 words]  ** 
                    - This would likely be successful in making your product seem more trustworthy, as it is bundled with the air of legitimacy banks have but don't deserve. However, this would still have to combat lock-in, where people already with a malware protection service may be reticent to swap. Also, the price that would need to be paid to the banks to advertise your service would likely be very significant - and the firm would have to consider if the potential increase in customers is worth the outgoing cost. This method does have the advantage of using people propensity to go with the flow - if their banking app tells them to install a certain program, they simply go with it and not question if there are cheaper or better alternatives. ^^Assumption being that banks have technical knowhow to detect lemons, and lemons cannot trick the banks. This would then be a good signal. ^^ 
                - c.) ** You tell customers that if they are the victims of a scam that used malware on their  phone you will pay their legal bills. [200 words]** 
                    - This gives the customer a signal that you are a efficient malware detection site, as a failure in your system becomes more expensive to you meaning you are incentivized to stop such failures (very similar to car warranty). However, this will come against the behavioural psychology problem that most people don't think they would fall for a scam or trick. Additionally, if a problem with your service is found and exploited by scammers you may end up having to pay for hundreds of users refunds while the bug is still in place - this means very robust bug-checking features must be in place. This method does have the benefit that it sounds good, but few customers will be able to use it - as a tiny percentage of scam victims are able to pursue any legal action (many scammers being overseas). However, when scam victims attempt to use this service and find there's no recourse - there could be public backlash against your firm. If a firm was truly certain of their product, perhaps they would advertise refunding scam victims (who are scammed through malware their service failed to detect) rather than paying for their legal bills. ^^Make assumptions and solve problem based off those assumptions, assume code is really bug free (obvs not realistic) - assume competitors code worse than yours, and assume claims do occur. Finally point out the drawbacks of your assumptions. Because hyper-rational customer would know few claims go to court, would know the signal is worthless.^^ 
        - **Exam Question 2** 
            - a.)
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/fmDPF-dInQpQH71USeyACbGDBgB3nscLlH3JJzNT4er96vIhCtjR1TYQGylX4N1pvTc6Vt6Sr3_pZcqlcEMQgX1KadmjmFAHIMDqaEx9SY8cG9oGrHlHWDcwUI1pK1WI.png) 
                - b.) In case v>c, then it's always better to choose hawk (as you don't run the risk of getting 0) so must have case v<c:
If the utility of choosing hawk is the same of that of choosing doves, where hawks are chosen with some probability p, this will form an equilibrium.
                - c.) Set the initial conditions and calculate:
                - $$\frac{v-c}{2} \cdot p + v(1-p) = \frac{(1-p)v}{2}$$ 
                - $$\frac{vp}{2}-\frac{cp}{2}+\frac{v}{2}(1-p)=0$$ 
                - $$- \frac{cp}{2} + \frac{v}{2}=0 \implies p=\frac{v}{c}$$ 
            - b.) In real life encounters, the probability of death is 0 - if you strictly consider this (without replacing c with some other factor) then the optimal strategy will always to be aggressive (choose hawk) as you gain at least $\frac{v}{2}$ and don't stand to gain $0$.  
            - However, if you replace c with some embarrassment factor where the other aggressive user wins the argument then the game plays out the same way as the hawk and dove game. Depending on the probability of getting embarrassed (a function of how good you are at arguing and how embarrassed you get at losing) you will decide to be a hawk or a dove .
        - **Exam Question 3**
            - a) **What are the first and second theorems of welfare economics? [200 words]** 
                - The first theorem states that market equilibrium is pareto optimal, that is there is no further way for anyone to be made better off without making anyone else worse off - further changes would negatively impact some players. 
                - The second theorem states that any pareto optimal allocation can be achieved by market forces provided preferences are convex. Preferences being convex means any line between two bundles on an indifference curve will be made up of points that are **weakly preferred** to the bundles on the indifference curve. So given some initial conditions, we can reach any pareto optimal allocation (whether that be communism, monarchy or anywhere in-between) can be reached using a market.
                - Both of these theorems behave under certain assumptions, such as:
                    - Complete markets, everything is traded on the markets. 
                    - No transaction costs on the market.
                    - Perfect information with rational actors
                    - All consumers and firms are price takers
            - (b) **Give three examples of ways in which markets can fail to reach competitive equilibrium  when the assumptions of the first theorem do not hold, discussing the implications for the  information goods and services industries in each case.** 
                - One assumption is that the markets are complete, that is everything can be sold on the market. Consider a country deciding that food should not be sold on the free market, this will result in farmers suddenly unable to make money resulting in a decrease in a supply (without a corresponding decrease in demand). A change to government funding will have to be put in place, resulting in a lack of competition as farmers will be given a set rate. The equivalent for information goods and services industries would be if information on users could no longer be sold, platforms like Facebook and Google would have a large chunk of their business model wiped out as selling information on users through real time bidding for targeted ads is a large part of their business models.
                - If the assumptions that actors in the market are rational with perfect information were not fulfilled (and generally they aren't), this could lead to people purchasing things with little to no utility - meaning people who actually require the item could suffer, and results in people having less money to spend on utility rich items - potentially leading to a decrease in price as the price people are willing to pay decreases, finally this could lead to a stagnation of growth in those industries as they have less money to expand. In relation to the tech industry, this could be people spending all their money on NFTs with incomplete information on their worth - leaving nothing to be spent on the items YouTube, Google and Facebook advertises to them.
                - If the assumption that consumers and firms are price takers isn't met, then firms may list items at a price too low where they cannot keep up with demand - while they struggle and battle with the initial throws of this supply and demand curve:     ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4rqcmEIjQt_7SHMQvvfC0rawX7bN5sS307ywCIuC9CtuiDA4SXZ6n-m_2m2tyJjY8jsZmnz5i4uL858ZndmTTYwcLCrjvqOMFW34IqhJP-2knWk6Nca6sixpTfBWWhHs.png)                                                                                           Until they reach the later stages, other firms will be met with a huge decrease in demand - leading to stagnation of growth. Contrarily, if consumers buy the more expensive items when cheaper alternatives exists, competitors will have to change their product or lower prices even further to appear palatable. In regards to the information technology industry, this would be the equivalent of word becoming free to win back users of google docs - or if github started charging for the service and people kept using it.
        - Exercise 1:
            - a.) **  Suppose that we say that an allocation x is socially preferred to an allocation y only if  everyone prefers x to y. (This is sometimes called the Pareto ordering, since it is closely  related to the idea of Pareto efficiency.) What shortcoming does this have as a rule for  making social decisions? [100 words]   ** 
                - Everyone needs to be polled in order to make any small decision, so decision making will be slow and cumbersome. Additionally, If even one person disagrees, no matter how absurd their reason is the idea will be thrown out, and as almost all decisions are likely to have some level of disagreement very few decisions will be accepted. 
            - b.)** A Rawlsian welfare function counts only the welfare of the worst-off agent. The opposite of  the Rawlsian welfare function might be called the “Nietzschean” welfare function—a welfare  function that says the value of an allocation depends only on the welfare of the best-off  agent. What mathematical form would the Nietzschean welfare function take? [100 words]   ** 
                - $\max U_i$  
                - We select for the maximum utility of our population, and try and boost that. ^^Assume we're looking at the utility of a single good^^ 
            - c.) **Suppose that the utility possibilities set is a convex set and that consumers care only about  their own consumption. What kind of allocations represent welfare maxima of the  Nietzschean welfare function? [100 words]** 
                - At face value, improving the utility of the best off person seems to be giving them all the resources. However, then the surrounding agents will suffer and the world around the richest person will degrade. Additionally, due to the convexity of utility functions resources become less desirable the more you have of the resource - meaning more money means less to a rich person than to a poor one. Thus, while some effort must be spent further enriching the best off agent - some money must be spent to maintain their surrounding population so the best off agent needn't witness poverty or drive on broken roads. 
            - d.) ** The ability to set the voting agenda can often be a powerful asset. Assuming that social  preferences are decided by pair-wise majority voting and that the preferences given in the  table below hold, demonstrate this fact by producing a voting agenda that results in  allocation y winning. Find an agenda that has z as the winner. What property of the social  preferences is responsible for this agenda-setting power? [200 words]** 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/S1XX-5lu6CMf8Oex4OuNutrHIHl8lA_z2RtN62sSS1UOlyLVRJ7fXN8frGL6TGGjzsMr_YJbGNr_STTvSPBZZuGJtZJmTvClb6EsVz4a2kqikwXXrgbQSJqvtTl9RW_j.png) 
                - ^^Not sure if my understanding of voting agenda is correct^^
                - Obviously, without an agenda the entire vote is a three way tie. If we set the agenda to who wins out of y vs z, we have y winning - as we get to wins for y and one for z. If the agenda is x vs z, we have z winning out with 2 votes to 1. ^^Agenda means, first have a and b fight then have b and c fight^^ 
                - I believe it's the property that people vote for the candidate they actually want to win first, and the following results are murky - especially if given a choice of the top X candidates rather than ranking all candidates. Thus, if specific candidates are chosen the results can vary wildly as less strict rules hold for the last two options.
        - 
    -  _**Lecture 1:**_  
        - Macro vs MicroEconomics↔Macro: Performance and structure of global economy or a nation or region.  Micro: Individuals and firms responding to incentives, how market mechanisms fail and circumstances in which markets fail.
        -  _**Prices and Markets**_ 
            - Consider searching for a flat, one bed or house share - people who can afford flats will get them, and others will cycle to far away house shares.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/RJdFdwqCAq_YvvqEJmjnukPI87T0GMU2tOel0cVyW8yoJAQxx6SCnpH0QIfVz6MJLmNtUDpXBR3-7ZUCIzErrtZwX-0bvHUkYRsmImVt4wuojOMT32vY-EO8qTHX4Fw3.png) The equilibrium price is where the supply and demand curves corss - e.g. £500
            - Consider if there's rigging - the cartel meet and restrict supply, 800 flats at £700 can earn more than 1000 at £500 - **This is inefficient, houses are left empty for which there is demand.** 
        - **Efficiency:**
            - A monopolist might leave flats empty, despite people being prepared to pay for them.
            - Pareto Improvement↔A way to make some people better off, without making anyone worse off
            - A Pareto efficient allocation↔Is such that no Pareto improvement is possible
            - Pure monarch and pure communism are **both** pareto efficient.
            - Discriminating Monopolist ↓ 
                - If you know what the person can pay, charge them exactly that, this is pareto efficient and lets you extract the most from the market. The monopolist captures all of the consumer surplus:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/i1z7Qw6bTJvxLthQPGUlCWVpvDvoBp5rLqa46oeI4ScBvHRJLeroPu7YnmfCNlFY6GR9u6z00gATNgS873ZixfReC3zNi38M_aOH05ZUcVGhMgjh0HrrSxZ1PfEtQVyj.png) 
                - This is what the IT industry tries to do with different prices of service (microsoft word). 
            - **Consumer Surplus** 
                - Consumer surplus↔Is the total amount people saved off their reservation price (What they were willing to pay)
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/O-15rQakD1bu-vSC_cXcj6TSpt-v5tqk6yRcyAdBYwMXKfwTC8k5N7ZwWLTX67VhATkCvqjj4imubQ4tjjQOKA31QHEIX9a6Ll_wioRt23rWQcnf0lPgQfy5oGLVwZ2-.png) 
                - People would have payed 2000 payed only 700. Lost out on A & B. The discriminating monopolist gets the lot 
        - **Basic Consumer Theory:**
            - Consumers choose best bundle of goods they can afford. Most of the time two goods enough, books versus everything else. 
            - Assume a budget constraint m, $p_1 x_1 + p_2x_2 <= m$ 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/sECy__ijlVN8kbj_fZJR4bWZyWg-uGKgWjhyHCKYxtPsD-0wwqGAl3LhbhkozcnIjzbW3PgidkM-WVKJ5K0AxxozqZvOWKCXdwyGDpeX3FC3TUfOzSNjcp2rbod-3wda.png) Choices lie within this line
            - **Preference:** 
                - Using Indifference curves or isoquants, we plot where a user has no preference between bundle $(x_1, x_2) \ vs \ (x_1', x_2')$. They are indifferent:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Rnc8D1UP6kPGTUwukPeOKun0fV8lBEH4Pz6V5FnQKDiFoq6_cLuS8-Km9zTYqZQLT37RzJxSTJFAGVfvU9vUxXxf4920JH-yUEbBjt8RE_d4VqR7Z4LVW7lvN96wR_dW.png) 
                - We assume they're well behaved and don't cross, **this is the weak axiom of revealed preference**. I.e. If I'm indifferent to having 10 apples and 10 chocolate bars, I'll be happier with 20 apples and 10 chocolate bars.
            - **Perfect Substitutes:** 
                - Perfect Substitutes↔Don't care whether I have good 1 or good 2, e.g. sugar from Tesco vs Sainsburys.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/RtW4sVt6ZsJ0q8l-QmqUbEUw5Q9eryLcS5Nmn4D30fl0DS-w5BQo2QkEPPSKuqAaimDiKYHLkdB_LUJhkNMkuPJLsjWGQh3y4EiHy9cptDrBpAwQp8itUTiUnYVSdsv3.png) 
            - **Perfect Complements:** 
                - Perfect Complements↔Want exact same quantity of good 1 and good 2, left & right shoes for example.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/v0o8b3wdSbHqfQhwfS0ixECIKjMrHcSB7onxgFp8l3iqdca2mLhezud9q8iNgz1_qgaWwYzpn6arhkGmVjkMK_hPuLo29m99yrgEHrbLa6ILYEXnIkSAHhjX-RNr1hHF.png) This indifference curve says, once I have 1 left shoe and 1 right shoe, it doesn't matter if I have 1 left shoe and 300 right shoes.
            - **Bads:**
                - These are goods I'd rather avoid, sometimes I have to consume of the bad in order to have some of the goods.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/M4iSNms1tnx-YOSJMhigTNsGoB6JonMSKNy76ZC2gStAI835LxRgzx6dSJyXqwCj8Fy0f8dlXwTcxoT_z-upEfAFNXbTHk1ptbErRrIgNayhrmjOruwqCN_0Zgmap3Yi.png) 
                - I'm indifferent to getting more sprouts as long as I get more turkey.
            - **Marginal rate of substitution**
                - The tangent to an isoquant gives the marginal rate of substitution. This is the exchange rate at which the consumer will trade the two.
                - Convex curves: You're more likely to trade a good if you have more of it
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7ECMsjYfQPiyz0X6fyHargCzgFHlL44jINYU5fjzGEQRlvSLSC-07qn4Yv5HIkq8o6B5WLRxAb276LOR8M7wg3m49zPeW6AFS_b3Uvm1NaLp7oarKvPhe57wFz4VDhrS.png) 
                - **Diminishing MRS**:
                    - You are less willing to pay for more books if you have less money. 
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xdD_GZn9yyeAJ9L-H3Cin_MTBznLB2lJirWVTYvNfZAVBSQFCXjanoE6nI-63ytQbJfOXKTnKPuwCd8IuPO4zmLGld-XmtAn2JTbUuU_JyTAcqtzGiJGsxygUPncLikN.png) 
                - **Utility**
                    - Indifference curves can be parametrised.
                    - Marginal cost↔Cost of producing one more good or service
                    - Marginal Utility↔Is  MU_1 = dU / dx1 - e.g. the change in utility with respect to a given good.
                    - Then MRS is -MU_1 / MU_2 , utility functions can be useful for describing customer choices. And can be inferred from things like shopping patterns.
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/U6CZ7hN8XHwXnTqE3AbKr7UoyFEWUMREiibQn8XtkMKG0s-TWRHFj_hXoRwIZqG7mLqAeX2iNaWLS90BuXcWIAlvmgZCO2VpqCXD6Xv96xFaPQlqE7kltJAJI6nUpc0q.png) 
        - **The Marginalist revolution:**
            - Why is water cheap and diamonds expensive. 
            - The value of the last and least wanted addition to your consumption of a good sets its value to you. 
            - Marginalism asserts that individuals make purchasing decisions on an additional item, based on the added utility it will garner them. This idea shifted thinking from costs of production to demand.  
            - Local coal market has 3 producers and consumers:
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/-vko3s4LW2USaWft_HrsAWSr10bXcb_C5wmB0s8pFnN531Eb6BWtGhU0l2dMlf523KiyQYq-k3mu56BBm7lQT_sJbEaOgR3Yj3JN8Bv_G87FdEBd-bdGFHRjpQEEBIYY.png) The price of coal will fluctuate between winter and summer with demand. It's determined by the marginal transaction
        - **Demand** 
            - Market demand is the sum of the demand over the consumers. We can get a consumers demand from their utility or vice versa.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dYeW6tK9xXJ8L56YeOFbm-OJiuK9YxaS8lvYvMJKVcB0APpamzdLloeSgDbpOPJSnRrl8IR71jFS7wt2wsZLyAoYzdyYUSo5DJBQMOfksz8TqipMWqFJG9oTi_A41Nmi.png) 
        - **Elasticity** 
            - Elasticity measure the effect on demand of a small change in price. When do people stop buying your product given an increase in price.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/vTT7b5HI05V2gkljJuvA-N__lA99IpgPl85EaPEArA7LQI3OBb_14H0vUQULw9QgVAUM_GycldqTKIyHMo2J1HZw3pYRqif6-1eqyzoqtzvSwxdul-yfTPqtZm9LkaoP.png) 
            - 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/IwIUmuMf3EuWulCyFKAzRgs5RWZMSx4okIlM-S8wfP39AZrtjtg33kzqwB3dbZ6ETSBR92QD4B0jO2nFDj6mOSD4JMGjeB8dwCIH5gRYg2kPLMRLUdzllgofWY-7Zqsb.png) 
            - Elasticity = 1 means theres likely to be a substitute.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7-y8UFFxlppXF8VuLxiOQsmI4CwPQKhulJqIngb1n74FMQtaiTw18DBRmMqIVadikqJqjN-pHU7e-3nXiz_yNqBa914UqdGRQxCNTVYdm0xd0zL9LJ_6rIueMmNNsF9a.png) 
            - Elasticity = $\frac{\text{Percentage change in quantity}}{\text{Percentage change in price}}$ - so if we have 10%/30% - we have an elasticity of 1/3, meaning that change doesnt have a large effect. 
        - **Supply** 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4rqcmEIjQt_7SHMQvvfC0rawX7bN5sS307ywCIuC9CtuiDA4SXZ6n-m_2m2tyJjY8jsZmnz5i4uL858ZndmTTYwcLCrjvqOMFW34IqhJP-2knWk6Nca6sixpTfBWWhHs.png) 
            - Average cost of goods initially falls are more are produced, then something occurs (overtime etc) and costs rice quickly due to capacity constraints. Thus supply curve is typically convex.
        - **Cost Evolution**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/j8i2xcfsdw00xI7OybDEvjmbqTMqFbrib9AoTvvNW9kGwRQP5GxFErq8238MCh1M1BHafGLiIzkfUU1dsuUCP5NgHIVSy4clXG7KGm0JnJHRRI4EUHr_5oLEnz0j8uGf.png) 
            - Firms can build more factories to build capacity constraints, gives nearly constant fixed cost as firm expands.
        - **Firm Supply**  
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/0eUwnpy4Evz5Y61Fw6bosytT0EYGJI4OXlf9bJsIBIyAqmN2f9C5U6bnVahOWpTroGe-JTmuDthRyGSI_wtsOKstpmXmGeAZ6iaFnRzpUr6AhGksSFSBl0tfHkJ5Muvt.png) 
            - MC = Average cost
            - In a competitive market, at a price above p* the firm would have no demand and at a price below p* the firm would be faced with all the demand. The firms profit is maximised when it sets output so that its marginal cost equals the price p*.
        - **Putting it all together** 
            - Prices are set where supply and demand curves intersect.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/2dG1jmObyO9oF7hWBzX3xm60RFWD5Z-wH5Ue-LJ9e_nn1_fam7JbMvMs266_GAa36ufhBP5oPksvynADsergwaYZE3VMQyVQSlMujO1wKRLkxT0mk-KOLp3fuOLnJSly.png) 
            - p* = marginal cost of marginal supplier.
            - Intrinsic advantages of non-marginal suppliers (good farmlands or easily mined coal) get build into rental values - more expensive. 
        - **Equilibrium** 
            - Supply and demand for 1 good↔partial equilibrium analysis
            - General equilibrium analysis adds labour, capital etc. 
            - Theorems of welfare economics 
                - Theorem 1: Market equilibrium is pareto optimal
                - Theorem 2: Any pareto optimal allocation can be achieved by market forces provided preferences are convex.
            - This has lots of conditions to be correct.
        - **Efficiency, welfare and justice** 
            - There are different theories of justice: 
                - $W = \sum U_i$  - The average citizen, classical utilitarian welfare
                - $W = \min U_i$  - the most miserable citizen, Rawlsian welfare
            - Diminishing marginal utility of money means that transferring £1 from a rich person to a poor one improves welfare.
            - Arrows impossibility theorem↔There is no perfect way to aggregate personal choices into social welfare that's consistent with democracy.
        - **Transaction costs**
            - Trades are not free, time effort comissions bargaining policing and enforcement.
            - External transactions costs higher than internal ones
            - Agency costs within firms also matter hugely
            - Incomplete contracts, opportunistic behaviour comes out.
            - So should tech make firms smaller on average? 
        - 
    -  _**Lecture 2:**_ 
        - Effect of technology on supply and demand: 
            - Increase of supply much easier than other industries, **marginal costs may never rise**. Microsoft enjoys ever increasing returns to scale. 
            - Technology can also improve efficiency.
        - Competition and information:
            - Marginal cost of producing information is zero. Market clearing price. Encyclopedia vs wikapedia
            - Machine readable phon ebooks, Nynex charges 10000 per disk, ProCD starts selling for 300 - finally price dropped to $20.
            - Nowadays free online, how do you make money from selling information?
        - Lock-In:
            - Buying a product commits you to buying more of it, or spending money on one or more of (consider apple): 
                - Accessories - apps for phone
                - Skills - fluency with microsoft
                - Services - network service for phone
            - Time and effort and bother to change.
            - Fewer people change their bankers than their spouses.
            - Fundamental Theorem:
                - The net present value of your customer base, is the total cost of switching.
                - Suppose it costs £25 pounds to get a new customer, and it costs a customer £50 to switch. If you offer them £60 cashback to switch and customers are worth £100 to you - The customer is £10 ahead and you're £15 ahead.
                - **SO** the value of microsoft is what it would cost people to switch to google docs and linux. 
            - The incumbend will strive to maximise switching costs, competitors to minimize them
                - File format wars
                - Loyalty programs 
                - Phone number portability
            - Incumbents promote complementary goods and services that increase lockin, tied printer cartridges to G suite.
            - Asymmetric switching costs, a phone network may supply a phone to win a customer, but keeping them they can simply offer minutes which costs nothing.
        - Network Externalities:
            - Networks more valuable the more people use them.
            - Metcalfe's law↔The value of a network is proportional to the square of the number of users.
            - More complex than this, local effects are stronger, but still more than linear.
            - Overall effect - past some threshold, network use takes off rapidly and creates lock-in (telephone takes off as more people have them).
            - Real networks like fax and email, virtual networks like pcs and software. 
            - Most people choose to buy PCs rather than macs because of software. Then people decided pc was winning, so people just developed software for PCs. This pushed microsoft forwards.
            - It works for bads as well as goods, malware writers target windows while mac and linux are also vulnerable.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4zvGoVnMRgE48-8A6GJHCZmDyD5mS0Pkp0xFV_cUPCjZdKgAKmX9BWKFCAaTHMIzYkMqoguOzoC1jDcS5YatuMeEzaDD9zfs-PBtenaEFP3BTJCum_yNmSdrM3d7THgW.png) 
            - Markets with network effects can "tip", one suddenly taking over. Consider rail gauges in the 19th century. Colour TV standards in the 1950s. Paypal vs other payment startups. Facebook vs myspace. Google meet, skype, zoom etc.
        - Strategic issues:
            - High fixed cost + low marginal cost. Significant switching cost due to lock in and network externalities. Tends to lead to a dominant firm market model.
            - Given all three monopoly VeRY likely. 
            - Hence the race for market share when a new product or service market opens. IBM very well engineered, windows ship it tuesday and get it right by version 3. 
            - Is your customer acquisition cost still less than the lifetime revenue.
            - How bad are monopolies? No competition to allow equilibrium, however what if consumers arent paying anything? EU LAW: A fairly-won monopoly is ok, but cant leverage monopoly in one field to another - google cant direct people to their travel service.
            - US - monopoly used to be measured by consumer surplus, doesnt work for google and amazon. 
        - Price discrimination:
            - An efficit monopolist sells to each customer at their reservation price.
            - Pigous three degrees of price discrimination:
                - Personalized pricing - haggling or loyalty cards
                - Versioning - first class vs economy
                - Group pricing - student
            - Tech increases the motive for price discrimination, have more information about you. Also firms are more likely to have market power.
            - Price discrimination is often unpopular, people don't want to pay more for the same things. 
        - Bundling: 
            - How to conceal discrimination - selling a number of products together.
            - A & B price willing to pay for word and excel:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/nbzIJ1zjMLLSUb48JiYJcBC556k1-06cjLSkbAqBf6PyOqKYZbC_s1vV0Ki0-js5medhE1e8q6zaTxUO_7wt7tludXk-1sj8prILOrpRYCUd70Rdg7GhAAmosxXqN4Ts.png)            By bundling word and excel together, they can make £125 per customer, rather than £50 or £75 each.
        - Income distribution:
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dCQbixGY2SMyLGp7phuvx8Bpv40tdxMvcqMDSJrkaTbj6X2QT60UstgET7AjpxfMqy7LbLcAnFbKYBegmCtQHdbNYZ-J7bfV0qvYUcTe7MkSaxGRWr6bIWBb6puzisw1.png) 
            - The Gini coefficient is used to measure inequality. Gini = A/(A+B) where B is the cumulative income distribution. If Gini = 0 then communism, Gini =1 then the king has the lot.
            - Gini falls with development, rate of violent crime correlates with the Gini coefficient. US has similar Gini coefficient to a 3rd world country. The poor fight harder for welfare than the rich resist them.
            - Democracy is strongly corelated with equality, however cuts both ways. Farm subsidy that gives each farmer £200000 but costs non farmers £200. 
    -  _**Lecture 3:**_ 
        - The Business Cycle: 
            - Global economic crisis, money out of banks, banks bought out leading to economic debt doubling. The more recent economic crisis was not as deep as the last, but the recover has not been as thorough:
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zoTwERlnGfC_RiVFcJ1dOuWTgSPSSAYBF3IdssGfOc6JqVzNJPfGNqJHhPFTr637zqbghRfc0-vT2-qVgxU6xSlW0wkQn7JM0qezdregQ8wDhc5LhSPxAU-J1aLmdu0K.png) 
            - Pandemic causes greater impact on economy than the 2007 crisis, tech industry doing much better than other industries. 
            - Why the pattern of boom and bust?  
            - Mill and Ricardo argued that: demand for goods + savings = supply of goods + investments. Further savings = investment, so demand = supply. Meaning that the market for money needs to be considered, just the market for goods.
            - People want a certain level of savings, maybe 3 months salary. In a recession, liquidity preference rises.
            - In a boom, people and firms borrow assets that can be sold later. A bank that takes in £100 pounds in deposits might lend out £94, meaning £6 of capital underwrites £94 of lending. 94/6 = 15.7  
            - In a recession, loans go bad, share prices of banks fall and banks call in loans, capital requirements increase so governments compete for available loans. Money supply contracted leading to large unemployment.
        - Recession and Tech:
            - Booms as people built railways, Electricity replacing steam lead to boom, mass production of cars led to a boom. Whole industries replaced with online alternatives, amazon half of book market, newspapers move to online. 
            - Increase in demand of online shopping.
        - Trade:
            - Wealth of Nations - if a foreign country can sell something cheaper, buy it with produce from own industry, employed in a way in which we have some advantage. Was a radical view, previosuly maximizing exports and minimizing imports.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Pj6uafDRyN_Xgjw4HIGLkLjzqN033NruSKXd6dKINmjEs4wCRkco_Dnr73azj7MY6vrAFk6m1ZVyUsnAmytxBDho2eP6yNvIQNKiK9g2dy49PjKClnxycSM4Yy576RwD.png) 
            - Comparative advantage, England unit of wheat costs half a unit of wine, while Portugal costs 2/3 a unit of wine.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4IQclGj4j4zfCGoEPFsD7fpo_xlYYips86GGOC2nfPQneZvkEeEGBjrgaYIX8eiTs5Zi5XpdvU69zkTog9TUpcIhQaqb9ljag_MKYQhQzXlIUHuyFl3kvF5vW2ye-TwW.png) 
            - If each play to their advantage, each are better off. 
            - Capital v labour, outsourcing.
            - Under perfect competition, free trade optimal but there are still losers in this case English Vintners.
        - Growth:
            - Output = f(land, labour, capital). Implies colonization and increase in capital. 
            - States invested in industry for time, as governments could borrow money cheaper than private companies.
            - Neoclassical school, all about technology and population growth.
            - Modern view, mostly knowledge that leads to growth. 
            - Prescription, world should spend 4 times more on research and development.
        - Tragedy of the commons:
            - If 100 people each graze a sheep on the commons, if one person adds another sheep he gets 100% more and you get 1% less. That small decrease is unlikely to cause a row, meaning the logically correct move is to have more sheep.
            - Leads to overgrazing, overfishing etc.
            - Welfare theorem assumes complete property rights, this can be used as a reason to privatize common property and fence it off.
        - Externalities:
            - Effects that people care about but not traded - side effects.
            - Consumption externalities include smoking in restaurants, increased education decreases crime. Competitive equilibria are unlikely to be pareto efficient in light of consumption externalities.
            - Can in theory fix with property rights, can only have 100 sheep on the commons.
        - Public Goods:
            - Scientific knowledge is a public good. 
            - Public bad being CO2 emissions, every country affects it equally meaning temptation to free ride.
            - Can capture benefit from scientific discovery, without contributing. Need to institute grants, nobel prizes, doctorate programs etc.
        - Club Goods:
            - Traditional communitites can limit scale.
            - Fishermen in a community can gather and form a rota, signed by the mayor. This is self-enforcing, have the right to chase people off.
            - Needs to be a small enough group to come together and make decisions. 
        - Enter Politics when the club breaks down:
            - Buchanan: " Politics is  a structure of complex exchange among individuals, a structure within which persons  seek to secure collectively their own privately  defined objectives that cannot be efficiently  secured through simple market exchanges  "
        - Monopoly Rents:
            - Firms will enter a market until excess profits competed away, **if no barriers to entry in place**. 
            - Economists define **a rent** as an excess, undeserved income resulting from barriers to competitions. 
            - Rent seeking drives much of politics.
            - What if we regulate prices?
                - Sometimes an increase in prices through regulation can help the owners rather than the workers, taxi license cost.
                - Taxi license bubble.
        - Asymmetric information:
            - 100 used cars, 50 which break down $1000 and 50 which work well $2000 - would think price would be the average. **But buyers cant tell the difference, so price is $1000.** 
            - Additionally, if the price was $1500 those with the good cars wouldn't sell - leading to only the bad cars getting to the market.
            - Can offer a warranty, this is cheaper for those with good cars and acts as a **signal **for the hidden information. Signalling theory important for recommendation systems like Google, eBay, Uber... 
            - Uber drivers more likely to be courteous than black cab drivers,  due to their attached rating. 
            - Do Volvo drivers have more accidents because:
                - Bad drivers buy volvos to survive - adverse selection.
                - Drivers go faster due to increased safety - moral hazard
            - These are examples of hidden information and hidden actions.  _Adverse selection is a lemons market._   
        - Behavioural Economics:
            - Classical economics - indivifuals are rational, they maximise utility with no cognitive limitations.
            - Behavioural economics:
                - Behaviours deviate from this, based on experimental psychology. 
        - Bounded Rationality:
            - People tend to act intuitively rather than rationally, Prospect theory: People offered £10 or a 50% chance of £20 people prefer the former. If it's a loss, they usually prefer the latter.
            - **Framing actions as saving can make them more efficient.** Political marketing with terorrism takes advantage of this.
            - Cyber crime vs terrorism. 
            - Satisfice↔People want to make just-good-enough decisions. Stop once meet goals.
            - Hyperbolic discounting, discount events likely to occur in the future. 
            - The endowment effect→People are more willing to buy an object than sell the same object.
        - Cultural Biases:
            - The way in which people make consistently irrational decisions. It was noted that machine translation from gender-neutral turkish text made Doctors hes and nurses shes. 
            - How to capture implicite biases ingrained in culture?
        - Nudge Theory:
            - Application of behavioural economics to policy. Consiiders how choices are presented, this can have a powerful effect. Can induce individuals to make better choices, **but does not affect underlying structural issues**. 
        - The Power of defaults:
            - Most people go with the flow. Accept product as it comes out of the box. Checkboxes to opt out of market hard to find, used to have to sign up for pension now its opt out rather than in.
            - Organ donation laws in Spain opt-out, now has highest donation rate in the world.  Same in the UK.
            - What is the ethical requirements related to opting in/out to sharing of medical data for research.
        - Agency effects:
            - Classical economics sees instutions as rational, however managers make decisions that improve their **personal** utility as well. 
            - Some companies give stock options to align interest, public choice economics apply this incetive analysis to civil servants and politicians.
            - Why do public sector IT projects fail more than private sector projects? 2/3 fail in public sector, vs 1/3 in the private sector. 
    -  _**Lecture 4:**_ 
        - Auctions:
            - Corporate takeovers to house sales are also really auctions. Auctions are a big success of the internet, from eBay to Google. 
            - Types of auctions: 
                - English, start at reserve price and raise till a winner is left.
                - Second price sealed-bid auctions, highest bidder wins and pays second highest bids.
                - All-pay auctions: everyone pays at every round until one remaining bidder gets the goods. Times of war or litigation.
                - Dutch, start high and cut till somebody bids.
                - First-price sealed-bid auctions: one bid per bidder. Higher bidder wins.
            - Strategic equivalence:
                - Dutch and first price the same result, highest bidder gets the goods at their reservation price. Should bid low if you think your valuation is much higher than everybody else's.
                - Second price and English the same - best to bid truthfully. 
            - Revenue Equivalence:
                - Not who will win, but how much is paid on average.
                - According to the revenue equivalence theorem, you get the same revenue from any well-behaved auction under ideal conditions.
                - Conditions Include:
                    - No collusion
                    - risk-neutral bidders
                    - Pareto efficiency (highest bidder wins)
                    - reserve price
                    - independent valuations
            - What goes wrong?
                - Private value auction, every bidders value is personal and the piece generally has no intrinsic value - say art.
                - In public value auctions, the items do have an intrinsic value - say oil drilling rights. The buyer is the sucker who overestimated the most - the winners curse.
                - Most real auctions lie somewhere between the two.
                - Bidding rings: 
                    - Bidders collude to buy low, have a private auction later and split the proceeds. 
                    - First price auctions harder to rig, everyone must collude. Second price easier to bid. New Zealand bit of 7000000 payed only 5000.
                    - Deter people from entering low quality bids, TV rights where detailed programming plans need to be drawn up. However, placing barriers can result in larger companies scooping up all the TV rights at low prices.
                    - Predation: we'll top any other bid - aggressive behaviour designed to scare people off. 
                    - Also sniping, where a bid is placed in at the last second.
                - Bidders should be risk-neutral, however rationality is bounded - with most people being risk averse. People put in bids that are far to high, from fear of not getting the item.
                - Bidders may pay signalling games, show aggression by a price hike - bidding for TV, do a price hike in their area if they are trying to buy in your area.
                - Also budgets constraints, revenue equivalent theorem only works for infintie money. 
                - Externalities between bidders - profit from selling to both sides with arms.
            - Combinatorial Auctions: 
                - Externalities may lead to preferences for particular bundles of goods.
                - Bid $x for A+B+C or $y for A+D+E
                - Critical app for CS, routing in presence of congestion. This is NP complete.
                - How can we make an auction strategy-proof, if its second price people have the incentive to tell the truth (pay too much and someone else may have as well, suffer winners curse).
            - Ad Auctions:
                - Google makes about a third of all digital advertising revenues.
                - Basic idea, second price auction mechanism but tweaked to optimise platform revenue.
                - Bidders bid prices $p_i$ platform estimates the quality e, and then ad rank $a_i = p_i e_i$
Where ad quality is a function of the relevance and the clickthrough rate.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rZvVd8BnX4p36wkAIOnBIrPmXwuFBJdQxmIh8Qe9GK6s4uUrME6cRllFuxR2NMrCB3yoWAgdgy1N6zL0wUu-KcXkC20MyaUQWYnmTvmuNJyIQOsuDfzhzRisOx-fBZf3.png) 
                - With four people bidding for the first ad position, jerry has the highest rank. And has to pay 1.50 per click - This is calculated by taking Elaine's score divided by Jerry's score multiplied by his bid $\frac{6}{8}\cdot2 = 1.5$ 
                - Each advertiser is paying less than they initially bid, but as their bid affects their ad rank they have an incentive to tell the truth about their valuation. 
                - Ethical Aspects of ad auctions:
                    - Ad quality can easily transform into virality, so if your ad is good as clickbait you pay less. Trump paid less than Clinton. 
                    - Many sites then tend to server more provocative and extreme content, as they have a high quality score.
        - Game Theory:
            - Cooperation or Conflict:
                - If you want something, you can: Make something of value and trade for it - Economics.
                - Just take it, by force or the ballot box - Politics.
            - Game theory is a focus on games of strategy, with problems of cooperation and conflict among independent decision makers.
            - Games of perfect (chess) or imperfect (battleship) information
            - Example matching pennies, if two pennies are different Alice gets bobs penny - else he gets hers. The strategic form is:   ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/E9YwIxeKkXu1lqHplqGdrv_SHFUVKUHeKCQ0LjNFA2RkUPgpGYpM9dx0TQDat9fJSZHyo3ucSbKnSSli5sD1DGJ6U4X0iuD4kGbUSbku1aF_nviqMyBS4KXuRX45cTNQ.png) 
            - Zero sum game↔One players gain is anothers loss.
            - Consider this strategic form: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7TKd0Fp1aHGZbdkyQUxKi5Lxr39MDqVSauBOuS5_ILDagnfuq3y8xDZpKU7WO3cUdRUOxI39qP_e_gTMxp77RedwPik8XjbZIJFsO-d9ygFuVS4fwcq-Lq2yktrAgeqf.png)         Bob is always better off playing left, regardless of whatever Alice plays. A strategy is an algorithm - input state and output play.
            - Nash Equilibrium:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/J9BK-4asv8GkG0WFHEGH2Ivz9dwSg2HWDoeAOGFE-aSRAY4bHh3dXjS0Hvr5UV3offClGwlr7A8bhcXq86_K-1AzlFUCkc8C7OIkI1aT2YjaerrHGfYmTPjBsoKQt9Fn.png) 
                - **The optimal strategy depends on what they think the other will do. **
                - Nash Equilibrium↔Two strategies are in Nash's equilibrium when A's choice is optimal given B's and vice versa.
            - Pure v Mixed Strategies:
                - Rock paper scissors - has no Nash equilibrium. 
                - Alice plays scissors ⇒Bob plays stone ⇒ Alice plays paper... Fix this using a random algorithm.
                - **Deterministic algorithms called pure.**
            - Prisoners Dilemma:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4_VH7AgZnVE6DQrL2943-HqDL8F7f1NDAfUYJZB-X8mT4VDHQqgzh-JYPMGEf9hLXsKvfxXNcOz9Pvih0aGZU8jv4owcwStUmIe7GRsQcAJ4TUzbhKHfXmC4Q8XcihTI.png) 
                - Both will cheat rather than cooperate, applicable to defense spending - fishing quotas etc.
                - If played repeatedly - Tit for Tat solution. Cooperate at round n, do what other guy did at round n-1.
            - Price Fixing:
                - If it costs x to fly from A to B, to flights compete and spend x + 5, OR collude and charge 2x?
                - Competition laws forbid price fixing cartels. Bug can occur naturally. Try charging 500 and see what other airlines do. If they defect by competing, play tit-for-tat.
            - Stag Hunt:
                - People have to work together to hunt stag, but hares can be caught individually. 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/phJ_0IA1kUxgZYTwYfjs5TWPxZiCXUMMC1qx9kAoUpv0roCC9Cls5Rr9qdpSL-CjWTPL2-8RQ6N1tEj2kYlbRduANgpGaXXQL0Tz0-Zyps4fQF0SD6nqGzWru57hCkci.png) 
                - Only chase hare if you believe your buddy will defect.
            - Volunteer's dilemma:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4TatYBq4ak-QZMZdc2hj8oynqq_AaHmyBrGd6Ykw8EoRQLCVM5Nq6tjPAMeWuEZdjr88WrIUBrGCm-gLpzVv4L-qBZ9zWodZffo_2QzfuJLCg4a3_o6ME9AKW6ca1s-P.png) 
                - Leader shows bravery.
            - Chicken:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/1ns9L4OCTV0Luda7C0jR0aQ6SMnCZPNYWqJI6637KmuvrYiTGh1Y5Oj-WVYv9J3lkUB7894mIUe5BHvLaViUXT4UVVbs-d1wlaVKF2LXe8ZMd7UNuzY7MxJx0XseT_5p.png) 
                - Iterated version of chicken ⇒ hawk dove game.
            - Hawk Dove Game:
                - Food v at each round, doves share and hawks steal from doves. Hawks fight with risk of death c.
                - If v > c, whole population would become hawks - if c>v then hawks will start to die off and an equilibrium reached.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/fmDPF-dInQpQH71USeyACbGDBgB3nscLlH3JJzNT4er96vIhCtjR1TYQGylX4N1pvTc6Vt6Sr3_pZcqlcEMQgX1KadmjmFAHIMDqaEx9SY8cG9oGrHlHWDcwUI1pK1WI.png) 
                - $\text{note}: (1 - c)v/2 = \frac{v-c}{2}$ 
                - if v > c:
                    - If one player chooses Hawk, the other should also choose Hawk, as (v-c)/2 > 0
                    - If one player chooses Dove, the other should choose Hawk, for the same reason.
                    - **So hawk dominates.** 
                - if v < c: 
                    - If one player chooses hawk, choose dove.
                    - If one player chooses dove, choose hawk. 
                - Small number of hawks prosper, as most interactions will be with doves. DO THIS: at hawk probability p setting hawk payoff = dove payoff.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xXsTJGAs1j2Rt3ZGXAFFl7tRuvM7ICZf_NUdOoVkV-OjMxssCw1B8-XRpKiWrV3pIf9DIIQ8kF3Ui556E7zsM9rrmUU11er2-fUmGlMbsso-wIczS2xn9-OZyTxDxd9G.png) 
                - So stable equilibrium at p=v/c, Models the probability that population in a species will be aggressive.
            - Broader Implications:
                - In pre-state societies, better kill someone you don't know. We know live in more fair society. Evolutionary basis of morality, fairness from tit-fot-tat - hierarchy from hawk-dove.
                - Internet - less cooperative social mechanisms and more echo chambers. No equilibrium reached as in hawk dove. 
            - 
            - 
        - 
        - 
    -  _**Lecture 5:**_ 
        - 
        - What is law?
            - Can't get all we want through buying and selling through marketplace - because of externalities
            - Politics system which persons seek to secure their own objectives, which cannot be achieved through simple market exchanges.
            - The main mechanism is law!
            - Many origins & flavours, state religion common Roman Napolean etc. **We are interested in Criminal and civil law** 
            - Criminal: Alice harms bob seriously, so state prosecutes her
            - Civil law: Alice harms Bob or breaks a contract, Bob can sue Alice 
            - SIGNIFICANT OVERLAP - if police too busy and there's an assault can sue.
            - Difference between showing image in video to pirating large scale
        - Criminal Law:
            - Requires:
                - A guilty act
                - A guilty mind - if no intent cant be prosecuted. 
            - Prosecution must prove guilt beyond reasonable doubt
            - CPS guidelines matter and agreements - e.g. with the IWF. Hacking tools are offensive if they are intended to be used for damaging or stealing from computer systems. **Wireshark could be considered a hacking tool!** Need a good reason.
        - Civil Law:
            - Contract - making the agreements you want
            - Tort - avoiding infringement of the rights of others, give adequate notice to other of your rights you want to enforce
            - Regulations - specific things needed to avoid penalties and enforce your rights
            - International law - agreement with customer in other countries
        - Contracts:
            - Offer and acceptance my competent people, for a lawful purpose. Must be at **least 10 years old!** Need both people to supply something
            - Can be made in writing, orally, by conduct
            - We make dozens of informal contracts every day. 
            - When you have offers, this isn't an offer but an 'invitation to treat'. The customer then makes the offer and the shopkeeper accepts!
            - **This is important if you run out of stock, won't get sued.**
            - Linking to terms and conditions generally enough - train ticket too small
            - Many laws require some contracts in writing - in USA all goods over $500
            - Many jurisdictions have electronic signature laws; electronic writing fine as **essence of signature is intent.** 
            - Clicking on button evidence of intent in the us since 2000
        - Limits:
            - You're now liable for any malware you give to customers 
            - Retailer has one chance to repair or replace - - else refund.
            - Can't enforce unfair contracts against retail customers
            - Can't exclude liability for death or injury, even if excluded in contract
            - **However, this doesn't apply to services. **If your satnav sends you to an inappropriate place, the makers can be sued - **not so for google maps** 
        - Globalisation:
            - Can be tiresome for a firm in the UK to be sued in Australia, need to make it clear who's laws apply and **separately **where claims should be heard.
            - Enforcement of foreign judments not straight-forward, USA is rogue
            - One fix is to specify arbitration - private civil law 
        - Arbitration:
            - Contract can specify binding dispute resolution by an arbitrator
            - Can also specify applicable laws and other things **like** limits on cost
            - Arbitration awards are recognized and enforceable everywhere.
            - **This is a method of optimizing and privatizing the law to settle disputes between companies.** 
        - Costs:
            - US system - Each side pays own costs in sueing. Can be expensive for some firms 
            - UK system - Loser pays the winners cost, over £5000 pound threshold outside of small claims court - rich consumers can ruin you, but poor customers may lose their house.
        - Tort:
            - Second main way you can become liable online, after contract
            - A tort, is a wrong which unfairly causes someone else to suffer loss or harm
            - Examples are negligence, defamation or copyright infringement
        - Negligence:
            - Arises if you break duty of care, e.g. if you cause a car crash, you are liable for damages to cars
            - **Doesn't apply to indirect harm, **if you cause a traffic jam its too hard to measure the damage 
            - Usual yardstick is the standard of the industry. E.g. if some banks start using 2fa, all banks need to do that to not be negligent
            - Insurance laws tied up with liabilty, car crashes - medical malpractise.
            - If you software harms a **non-customer**, you didn't disclaim liability as they didn't make a contract with you - **negligence rather than breach of contract**  
        - Defamation:
            - Libel (if spoken, slander) is a tort, **UK is a popular venue for this** 
            - Direct defamation; innuendo; linking
            - Burden of proof on defendant in UK
            - Uk system of costs shifting, loser pays winner's costs.
            - Defamation act 2013, excludes trivial claims, creates public interest defence - journalist can claim public interest. Makes the claimant pursue the author first rather than the organization they work for
        - Intellectual Property:
            - Patents:
                - Mechanism to tackle lack of money given to R&D from externality in research
                - Protects an invention which must be: 
                    - Novel (no prior ideas)
                    - Useful (Not something that doesnt work)
                    - Non-obvious (to something skilled in the art) 
                - Typical duration 20 years - **Only granted if applied for** - **Also will most likely want to apply for one in ** _**multiple countries.**_  
                - Traditionally only physical inventions
                - Public key encryption made huge amounts of money
                - But the economoic case is weak, except in the pharmaceuticals - to IT firms, patents are a nuisance many thousands of patents that are said to conflict
                - Software patents not allowed in Europe **in theory, often discarded by courts. **The court keeps stretching this - not to be believed. 
                - In general innovation in CS very incremental - thousands of ideas in code, as opposed to a blockbuster molecule drug.
                - So far only 4 CS patents earn serious money
                - Microsoft has an open invention network, "trade patents"
            - Trademarks:
                - Marks that distuinguish your good or service (IBM)
                - May be registered (®) or not (TM) - registering can make litigation easier. If registered, usually win in domain name disputes
                - Can sue infringers, but have to show misrepresentation **damages your business** 
                - McDonalds used to sue anyone with Mc in the name in catering - too aggressive. 
            - Copyright:
                - Statue of Anne, protects your literary works - extending from novels and drama to art, music. **Beforehand, courts gave monopolies to businesses to write books of particular types. **Oxford making dictionaries 
                - Is the main protection of software - No need to register but asserting copyright can make litigation easier
                - Duration of copyright has steadily increased, lifetime + 70 years. Walt Disney
                - Protects against copying - but fair use and fair dealing get outs from criticism
                - Moral right - **right to be recognized as creator **remain yours even if copyright is sold. Can refuse that your sold work be published if damaged
                - Many orphan works, where author not known. This stalled the Google Books project
                - How to avoid software having thousand of competing claims -  Stallman GPL Licence if you use free work, yours additions must be free too. BSD license allows companies to use as they like
                - Creative commons gives a general framework for sharing 
            - Other IPRs 
                - Specialist rights
                    - Databse rights 
                    - US semiconductor chip protection act
                    - Plant breeder's rights
                    - Design rights
                - Rights based on contract
                    - Materials transfer agreements 
                    - Confidential information NDAs
                - Limits - employers cant restrict knowledge that becomes part of the tools of your trade - if become very good at coding at Google, can go elsewhere
            - DRM - Digital Rights Management
                - Copyright ownders panicked at printing, internet, cassetes 
                - Huge push to introduce DRM - but shifted power to Apple, Google, Amazon from old-style record companies
                - US law made it illegal to mess with DRM mechanism
                - Lexmark vs SCC case allowed for reverse engineering for compatibilty - allowed people to circumvent Lexmaark ink cartridge certification
                - October 2018 - John Deer put software in tractors that made them stop working if taken to unauthorised repairers - **breaking this illegal, but selling tools to break it legal.** 
                - Open-source tools grey area still
            - Strategy:
                - IPR often a combination of patents, software copyright, MTA
                - IT industry strat, patent portfolios mostly defensive, used to get access by cross-licensing
                - Compound models, GPL the linux version and sell the Windows version - can then charge for support and other things
                - Startups: VCs like to see some IP
    -  _**Lecture 6:**_ 
        - UK Law and the Internet
        - Computer Evidence:
            - Until 1968, relying on computer evidence was akin to hearsay - e.g. if Fred says something, Fred should speak in the witness box. **Civil Evidence Act 1968** solved this, computer must be operating properly.
            - **Police & Criminal Evidence Act 1984**: Required evidence to be brought by an expert that system was operating correctly. Now replaced by presumption that its operating correctly, if disputed the relying party must demonstrate their computer works right
        - GDPR:
            - Applies to EU firms from 25 May 2018. Law has survived Brexit, unchanged so far. If Uk changes too much, EU might stop sending data. **Applies to those who process data about people residing in EU** 
            - Aim is to protect the interests of the Data Subject. Differs from US privacy protection landscape, companies **volunteer to not do types of processing for privacy.** 
            - Six Principles to be compleid with, data must be:
                - Fairly and lawfully processed
                - processed for limited purposes 
                - adequate, relevant and not excessive
                - Accurate and up to date 
                - Not kept in  aform that identifies for loinger than you need it 
                - Processed securely and protected against loss or damage - losing just as bad as having it stolen
            - Extra protection applies for "sensitive personal data" - health, about political affiliation, trade union etc.
            - Requirements to keep internal records of your databse:
                - Who you are, the type of data and who provided it
                - Retention schedules, how long until its discarded or anonymised
                - Security arrangements, technical & organisational 
                - Details of transfers (especially when 3rd countries involved) 
            - Essential to identify why processing is allowed:
                - Consent: for each purpose, data must be freely given (no bribes), specific, informed and unambiguous (no pre-ticked boxes)
                - Contract - will say what data gas company keeps and who they share it with
                - Legal compliance, banks have to keep some data
                - Vital interest of a human, public interest, legitimate interest (have a legitimate reason to process and run their business - complex), member state specific reasons, crime & justice ... etc 
                - Must get permission from parents if under 16 (UK: 13)
                - Regulations apply all across the EU right from when it's put in place, unlike directives. **Intent to have consistent set of rules across EU.** 
            - GDPR provides the following rights for individuals:
                - The right to be informed - privacy notice that explains processing
                - The right of access - systems need to be designed to provide data
                - The right to rectification - complicated when opinions come in
                - The right to erasure - if you have no compelling reason to keep the data, right to remove it. Google has this problem, man bankrupt 10 years ago
                - Right to data portability - allowed to get a copy to feed it into a different system
                - Right to object - they have to record this, can hold but not process or remove
            - New systems must have data protection designed in - may have to do impact assessment
            - Data breaches must be reported to regulators **within 72 hours - **plus a req to notify data subjects (if data high risk) 
            - Fines can now be much bigger - used to be 500,000 now percentages of world wide turnover! BA got a 1.5% fine got reduced to 20,000,000 as shopping card got hacked
            - Firms processing data at scale (& public authorities) must have a Data Protection Officer
                - Can be a contractor
                - Must be capable of advising on GDPR obligations
                - must monitor compliance with GDPR
                - must report to the board and cannot be fired for doing their job!
            - DPO optional for other firms, but must have sufficient staff & skills to discharge their duties under GDPR
        - **Computer Misuse Act 1990:** 
            - Various hacking activities in the 1980s, prosecuted with forgery or criminal damage legislation
                - Gold & Schifreen gained top level access, altered messages in the Duke of Edinburgh's mailbox. Originally found guilty and fined, forgery convictions overturned on appeal
            - Failure of existing legislation to be effective led to legislation cover hacking, virus propagation etc.
            - Section 1:
                - Unauthorised access to a program or data, - need to **know **it's unauthorised 
                - Need not be a specific machine (or in the UK) 
            - Section 2:
                - As S1 but done with intent to commit another serious offence
                - Raises the stakes from 2 to 5 years - s1 was a mere 6 months but amended in 2008
            - Section 3:
                - Unauthorised modification - tariff is up to 10 years 
                - Intended to make virus writing illegal
                - Added denial of service of attacks in 2008
                - Making/distributing hacking tools is illegal since 2008 - confusing when white hats use
            - Case Law is Chequered:
                - Fines often much smaller than damages caused 
                - Only aroudn 20 cases a year, often easier to chrage under Fraud act
                - Paul Bedworth got off on an "addiction" defence - couldn't know what he was doing was wrong
                - Whitaker convicted (but conditional discharge) for not disclosing a time-lock that froze the software when clients were late on making payments
                - Pile convicted and received custodial sentence for writing virus
                - AMEX case shows multi-level access can matter - not entitled to access part of system so unaurthoised access
                - police officer found to access data on a car parked outside ex-wifes house to find out who it belonged to. **Found to be legal, but subject to disciplinary action** 
                - Wimbledon case, mail bombing with 5 million emails is an s3 offence - test of unauthorised becomes "If I were to ask would they say 'yes'" I.e. Can I send you 5 million emails, No.
                - Cuthbert ("tsunami hacker") convicted of s1 offence for trying out ../../../ URLS. Donated money and poked around in the website, lied to the police.
        - **Electronic Communications Act 2000:**
            - Part II - electronic signatures:
                - Admissable in evidence
                - Creates power to modify legislation to allow the use of electronic communications or storage
                - Not as relevant in practise. Most companies care more about if you have the money, than who you are
        - Investigatory Powers Act 2016: 
            - Replaces RIP Act 2000
                - Much remains the same, but legalises lots of things that Snowden revealed - made to allow GCHQ and the NSA to keep doing what they were doing before
            - Deals with interception - revealing content other than the sender/receiver 
            - Deals with communications Data 
                - Metadata describing communication - length of communication, IPs, etc.
                - Provides for retention regime by ISPs
            - Permits equipment interference (with a warrent) cab put malware on your system
            - Permits bulk initerception, bulk acquisition, bulk equipment interference and collection of bulk personal datasets. Allows GCHQ to access all data coming out of UK, get all database data from Swansea etc.
            - Interception:
                - Tapping a phone, musut be authorised by warrent signed by the Secratery of State:
                    - Product is **not currently admissible in court** - would only disclose some of the information, as don't want to show the holes in the collection regime.
                    - GCHQ can scan international communications for "factors" (keywords)
                - Some sensible exceptions:
                    - Delivered data
                    - Permission from both aprties
                    - Stored data can be accesseed by production order - just a judge
                    - Techies running a network, can intercept for debugging
            - Lawful Business Practise:
                - Reulations describe how not to commit an offence under the RIP/IPA acts. Do not specify how to avoid problems with data protection legislation or other relevant laws.
                    - Only applies to business
                    - Must be by system controller
                    - For recording facts, quality control etc
                    - Detecting business communications
                    - Or for keeping the system running
                - Must make all reasonable efforts to tell all users that interceptions may occur
                - RIP Act 2000 - Encryption:
                    - Still in place, deals with encryption
                        - End of  along road, starting with "key escrow" where encryption keys had to be given to the government
                    - Basic requirements is to put material into an intelligible form - can be required to decrypt
                        - Can apply to messages
                        - Stored data 
                        - If you claim to have lost or forgotten the key, prosecution must prove otherwise
                    - Keys can be demanded:
                        - Signed by Chief Constable
                        - Notice can only be served at top level of company
                        - Reasoning must be reported to commissioner - ensure different police forces use the power consistently
                    - Specific "tipping off" provisions may occur, must not tell anyone you've been served the Notice
        - E-Commerce Law:
            - Stayed the same after Brexit
            - Consumer Rights Directive (2011):
                - Remote sellers must identify themselves, and where they're based 
                - Details of contract must be delivered, email ok
                - Right to cancel (unless service already delivered)
            - E-Commerce Directive (2002):
                - Online selling and advertising is subject to UK law if you are established in the UK - no matter who you sell to
                - Complexities if foreign consumers have rights in their country, **the test is if you marketed them. E.g. £ and all in English, clearly advertising to UK people** 
                - E-Commerce Directive also priveds key immunites for ISPs:
                    - Hosting, Caching, Mere Conduit - if you do any of those things, not your fault if there's bad things on those.
            - Privacy & Electronic Communications:
                - Rules on phone directories and location info etc
                - Bans unsolicited marketing email to natural persons. But see your ISPs acceptable use policy
                - Controls on the use of cookies, superceded by 2010 legislation
                    - Must give clear and comprehensive information
                    - AND must have consent ...unless cookies are strictly necessary for provision of an information service
                - Was intended to be replaced by time GDPR in force - now left EU not clear what will happen
            - Lots of other Legislation!
                - Lots more E-Commerce stuff:
                    - Sale of Goods, Contract law, Unfair terms, Unsolicited faxes etc etc etc
                - Lots of rules for adult stuff
                    - Children stuff illegal
                    - Extreme porn making + poss illegal
                    - Obscene publications act - webmaster conviced
                - Lots of other specialist issues
                    - Fund raising for political parties
                    - Selling age-restricted goods
    -  _**Lecture 7:**_  
        - **Philosophies of Ethics:** 
            - Ethics:
                - Laws are often 10 years behind, and even then don't often fit reality very well
                - Practical Ethics - in what circumstances should we restrain ourselves, more than the law requires
                - Analogy: medical ethics constrains doctors behaviours - how can we form these for software developers
            - Philosophies of ethics:
                - Often authority theories arise, coming from religion - these often have disputes that need to be resolved. E.g. should slavery be legal, scriptures often allow for it.
                - Intuitionist theories say we can tell what's good or bad - but intuitions can differ. 
                - Egoist theories say people act rationally in their own self interest.
                - Consequentialism:
                    - If an act is right or wrong depends only on consequences.
                    - If more positive acts, the better or more right the act
                - Maximise $W = \sum U_i$ , however the consequences cannot be worked out in detail, and welfare is difficult to define.
                - Ticking bomb argument, torture should be allowed if terrorist knows the unlock code - does the end justify the means
                - Modern debate: act vs rule utilitarianism
                - Would you rather be reincarnated in the USA or Portugal - poorer but with better welfare.
                - Aristotle: Consequentialist theories are for beasts, you'd be happier if you were stupid. Prefers people acting in accordance with nature and duty
                - It's not all about the consequence of actions, but the motives as well.
                - The many flavours include Kantian theory of duty - act only on maxims you'd like to be universal, and treat people not as means to an end
                - John Rawls Theory of Justice - should make moral decision based on ignorance, ignorance of whether we'll be reincarnated poor or rich - leads to maximising $W = \min U_i$. 
            - Moral Reasoning:
                - Koglberg's theory of moral developmentL
                - -Pre-conventional:
                    - Stage 1: Punishment and Obedience (greater the harm the greater the wrong, law breaking morally okay if no punishment)
                    - Stage 2: Instrumental hedonism (Conformity to gain rewards)
                - -Conventional: 
                    - Stage 3: Conformity, what is right is what your family views as right. Conforming to those rules preserves relationships.
                    - Stage 4: Authority and social order, what is right is according to authority and duties
                - -Post Conventional: 
                    - Stage 5: Morality of contract, individual right and democratically accepted law. Rules based on concensus, lawbreaking alright if based on social justice and preserving human rights. Changing laws preserved to breaking.
                    - Stage 7: Morality of universal principles of conscience. Behaving in the way that one believes to be right, hold beliefs and behave in line with them
        - **Professional codes of Ethics:**
            - **ACM's code of ethics**, a computing professional should: 
                - Contribute to society and human well-being
                - Avoid harm
                - Be honest and trustworthy
                - Be fair and take action not to discriminate
                - Respect the work required to produce new ideas, inventions, creative works, and computing artifacts
                - Respect privacy 
                - Honour confidentiality
            - Responsible vulnerability disclosure:
                - If vulnerabilities found, do we keep quiet or tell everyone at once
                - Responsible disclosure: confidentially disclose to those that can remedy or mitigate the impacts - heart bleed. Meltdown and spectre
                - Bug bounty programs
                - Should we make it public, if no efforts are made to fix the bug post responsible disclosure
            - Ethics in research
                - 1940s: Nazi human experiments
                - 1930-1970s: Tuskegee syphilis experiment
                - 1970s: Stanford prison experiment
                - 1960s: The Milgram experiment
                - 2010s: Facebook emotional manipulation study
                - 2019: use of organs of executed prisoners without consent in China
                - People now screened before research, trauma, mental fortitude etc.
                - Nuremberg code:
                    - Voluntary and informed consent of subjects essential. Must be able to leave the experiment at any time
                - Research Ethics Boards  - declaration of Helsinki independent review board or committee
                - Research funding bodies must consider ethics
                - Program committees and journal editors, consider ethics after research is done but before publishing
                - Professional ethical guidelines or codes of practice - ethical framework that provide ethical guidelines
                - For Computer science: The Menlo Report:
                    - Acknowlodges the speed of distributution of computer science research
                    - Core principles: respect for persons, beneficence (minimze harm, maximize benefits) , justice (risks and benefits distributed fairly) and respect for law & public interest. 
                - Your Part II project may involve human experimental subjects
                    - Independent review by uninvolved scientists greatly reduce risks of civil litigation and criminal prosecution if things go wrong
                    - Pay attention to the procedures for ethics committee approval - if they say no don't do it (unlike Cambridge Analytica).
- Semantics
    - 
    - Semantics Supervision  1
        1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/EWCgcOK-lZJ6GXtKgqpmCeQA2MFAPMXNYxRMBbtq1Xo64BIrKQCe2_wG2RV3mMZDM0vlnXIIDh2jgmHZ7JV5hYlLSXv7Nh7gdgyv65mlLn2cT_dn6BefcHmjX5Q-Un2e.png) 
            - ```python
l2 := 1;
while !l1 >= 1 do (
	l3 := !l2;
	l2 := 0;
	while l3 >= 1 do (
		l2 := !l2 + !l1
		l3 := !l3 + -1
	)
	l1 := !l1 + -1;
)
l1;
``` 
        2. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5Ris8GT10bHMokG27aJov3qS-y0LOsB4EbaA3x1h1pbTkoRyJWK9FX4GYRcTAdUtR-ckWJZ8cnaVcBBGlOy6idjILbTxVkbiAEgSiSujgYSpbiCSXSOq3cc6xGtHBf4x.png)  
            - Assign1: $\langle (skip); (l_1 := (!l_0 + 2)), \{l_0 \rightarrow 7, l_1 \rightarrow 0\} \rangle \rightarrow$ 
            - seq1:      $\langle (l_1 := (!l_0 + 2)), \{l_0 \rightarrow 7, l_1 \rightarrow 0\} \rangle \rightarrow$ 
            - deref:     $\langle (l_1 := (7 + 2)), \{l_0 \rightarrow 7, l_1 \rightarrow 0\} \rangle \rightarrow$ 
            - op+:       $\langle (l_1 := (9)), \{l_0 \rightarrow 7, l_1 \rightarrow 0\} \rangle \rightarrow$ 
            - assign1: $\langle (skip), \{l_0 \rightarrow 7, l_1 \rightarrow 9\} \rangle$ 
            - $\not\rightarrow$ 
        3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/PU6c_xWMwTB5BMOi_AkS3jCdEHAoljIZzyNF1tKO8M5b7SWREeV8y14p8GfIL5rYW4YehyDDK53ae1Lbm1Agt0aUFcc-bcBJTW_NXNnZsDT23rxT1KosrOxxyUvB6YkD.png) 
            - Assign1: $\langle  (skip;0)+(l:=2;0),\{ l \rightarrow 1\} \rangle \rightarrow$ 
            - seq1:      $\langle  (0)+(l:=2;0),\{ l \rightarrow 1\} \rangle \rightarrow$ 
            - op1         $\langle  (0)+(skip;0),\{ l \rightarrow 2\} \rangle \rightarrow$ 
            - assign1   $\langle  (0)+(0),\{ l \rightarrow 2\} \rangle \rightarrow$ 
        - 6)
        - 7)
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Rc4c9TOhFHPbRYzj828cEU4_JRuZDmfE-v24Gu_YmS6y--EURzhWW-PMU88sEU22nb49y_9OYtEjwwEdB_PleXYOnxhWitd-yfqix22QhzlPCYXoVZTXboLjKpahlJJQ.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Jc0qhbdhd-lL9d7htzVB0_f9SqP9bb5cg1QrRt-2_XH6PLNFBcCgD0PslnWjyxw__WxN4QVXJjagXmCzgDniPmUKrGjhscxgVhtRB8CdcFzhVshxtcn2trM9rlsZMn9w.png) 
        - 8) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tphLaWwDL-YsZsNbnqyIY3lPP1hldIbTHJjTmHTf32HFBRl65rLnYtqVRM6pgTP8FCPyBd__LGWK4u1OgePF-XJQuSVxTgMWJ4kxnnMBdwSzgPEuCnol18OwFxHrv_y4.png) 
        - 9) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/qWfnPEWfH_HIYJemqT-IHCZx3cpmYU4lSexlKMO_mKxcgZzZw9j6HqDFubB9XnHoPVzY1gO3e4NRsLSceJ4jPHuDdtlSIX0w8DPVnLA4Z84VFK6YPlm2P36wGpaDocVO.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Vx3Ur63En_V4zF2JiCllUlKE3nqF6yIrgRJgxZDUTiVBZbtgPw95U_0dzJ9ArCj0M2dHGq0ShIQvgEU7-qOfFNlq71eF0K92PslbFFBcAfcdHZe2JftJGAqZdtED7v6t.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/E7T2oUrHiW5yHfKarhk0Rw6izgx2OfDpiJeCAOGa7s0oL6DieyFBMB28SgTmCmvKGdjPiEmjsPbeNy5KSJZaTM30AIA4oJYf3Mu9mm24NPYbMmqtuFjMnQp_SGLdEvp0.png) 
            - N̶o̶,̶ ̶i̶f̶ ̶e̶ ̶i̶s̶ ̶v̶ ̶i̶n̶ ̶v̶;̶e̶2̶v̶;̶ ̶e̶_̶2̶ ̶v̶;̶e̶2̶ ̶​̶ ̶$v; e_2$ ̶ ̶t̶h̶e̶n̶ ̶v̶'̶s̶ ̶v̶a̶l̶u̶e̶ ̶i̶s̶ ̶a̶t̶ ̶f̶i̶r̶s̶t̶ ̶i̶n̶t̶,̶ ̶b̶u̶t̶ ̶u̶p̶o̶n̶ ̶t̶h̶e̶ ̶n̶e̶x̶t̶ ̶s̶t̶e̶p̶ ̶t̶h̶e̶ ̶v̶a̶l̶u̶e̶ ̶i̶s̶ ̶n̶o̶n̶e̶ ̶  - No cant step in a section of a statement.
            - I believe type preservation does still hold, I don't see how assign1 could change that, as the type should be unchanged - and seq1 shouldn't affect the final 'return' type, as we evaluate left to right - meaning our new int value is stuck at the front.
        - 
    - 
    - 
- Data Science
    - Supervision 1 Work
        1. 
            - ```python
import numpy as np
import matplotlib.pyplot as plt

def circle_func(x):
	y = ((1 - x**2)**0.5) * np.random.choice([-1, 1], p=[.5, .5]) + np.random.uniform(-0.03, 0.03)
	return x,y

def smile_func(x):
	x = x/2
	y = x**2-0.8+ np.random.uniform(-0.03, 0.03)
	return x,y

def eye_func(x, left):
	x = x/20
	if left:
		x -= 0.4
	else:
		x += 0.4
	y = x*0+0.3 + np.random.uniform(-0.03, 0.03)
	return x,y


def rxy():
	functions = [circle_func, smile_func, lambda x: eye_func(x, True), lambda x: eye_func(x, False)]
	function = functions[np.random.choice([0,1,2,3])]
	return function(np.random.uniform(-1, 1))

results = np.concatenate([rxy() for x in range(1000)]).reshape([1000,2])
print(results)

fig,((ax_x,dummy),(ax_xy,ax_y)) = plt.subplots(2,2, figsize=(4,4), sharex='col', sharey='row', gridspec_kw=dict(height_ratios=[1,2], width_ratios=[2,1]))
dummy.remove()
ax_xy.scatter(results[:,0], results[:,1], s=3, alpha=.1)
ax_x.hist(results[:, 0], density=True, bins=60) # fill in the ???
ax_y.hist(results[:, 1], density=True, bins=60, orientation='horizontal') # fill in the ???
plt.show()
``` 
        2. 
            - density func:
                - $\int_{0}^{u}{u\cdot(1-u)du} = u^2/2 - u^3/3$ 
            - cumulative distribution function:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5RCG5z7hsBmrF-QFWJFCBf4JNmoCJWWx1qb5NumaUsGp05deuEiDNdkSuJLW2PQmSACOmx8S-k1pBEO1jmKnZGBPbRQ-EKVs2a7Oaabi-_-Z4AFpPJW26YzZLt1ZzFnt.png) 
        3. 
            - pdf = $$\frac{d}{d\theta}(\text{cdf}) = 1_{\theta \ge b_{0}} \cdot (\alpha \cdot \frac{1}{\theta}\cdot (\frac{b_{0}}{\theta})^\alpha )$$ 
            - b.) 
                - $$Pr_\Theta(\theta) = 1_{\theta \ge b_{0}} \cdot (\alpha \cdot \frac{1}{\theta}\cdot (\frac{b_{0}}{\theta})^\alpha )$$ 
                - $$Pr(x_1, x_2,...,x_n | \Theta=\theta) = \left( \frac{1}{\theta} \right)^n$$ 
                - $$Pr(\theta | x_1, x_2, ..., x_n) = 1_{\theta \ge b_{0}} \text{Pareto}(k, \alpha+n)$$ $\text{let} \ c = (\alpha + n) k^{\alpha + n}$  Then $Pr(\theta | x_1, x_2, ..., x_n) = 1_{\theta \ge b_{0}} \ \  c \ \ \frac{1}{\theta} \cdot (\frac{1}{\theta} ^{\alpha + n})$ 
            - c.)
                - $P(\Theta \le \theta) = 0.95$ ⇒ $0.95 = 1 - (\frac{k}{hi})^{(\alpha+n)}$ ⇒ $hi = (0.05)^{-\frac{1}{\alpha + n}} \cdot k$ 
        4. 
            - 
        5. 
            - $X \sim Bin(n, \theta)$  then $Pr(\theta | x=0) = (1-\theta)^n$  
            - $P(\theta | x=0) = \kappa \cdot(Pr(\theta)) \cdot (1 - \theta)^n$ 
            - $1 / \kappa = \int_0^{1/2}{\epsilon (1-\theta)^nd\theta} + \int_{1/2}^{1}{\epsilon (1-\theta)^nd\theta}$ $\rightarrow \kappa = (n+1) / \epsilon$ 
            - $P(\Theta \le 0.5 | x=0) = \kappa\int_0^{1/2}{\epsilon (1 - \theta)^nd\theta} = 1 - \left( \frac{1}{2} \right)^{n+1}$ 
            - This equals a half when n = 0, if epsilon = 0 our results would have been nonsense and the probability would be zero. 
        6. 
            - 
        - 
        - 
        - 
    - Supervision 3 Work
        -  _**Question 1:**_  We are given a dataset x1, . . . , xn which we believe is drawn from Normal(µ, σ2 ) where µ and σ are unknown.
            - a.) Find the maximum likelihood estimators µˆ and σˆ: 
$\hat\mu = \frac{1}{n} \sum_i x$ , $\hat \sigma = \frac{1}{n} \sum_i x^2 - \hat\mu^2$ 
            - b.) Find a 95% confidence interval for σˆ, using parametric resampling: ```python
 # x = [x1, x2, ...]
mean, std = np.mean(x), np.std(x) 
n = len(x)

def h(x):
	return np.std(x)

def sample():
	return np.random.normal(mean, std, n)


t = np.array([h(sample()) for x in range(10000)])

interval = np.quantile(t, [0.025, 0.975])
print(interval)
```
        -  _**Question 2:**_   
            - a.) Report a 95% confidence interval for νˆ − µˆ, using parametric sampling: ```python
x = np.array([3,1,5])
y = np.array([2,3])

null_val = np.mean(np.concatenate([x,y]))

def h(x1,y1):
	return -np.mean(x1) + np.mean(y1)

def sample():
	return np.random.poisson(null_val, size=3), np.random.poisson(null_val, size=2)

t = np.array([h(*sample()) for x in range(1000)])
interval = np.quantile(t, [0.025, 0.975])
print("Observed difference in means", np.mean(y) - np.mean(x))
print(interval)

# Observed difference in means -0.5
# [-3.          3.33333333]
```
            - b.) **The above code AND: **  ```python
t_ = np.mean(y) - np.mean(x)
print( 2 * min( np.mean(t_ <= t ) , np.mean( t_ >= t) ))

# 0.801
``` I chose two sided because the difference between the two items can be positive or negative, and whether the difference is positive or negative is important to report. We would like to know whether one chief is having a significantly better or worse impact.
            - c.) ^^Not sure about this, could we go through^^ 
        -  _**Question 3:**_ 
            - a.) ```python
import numpy as np
import pandas
import matplotlib.pyplot as plt
import sklearn.linear_model
import scipy.stats


# Load the dataset
url = 'https://www.cl.cam.ac.uk/teaching/2021/DataSci/data/climate.csv'
climate = pandas.read_csv(url)
climate = climate.loc[(climate.station=='Cambridge') & (climate.yyyy>=1985)].copy()
t = climate.yyyy + (climate.mm-1)/12
temp = (climate.tmin + climate.tmax)/2
# Fit a simple model, and plot it

π = np.pi
X = np.column_stack([np.sin(2*π*t), np.cos(2*π*t), t-2000])
model = sklearn.linear_model.LinearRegression()
model.fit(X, temp)

tnew = np.linspace(1985, 2025, (2025-1985)*12+1)
Xnew = np.column_stack([np.sin(2*π*tnew), np.cos(2*π*tnew), tnew-2000])
tempnew = model.predict(Xnew)


sigma = np.std(temp)

def sample():
	return np.random.normal(tempnew, sigma)

def h(x):
	# The increase in temp between the first and second halves of the dataset averaged
	return (np.mean(x[len(x)//2 : len(x)-1]) - np.mean(x[0: len(x)//2])) / len(x)


samples = np.array([h(sample()) for x in range(10000)])

plt.hist(samples, density=True)
plt.show()
interval = np.quantile(samples, [0.025, 0.975])
print(interval)
``` 
            - outputs: [-0.00038061  0.00329347] which equates to a temperature change of between [-0.4663143317809455, 3.971734353796922] per century.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/G_vvYKWsUWgTdYvAraIN937T7jMUPxJNw3D4J3TBmz3nNBU-JTH7auSCnNNQ5iXccjaU35iQLwfdIXLwOEKOyCo9njrktDsGFCkn_rq7S1kOekWhRvvWFM0VGx6whilm.png) 
            - 
            - b.) ```python
import numpy as np
import pandas
import matplotlib.pyplot as plt
import sklearn.linear_model
import scipy.stats


# Load the dataset
url = 'https://www.cl.cam.ac.uk/teaching/2021/DataSci/data/climate.csv'
climate = pandas.read_csv(url)
climate = climate.loc[(climate.station=='Cambridge') & (climate.yyyy>=1985)].copy()
t = climate.yyyy + (climate.mm-1)/12
temp = (climate.tmin + climate.tmax)/2


# Fit a simple model, and plot it
π = np.pi

tnew = np.linspace(1985, 2025, (2025-1985)*12+1)

# Null hypothesis that the dates are the same, 
# so one variable to be fit is between 2010-2020 OR 1985-1990

datesTnew = ((1985 <= tnew)*(tnew < 1990)+(2010 <= tnew)*(tnew < 2020), (1990 <= tnew)*(tnew< 2000),
             (2000 <= tnew)* (tnew< 2010), (2020 <= tnew)*(tnew <= 2025))

Xnew = np.column_stack([np.sin(2*π*tnew), np.cos(2*π*tnew), *datesTnew])
tempnew = model.predict(Xnew)
print(model.coef_)
## Result : [-1.06969483 -6.55184889  0.61248728  0.61731992  1.01231992  1.77490753] 

sigma = np.std(temp)

def sample():
    return np.random.normal(tempnew, sigma)

def h(x):
    # The difference between the 1980s and 2010s
    year80s = x[0  * 12:   5 * 12]
    year10s = x[25 * 12 : 35 * 12]
    
    inc80s = ( np.mean( np.split(year80s, 2)[0] ) - np.mean( np.split(year80s, 2)[1] ) ) / len(year80s)
    inc10s = ( np.mean( np.split(year10s, 2)[0] ) - np.mean( np.split(year10s, 2)[1] ) ) / len(year10s)
    return inc10s - inc80s

samples = np.array([h(sample()) for x in range(10000)])

plt.hist(samples, density=True)
plt.show()
interval = np.quantile(samples, [0.025, 0.975])
print([x for x in interval])

real_diff = h(temp)
print(2 * np.min([ np.mean( samples <= real_diff ), np.mean( samples >= real_diff ) ] ))

# result is 0.3566
# 0.3566 > 0.025 - so we accept the null hypothesis
```
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/cghRRf1V5S_SBfXGXm3z2enSqJJTBVaVsGimVxqxyFDgShejwOGxpplY3p3TJAtCtYy7roFLeMVgiQ3oZMQJtU-ryvqcMICADe7Yj6ieR2eAocYi6qvgJtE1YDPep0ON.png) 
        - 
        -  _**Question 4:**_ 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hYVpdF3g_616zJwKqv979ygzaZOcIulZKc00b9rLC1Q0XfK95UD5FAD1jEM8M_9oY7E_XvZkQZKxynieI8yBYM9FnhwdJmsbCM5OCRB0GyuceMWn4bfnS6JPZB7V2arN.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/buFolL0zHPl78VhEl4Phop6IY4uJk4Ac9lUSJKuUuRLbwKL6oxwf89zKdcsPEMmuA_3amLUO60VeEHNEGdCBB8Fcqfp8paXwlMQr9LX1_UHtiPrQzZ7KFNtbM45rSxB-.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/DXf6ni8P8txwwpykxN7UTe8MH86jgdI5DhYhIQitVMSubEMUOyjpPjACyDAXG2qsnmc716I4m-6ywj9P94LEnV8H_zpdZaCq-OsM5dQBRTzlGg42id-QSJqeAMCfPEqy.png) 
        - 
        -  _**Question 5:**_  
            - Consider that the value of theta (success) that makes a run of failures most likely is the lowest possible value, in this case 0.5. 
            - $$(1/2)^n \le 0.05$$$$n \ge \ln(0.05)/\ln(0.5) = 4.32...$$
$$n\ge5$$ 
        -  _**Question 6:**_ 
            - A recent paper Historical language records reveal a surge of cognitive distortions in recent decades by Bollen et al., [https://www.pnas.org/content/118/30/e2102061118.full,](https://www.pnas.org/content/118/30/e2102061118.full,) claims that depression-linked turns of phrase have become more prevalent in recent decades. This paper reports both confidence intervals and null hypotheses. Explain how it is computes them, in particular (1) the readout statistic, (2) the sampling method.
            - The readout statistic is the number of n-grams each year that were labelled as indicative of cognitive distortion, "normalized" by dividing by the number of books published each year.
            - The sampling method was examining millions of books within the Google Books database and calculating the readout statistic. When generating the Null data that formed the null hypothesis they generated 10000 sets of 241 randomly chosen n-grams for each year.
            - The null hypothesis would then be that the readout statistic of the values sampled from Google books is the same as the Null data.
            - Confidence intervals were calculated by generating 10000 different random samples of CDS engrams from the google database for each year - the interval is then between the lowest and highest percentage of CDS detected from those 10000 random samples.
            - longitudinal prevalence of hundreds of short sequences of one to five words (n-grams), labeled cognitive distortion schemata (CDS), that were designed by a team of CBT experts, computational linguists, and bilingual native speakers and externally validated by a panel of CBT experts  
            - To account for changes in publication volume, for each CDS n-gram we define its prevalence in a given year as the number of times it occurred that year in the Google Books data divided by the total volume published  
            - against a null model of 10,000 sets of 241 randomly chosen n-gram  
            - sets of random n-grams were sampled from all n-grams in the respective English, Spanish, and German Google n-gram corpus such that they have the same number of 1- to 5-gram  
    - 
    - 
- Programming in C & C++
    - 
    - Supervision 3
        1. ** 2015 Paper 3 Question 1:**   
            - a.) It encourages the compiler to immediately evaluate the function inline. However, it gives no guarantee that the compiler will actually do that. Can waste space if an inline function is reused many times, less space efficient than creating a stand alone function to be run.
            - b.) ```cpp
 #include <tgmath.h>
 int receive_int() {
    unsigned int result = 0;
    for (int i=31; i>=0; i-- ) {
        result += receive_bit() * pow(2, i);
    }
    return result;
}
```
            - c.) ```cpp
template <class T, int len>
T receive(void) {
    T result = 0;
    for (int i = 0; i < len; i++) {
        T bit = receive_bit();
        result += bit * pow(2, i);
    }
    return result;
};

ans = receive<short, 8>;
ans = receive<unsigned long,32>;
``` d.) 
                - Line 6: buf is a value on the stack, thus the value returned will be lost once the function returns.
                - Line 4: fuel is never initialized
                - If Message is not 1 or 2 the function will not return a value, when it's supposed to return a char
                - Line 5: THRUST will overrun buf, as buf doesn not have space for the /0 that ends the string
        2. **2015 Paper 3 Question 2:**
            - a.) The differences between C pointers and C++ references. [Hint: Consider issues of syntax, initialisation, mutation and safety in your answer.] [5 marks]
                - Pointers are created using the * syntax, while references use the & syntax: 
                - ```cpp
int x[] = {1,3,5,7};
int* ptr = &x[0];
int& ref = x[0]; 
```
                - References act as aliases to the data item in questions, meaning they can only affect the value they are initialized to reference - references cannot be changed to reference a different data item. On the other hand pointers act as an address to the data item, an address which can be changed to point to somewhere else in memory:  
                - ```cpp
ptr++;
printf("%i ", *ptr); // outputs 3 as ptr is now pointing to the second array item
ref++;
printf("%i ", ref); // outputs 2, as this incremented the 1st array item 
```
                - Where references point to is an immutable feature, because can only change the value they point to they are much more safe than pointers - arithmetic of pointers can be done in error, resulting in the changing of arbitrary bits in memory.
                - ```cpp
ptr+=10; // pointer now points to an arbitrary place in memory
printf("%i ", *ptr); // unkown output
ref+=10; // Increments the 1st array value by 10
printf("%i ", ref); // outputs 12 
```
            - b.) extern "C" {} tells the compiler that the enclosed code should be linked as C, not C++. Declaration and definitions can then be grouped inside the scope. This has the limitation when combined with C++ name mangling, i.e. C++ uses name mangling to allow for default arguments and overloading for functions - this gives each possible combination its own symbol name. If the C function name clashes with an overloaded function, a compile time error will occur. 
            - c.) Implementation defined behaviour means the creators of the compiler have documented the behaviour of the compiler when facing certain incorrect code, and the compiler will adhere to that behaviour. Unspecified behaviour means the C compiler can do whatever it wants and there is no specified behaviour. An example of implementation defined behaviour is the size of all data types char, short int etc. Examples of unspecified behaviour include how inline functions are handled, the order that operators like ++i i++ are evaluated when combined. ^^This loosely specified behaviour allows for more freedom for optimizations by the compiler.^^ - not sure about this
            - d.) Interactive debuggers give you a large range of tools for fast debugging, including stopping the program if assert conditions are not met, get the value of variables during running, stepping through the program, getting the trace of function calls.  A breakpoint gives the line of code where application will pause, a watchpoint allows you to set a data item such that the program will pause if it changes. The symbol table keeps track of the location of variables and stack offset for function callstack inspection.   
        3. **2013 Paper 3 Question 3:** 
            - b.) ```cpp
 class T {
    const int n;
    public:
    T (int n=0) : n(n) {
        printf("%i", n);
    }

    virtual ~T () {
        printf("%i", n);
    }
};
```
            - Fields and constructors cannot have the virtual tag. Virtual destructors are useful for when a class is derived from, and when the static class varies from the dynamic class with a non-virtual destructor undefined behaviour can occur. 
            - ii.)   T Objects are allocated to the heap using new, and removed using delete ```cpp
 T value = new T(1);
 delete value;
```Delete runs the destructor and then deallocates from the heap. New allocates to the heap and runs the constructor. Stack constructors are run when a scope is entered, and destructors are run on exit. Static store is used by writing static C x. Virtual is essential for destructors when a class is derived from. Try finally ensures the finally block is always run at the end of a block, similarly stack allocated objects run their destructors when they go out of scope.
        4. **2012 Paper 3 Question 3:**
            - a.) 
                - i.) What is the difference between a local and global variable in C? (Consider variable scope, storage and initialisation.)
                    - A local variable is one who can only be accessed within the current scope, after the end of the scope the allocated memory is removed. 
                    - A global variable is one who can be accessed anywhere in the program, they are initialized to zero and consume storage throughout the program.
                - ii.) What are the properties of a static member variable in a C++ class?   
                    - A static member variable only has one instance of the variable, rather than one instance per variable. 
            - b.) 
                - i.) The section of memory the pointer addresses can be changed using pointer arithmetic: ```cpp
 int * p1, p2; // integer and int pointer declared not two int pointers
 
 int sam = *p1; // pointer uninitialized 
```
                - ii.) A pointer can be used to point at an array, and you can use array syntax with pointers - however a pointer is a variable (you can reassign it), while an array name is not.
            - d.) 
                - i.) void * can point to anything, any data item. ```cpp
void sort(void *arr, int nitems, int size, bool (*compar)(const void *, const void*));
```
                - ii.) void * has no type checking in C, C++ helps this using template functions:  ```cpp
template <class myType> 
myType GetMax (myType a, myType b) {  
	return (a>b?a:b); 
}  
```
            - e.)
                - i.) We can "copy" instances using simple assignment, meaning all the values are copied - however if some of the values are pointers this may not be the desired behaviour. Thus, a copy constructor could solve that problem by properly dealing with those items.
                - ```cpp
Dog::Dog(const Dog& old_dog) {
	bark = old_dog.bark;
	name = new char[5];
}
``` ii.) 
As in i.) when one class instance is assigned to another, variables are overwritten and this behaviour may not always be desired.
```cpp
Test& operator = (const Test &t) {
    cout<<"Assignment operator called "<<endl;
    return *this;
} 
``` 
        5. **2009 Paper 3 Question 1:**  
            - e.) Pointer arithmetic is the manipulation of the pointer address, the main (good) use is to manipulate an array using pointers - however there is no bounds checking so precautions must be taken: 
            - ```cpp
int sam[3] = {1,2,3};
int *ptr = sam;

printf("%i", *ptr); // print 1
printf("%i", *(ptr+2)); // prints 3
``` 
            - d.) ```cpp
class dog {

    int age;
    const char* name;
    public:
    
    dog (int age, const char *name) : age(age), name(name) {
        printf("Constructor run");
    }

    void bark(char* msg) {
        printf("%s", msg);
    }

};

int main() {
    const char * name = "Apollo";
    dog* Apollo = new dog(5, name);
    Apollo->bark(name);
    return 1;
}
``` 
            - c.)  New and delete are features of the language that call an objects constructor or destructor - malloc() and free() are functions, and are not features of the language but are provided from a library. Malloc and free manipulate a large data structure (a heap) to allocate data for variables, while new and delete need not use this external data structure.
            - f.)   Catches take a single argument and allow for the escape of a code block to a predefined location if an error occurs```javascript
int main () {   
	try {     
		throw 10;   
	}   
	catch (int e) {     
		cout << "Exception number " << e << '\n';   
	}   
	return 0; 
}  
```
        - 
    - Supervision 2
        1. Arenas are a useful tool for amortizing allocated memory discovery, and have the side effect of potentially more efficient cache usage through the introduction of an array for item storage. I would use one when I have a data structure that may contain cyclic sections or sections where a given item is pointed to twice from another item (DAG) - in which case traversing the structure myself at the end becomes complex & error prone, and can result in memory leaks if not carefully thought through. Arenas trade-off complexity with memory usage, as we must allocate a large array of items (the size being the maximum number of items the program could use) to eventually deallocate. An example control flow would be creating a graph, every time I create a node I add it to the arena (wherein we already specified the max possible number of items) incrementing the current value in the arena - then when finished with my data structure I free the arenas elements array and free the arena itself.
        2. In mark and sweep garbage collection we store an list of "root" nodes (items that are alive, and we'd like to keep alive) and an list all nodes (these may be the lists). In the mark phase we iterate through all the root nodes, and mark all nodes reachable from each root node (i.e. depth first exploration, stopping when we hit a marked node). Then in the sweep phase, we step through our list of all the nodes and free any unmarked nodes and unmark any marked ones. When we next run the garbage collector the nodes still alive will form our roots.
            - a.) A conservative garbage collector is one who scans the execution stack, and upon finding a value that **looks like **a pointer to the heap - if there is an object at that pointer, the collector must mark it. This conservative estimation is that this is a pointer to the heap and not (say) an integer value. This is necessary many reasons, including:
                1. C lets you easily convert from values to pointers, so we can't know if in future the programmer will use that int as a pointer to an item in heap memory.
                2. The garbage collector should **never **alter the execution of the code, and storing extra blocks of useless memory is better than deleting a useful block. Especially considering that if the value on the call stack is not a pointer, it is likely to change at which point the memory can be freed. 
            - b.) Garbage collection solves the issue of cyclic data structures that reference counting cannot - under reference counting, two cyclic items pointing to each other can maintain a pointer count of 1 each even if there is no way of accessing either item (all pointers to those items has been removed) - thus these marooned items cant be freed resulting in a memory leak. Garbage collection stores all the nodes, and will find these items to be unmarked in the sweep phase - thus they will be freed.
        3. Show how a struct of arrays performs better than an array of structs when traversing the elements of the form ```c
struct entry { int id; double val; };
typedef struct entry Entry;

struct struct_of_arrays {
	int *id_array;
	double *val_array;
};

Entry *array_of_struct = malloc(sizeof(Entry) * NUM_ITEMS);

struct struct_of_arrays Struct_of_Arrays;
Struct_of_Arrays -> id_array = malloc(sizeof(int) * NUM_ITEMS);
Struct_of_Arrays -> val_array = malloc(sizeof(double) * NUM_ITEMS);
```
            - For simply iterating through the array of struct, we have an int of size 4 bytes and a double of size 8 bytes - this will then be padded to size 16 bytes. So we can fit 4 entries into a single cache line before getting a miss (whether we're storing an int & a double or only an int/double) - alternatively if we iterate through the id_array and then the val_array, we first have 4 byte ints to iterate through - resulting in 16 items before getting a cache miss - and secondly 8 byte items, resulting in 8 items before a cache miss. 
            - $\text{array of structs}: \frac{n}{4} \text{ cache misses}$ 
            - $\text{struct of arrays}: \frac{n}{8} + \frac{n}{16} = \frac{3n}{16} \text{ cache misses}$ 
            - So as $\frac{3n}{16} < \frac{n}{4} = \frac{4n}{16}$ we'll have less cache misses in our second solution, and as cache misses are hundreds of times more costly than arithmetic operations - our struct of arrays will perform better.
        4. Describe loop blocking and when it's useful:
            - Loop blocking is a technique for deconstructing accesses of large contiguous data structures into smaller chunks which can be stored in cache lines. The first access of each chunk will result in a cache miss, but subsequent accesses wont. In short it attempts to introduce spatial locality of data, for fast accesses.
            - The technique is useful when a given array access scheme jumps around a lot, and does not return to a chunk of memory for a long time (at which point the cache line can have been cleared). Alternatively, your method of jumping could cause conflicts within the cache and force eviction of prior cached lines. In general, loop blocking is useful for items with poor spatial locality.
        5. [1998 Paper 6 Question 6](../y1998p6q6.pdf.md)
            - a.)
                - Memory corruption 
                - Hard to read programs 
                - Security liability
            - 
                - Low level control
                - 
            - b.)
                - Forgetting to deallocate sensitive data?
                - Memory leaks
            - 
        6. [2010 Paper 3 Question 6](../y2010p3q6.pdf.md) 
            - a) 
                - ```c
typedef struct node* Node;
struct node {
    int value;
    Node xor_pointer;
};
Node head;
Node xor_addresses(Node a, Node b) {
    return (Node) ((long long)a ^ (long long)b);
}
void add_value(int value) {
    Node new_node = malloc(sizeof(Node));
    new_node->value = value;
    new_node->xor_pointer = head;
    head->xor_pointer = xor_addresses(head->xor_pointer, new_node);
    head = new_node;
}
Node get_next(Node prev, Node current) {
    return xor_addresses(prev, current->xor_pointer);
}
void traverse() {
    if (head==NULL) return;
    Node current = head->xor_pointer;
    Node prev = head;
    printf("%i  ", head->value);

    while (current != NULL) {
        printf("%i  ", current->value);
        if (current->xor_pointer == 0)
            break;
        Node temp_prev = current;
        current = get_next(prev, current);
        prev = temp_prev;
    } 
    printf("\n");
}

void delete(int value_to_del) {
    if (head==NULL) return;
    Node current = head->xor_pointer;
    Node prev = head;
    
    if (head->value == value_to_del) {
        if (current->xor_pointer != 0) {
            current->xor_pointer = get_next(head, current);
        }
        free(head);
        return;
    }

    while (current != NULL) {
        if (current->xor_pointer == 0) {
            if (current -> value == value_to_del) {
                prev->xor_pointer = 0;
                free(current);
                return;
            }
        }
        if (current -> value == value_to_del) {

            Node next = get_next(prev, current);
            Node prev_prev = xor_addresses(prev->xor_pointer, current);
            prev->xor_pointer = xor_addresses(prev_prev, next);
            Node next_next = xor_addresses(current, next->xor_pointer);
            next->xor_pointer = xor_addresses(next_next, prev);
            free(current);
            return;
        }
        Node temp_prev = current;
        current = get_next(prev, current);
        prev = temp_prev;
    } 
    printf("Node not found to delete\n");
}

``` 
                - b.)    Comment on this form of linked list. Consider the comparative speed, memory overheads, maintenance and other advantages or disadvantages of the XOR doubly-linked list approach when compared with an approach that stores both previous and next pointers  
                - 
                - In this form of doubly-linked list, each node takes up less space - while before they store two pointers and a payload now they store only one , resulting in less overall memory usage of the new data structure. (16 bytes vs 24) For large lists, one list being two thirds the size of another while accomplishing the same thing could be important.
                - However, if you want to hold specific nodes to edit later - you need to hold that node **and **the previous node if you want to be able to traverse from your node and edit preceding nodes - this makes it harder to maintain, as management of individual nodes is more complex. Additionally, traversing the list is more expensive in the XOR doubly-linked list as we must compute an XOR every time (which is admittedly a relatively cheap operation). 
                - You could make the argument the XOR doubly-linked list is more secure, as you can pass your node value to another function safe in the knowledge it cannot destroy any other of your nodes as it will have no way of traversing to them. 
        7. [1996 Paper 5 Question 5](../y1996p5q5.pdf.md) :
            - a.) Pre-processor macros and conditional compilation:
                - ```c
#define BIT64 1

#if BIT64==0
#define BIG_INT (64*1024*1024)
printf("%i", BIG_INT);
#else
#define BIG_INT (1024*1024)
#endif

// This defines a macro BIT64 set to 1, and chooses different definitions of BIG_INT depending on the value of said macro
``` 
            - b.)
                - ```c
char t = 'a';
char *p2 = &t;
int *res = (int*) p2;

// We created t, which holds the a character. Then we instantiated a char pointer to t. Then we created an int pointer res, and cast the char pointer to an int pointer.
``` 
            - c.)
                - ```c
// This is a single line comment
/*
	This is a multi-line comment
	!!!
*/
``` 
            - f.)
                - ```c
jmp_buf current_env;    
int sam = 0;
int val = setjmp(current_env);
printf("%i\n", val);
longjmp(current_env, sam++);

// This code infinitely loops printing 0, 1,2,3...
// setjmp copies the PC and stack pointer into the jmp_buf current_env, then we print sam and finally we longjmp back up to int val = setjmp(current_env); val will then be overwritten with the value of sam+!
```
            - g.)
                - ```c
unsigned int sam = 3;
switch (sam) {
    
    case 0:
        printf("Sam less than 2");
        break;
    case 1:
        printf("Sam less than 2");
        break;
    default:
        printf("Sam more than 2 ;( ");
        break;
}
// if the unsigned int sam is 0 or 1 we print "Sam less than 2", otherwise we print "Sam more than 2 ;( ".
// In this case we'll print the latter, as sam is 3. Each constant case is checked against the value in the switch()  braces and a case is selected. 
// The breaks ensure the default case doesn't always run.
``` 
        8. [2014 Paper 3 Question 3](../y2014p3q3.pdf.md)   :
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zB0WVJroIQK0RkHQzho8zvjIfCkmXtlmIL3jLz1ZOLw0MoLHOFDLFaEUh1PaKLG-bc64iVhJIajoLCoCy2b996jK4MoffBw6nDR-nU2P_UYxEe8qrzNow4mU46s9QqRk.png)
            - ```c
char revbits(char to_reverse) {
    int working = (int) to_reverse;
	int result;
    for (int exp=7; exp>-1; exp--) {
        if (working > 1<<exp) {
            working -= 1<<exp;
            result += 1<<(7-exp);
        }
    }
    return (char) result;
}
``` ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4EncOulylcP3ibS2i2YvFWOnzfLIxKEKnPaaiubqq7GDBEapF3kAEAU-uD7XBSla7UjDwumB_HkKu4FrEu1z6Zt9XdJ1EG6EnsNg07bjh9XbeYN6QInE3JQbCpm6AdPo.png)
            - ```c
void revbytes(char *ls, int num_bytes) {
    int left = 0, right = num_bytes-1;
    while (left <= right) {
        if (left == right) {
            ls[left] = revbits(ls[left]);
            break;
        } else {
            char temp = ls[left];
            ls[left] = revbits(ls[right]);
            ls[right] = revbits(temp);
            left++, right--;
        }
    }
}
``` ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5CvOkCE8ymJEeAFOsAjUVCQ44LCbCUtbJYWKdAgIN0OS8u2Wsy8ILFqk3zp-DPTbnJzLqlTcGVHd5dTnEuRc-4ql_tRA0umkx1Z9W4pm4vhHkDiAUYf7cgRiqiUI5SfJ.png)
                - The problem here is the file is left open after the result is returned, we should change the block to:
                - ```c
if (...) fclose(p); return ERR_MALFORMED;
``` 
        9. [1995 Paper 5 Question 5](../y1995p5q5.pdf.md)  
            - This is an attempt at an implementation of quicksort.
            - ```c
typedef unsigned long int thing;
// Bad unilluminating variable name
``````c
 #define swap(p,q) v = p; p = q; q = v;
 // the type of v is not defined, this will result in an error.
```
            - ```c
		/**********************
int i, j; * Declare variobles! *
thing v; **********************/
// int i,j and thing v will be commented out here. Also incorrect spelling of variables
``` 
            - ```c
i = left, j = write;
// i & j are not given types
``` 
            - ```c
 while (a[++i] < v};
 // Wrong ending bracket, should be  while (a[++i] < v) 
```
            - ```c
while (a[++i] < v};	
while (a[--j] >= v);
if (i < j) swap(a[i], a[j]);
else break;

// I believe what they intended was:
while (a[++i] < v} {
	while (a[--j] >= v) {
		if (i < j) swap(a[i], a[j]);
		else break;
	}
}

// What they achieved simply repeatedly increments i until a[i] >= v, and repeatedly increments j until a[j]<v and then swaps a[i] & a[j]

// ALSO these should be a[i++]... and a[j--]... . Otherwise we dont test the initial values of i & j.
``` ```c
 write would more sensibly be named right
```
        - 
        - Questions from lectures:
            - In the lecture on reference counting, the lecturer builds a binary tree using:
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/crzic95YRyiryiMHGIrmxmqkDggUe_2KbJnaftk-5YUTWrhbDsP0rUPfufcy8XmrHUAHD9C9DPDpkqALR3EPC4UDY5wVP-WUnHm3WYEhxJX-Ea59BIvdWIrXP6XKJJO9.png)
            - But wouldn't this mean, If I edit a value on the tree (other than the root) I'm actually editing two? Given that both left & right point to the same node. Sure the tree is build, but it can't be used.
        - 
        - 
        - $$\text{speedup}(n) = n(1-B)+B$$ 
    - Supervision 1
        1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5x-kpFtSmurzNUmXPlR8GMTKt44S-pGI_uXQn-loC5FTlBbwH2KnTOZb_8vHNtz5Vc-B7ENcAojGyI83lmpHfPa1uVKKFQiiso5afgZZSAndShPRGx_1n1jctwLtBL13.png) 
            - 'a' is a char while "a" forms a string literal - e.g. an array of chars terminated with a null terminator \0.
        2. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Y7TUSDPht8rMMmjwyibGk-4zzDDtqFry6U0sB0wSGHN80olxqx8IhSL4w7q1B7AwdfL5s1F1G8LzJ8q7-K3oTPmuVAZMovFSPG6aKrPGL5mZ2dLldl2lZEglvvYQf7oj.png) 
            - Yes, it will terminate when j equals 5 (e.g. the 5th ASCII character) as long as the two chars were initialized to 0 (which is not guaranteed). This is because you can store integer values in chars, ranging from -128 to 127 for unsigned chars.
        3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dpZ64aPO1RH5e4EsS1UpUmsF6S1j8sYlwLx6vDShfHV1sW0kweO6ow9QUln0VP0NK6dzaTv2HQGT_siYVBxZQugXD5dBNPaOHMVYXAvK5T_8rvmGEmV0otOOn9oYFKxz.png)
            - ```c
#define SWAP(t,x,y) {\
    t temp = x;\
    x = y;\
    y = temp;\
}
```
        4. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/wnEQh3sjj-ggBtFu8O9dNmiI2bL6F-ycmM394KL46Q4W-zJ1YH1L8zb5AuhRQgO0yH7tmlkZoS4jhEaKhz0CZSQcIHphGvCgeGCD5LGCuKrC4Cx7S9oxORSzpGNZE18s.png) 
            - No, the i++ will be evaluated twice - meaning the x in the second line of the macro will differ from the x in the third line of the macro (unless the values of v[i+1] and v[i+2] are the same). Similarly, if f(x) changes when it's called twice we will be getting different indices of w.
        5. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/29dC0HQ66WGsn2vo69u4gNIJZt9N4FnfT5RwFJfM_G3BW7d5EhdsZOHsXWNjWacNu5zL96DZhIyb0C6NbtTEcqJ-TlSKnzxtwO9zn0fVU-ErJJFrKkkTJH3OY9HJb7no.png) 
            - ```c
#define SWAP(t,x,y) {\
    x = x - y;\
    y = y + x;\
    x = -x + y;\
}
``` 
        6. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/VjH7bsEoeEXOb-ZAO4st3yXVKrJqqTgta_w8kMyod9Oe22Y2SY3BN4_UwFKmCzzzfdD_XCnzJG4-JQsuy9qVOjbjp3QFCvNPX9JwYgL0iIb2bJSPIhuJLUjEDjsW6djw.png)
            - p[-2] means the value two items before the pointer, this is legal if p is a pointer inside an array - this works because arrays allocate a contiguous block of memory which we can simply step along (pointer-wise) to reach earlier array-items.
        7. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/6xCzQuVGM16QjzvbI4VY4CytzsorrFvjZX1148C4R1ovPU0H4YfSVTLPf1cagxhM-sD31wpTXg6cKaq74aQ609n_mIrRaPIb0Yvmv8tjBgN0IUPrbDjxPksgy8rh1VM-.png)  
            - ```c
char *strfind(const char *to_find, const char *to_search) {

    for (int i=0; i <= strlen(to_search) - strlen(to_find); i++ ) {
        int bookmark = 0;
        while (to_search[i+bookmark] == to_find[bookmark]) {
            if (bookmark == strlen(to_find)-1) {
                return to_search[i];
            }
            bookmark++;
        }
    }

    return NULL;
}
``` 
        8. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/GtHkEKbpOG6jIjweOng_l6W05H7Yu9StIWUwwxs9dLB2QzAVtBTakVMQh-pHkARbLFo5t3z56QsppajKkhummkk_929JjfaKqROSQEgcZnq0Z_E6z2HzmF_wMr1mqUGD.png) 
            - A const pointer to an int is a pointer that cannot be changed, e.g. it will always point to that integer. However, the integer value itself can be changed. A pointer to a const int means the pointer can be changed to point at something else but the integer value cannot be changed. For a const pointer to a const int, neither the pointer nor the integer value can change.
        9. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ux0pai4I1dl1vDxBhD-cTy9Pz5Ne3eDRwJRRZ6_oW7PPjGjn5gxRXK5Yci7-xFVq4OFPnbgim5O5YHtj-Atp0MF37r5LXuplWnJQLl4xKYwVvp2RaesqucxNl1jgu8zW.png)
            - You could pass the values as const:
            - ```c
int adds_wont_change(const int *x, const int *y) {
    return *x+*y;
}
``` However, this is only an indication not a promise - the function still has it within its power to alter the arguments using casts.
        10. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/q7tzntYJoJxSzhSjxKKL5xo7tQqMM2aUb8ggmcPB4hgSru1O59WOwTIIP62lL9UZ0YPkGiR0WsTifUx0OSi5me7cNjbveENoAqi5HehC-Vkt1tGajaBGdTSkVhekzIGE.png)
            - ```c
char* read_a_file(char input_filename[]) {
    FILE *file;
    file = fopen(input_filename, "r");
    char *string = malloc(1001);
    int memory_len = 1000;
    int currently_used = 0;
    if (file) {

        char c;
        while ((c = getc(file)) != EOF) {
            if (currently_used >= memory_len) {
                memory_len += 1000;
                string = realloc(string, memory_len);
            }
            string[currently_used] = c;
            currently_used++;
        }
        string[currently_used] = '\0';

    }

    fclose(file);
    return string;
}
``` 
        11. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/0P3QCnLO7m_QReMJWnZiOuxdyR3x8rUtd4bSxrgQch_t8UEhDy3_iGE_cLCbN7043bbQXt9NcOorpBdzmfdQnEzNhkW0RsMTM0Ltx9cSEdIhb1jvO9vaDtXgTKXoCGka.png)
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gcBE6wQaCcIKAs4I7o-7BUREOglWeWiNw8BVM06fB5iiiNPfsSRYKNJn0vki2qk-RDt2nyizBGi96ckZmwg_rQFMd10Tci3VUG2wwnunH84ZH-_MHy6VY6QWxUhE4njR.png)
            - Func1 can pass the pointer to the array to bar as the array still exists while bar runs, however when Func1 attempts to return the pointer to the array it's memory on the stack will be deallocated and thus any local variables will be lost and the values the pointer points to will be undefined - that is it's very possible they will be overwritten.
        12. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/KmKDW7D5NUYnv6HW7bY0Ut9L2F_PSp9sxF8ykkzky4_dUrWqcETQTVvt38Ziv905iqB3iSvV7SQEiPUOhrVvgJ79DOcg_jc1y26c4jvSACgavfpB3Sdz3ZP4AHY3UU-C.png)
            - Declaration simply tells the compiler a variable with the given name is going to be defined at some point, while definition allocates an area of memory for the variable. 
        13. 
            - a.) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BlbZtBHf-NMCqx0Ni45FvW9jsJN0z5SnOn0pjG_FusfpndxTwr2s-jl7bfzlokLtRs-Q0rR3NqUjvoXWEm5YZkOonm8F1twD90e2am_nDGl_2sn6oatalYCCy3Zahj_l.png) 
            - **i is the integer value 78 0c 00 00 - which is  c78 which is 8 + 7*16 + 12 * 256 = 3192
            - p⇒c[2] is 62 in hex = 6*16 + 2 - slightly confused by this one, how does the compiler know to move 2 bytes along (as if its working with a char) rather than 9 bytes along (as if it was working with a struct i2c)
            - &(*pps)[1] is 0x18 + 2 = 16+8+2 = 26 (we move 2 forwards because we're dealingiwth a short)
            - ++p⇒i is 3192 + 1 = 3193 
            - 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/01AJtT87kPJuaTX5C5XZt2fkDMlszM_KcOj76VYkPP3spld9TxWz8igbTte2mVcT__CsI1CFlFlr5dQEdpgf-iLHbBo6NlIEVf1o_opvopjYa6F9XEK7M8kOF47i33A5.png)
                - First we cast our manager pointer to an employee pointer, however when we call wage(e) it sill uses the wage calculating function wage_man as the address not wage_em (we never changed the function being pointed to in the cast) - this then casts our pointer back to a manager pointer and calculates 40*10 + 20 = 420.
        14. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/8zVLbpTXRupf0NULVKpgctjp9VkjS4ZcHNDQLuTRUyCGgd-edbhLPclwFXnuh2uXkjhKEDkIJdy5lWAaQEGJWZsfd_psK0fXIA_-BxK-hqwe3y9Ljza6RhcTgKYN287h.png)
                - ```c
#define CONCAT(a, b) (a b)
```
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tic3LFyhReYVg9QlQVNVKS7tIwEUZBzjUdDYyiQSwuZ9_n2oEAijrte48htdQ-JcRmPa7VhPCys-1hnYCqOysIGcx4ATPZnLFITqbksPDrIto3T51OM49qsvJWNfTpJj.png)
                - Line 3 would not work, as CONCAT only works by leveraging the fact that string literals next to each other get concatenated in c - e.g. "a" "b" ⇒ "ab". All CONCAT does is paste the values next to each other and let the language do the rest - however CONCAT(b, a) will result in CONCAT("UoCCL", a) and the compiler cannot simply infer the value of a to combine the strings (not a string literal). 
                - Line 4 would not work, as j is not a pointer and you are thus taking the integer value of the pointer that concat(a,b) returns. 
                - concat(a,b) allocates memory on the heap and creates a list of chars, while CONCAT simply places two string literals next to each other (uses stack memory). concat(a,b) returns a pointer to the char array while CONCAT(a,b) will evaluate to the combined string literals. 
        15. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Yc7pDYou5sDFsk8G-vXRMbYZJZkvIvoPnxYzVJzVgAFYuEB1gHaD_VDxY8yvyAernjZfJxRStzCKWnlxhKLebEBiAt38UsEs5HBe0iDRIrJeeAJE7wnMXcHI_ZDczi3L.png)
                - 500 bytes: (4 + 1 bytes) * 100. sizeof(struct Elem) =  5 bytes. long is 32 bits - compiler supports unaligned access, unlike all below.
                - 800 bytes: 32 bit machine, the long is 4 bytes, char is 1 byte. sizeof(struct Elem) =  8 bytes - but as 32 bit machine have to use two 4 byte words. Resulting in 100 * (4 + 4) = 800. 
                - 1200 bytes:  ^^48 bit machine, the long is 6 bytes, char is 1 byte, sizeof(struct Elem) =  12 bytes - but as 48 bit machine have to use two 4 byte words. Resulting in 100 * (6 + 6) = 1200. ^^ - possible answer but more likely: long 64 bits but aligned to 32 bits - 4+4+4 = 12
                - 1600 bytes: 64 bit machine, the long is 8 bytes, char is 1 byte sizeof(struct Elem) =  16 bytes- but as 64 bit machine have to use two 8 byte words. Resulting in 100 * (8 + 8) = 1600. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Ep4ntJAbb4n94rCUys5-sCXlO1A_qHTJLLNhp1VaSOwwGa6LU1mKBgnyYGPDlAocg7j39QT7M7vUoPh_zTSCQKRoMdoaB5ne8E74h4aC1Mc6_P7-HdZsak0E_be6VYwQ.png) 
                - The fundamental changed is converting the file that was created by a compiler using unaligned access to one that does not support unaligned access (no need for the added complexity when memory so abundant).  Also assumed little-endian.
                - ```c
struct Elem { signed long val; char flags; } v[NITEMS];
char temp[5*NITEMS]; // Each byte in the 5 byte line is going to become it's own item
fread(file, 1, size_of(temp), temp); // First we read the file and get every byte as a char value in our temp array
for (int i; i<size_of(result); i++) {
	
	v[i].val = temp[5*i] | temp[5*i+1]<<8 | temp[5*i+2]<<16 | temp[5*i+3]<<24; // This line combines them using bitwise ors - consider 00001010 | 1010000, combines the values as the zeroes are ignored
	v[i].flags = temp[5*i+4]; // last value is an actual char as we want it
}

``` We could simply have a flag to compute this for or not depending on if we're using this outdated format or not.
        - 
    -  _**Lecture 1**_ 
        - Primitive Types in C ↓ 
            - What are the three primitive types?↔Numbers, Characters and pointers
            - Are there primitives of composite types in C?↔NO
        - The **Stack **and **static locals** {{are built in}}, the **heap **is implemented {{by a library}}. 
        - Sizing of various types ↓ 
            1. Char→≥8 bits
            2. Int→≥16 bits
            3. Float→Single precision
            4. Double→Double precision
        - Type operators meaning ↓ 
            1. unsigned―Makes the value unsigned
            2. short―Synonymous to short int, varies but is at least 16 bits
            3. long―8 bytes
            4. const↔Informs the compiler that this value will not be changed, can still be changed using pointers though
            5. volatile↔Means the storage can change at anytime, compiler must check it every time it's used
        - How do you specify different types of number in C? ↓ 
            - long―123L
            - float→123e10F OR 12.5F
            - double→123e10 or 1.4
            - octal→053
            - hex→0x54
            - 
        - **Enumeration**
            - ```c
enum boolean {TRUE, FALSE};
enum override {TRUE=1, FALSE=5, T=5}
``` One can define Booleans, they are indexed from 0 by default - but this can be overridden. 
            - What items in a enum need to be distinct and what don't→Names must be distinct but values need not be.
        - **Declaration**
            - Variables must be declared before they are definition, where definition means giving them storage. They can be declared, defined and initiated inline.```c
 int i = 5;
 char a, b, c;
```
            - What's the different between Declaring, defining and initiating a variable? ↓ 
                - Declaring↔Telling the compiler this variable name will be used
                - Defining↔Setting aside storage for a variable
                - Initiating↔Putting a value in that variable
            - What does the extern keyword do?→It declares but doesn't define a variable, means the variable will be defined elsewhere - i.e. we allocate it no storage.
            - What does the **static keyword** do in regards to
                - **Static functions**→Usually functions are global, however static functions can **only be accessed within the file they're declared in** 
                - **Static variables**→Static local variables **don't lose their contents when they go out of scope** - so functions can reuse their values when called a multiple time. Static global variables are only seen in the file they're defined in
            - 
        - **ALL OPERATORS RETURN A RESULT INCLUDING ASSIGNMENT**!```c
 int y;
 int x = (y = 3);
 // x = 3
```
        - **Type Conversion**:
            - Type conversion occurs when a binary operator takes in two elements with varying sizes. The operator will return a value with the same size as the larger of the two elements - e.g. short + int ⇒ int.
            - However, narrowing is possible.```c
int x = 1234;
char y;
y = x + 1;
// y is overflowed and is the last 8 bits of x+1, in this case -45 in denary.

// CASTING:
y = (char) 1234;
``` 
        - **Expressions and statements**
            - What is an expression?↔An expression is a formula in which two or more operands are combined with an operator.
            - What is a statement↔A statement is an Expression ended by a semicolon
            - What type and value will this expression take on?```c
int x;
short y;
x = 5, y = 3
```↔The expression has type short and value 3. (The rightmost expression)
        - 
        - **Arrays and strings**
            - Strings or arrays are created using this syntax:```c
 int x[10];
```
            - Give 3 facts about string arrays ↓ 
                - They must end in "/o"
                - No bounds checking is performed
                - The compiler places them on a contiguous chunk of memory
            - What does the following result in and why does it work?```c
 char x[] = "abc" "def";
 printf("%s", x);
```↔This results in abcdef, it works because string concatenation is done by default. "abc" and "def" are set to strings using double quotes. This happens at compile time
        - **goto statement**
            - Works but shouldn't be used```c
 some_label:
 	printf("We used a goto")
 goto some_lable;
```
        - 
    - 
    -  _**Lecture 2 (Only address space layout)**_ 
        - 
        - **Address space layout** 
            - 
            - The **four most important areas of memory** within a **compiled x86 C** program→The **Stack**, the **heap**, the **static variables** and the **C binary code**.
            - Describe the **layout **of the **heap**, the static **variables**, the **stack **and the **C binary** code within the address space of a c**ompiled x86 C program**.→![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/9EqclGaeJ229axupOmXVqqvMy9SUdPUX7V3UUJKfqAvlQamJKCqsY20bbll3HJaaplmHBKojGNlm-veoZGeWqEKPswm8cEwA_HSec_wpoL4PW054VXI79WQoWA_A92Yu.png) 
Start at 0xffff ffff the top of the address space
The stack grows downwards
The heap Grows upwards
0x0 is often mapped to an illegal address to cause a seg fault if accessed
            - Describe the **features **of the** heap **→The heap is **manually managed**, using malloc and free - it is **generally larger than the stack**.
            - Describe the **features** of the **stack **→The stack is **managed by the compiler** and holds temporary local** variables** **declared in the body of a function** which are freed when they go out of scope. It **grows downwards on the address space**. It grows and shrinks as function calls push and pop their values.
            - Describe the **features **of the **data segment **→The data segment holds **global and static variables** who have a value.  
            - Describe the **features **of the **BSS**→The **BSS **stores **uninitialized local** or global variables initialized to 0. 
        - **Unspecified behaviour is **→behaviour where the C standard give's 2 or more options of implementations - the implementation chose can be decided by the compiler. It gives more freedom to optimise code for a given architecture. Some examples are whether to implement inline, evaluation order of function arguments, order and contiguity of memory in the heap. Memory layout of storage of function arguments.
        - **Undefined behaviour is**→behaviour not described by the C standard, when a compiler is faced with such behaviour it can do **anything it likes**. An example is modifying a string literal (string literals are in read only memory) or i++ + ++i.
        - 
        - 
    -  _**Lecture 3 (Only unions)**_ 
        - 
        - **Unions**
            - A union variable is a variable can store {{one of multiple types}}, the size of a union variable is equal to the {{size of it's largest member}}, the type retrieved must be {{the last value set }}. The syntax for fetching from a union is {{the same as for structs (⇒ and .)}}. The syntax for defining a union is {{ union u {int i; char p; short x;};}} The type stored within a union can change {{during the execution of the program}}.
        - 
        - **Bit-fields**
            - Bit fields are used for {{low-level control over bits of memory}}. They are useful when {{memory is limited}}. Bit fields are defined within {{structs}}. The syntax for bit fields is {{struct fred{int x : 4; int y : 10;};}}  The details of bit fields is very {{implementation specific}}. Bit field members do not have {{addresses}}.
        - 
        - 
    - 
    - **The C Pre-processor**
        - The C pre-processor executes {{before the program is converted to an object file}}, it examines lines beginning with # and does textual replacements. It can be used for debugging by setting a DEBUG variable to 1 or 0, and having if (debug) printf(...) - these are optimized away if debug is set to false. 
        - 
    - 
    -  _**Lecture 10:**_  
        - C++ is said to be: 
            - Better than C
            - Supports data abstraction
            - Supports OOP
            - Supports generic programming
            - Much is familiar with Java with subtle differences
        - Use C or C++ ↓ 
            - Don't want two conflicting IO libraries active
            - Using a standalone library coded in C is fine
            - Code with different metaphors in C & C++
            - C code may not expect an exception to bypass their tidy-up code ?
            - DECIDE AT THE START OF A PROJECT
        - C++ vs Java ↓ 
            - Speed or safety
            - More vs fewer features
        - Java trying to follow C++ with value types - types as values (like int or string) not wrapped in classes
        - **Types:**
            - A lot like C types, but additionally: 
                - Character literals 'a' type char (int in c) 
                - New bool type
                - Reference types: New type constructor &
                - enum types are disticnt, not just synonyms for integers
                - New type constructor class 
                - Names for enum, class, struct and union can be used directly as types - e.g. struct sam{...} can just use sam not struct sam
                - Member functions (method) can specify this to be const - can say this method does not mess with contents fo this
            - Auto and thread_local:
                - auto now means, the type of the initializing expression - like type inference```cpp
 auto sam = 5;
```
                - thread_local is an additional storage class e.g. only one thread sees that same value, opposite of static
            - C++ booleans:
                - bool types true (1) and false(0) when cast to integer.
            - C++ enumerations:
                - ```cpp
enum flag {is_keyword=1, is_static=2, ...}
``` Defines a new type where you can use it's name: flag f = is_keyword
                - Implicit type conversion **not allowed**: ```cpp
f = 5; // WRONG
f = flag(5); // ALLOWED, enum secretly is a bitmap
``` 5 is allowed because bitmaps have explicit max and min values based on the max / min binary values contained in the.
            - References:
                - Alternative name (alias) for a variable
                - Generally used for specifying parameters to functions and return values as well as overloaded operators.
                - Reference declared with &:```cpp
 int i[] = {1,3};
 int *ptri = &i[0];
 int &refi = i[0]; // NEW
```
                - Must be initialized when it's declared!  
                - You cannot change what a reference refers to after creation. E.g.: ```cpp
 refi++; // Results in i[0]=2
 ptri++; // Results in ptri point to 3
```
                - Can think of reference types as pointers **with implicit use of * each time.** 
            - References in function arguments:
                - When used as a function parameter, the value is not copied: ```cpp
 void foo(int& i) {i++;}
 
 //Same as
 
 void fooTwo(int* i) {*i++;}
```
                - Declare a reference as const, when no modification takes place. 
                - It can be noticeably more efficient to pass a large struct by reference than by value.
                - Implicit type conversion into a temporary occurs for const references but errors otherwise: ```cpp
 float fun1 {float&};
 float fun2 {const float&};
 void test() {
 	double pi = 3.14159;
 	fun1(pi); // ERRORS 
 	fun2(pi); // ALLOWED because it knows the value is not going to be changed. Implicity type converts to float. 
 }
 
``` 
            - Overloaded functions:
                - Works just like java, functions with varying argument type but same name.
                - Type conversion is used to find the best match, but that isn't always possible: ```cpp
 void f(double);
 void f(long);
 void test() {
 	f(1.0);
 	f(1L);
 	f(1); // Fails, f(double) or f(long) ?
 }
```
                - Can also overload built-in operators, such as assignment and equality
            - Scoping and overloading:
                - Overloading does not apply to functions declared in different scopes. ```cpp
 void f(int);
 
 void test() {
 	void f(double);
 	f(1); // calls f(double);
 }
```
            - Default functions arguments: Uses overloading, creating two separate functions.
                - ```cpp
double log(double v, double base=10.0);
// Like python, non-default cannot follow default:
double log(double base=10.0, double v); // NOT ALLOWED

// A DECLARATION does not need to name the variable:
double log(double v, double=10.0);
// Obviously when I actually DEFINE the function I would need to do:

double log(double v, double a) 
{... // do some stuff};
// where log(1) same as log(1, 10)


// But beware of lexical interactions between * & = 
void f(char*=0); // Wrong *= is assignment
``` 
        - **Namespace:**
            - Related data can be grouped together in a namespace,  not the same as a class as we can't create an object of the namespace type - just a logical grouping of values & functions.
            - ```cpp
namespace Stack{//header file
	void push(char);
	char pop();
}

namespace Stack {//implementation
	const int max_size = 100;
	char s[max_sizez];
	int top = 0;
	
	void push(char c) { ... }
	char pop() { ... }
}

void f() {//Usage
	Stack::push('c');
}
``` Ensures we don't have clashes of external functions, namespace formalizes naming conventions (gm_openscreen meaning graphics manager openscreen for example). 
            - ```cpp
using namespace Stack; // imports everything to the scope

int main() {
	pop();
	push('a');
}
``` More like java packages than modules in java.
        - Using Namespace: 
            - Scope and expresses logical program structure - collect together related pieces of code.
            - A namespace without a name limits the scope of vars, functions and classes within it to the local execution unit.
            - Can declare the same namespace in multiple source files.
            - Can be defined more than once.
            - Global function main() cannot be inside a namespace.
        - Linking C & C++ code: 
            - extern "C" specifies that the declaration should be linked as C NOT C++ Code: ```cpp
 extern "C" int f();
 
 extern "C" {
 	int globalvar;
 	int f();
 	void g(int);
 }
```
            - 'Name munging' for overloaded functions.  A C compiler typically create a linker symbol '_f' for the f above, this gives the compiler a namespace the programmer cant use (funcs beginning with _). A c++ compiler generates '__Z1fv' function of length 1 that takes a void argumeny.
            - Function calling sequences can differ, e.g. exceptions.
            - If we want to write a library in C, and specify it to be importable into both C & C++: ```cpp
 #ifdef __cplusplus
 	extern "C" void myfn(int, bool);
 #else
 	include <stdbool.h> //No boolean in C
 	extern void myfn(int, bool);
 #endif
```
            - Care must be taken with pointers to functions and linkage - if I pass a C++ function to a extern "C" piece of code, could get errors.
    -  _**Lecture 11:**_ 
        - **Classes and objects in C++**:
            - ^^C++ classes are somewhat like java.^^
            - ^^**Two**^^^^ main components^^ of classes↔^^Data members^^ and ^^member functions^^ which act on the data. Both data members and member functions can be static.
            - The^^ 3 access controls^^ of C++ members are→^^private, protected and public^^ 
            - **Class and struct are almost synonyms** in C++, the only difference is→class members are by default private while struct members are private by default.
            - ^^Classes ^^are ^^created ^^with→^^**class or struct keywords**^^**:** 
                - ^^Struct^^ ^^members default to ^^→^^public^^ access ^^^^
                - ^^class members default to ^^→^^ private^^. 
            - A ^^constructor ^^is simply a↔^^Member function with the same name as the class^^ 
            - C++ supports overloading on both→constructors and member functions
            - A **destructor **is named with↔the same name as the class prefixed with a **tilde **(~)**.** 
            - Big differences from Java:
                - ^^Values of class types are^^→^^ ^^^^**not references to objects**^^**, but**^^** the objects themselves**^^**. **
                    - So we ^^access members with C-style . (dot)^^ ( using -> more convenient when we have pointer to objects). 
                - We ^^can create an object of class C,^^ two ways  ↓ 
                    - ^^On the stack by declaring a variable C x;^^^^^^
                    - ^^On the heap: new C() ^^^^**which returns a pointer to C.**^^ 
                - If a function is ^^**statically resolved**^^** **it means→the code to execute for a given function name is ^^**generated at compile time (or linked at link time) not runtime**^^.
                - If a function is ^^**dynamically resolved **^^it means→the code to be executed will be ^^**determined at run-time**^^. 
                - ^^Member functions by default are resolved ^^→^^**statically**^^. For java-like code ^^**declare them virtual.**^^ 
                - The virtual tag and the dynamic resolution allows for→runtime polymorphism.
                - ^^Member functions can be ^^^^**declared **^^^^{{**inside a class**}}^^^^** **^^^^but ^^^^**defined **^^^^{{**outside it using : : **}}^^^^  ^^ 
                - C++ uses {{new }}to allocate and {{delete }}to de-allocate. No garbage collector.
            - Example (emphasising differences from Java):
                - ```cpp
class Complex {
	double re, im;
	public:
		Complex(double r=0.0, double i=0.0);
};

Complex::Complex(double r, double i) : re(r), im(i) {
	// This is the preferred form of constructor initialization
	// NECESSARY FOR CONSTANTS
}

Complex::Complex(double r, double i) {
	re=r, im=i;  // DEPRECATED initilization by assignment
}

int main() {
	Complex c (2.0), d, e (1, 5.0);
	return 0;
} // local objects c,d,e are deallocated on scope exit!!
  // IMPORTANT - STACK ALLOCATION
```
            - The preferred form of **constructor** **initialization in C++ **is (somehow). **It MUST BE USED WHEN**...→```cpp
 Complex::Complex(double r, double i) : re(r), im(i) {...}
 
 // You MUST use it when itializing
 // const and reference members
```
            - In java, **constructors only **{{**initialize heap storage**}}** **(which has to be pointed to), only way to update is {{x.f = updated_val}}; 
            - In C++ because objects values are "first-class-citizens"→there are more update behaviours
                - In "C x;" x is initialized using→The default constructor   
                - In "C x = y;" x is initialized using→The copy constructor
                - We need to worry about what "x = y" does. 
                - We split class definitions into separate behaviours and control them to→Preserve **class invariants **(If I can define an object, with no members initialized - certain invariants may not hold) and **object encapsulation** (All the behaviour of the class should be held within the class)
            - **Default Constructor ** 
                - Default constructors are called when→you type "C x;" or if you do "new C();" i.e. with no arguments.
                - If no default constructor is specified→The compiler creates one, with little to no initialization.
                - To disallow users to use the default constructor we→define the default constructor and set it to private.
            - **Destructors **
                - destructor are called→when a stack-allocated object goes out of scope **INCLUDING when an exception causes this to happen**, when a heap allocated object is deleted
                - There can only be {{one}} destructor for a class
                - Make destructors **virtual** when→The class has subtypes or super-types - as we'll want to inherit the destructor
                - Stack allocated objects, with {{destructors}}, are a good way of freeing memory after the scope is exited.
            - **Copy Constructors**
                - ```cpp
// Initialization methods:
Complex c(1,2);
// VS
Complex d = c; // Copy constructor evoked
``` 
                - To augment the default copy constructor use the following syntax→```cpp
class Complex {
	Complex (const Complex& c) {...} 
}
// we don't pass a value
``` This is useful when I have member variables with pointers in for example. Don't just wanna copy everything
                - To **disallow **copying of objects→Make the copy constructor **Private!** Note, can still use assignment );
                - ^^IMPORTANT NOTE:^^ Assignment (d = c) differs from invoking the copy constructor: Complex d = c. **Does not** use the copy constructor.
            - **Assignment operator**
                - By **default **when the assignment operator is used→all the **non-static** members of a class are **overwritten **(x = y;). 
                    - This may not be desirable if the class contains pointers, when I copy a dog I want it to have a pointer to its own dog bowl?
                - You can implement your own assignment operator this syntax (for the class Complex)→```cpp
Complex& Complex :: operator=(Complex& c) {...}
// We take the input to the right hand and return a reference
// e.g in x = y, c = y
``` 
            - **Constant member Functions**
                - **Member functions** can be declared **const **→This prevents the function from modifying any object members.
                - The syntax for constant member functions is (for a function real in the Complex class )→```cpp
 double Complex::real() const {
 	return this->re;
 }
 // Note that if you declare beforehand you need to include the const:
 double real() const;
```
            - **Arrays and heap allocation**
                - If we want to create an array of objects, the class needs a {{default constructor}}.
                - To create and delete objects on the heap, we use this syntax→```cpp
 Complex* c = new Complex(1.0);
 // To delete them we use
 delete c;
 // This invokes the object destructor !!
```
                - We **need **a method for **array heap deletion** because→C doesn't distinguish between a **pointer to an object**, and a **pointer to an array of objects**. 
                - Array heap deletion is done using the following syntax→```cpp
 delete[] c;
```
                - Deleting objects using the array heap deletion invokes→the object destructor on each object.
            - **Operators and Virtual (11.2)**
                - **The "this" pointer**
                    - 'this' is used much like self in python (while in python you need to explicitly pass it, C++ does that behind the scenes). Useful for many tasks. Such as overloading in the body of a function:
                    - ```cpp
&Complex Complex::operator*=(Complex input) {
	this->re *= input.real();
	this->im *= input.imag();
	return *this;
	// Note this returns a reference NOT the object itself
}
``` 
                    - Remember, at its core this is a {{POINTER}}.
                - **Class instances as member variables:**
                    - Consider a class with objects as member variables Complex a, how do we initialize said objects? I.e. how do we call the constructor?→```cpp
class Example {
	Complex a;
	Complex b;
	Example(double im, double re) : a(1.0, 0.0), b(im,re) {
		...
	}
};
``` 
                - **Temporary Objects**
                    - Jesus Christ. 
                    - Temporary objects exist for the duration of a {{full expression}}, after which they are lost.
                    - What is wrong with ```cpp
string a("abd"), b("def");
 const char* SCARY = (a+b).c_str(); // c_str converts a c++ string to a c string
```→Temporary objects are things such as: ```cpp
 string a("dsadsa"), b("dsadfsadsaadsa");
 // THE TEMPORARY OBJECT BELOW IS FORMED FROM (a+b)!!!
 const char* SCARY = (a+b).c_str();
 // c_str() just returns a pointer to the objects string value
 // HOWEVER, because its temporary the value is lost!!!
 // SCARY don't got nothin' in it
```
                - **Friends**
                    - Within our class, we can define another class to be our **friend, **this means→Code within the other class, can **access the private and protected members** of our class: ```cpp
class A {
	friend B;
	private:
		int myPrivateNumber = 3;
};
class B {
	static doStuff(A someObject) {
		// Because their friends, they share the number
		A.myPrivateNumber;
	}
}
```  
                    - We can even define non-member functions to be friends, this means→that functions defined elsewhere can access our private methods: ```cpp
 class a {
 	friend void outputTheNumber();
 	private: 
 		const static int myPrivateNumber = 3;
 }
 
void outputTheNumber() {
	std::cout << a::myPrivateNumber << std::endl; 
}
```
                    - Note: Friendship is **not symmetric** 
                - **Operators**
                    - **Operator Overloading** 
                        - C++ allows for {{operator }}overloading, this is syntactic sugar.
                        - It can be done outside the body of the class, using the following syntax→```cpp
bool operator==(Complex a, Complex b)
	return a.real() == b.real()
		&& a.imag() == b.imag();
``` 
                        - Or it can be done inside the class, in which case we can use the following syntax→```cpp
 bool Complex::operator==(Complex a) {
 	return re == a.real() && im == a.imag(); 
 }
```
                        - Operator overloading can be done on almost all operators.
                    - **Streams**
                        - Streams output the {{left argument}}, this allows for {{chaining }}of streams.
                        - ```cpp
std::cout << "Like this" << std::endl;
``` 
                        - We can use overloading with streams like the built in type using either syntax below: The difference is:→```cpp
const char* s = "Hello World";
cout.operator<<(s);
cout.operator<<(std::endl, s);
// The << operator is overloaded, if we pass one value it behaves differently to two (in this case it would pass &s[0])
```
                - **Inheritance** 
                    - C++ inheritance works much like java
                    - The syntax for C++ inheritance is→```cpp
class Animal {
	int legs;
	public:
		Animal(int l) : legs(l) {}
};
class Dog : public Animal {
	int ears;
	// Could have lost 1+ ears
	public:
		Dog(int e) : Animal(4), ears(e) {}
};
``` 
                - **Virtual Functions** 
                    - What will the following code output?```cpp
class Animal {
    public:
        void makeNoise() {
            std::cout << "A noise!" << std::endl;
        }
};
class Dog : public Animal {
    public:
        void makeNoise() {
            std::cout << "BARK" << std::endl;
        }
};

void makeAnimalBark(Animal* a) {
    a->makeNoise();
}

int main() {
    Animal* a = new Animal;
    Dog* d = new Dog;
    makeAnimalBark(a);
    makeAnimalBark(d);
}
```→The problem is, makeAnimalBark isn't virtual, so the output will be - "Bark" "A noise!". Note this is **only **the case if we pass a pointer - if makeAnimalBark took the value it would work.
                    - Non virtual member functions depend on the {{static type}} of the arguments. 
                    - We need the virtual keyword because→a pointer to a subclass can be cast to the base class, then the base class cannot see the overridden function. 
                    - To get polymorphic behaviour we must→define the function as virtual in the superclass. Then it will be dynamically evaluated at runtime.
                    - **Non-virtual** member functions are called depending on {{the static type }}of the variable, pointer or reference. Since a pointer to a derived class can be cast to a {{pointer to a base class}}, calls at base class do not {{see the overridden function}}. To get polymorphic behaviour, {{declare the function virtual}} in the {{superclass}}. 
                    - To enabe **virtual functions **the C compiler must→generate a "virtual function table" or vtable. This table contains the function to call for **each object instance**. This adds **run-time overhead **as every function call **must go via the vtable.** 
                    - Why does C++ give the option of none virtual overridden functions?→It's a **trade off of performance vs Programmer conceptualization** - dynamically** type checking at run-time can be slow**, so if it's not explicitly needed we don't want to do it. Instead of a function call in machine code, its an indirect function call - While at first glance this is not much slower, the **effect on the cache and branch predictor can be large** 
                    - **Enabling Virtual Functions**
                        - To enable virtual functions, C++ uses→a vtable or virtual function table. These store a pointer to the specific function to call for every object instance. They are slower.
                        - C++ vtables also encode RTTI - runtime type information about the class in question. Can ask if an object has the same type as another.
                - **Multiple Inheritance and Casts (11.3)**
                    - **Abstract Classes** 
                        - Works like java but with a different syntax 
                        - In C++ it is verboten to {{instantiate }}an abstract class.
                        - What is the syntax for C++ abstract classes→```cpp
 class shape {
 	public:
 		virtual void drawTheShape() = 0;
 }
 
 // Inherit it as normal
 class Triangle {
 	public:
 		void drawTheShape () {...};
 } 
```
                        - When can a derived class be instantiated?→When all the abstract functions are implemented. If some of them are, you cannot instantiate the class. 
                    - **Multiple Inheritance**
                        - In C++ you may inherit from multiple classes, if you have a name clash you must...→```cpp
class Car {
	public: void noise() {cout << "Beep";}
};
class Bike {
	public: void noise() {cout << "Toot";}
};
class Cabike : public Bike, public Car {};

// Explicit Naming is required
Cabike.Car::noise();
// or
Cabike.Bike::noise();
```
                        - The Diamond problem with multiple inheritance→Is when a subclass contains two instances of another class. E.g. two sets of the same variables. It can be achieved like so ```cpp
 class A {int someInt;};
 class B : public A {};
 class C : public A {};
 class D : public B, public C {};
 //We can do the following:
 D dInstance;
 dInstance::B.someInt = 3;
 dInstance::C.someIne = 4; 
```
                        - If we have a case of the diamond problem in C++→All variables from the "top" of the diamond, must be chosen explicitly in order to be used. E.g. we need to know which A class to choose from if we have two instances.
                        - **Virtual base classes**
                            - Virtual base classes allow for only {{one instance}} of the "top" class within inherited classes. 
                            - Virtual base classes mean that↔any class that **inherits **from multiple classes **containing the same virtual base class**, will share that class instance without ambiguity.
                            - The syntax for virtual base classes is simply ```cpp
 class A {public: int a};
 class B : virtual public A {};
 class C : virtual public A {};
 class D : public B, public C {};
 
 // Means we can do:
 D d;
 cout << d.a;
```
                    - **Casts**
                        - ```cpp
double* p;
int i = (int)*p; // fine
int j = *(int*)p; // Undefined - we've lied about the type of the pointer and then got the value of the supposedly int pointer
```
                        - In C++ the role of casts and constructors can overlap, casts can be seen as implicit calls to the constructor. Give an example with Complex→```cpp
 double x = 0.1;
 Complex s = x; // Because there is a constructor that take a single double
 
 // Similar to this: (which simply does the cast)
 int a = int(x);
 int b = x; // Implicit cast!
 
```
                        - To disallow ```cpp
 double x = 0.1;
 Complex a = x;
``` we must→Declare the constructor **explicit.** Implicit vs explicit casts.
                        - If I want to allow casts from a class type to a default type I do the following→Overload the operator of the type we wish to cast to, e.g.: ```cpp
Complex i(0,1);
double x = (double)i; // TYPE ERROR

Complex {
	double operator double () {
		return a->re;
	} 
} 
``` 
                        - **New forms of casts in C++** 
                            - Problems with C-style casts include  ↓ 
                                - They do no type checking
                                - They are hard to find in the code
                            - Describe what these do ```cpp
dynamic_cast<T>(e)
static_cast<T>(e)
reinterpret_cast<T>(e)
const_cast<T>(e)
```→```cpp
dynamic_cast<T>(e)
// This uses RTTI and performs runtime checks
// when casting pointers within an inheritance 
// hierarchy
Car car;
dynamic_cast<Vehicle&>(car);

static_cast<T>(e)
// This is very similar to C, does it's best effort
// at compile time: static_cast<int>(3.14)

reinterpret_cast<T>(e)
// Explicitely flags re-use / reinterpiration of bit pattern

const_cast<T>(e)
// remove const or volatile from a type, allowing you to edit it as you please
// Specifically for const pointers
```
                    - 
                    - 
                    - 
                    - 
            - 
    -  _**Lecture 12:**_ 
        - **Exceptions and RAII**
            -  _Exceptions_ 
            - Done just like java, but **throw object values** not object references - the reason for this is→if you **run out of storage**, a reference requires the creation of an object in storage... 
            - The **principal of exceptions** is a given piece of code (**a library**) may  _encounter an error and not know what to do with it_  - the user code may know how to handle it.
            - One portion of code **throw**s an exception, another **catch**es it.
            - If an exception is thrown, the **call stack** is→unwound until a function that can handle the exception is found
            - An uncaught exception results in the program **terminating**.
            - **Throwing Exceptions**
                - Exceptions in C++ are just {{normal values}}, matched by type. Often a {{class}} is used to define a particular error type.
                - An instance of the class can then be thrown, caught and possibly rethrown. The syntax for these is→```cpp
 class myError() {
 	public:
 		int X;
 		myError(int x) : X(x) {}
 };
 
 void f() { throw myError(10); }
 
 try {
 	f();
 }
 catch (myError) {
 	//handle the error
 	throw; // re-throw
 } 
```
                - The thrown type can carry information ```cpp
 try {f();}
 catch (myError instance) {
 	std::cout << instance.X; // outputs 10
 	// We could simply make myError a struct so all members are public
 }
```
                - The syntax for catching multiple errors is the following (also what does catch(...) do?)→```cpp
 try {...}
 catch (errorA) {...}
 catch (errorB) {...}
 catch (...) {} // is a wildcard that catches all exceptions - discouraged, what have I caught?
```
                - Class hierarchies can be used to express errors→e.g. someError > myError. However, this requires runtime-type-information!
            - **Exceptions and local variables**
                - When an exception is thrown, that **stack is unwound** this **differs **from **stepping down the stack** as→all  _local variables we meet call their destructor_ . This plays the role of try - finally (in java finally frees memory)
                - It is **good practise** to wrap locks, open file handles, heap memory etc. in **stack allocated objects** - this is because→when the stack is  _unwound the destructor of the stack allocated object_  will be called and all the  _memory can be freed. _  
                - RAII is→**Resource acquisition is initialisation** (this is a terrible name), actually means  _memory is freed once the object is out of scope_  - done by  _wrapping resources in stack allocated objects_ .
        - **Templates**
            - Templates support **metaprogramming**, this is where→code can be  _evaluated at compile time_  rather than run time
            - Templates support **generic programming**, this is where→ _types are_   _parameters _ to a program
            - Generic programming in **void * pointers** has the **disadvantage**→that we lost type-checking
            - **Class templates**
                - The syntax for defining and instantiating a class template is→```cpp
 template<typename T> class Stack { ... };
 // Or alternatively, this is the same
 template<class T> class Stack { ... };
 
 // We can the instantiate the Stack
 Stack<int> stack = ...;
 
 // the template parameter T could be any C++ type - hence preferring typename to class
```
                - Stack could then be implemented like: ```cpp
 template<typename T> class Stack { 
 	struct Item {
 		T val; // the important bit
 		Item* next;
 		Item(T v) : val(v), next(0) {}
 	}
 	...
 	public:
 		void push(T val);
 		T pop();
 };
```
            - **Template richer details** 
                - What is the syntax for setting a specific template type?→```cpp
template<int i> class ... 
```
                - How do you give a template several parameters?→```cpp
 template<typename T, int i> class ...
```
                - How do you declare a subsequent argument with a template argument?→```cpp
 template<typename T, T x> class...
```
                - What's the syntax for a template function with a default value?→```cpp
template<typename T, int x=100> class ...
```
            - **Templates behave like macros**
                - Templated classes are **type checked** when→the template is instantiated. 
                - Template **definitions are often placed** in the→header file, because if we had it in one file and another file used it - we'd end up having to recompile a load of files whenever we updated the template. Additionally, it makes separate compilation impossible.
                - The **difference between java and C++ templates** is→** Java does type erasure** setting all the types to Object, while C**++ works like a macro** where the type is replaced and the new function for that type is added to the binary 
            - **Templated specialisation**
                - What does **Template specialisation allows** **us to do** and what is the **syntax**?→It allows us to define **different definitions of a class** depending on the type parameter passed. 
The syntax is: ```cpp
struct Test{};

template<typename T> class someClass {
    void stuff() {std::cout << "HI!" << std::endl;}
};
// NOTE, the missing typename T is ON PURPOSE
// You must have empty angle brackets
template<> class someClass <Test> {
    void stuff() {std::cout << "NO!!" << std::endl;}
};
```
            - **Templated functions**
                - The syntax for defining and instantiating a template class is→this:```cpp
template<typename T> void sort(T arr[], const unsigned int& len);

// The type of the template is then inferred from the argument types:
int sam[] = {4, 1, 2};
sort(sam, 3);
sort<int>(a,3); 
```
                - Unlike template classes, template functions have {{type inference}}. 
                - Two benefits and a negative of using **templates for functions**  ↓ 
                    -  _Better type checking_  than using void *
                    -  _Larger binaries_  if multiple different types of sort() are invoked
                    -  _Potentially faster code_  than runtime type inference as we don't have vtables for functions - we know the type of the function at compile time
                - **Overloading templated functions** 
                    - Templated functions can be overloaded with {{templated }}and {{non-templated}} functions. Resolving an overloaded function call uses the "most {{specialised}}" function call
            - **Template specialisation enables metaprogramming** 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_qsNY9_ag-ZhMMnJoBIlTBcdNHf3yUahT-AMm2TonL3ay1_mtpzUixn0ACOUbvzuRBBUliHrc1qG9hED_MVdo29srt_WOUI7DZfbgABrzZ47XkYigIPhHplmm7HBr46h.png) 
                - Meaning templates are a Turing complete compile-time programming language! However the type you seek to evaluates value must be known at compile time - like enum or static
            - 
            - 
        - 
- Intro to Computer Architecture
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
        - 2. [2008 Paper 6 Question 2](../y2008p6q2.pdf.md) a, c
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rSCemIkz1ebYPPCOr7SiSWifHvnyMGhn6yrZ9to0JpDF1YhzqazpR0aBclMH_lj0DloczVqRw5a47AgXdpLRkVsQ2IYDWR1NA60tCiDN30tXtTWFlVRF_z3ZGBMGkceV.png)
                - RISC stands for Reduced Instruction set Computer while CISC stands for Complex Instruction Set Computer. In practise RISC commands are fixed length, while CISC commands are variable length (1 to 15 bytes) this means RISC commands are faster to decode as we don't have to wait for all 15 bytes to arrive - additionally, when CISC commands are decoded they are broken down into many short RISC like commands that go into the pipeline. However, given the greater length of instructions, you can often write complicated instructions faster (by hand) in CISC than RISC.
                - RISC tends towards making the common case fast (based on Amhdahl's law of diminishing returns of speedup) while CISC often pushes for specific domains of commands being made as fast as possible - e.g. adding a specific integer division command.
                - RISC has less pre-packaged instructions than CISC, but more can be emulated using subroutines that are attached to many of the Instruction types - CISC attempts to handle a wide range of instructions out of the box while RISC prefers the architecture to be built upon for specific usages.
                - CISC attempts to minimize the number of instructions per program, the logic being fetching instructions takes time - however the result is long instructions that take time to decode. RISC attempts instead to minimize the number of instructions available by default and thus the cycles per instruction (while still offering a good amount of functionality). 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/WZL6Sadbb6pgxZVdsiw95Y6XfhAd9nu9lmRaLHS618gTWt-VuLb_R7g1HiKWz7yOgUknIgOPRjJLlg7Vwxiy8TUcGgV774gb4Jrk8dEUdGp5aOCrhIEphZe3_cRJUzTQ.png)
                - For an accumulator to run an instruction on two operands, it needs one to already be in it's accumulator and the other needs to be fetched from memory - so the operation is run on the value in the accumulator & the value fetched from memory, finally the result is placed on the accumulator. For stack operations we need both operations on the stack, and then the two are popped from the stack the operation is applied and the result is pushed back onto the stack. 
                - In stack based we need to fetch the two values (if they're not already on the stack) and then apply the operation (which is a dense command, causing two pops, some arithmetic and a store) while for an accumulator we would need to fetch one value, apply the operation (which is less dense just one fetch, an operation and a store). Thus the stack is narrowly more dense.
        - 3. [2006 Paper 6 Question 2](../y2006p6q2.pdf.md)- part b:
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
        - 21. [2018 Paper 5 Question 3](../y2018p5q3.pdf.md), part b.  
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
- Further Graphics
    - Supervision 2
        - 
        - 13. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/17Edkai7g7Fd5qebWHcQ8u-c8mqJ2t8Fs2Ps0S0XNiNz-twUM2aCW9oIReBYPPF2Cto8FtoPALxoC4LxgpSmCdjF9_jYSw8tvh9oxWqE9eDXMeb-25IcpWVuPCf42kkW.png) 
        - 14.  
            - a.) Rigging is the process of adding joints and bones between said joints, and placing them within the model. The bones are given a weights that decide the area of effect of the bones, and the bones & joints form a hierarchy (a graph) that is used to filter down transformations from one bone to other connected bones. 
            - b.) i.) $T_f = T(1/2) + I (1/2)$ 
                - $x' = T_f(x)$ 
                - ii.) $T_f = T(\frac{1}{1+\sqrt2}) + I(\frac{\sqrt2}{1+\sqrt2})$  OR $T_f = T(\frac{\sqrt2}{1+\sqrt2}) + I(\frac{1}{1+\sqrt2})$ 
                - $x ' = T_f(x)$ 
        - 15.
            - a.) Dual quaternions allow us to represent translations and transformations in the same value - this makes animation much easier, before if one was to perform a translation & a rotation - careful attention would have to be payed that they were at the same rate (as we always translate around a point! We don't want our characters arm to rotate around where it was 30 frames ago) while with dual quaternions we get that for free.
            - b.) It's more computationally costly to use quaternions than linear blend skinning. (Not by a huge amount though)
            - Linear blend skinning can be repurposed with ease to 2D animation (or any number of dimensions, but so far we've stuck to 2 or 3 I await a compelling 1d tale), as the process is simply averaging transformations said process makes no demands about the dimensionality of the transformations. On the other hand, quaternions do not make the jump from 3d to 2d so handily - if we only have i & j we don't have the property ijk = -1 to differentiate them from imaginary numbers (ii = jj = ij = -1 is true for i = j = sqrt(-1) ) and just  i & j don't form a basis with which to perform animations.
        - 16.)
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Mq6Ih2CBkUzLCkQyVPcARUSPbWA6pB8Tx2ap3czxbNB39-2BElzVEn-sQqUY2Abm2zJV7mPGLGoUryKQhjmg7CdBsroRlPL1VLb3dvK0cJ0XTQPVHHQzjVrJs84SUWmx.png) 
            - We can separate them into three dual quaternions, one rotation about the z axis, on translation along the x axis with zero rotation and finally a translation along the y axis with zero rotation. Finally, if we multiply the three quaternions the resulting quaternion will represent our translation.
        - 
        1. ) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/w07UOHSZFJMNCuTGrCebgQaTJV7bJwcW8lc7f3lkThFZ9tvE24CUQy14UjfmU-vqgixnNwzUYgd2Rk0h58wPwTalUJxfvxAYa-hLaoGcvdfSxOvGQumLsnyiGlJaLG2H.png) 
            - Caustics - The interaction of light & curved surfaces or glass - e.g. the refraction of light. 
            - Subsurface scattering - Light entering and being scattered by a translucent material, e.g. skin.
            - Soft shadows - point lights cannot create soft shadows, as the incident intensity is the same everywhere (varying only with distance & angle) - there are not points in which light from multiple  points on a light source combine and a gradient of luminance is formed. 
            - >1 bounce lighting - light that arrives after performing 2 or more bounces is not accounted for. 
        2. In areas of low curvature, less sampling needs to be done as the effect of reflections and bouncing will be less pronounced. In areas of high curvature we should have more samples, as there is likely to be more occlusion of objects and more light bouncing effects.  
        3. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/13sI92Gd6ULRrF3ccPF88UmC8s1hGEqwULrVuPoak71HfJUjMn6D7XHAlHHjXgdk90XoI3P1xnGUd_2N5jAE4Qz3klTtLoto7vfoBu1AmZQgqY7GT9wmxvjcHZjkdki5.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/OezAp8d-MEVVCvNOfirN596uGuWLFVCq-Qg469KNo8-qjZs-dQBnLijynE-hDCBtH4-veMjI8wafwqHl1ulMM-65UFO81bz-DlRNfgguqThRLWfV3Lr4-kethFFQ5BPk.png) 
        4. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/wLzNg5gjNt3K68OaClfqbigNmPNV1-RdDY6KrQ0XOSSVr9m1HtRmrghguA5E7wOKx0SqNXOkot5n8MkJCmMEbVvta_N6SoFV-nYRTXAFJ-djLIY9CqYjYROLcXJlLSc6.png) 
            - c.) b shows that using importance sampling, we can still get a high quality approximation while sampling a smaller area - in reality we use monte carlo integration rather than analytical integration. 
            - d.) Using cosine we sample more light values at a greater angle to the surface, giving perpendicular light a higher weight. We assume that light is coming from all angles for this to work, however if light is coming from a more acute angle - less of it will be sampled resulting in a lower quality image.
        - 
    - Supervision 1
        1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gTK4JW5ryukfyXXqdHoX4VyrjOWKeMBIZR0MErPyy_mHWLsDjfYI4zrgxLoRfwEXncPqwwfL72zuQswpGmhrs_N-qTprQFaoxHUWpdUPJ19TiARF_nwV6yK5JSa4Afkv.png) 
            - Parametric surfaces are created using a function f which operates on sets $X \subseteq R^m$ and $Y \subseteq R^n$mapping set X onto set Y: $f : X \rightarrow Y$. Whereas Implicit surfaces are created using a (distinct) function f, where a point $x \in R^k$ lies on the surface if $f(x)=0$. 
            - While both use a function f to decide the resulting surface, the parametric function gives us a way of creating points while the implicit function gives us a way of testing points.
            - Advantageous components:
                - Implicit functions give us an easy way to check if a point is inside, outside or resting on a surface ($f(x) < 0$, $f(x) > 0$, $f(x)=0$), the parametric function gives us no such method.
                - Parametric functions give us a method of generating points on the surface (any point on our domain X can be mapped to our range Y), Implicit functions require us to check points to find one resting on the curve.
                - Parametric surfaces allow for easy computing analytic point wise differentials, while Implicit functions do not.
            - Implicit surfaces would be suited more for ray tracing applications, when checking if a ray impacts a surface is the norm - in particular, implicit surfaces can be useful for visualizing mathematical formulas and the conjunction of multiple formulae (computing $f_1(x) + f_2(x)=0$for two such formulae).
            - Parametric surfaces (most commonly Bezier surfaces) are used for 3d modelling and sculpting, however the surface would undergo a second process of being converted from a parametric surface to a normal mesh that can be rendered using rasterization.
            - Point set surfaces differ from parametric and implicit surfaces in a number of ways ↓ 
                1. They are generated from real world data.
                2. They can be used for direct rendering using rasterization with dishes rather than triangles.
                3. They are not analytically differentiable like parametric surfaces.
                4. Formed by taking points and examining other points in a region and forming a proxy surface and then checking if the given point lies on that surface.
        2. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7GDDM58Km_D6S_B7eTNJRuJuvQZ2lcJOW9WMCy-vyKsvkWTCPlVnMA6ULHFbsRn96NOYlogLBgaD02NrPdWYGVujgdOh2Tqld1J27kRYT0EL28IH24B7GaUblTqK91q-.png) 
            - $x^2+y^2=e^{2t}$
            - $R = e^t$
            - This describes a spiral centred at (0,0) where the distance from the origin is $e^t$
            - 
        3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ZmkyinQzH326IJwFAzKQAtsa4DjUaZkSKgdGN2ILCYoWxNMSz5LfKPKDRhxI_gCOzrpjNX9XzgBFrSJiE0U-q9q4g_AeCGpt8esliS1FG8NREOTPRZmrnrXCzhnFudMq.png) 
            - a.) First you must compute $S_u = \frac {\partial (s(u,v))}{\partial u}$ and $S_v = \frac {\partial (s(u,v))}{\partial v}$ , one can then compute the normal via $\frac{S_u \times S_v}{||S_u \times S_v||}$.
            - b.) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jWzZl4lN7321QOkwuLl-rQjLyrCTQHHloFpCA7i31xJ_aiViYTlSBWgQyh430XaZCzVQv66zT4atPR-jzFKdo7K03icYTVX3q89WQ2nMKXqS7V0XdJ91BT71WGRyLY7v.png)![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/VRgybaadKrIWnFcRLL4KuG_nZMVq3eWkG6IL2aQutOuyYrgkyEvqiFJU3oT9xTxH0x2R38Xxel-F-ld7kyFgLW0TZZU2xa_AmUc8RwNGFJxE3sQEZETk4hW9PkO_sv3H.png) 
        4. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/8UIPYfQEqMSbTmQI5-FBIbJ3mtNHi6yluVkNxBaGrWKOV4ToxB-e_ludB-kOIn7TCdZatDLxcfuDn0nKUG8cba9JGVYW53vTW4zqYDOWv0gesXcwuPRq0u60MoGIUHuf.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4sG-KtYTLnDXew39MLnWTljXM61KRrHhOyT_C5lSh3n9Md2ceefb3bBHHYowjiMzHZBdc5k3UTxMvcUreaIc7IonOk7PBVFy3yzNxMWlExbjp4LdhqwUbhPb4S7n5a8i.png) 
            - 
        5. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/XOvvZeCJvrhpTcf7nXIMF8k55A6mrKyG3U296WFcv6gSIkPOHkH2Rc602pUZH_Whj4Lj79-n9FjqHOAxdkqtHkHJVl9ZxW8L5qDGP6d1HBFnar1KZ11BscqFF1tl2WdS.png) 
            - This implicit function will comprise all (x,y) coordinates where either x, y or both x&y are zero, meaning the function will be a plus sign on the xy plane. The result will be at (0,0) there are infinite possible surface normals, while at every other point there are two equally plausible surface norms.
        6. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_Avg0u7PgJxITQwfaoK-ZxNT52GGyof6YJk5QVE2BQfM5c-Yblz20LZ2GAdY4Ataq4mGQTFU-a_MaFFfvf9iVgHvOmqToxKhKC7QR_ayMi_JHBQoteu2v9_IpU64ziYx.png) 
            - Triangle meshes store two separate lists, a list of vertices (containing the x, y and z of each vertex) and a list of faces containing **indices** of sets of three vertices. E.g:
            - v = [(2,1,4), (2,4,6), (1,4,6), (2,4,5)]
            - f = [0, 1, 2, 0, 1, 3]
            - From these lists surface normals and other factors are calculated later.
            - b.) The geometry would be the list of vertices, while the topology is the faces - while the topology deals with the more abstract concept of the connections between vertices, the geometry is the actual coordinates in $R^3$.
        7. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5b-NrE_NjGIA3t1Pie8OKt4e2vKrQb0aGEiVYC18feWaJh1s4lBqocECCpVNjNl_kwKR7TgVZvI4ohGBSyx6JDtNIiWWCQAL3keyYAyPjwOiSm0iBdf--8-p2QTxT7wV.png) 
            - For normal triangular meshes this is vital for a number of reasons ↓ 
                1. The order of the neighbouring vertices decides the direction of the surface normal, without that ordering the resulting vertex can be facing the wrong way.
                2. The choice of neighbouring vertices decides the size and direction of each face.
                3. The neighbouring vertices of a given vertex cannot simply be calculated by finding the 2 closest vertices, using this method can result in areas of the mesh being devoid of triangles (a see through part of the mesh) or alternatively an area where triangles overlap. 
            - Point set surfaces instead do away with triangular meshes and use dishes oriented in the direction of the normal. With a large enough number of dishes, we can cover the whole surface and remove the need for storing neighbouring vertices.#
        8. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/-VeCFokgTj5THyvZ9IIAPBfs_rDbc2vueDR3P-iZKsbBo85CCQRpSbltC7kceuyif3ffjF3SdUKohuqzmg2NaaFNWw6MMhX426EWBs3ckHEEeNzNbU5r5Wk_zIcKXFe7.png)  
            - A manifold is a topological space that is locally Euclidean, that is for every point there's a neighbourhood around that point that is topologically the same as a closed ball in $R^n$. This differs from a manifold with boundaries, where every point is either topologically the same as the closed ball or a half ball in $R^n$.
        9. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/PEM-naJb74Gs19Jh3tbbGf2pnLbzQiIt9rIYBLAV4Bm8XlmA5QrjfRs-XJIO8331tIU_0KcwatDz0JKNb5bsf_SFNwup9jx5DvQMkV1MxrUlo281wdNat3crFfkZt3pL.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/nbpdkz3g0QTGfwXYz_2uyTwCzjPTci0hfo3j38PyEvqyPA088yUhPZ5S8DYrtRSILq_vxGpcjNg3QkMwnv9-36llrfMzauxSAe6suBcpPtRlTBnX8wVFVC2XpyvvoG00.png)![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/owCO8hXdTgMd1Uu6nRgpsMYjlfdPbQauA2SNjhsFi1qT1KChWZiOPWQ2wc5lGVQVMQfdRKSeiCi2lVIamb2ajAhP8GWy0CXh2qxqp4VqS5VpasWB9bJvmHrx62VmNRU4.png)![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/HWlUsLlt6unQe7NVpUwo4q0Gc5-_adujByQFIgxpjRBtUIkqtYtoSZD4PsLTo83IXYPrZJz6VV1TXFel9HN352HXyVBeMcMXFmX7ZLz2DNAjQHozIymb-KxK7D4UyiOL.png) 
            - 
        10. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/uIcH7WGA54QIVhJ0azN-JgKybCDazS3nb53Q8fSnOopK2AxZLIDjzNsZ8VpCt9qxZ7HhT50ZzvhMiKJ2Q7rWt_E34F9u_1Rrt8J9_pg8SHGHp-QrlBvN1sC46gpxcP5G.png)![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_MYCKA-U6uo18yOOH0vg0MJCh-VbzUD6JEaBhkdeMkUAuIFH7rWS059UxTsrSIjNBY3opRO67MSX7fzCVwzptVrt_8P5eDMYc_Bqa4NNvjThGIKDg6RhF692uBzCV3iV.png) 
        11. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/XXtkOh1iTv2VMWTab58JYFEVXFb0HN5cExyDfPZfweVMW7f-nE2JzM6UBNkxSJXBkftd9ZKZl27snfG1dDvMMdfygheG4SRalotI6yU5B46hgRzMJAUQGI6Geyy3yzsi.png) 
        - 
        - 
        - 
        - 
        - 
        - 
        - 
        - 
    - **Lecture 1 Geometry Representations**
        - What are the two main sources of 3D geometry? ↓ 
            1. Camera sampling (Point clouds) 
            2. Digital 3D modelling 
        - **Considerations for 3D geometry**
            - Storage
            - Acquisition of shapes
            - Rendering of shapes 
            - Editing shapes
            - Creation of shapes
        - **Parametric Curves and surfaces**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jij8LnlRdQqRvRBAWGGdAQMBmBAFtnPIX84u1QnPQlrCKIOQJnD1KbTRNX_glroP69oKsNKhXOxi2qyMepdHfb5THuZ-07L1y9AX7YuqIzediVK3zAVFe-NmwQ3Zo6m9.png) 
            - What are the three fundamental equations for parametric curves ↓ 
                1. $f : X \rightarrow Y$
                2. $X \subseteq R^m$ 
                3. $Y \subseteq R^n$ 
            - Where  __usually __ m < n and infinite samples of the function result in the whole geometry.
            - **Planar Curve**
                - What are the m and n values for a planar curve, and give an examples function ↓ 
                    - m = 1, n = 2
                    - $s(t) = (x(t), y(t))$
                    - $r(\cos(t), \sin(t)) \space\space\space t \in [0, 2\pi)$ 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/f2zAZKGcOtm5cobCTsjFhv6Fdm2jafuCJtEazRN8u1fwJ-e9yv5kPMD2VnxBSWfibY_v5A0z5U25qKn968rSEQSoLLgcS-WlC503hNYuG9Jh5b6R0Bw6lWPaEtU2jpaU.png) 
                - 
            - **Bezier Curve**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/G_qXB6PERNCbBzvO_5ofEPkcZqZFNcDgss5N4PEJVEToDvw1xg3rlBXbOhEpkB5WGi2vVuIbiEib8fR3WkzywVfW-yDihEDZLk6dR69RHs9kkcb7UV_a6svTZ0dsUKFV.png) 
                - $s(t) = \sum_{i=0}^{n}{P_i B_n^i(t)}$ 
                - $B_n^i(t)={n \choose i}t^i(1-t)^{n-1}$ 
                - Allows for moving smoothly from point to point
            - **Bezier Surface**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ZE9Z9UBBbLbpiGj7UYd_gZSWf4HHEub6Iy-TWItU3QlrIOG8lGMYJ88XNuqV1tkLO5g7oZjcl2yQ3-PG_SQIaGAeSRLNXd9Dm_mUloD7Yyxb2l5pPC57N7sGLddAKmaz.png) 
                - $$s(u,v)=\sum^m_{i=0} {\sum^n_{j=0}} 
 \space P_{i,j} \space B^i_m(u) 
\space B^j_n(v)$$
                - Where B is shown above and P is the height of the control point of each vertex
                - A Bezier surface will always lie within the convex hull formed by its control points
            - **Normal and Tangent Planes:**
                - Give the equations used to calculate the basis vectors and normal vector for a parametric surface ↓ 
                    - $S_u = \frac {\partial (s(u,v))}{\partial u}$, $S_v = \frac {\partial (s(u,v))}{\partial v}$
                    - 
                    - $\frac{S_u \times \ S_v}{||S_u \times \ S_v||}$ ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/W0TDCq4d8uKp1i4ptIwB4wG8Py776569voOeqwE7HOAHqgZZaUPDZP1UraYIbiGfYAnrbnfVn7igdp5jIkBk3bUNu7BPxu1MVWxn8UKeFuK_QjoVzgOrqCm4rk3Klk-x.png) 
            - **Volumetric Representations**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/aFvD3btV7B1EOl8_jCMjS4vvfbnDY2LWxNnfD92VeckX4W_4Ot5HcSN6IKF_zCESGAGAJNJsngr2EWqySoex2RoWPyZ4F0LQIhelvG00OOGt56pDBpqC-xwoAZeLfFD9.png) 
                - $X\subseteq R^3 , Y \subseteq R^1$
                - Forms "density fields", useful for medical Data
        - **Benefits and downsides of Parametric Curves and Surface ** ↓ 
            - Benefits ↓ 
                - Easy to generate points on the surface
                - Nice point wise differentiation
                - Easy to control
            - Downsides ↓ 
                - Hard to reverse-engineer surface
                - Hard to decide inside-outside surface
                - Hard to decide if on the surface
        - **Polygonal Meshes**
            - Connected points that form a piecewise linear approximation to the surface
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/pVRbFTJiQ_QCs6i4Y2_KVqFIlF1n5sOjiJUwECTh8Q0OvPRz104EIuSfphvZzmsxnem5MnmDMlP8p2bPcy8ryFn6wYD8cGll_AEfCN99ozHuK-kN_QyLeLqXuckNysxI.png) 
        - **Implicit Curves and surfaces**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/OSyZL75cz9VCR7NvHHYyt6cgxA0xiF5C_u2ZT_qyb3PRulP0uzR6tO_6ftdws0WHs_aeJf3hrDffa-uPV9Z2CgFcu8lQT0v4XW1cqKxz_U7HJB-6MSxcbYvDCffYIl7n.png) 
            - What are implicit Curves?↔Curves that satisfy a given property $f.$
            - What are the two Fundamental equations of implicit curves and surfaces ↓ 
                1. $$f: R^m \rightarrow R$$
                2. $$S = \{x \in R^2 \space| \space f(x) = 0 \}$$ 
            - What three things can our implicit function tell us? And what is this useful for? ↓ 
                - $f(x) > 0$  Then we're outside our surface
                - $f(x) = 0$  Then we're on our surface
                - $f(x) < 0$  Then we're inside our surface 
                - Useful for collision detection
            - Example usage:
                - Give the implicit function for a circle↔$f(x) = x^2 + y^2 - r^2$
                - How do you find the surface normal of an implicit function? ↓ 
                    1. First calculate grad of f, for example $\nabla f(x,y,z) = (\frac{\partial f}{\partial x}, \frac{\partial f}{\partial y}, \frac{\partial f}{\partial z})^T$ 
                    2. Then normalize the resulting vector
                - How would we find the surface normal of the implicit function of a sphere? ↓ 
                    1. First note that the implicit function would be $f(x,y,z) = x^2 + y^2 + z^2 - r^2$ 
                    2. Then take the grad of f, $\nabla f(x,y,z) = (2x, 2y, 2z)^T$
                    3. Finally normalize the resulting vector
            - What are the pros and cons of implicit surfaces? ↓ 
                1. Pros ↓ 
                    - Easy to Know inside / outside / on Surface
                    - Easy to combine surfaces
                2. Cons ↓ 
                    - Not suited for real time rendering
                    - Hard to generate points on the surface
                    - Limited set of surfaces (for finite functions)
        - **Point Set Surfaces**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ezsxBHc9t5yBc3GfDoiccHryfozIxDjLE0beSaveN-VUt20FKhBkAs5eExIE-WxU_eiVIDWLodZpPCx_36B9SR0uV72ZJHl2OuTGf8zNaLc86vYCDi3F_FVQV2RFOMKl.png) 
            - Point cloud ⇒ a surface, end with the analytic form
            - What type of data can you use for point-set surfaces?↔Only point wise data (position, colour and sometimes normals).
            - Approximate measures ⇒ Smooth surfaces
            - What is the process of determining if a point is on a point set surface? ↓ 
                - First examine a region around the query point and map a simple proxy surface (line, plane, hyperplane) to that region![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/LVdEODyX7e5rr0D7IF1K5ENp7bN0Kyw8pclpQI6MfUzQYeFxTzxaXwRJcISTG2WXVc0263NC9bHnLz1I_s_PS6HIc1Hn3R8T5qUr-WgaHwTbkLGBqw7fjI_z9muuF2uH.png) 
                - Then if the point lies on that line it is on the surface
            - How can we project onto our point set surface?↔Using our proxy surface, we can get the line between said surface and our point and then project it onto our shape. Using this we are guaranteed to end up on the surface.
            - What is the resulting function after generating a point set surface?↔The result is an implicit function ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/b-PQYvFpJ5nOnDjLgeClezXc7nPGedb19FXDjcDJWKB4kWYIbghJQpzk80BlZ0thAfuLJ-knQPv3kSJzpA-hFdAhF9i7FT4vne5YUlO7olHcjeb5mrTHb7p_K5A_j4Dr.png)
            - Give three important features of Point Set surfaces ↓ 
                - They are robust to noise.
                - You can do direct rendering with them - can do rasterization using disks and surface normals around the points, rather than triangle meshes disks are used.![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hyf4-cGTIQB6M2_d20tHFIOEzJvtBcr7Zgfan8pnO_GBVSlOHPq8BNUSCxImeIDVsfhtz7od8HgcDY_Y7wBmPPV0wiUEh3y6gBNHfUaFvHzOESlZ1W9_yauMI6OsPCa_.png) .
                - You can convert them to meshes.
            - What are the Pros of Point set surfaces? ↓ 
                - Easy to determine if inside/outside the surface
                - Easy to generate points on the surface
                - Easy to determine if on the surface
                - Can use real world data - robust to noise
                - Can render in real time
            - What are the cons of point set surfaces?→Not efficient to use in some modelling tasks
    - **Lecture 2** **Discrete Differential Geometry** 
        - **Manifolds**
            - What is a manifold? ↓ 
                - A manifold is a topological space that is locally Euclidean (around every point there's a neighbourhood that's topologically the same as a closed ball in $R^n$) 
            - What is a closed 2-manifold?↔A surface is a closed 2-manifold if it is locally homeomorphic to a plane everywhere
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dKte5l_PI2Zm2NUj4i-Z275X5hPPeV15rfocqZmS4pNznAKURVu-dJQ2rAU7xMNx2qlXRw_CLYmWsIrF8KmhCQPr1XGGEMbbHj9Pmt7-7trIAjl1wahOzEvawX__l_4u.png) 
            - What does homeomorphic mean?↔One surface being homeomorphic to another surface, means it can be deformed (without piercing or pinching the surface) to become that second surface.
            - Math definition: 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/51gnM6JUfXL6wRogOH_bI-CTnPszmLiWWgdsmrRPopAai2XtfQNxsRA7iOgBdkiCa-0VrIV5i9ShHb5oXojk7G2DE0WZQmX3xXW0L1TUE7ZjZvsWmpBS-RkFGHi9YF2s.png) 
                - I.e. we create a volume sphere and get the intersection of the sphere and the surface and we can map it to a circle.
            - Manifolds with Boundaries:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/f2sNy5DHFQ7BmN09_acYPmqzWsLvEGCdqgS9iV3wZNBBAQQUVMT4ME-vUoYFStvFbVnmHlfLXVX6HIAdol28njMdslDyhepZIAIxn2geKpKkvIp2aITuRpK37fU_s1Nu.png) 
                - Each boundary point is homeomorphic to a half disk
            - We treat local areas on the shape as mappings to a 2d plane, we can then compute differentials. We get a continuous 1-1 mapping:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3Tz91ygPntWjdga7fwAFjx81uL3qA3c1t13TsPymjw-mfTnaWO3xYQ4xO0KXuR5NhuNVGSVfS2d8GLjz0NrFSMI2j2ZGapybMTT-pwzw5oMVF-cj-Y8ijaJNyf6q0w6p.png) 
            - 
        - **Local Coordinates**
            - After mapping from an area of the curve to a 2d plane, we can define local coordinate systems and thus a surface normal.
            - $$p(u,v) = \begin{bmatrix} x(u,v) \\ y(u,v) \\ z(u,v)  \end{bmatrix}$$
            - $$p_u = \frac{\partial p(u,v)}{\partial u}$$ 
            - $$p_v = \frac{\partial p(u,v)}{\partial v}$$
            - Having created this orthonormal basis, which is a linear approximation to the surface - we can then find the surface normal $n = {\hat{p_u}\times \hat{p_v}}$ where  $\hat{p_u} = \frac{p_u}{||p_u||}$ 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JaLVopTxOR2dzfUFnUOAOtId0SwnHmuJmT-7lhnt8yN2DJAjWt_wtUdElqImTuZj0gOI5yp8Cia9yXs5ZRUbQCU0TXOOfD6FsEH0aISXFn9pb41wauxQFsdRp4r4L-Ms.png) 
            - We can then define a vector t rotated within the local coordinate system $$\hat{t} = \cos(\phi) \space \hat{p_u} + \sin(\phi) \space \hat{p_v}$$
            - Finally we can use the plane defined by t and n which will cut the surface:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/-8Brlr1ugBaqXwEtdburKdWwts5IXK0KGgKbn3JTXIkCuBsuALdoLB-HJtlPx9gVII5CYpRLMP2RKb_8N5sgKdCvDA71542HKTaTYdAjrYe-BZSKmbS3JbhLBINtZCEZ.png) 
            - The curve $\gamma$ is the intersection between the curve and the surface, ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/B-hT4tHdYddzp1HPoRVNY0Sk0zJvW7pxz1QU3aHbpGz0ZUxT8cBJXYttuWf-vVuY4E69oB21phun1HRg6SuThqqaMbL9iA_q3Ol15hFj7gFww_hI7bKujdxHLz8HqBTi.png) 
            - What is this curvature we use for minimum and maximum curvature calculations? ↓ 
                - The curvature is the change in the tangent lines of the function as we move along it: $$||\frac{dT}{ds}||$$
                - Which is the second derivative.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/8EL3m2BKkI4-UtrtZGo2GDfHjMyNC-d7qJMKBCBS5_yz-HVrEPAsVnFXHwhlUwkZHANreEdZVGid5-uIEwaBcvFnqR78IsvKridxLnHBXt8pNc2tFi3ey4ZblmatvC8b.png) 
            - What are the principal Curvatures? ↓ 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zZFXEjt9KTY2MuWviuyzubq7nOxf_dddcS-iYeMJSJIX_O7bA5kcs8V-LEruq0dxKkcO6VNAKQec0ydo5f9huOYiLjoYKW5m34irU67gDY3WITlo-vq0LMAuy_5HsUmX.png) 
            - What is the mean curvature? ↓ 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/uI9S-7wP_kjtF1oI7_N8nF77BGS9FclFmtA2voIl9QU5qvMIAj0bnLKTLLcQMTEBZ6KTAU2yGCHuesvHm6qa6uNOUAksFQfKS2Boor5cLkUwycNlhjCaD-M12JwSrOy5.png) 
            - What is the Gaussian Curvature?
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/o_Of_U-l_rzIc_3dsrGGLIYZl-jFKCSXe7CMOq7Tv-5QbSl2F7eEzU2_emGPVC541PXjfc5DbNAzonYQD8Xzo3B-CAKN1ojRsnADJiW9zCHamXlLx1wdc29bgBDg0AIk.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/qFKiqndLatwB-2qb8juCneDmGFXkBxx3RHtzZMeLIjm6KPKlTVtSheQJ_SPB0dJNuGuwfm8RTHTxe0hdHLuFUUXsV8RV9sW4u1eIQd2h5qEntL2riDd9c-nF6QUU35Xv.png) 
            - What is Euler's Theorem? ↓ 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/znH-YE5uWUdRs5GdzTaPML-Buo2lQr7pdPjhaGS5PodRGR0Zhtw9KtKbQC9xYuiULnQqIaBjXcNzCul6Mb7anjnxG_JwSHmavEqZRW7BLhWzVcH3aLpspPerOjC8Bhkj.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bkQksDnoG9sHaytQuyOCfQ9BG44Nw1-It0AFWYaLUHGiwPHrILob9f5rTwc-UwZfvXeKovInsNag_oD4ZnyS_K1MKHJczu4tLotflOfABWSrRfcCmGOMYXQwTxonm-QP.png) 
        - **Local Shape by Curvature:**
            - Isotropic : Same in all directions
                - Facts about Spherical ↓ 
                    - k1, k2 > 0, k1=k2
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/FXocmZ9XYMUx3J4DnvFroQRfK_jpMQESHrLrGV7r3UX11vX4nr7kWRtEX8ff9gHWRPjoCXtxNUTUVqXYmp21lu63eW7Dc5zRD80mTldzbdEExc9QJCMfmb2LGvHgnZpN.png) 
                - Facts about **Planar** ↓ 
                    - k1, k2 = 0
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/UXK5d_EUdwEUhlAAV5jaJ0ZzN3QfBKikVGFUiAIbXKvm5fNZ9urNR3Zbe3zl3TdDF0bQ154zHoCVL9l6c_sRK-UP8eR7z3UJQEUfJxRZeQP2jyRgdL1RrD-oP_aeiBZm.png) 
            - Anistropic : 2 distinct principal directions
                - Facts about elliptic ↓ 
                    - k1 > 0, k2 > 0
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/01C4IoMzLHL7XbEetHy9hOFKX-09xE6GDIBQabk1hQRnznxdnX3c2xpTOrU8f4vnur9IdlUjkPzbLaUjP6tQzGjm85BfknmvwIpVlSRKqY3i2XLqiYzByNWCBsUrHat7.png) 
                - Facts about parabolic ↓ 
                    - k1 = 0, k2 > 0
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/l_M41qvVCPcHecuIqpu2eSHL2K18NgRPTJqGk3pjVyNrH80jKdNtp8rbqobl4KlLhJwd9N9Y-UmQteMGKX9RjH6DDLLABaJvh2qcwwIs4aYpl5pvNx_-W4FONFZ501tP.png) 
                - Facts about hyperbolic ↓ 
                    - k1 < 0, k2 > 0
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TLMhicO-U_9gxvd_t7-n6su7GwssPb5gPXqF6D8jBSqafojBsoo2_1go-LkNay2dgbUyLhMuI_I35Df-nj9eTFMLFawOaqpofYT13UXhpzrXxClFU0BqvFpasOvVtpgu.png) 
        - **Discrete Differential Geometry**
            - What two main approaches are there for approximating surface normal & curvature? ↓ 
                - Local surface approximation
                - Global surface approximation : discrete Laplace-Beltrami
            - What is the Laplace operator? Describe using its composite parts ↓ 
                - $f : R\rightarrow R^3$ $\Delta f : R\rightarrow R^3$ 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/AQHspVFkjdkY5T4ATL_BfZKdol8X_jMbzpuLIjbUuKxcf6Oo9tCuV4DF7a4coqV884PPL-ZuWo9K03tHeseRp3D4abrrdaZpPoIsHbXAg3Rv7Wap-4296ID9uncwVxHb.png) 
                - Grad f points towards the areas of most rapid increase, e.g. pointing towards a peak and away from a trough![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Cp5sUp1Hglr13hoB9ygBDhUrilQ9bG29O20JunrwdmmCrY_Aj2QOWdAvWlFyabxHXB9DZggBIqabgNCrlk8_jRg9q7K22hk0MFnR6ktGcegzlnmRQIcK1cEeXGQvBT-r.png) 
                - divergence can be imagine to be if we dropped particles and imagine how they would behave under the vector field, positive divergence meaning they would move out of the area and negative meaning they would move into the area.
                - So the Laplace operator can be thought of as a 3d differential, higher if the curve is increasing and lower if it's decreasing in an area.
            - What is the equation for divergence? ↓ 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/LnvQlR7K5uT3b4I8jx-vuUE1HxoOwDx2SJLvpXCeQhWo1hXyngmN_KeybHpBtPNkxJRDb0Nt30GCYnKoRKPZCdrFS91NUZeLl3Ksp8VXUoGtnUu6b8MVvmy-5IFpePFF.png) 
            - What is the Laplace-Beltrami operator? ↓ 
                - The laplace beltrami is the extension of the laplace operator to manifold surfaces.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/YdVLZ1lEJZ9Op8zdiQyq3hw1JdjASQ6LSmwPLXbzTQ7XRgKOp8VxaaRqD8bo7s6xU3SYZBLfszxVo4HeFqiJxhGJb-OgNE-9irDsr7gFBrfMbWqDc94rLP4IbMx__P_P.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/sK3lbCjN0RoQpKxLtelEvmg76R0hYeT7VN_UzuYMNrmmRSO_GCT_cGk3RpnM90cX7oNC7_Nnb2EKkKubwdazvWRabafL4GTizZ8T0Pe0KVL0dER8s_8NAYNIEqwz8qpn.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/icIUVjGxKotBfFMTmkn5KlfQAOSbeYJhF0q-L382TejUVBsRX1D9EtJbUIlSjwfQsFzZjxoSRUiBZ1vp9dAV_RXzGU8Z1TPwLfO3zq-ik-auC30qpDIEoFwqLjmtRS9F.png)
            - The Laplace-Beltrami for coordinate functions gives us -2 times the mean curvature times the surface normal. This is useful as we can calculate the Laplace-Beltrami discreetly and then use that to calculate the surface normal.
            - **Discrete Laplace-Beltrami:**
                - Method 1:
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/mJlIrYRU2cGwqnA_93w1-6enQHprSmwvnFO-sCxo-pjtU6nmRuatH_cXcgkJle9fFdeFQvtRpcx7P7GXBAQW459Nv1-9Zqosop9eiJsGk6MYHgipTlbrbOS3AorXAEJR.png) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JiZp0sH3O03p-BLspz-B9xdanb7G6o4ewv8lxHu_uvL_DLo0KmTu_yJZMGTJHatHeBVKoaV7wZhtUIP6pd6zO7uK4wDg4VAejEix7w8_mjeOD-H6d4C4D2PMgzo1QgLq.png) 
                    - The first method of calculating the Laplace-Beltrami is to calculate the average vector from a given point to all it's neighbours.
                    - Resulting in:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/IZd6ZDPxYXxMUwir1wc1ozsRmDAS0kj991y1VryOoxd9_YRZmUTc13bcNeV0eypOVHSbvTaRU_y_MGiNmlqyHnVpJS8FnTL41N20YEPVb8twbFEFrvl7yKuI5PpXNG32.png) 
                - Method 2:
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3JHJT7Qjw9p_4Cdb4ZCv6fIZJqNlR1Pkw96JrtIG2b6CxzFaGjYOs5jTcffMWnJbrQQiXBqbDkTH-JZfx0vY4QQmRnFHL5RKZUW2qYuXgwWa1XPV72pTqPoC9H3xmGHe.png) 
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Kj_TKwMNKF7tIRV3pZWpJybJD9MNftNvHDilcnmXGJY37r1BLjukV5ABnUlyH6CCTKvIXQkYvPv9_pllWlAmiXzALGG-Km7LDaUKu9vlV0zDGxdVVBzn9W_syqU4t-CG.png) 
                    - First take your neighbourhood and flatten it to a plane - then find the circumcenters (or just place the point on the edge if the angle is more than $\pi/2$) 
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/coHWS9QvP0MY3wzL4WUmItishrY7ZDgBwZG0UxMNPtCRuTyQRZAz1W_E-PYBqChf7bLXgXbag64QykG9dXk3jH303anW8DI_kBagt8xeL_UuVswtNWoCPmxEBxL7Lutj.png) 
                    - We then get the weights which is the area inside the triangles:
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rH9vm-MWTQv0PYxKOJIHC6wgrJTMN1HmHcmIxLAcLsSkOO9xbJpFnwhs2FOIvluPkJE_wMi7qOGSNIPt-MCWJCdQsyWtN7ekEwJJMsjpHbEbnheTe2dvx1_uim7kcSSI.png) 
                    - We can then compute:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/t4VYeXmxmvcIvYdZB31dwCImYhbr3l99RF0EypNX_nlLza4n4M2PK_OtXoV34GMqokBvQhZE2dUkrD55b85kAvDCPjyDrRr_9uN-zVRnZnhoixvOUf5scICT_DMNd_6i.png) 
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/D1X9bGGmh6f7AaUXpVjB_zROuWvwBXu98EF92mptAPmYyAF51si5aYMAOz2okeODANFw5EbES_QZ8luji2C6A4nHSCkTtlbHAw4MpOmVnnjnz6TgpxaVH8WwakPufh0W.png) 
    - 
- Concurrent & Distributed Systems
    - ^^ _Concurrent Systems_ ^^ _ _   
    - Supervision 2
        1. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Swiev7gzpJr99rrNiwQ5TgxsXFzzJnb9TDsw3XEAIPEcszEutqMEGgth5IkZjGmHMjrbrsUpMTebpMmwY6gia6b6fzs4e40gkgUjNsAa24VjL1d4CfQ3xROkgAYKh1rb.png)  
                - Atomicity: Not necessarily true that we do all of the transaction or none of it, as we could crash during the system and we have no specific roll-back procedure. More work needs to be done to ensure rollback should we crash - could copy shadows of the data.
                - Consistency: Not necessarily, one could still for example remove money from a system - invariants not necessarily preserved.
                - Isolation: More work is needed, as we must implement strict 2PL to guarantee this. This falls out with strict 2PL, as our work on the objects is not affected by any other threads as only we can access those objects because we hold our locks.
                - Durability: The system can still crash while running commands, we now have the additional task of having to release locks after a crash. 
            - b.) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3www75KrC9L4l9rLhFcV3IN-01D-iZpqMqQg3uMdruRyWkCnPbJNPuERRhQogTsi0qvReyD3RoKQC_EPUjkAp8XfhCp67_aBwKbHr5S6_w5A3z7S0n1FF8nscRIkJgRr.png) 
                - ```c
Serial possible results: 
	T1: A = A + A * interest
	T2: A = A * (1 + interest) + 100; B = B + 100;
	(A,B) = (A*(1 + interest)+100, B + 100)
	OR
	T2: A = A+100; B = B+100;
	T1: A = (A+100) * (1 + interest)
	(A,B) = ((A+100)*(1 + interest), B+100)
``` 
                - ```c
Interleavings:
1: a = A.getBalance();
2: A.credit(Interest*a);
3: A.debit(100);
4: B.credit(100);

1,2,3,4: Serial
1,3,2,4: Result for A: A = A(1+interest) + 100. Conflict Serial
1,3,4,2: Result for A: A = A(1+interest) + 100. Conflict Serial

3,4,1,2: Serial
Below will be Conflict Serial: Doesn't matter who we arrange change in B, since 1&2 dont alter B
3,1,4,2: Conflict Serial
3,1,2,4: Conflict Serial
```
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tzUTAneZ0s9AsmnNR00hdVj71jlOLoBLAjVEsRjWBDQPY5L5USmZY5KjscqZIsDiqTD8jfVjRTYrvmwV1b8RUCJhAUkQTtrvbwM3XZjAplhqnONhEFVHbui1ZWRKevyf.png)
                    - Because with OCC works on local copies of the data, and only does its commit right at the end when all computations have completed. Thus, if a computation does not complete it is not committed. However, with 2PL commands that augment the dataset can occur before we commit - thus crashes can occur after augmenting commands have run. We would need to implement some form of a roll-back mechanism.  
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ZxmkFIv7FVtFhWDGJNEmNntWkAPkBx0ji8GPHQCqzvHfPji44haQVbAwjVhOwWcShYuKjSG_iE6O-BQG920FrNyxo199WYCRcGgZHxwgH-GGmlqjXWM_oMQorNyEzdjV.png)
                    - ```c
T1: 
	lock(A)
	a = A.getBalance()
	A.credit(a*INTEREST)
	unlock(A)
T2:
	lock(A)
	A.debit(100)
	lock(B)
	unlock(A)
	B.credit(100) // If T2 aborts here, T1 could have acquired the lock of A and done some work, T1 would then have to abort in sympathy with T2.
	unlock(B)
``` Strict 2PL would have avoided this problem because no work that could have caused an abort would occur while we're unlocking A & B - as we do our unlocks at the very end of the program. 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zeXb8Y8jfZNbfPh9thhE-nn5c8NptqY5l3TRNLFjBN-_NmXcNv-ZlkWqE89Y2A32wrZ-0fW1nu3tr3ILAENnmP1Ce3ZIQfr_2lTbjlgcvWlwCc5lHaYQqKbnIpnVbWLP.png)  
                    - If the program crashes after having written some object updates to disk, as then the transaction hasn't completed but has still changed the state of the data. We would need a roll-back mechanism.  
        2. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/8Gmm-oC6vjMBJtvL4PA9fP7zCsvZyUlL-qzd3B5wtClDSZDbUl5q09Pws4pc_mrRL3mN7NYIIt4d7PPbQQDrCecLxizAZhJgkym_3PnZWsJ3OqZv6xe6wz3Xm0-eaq9G.png)
                - ```c
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C
// A deadlock is now in effect, no further work can be done
```
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/A2Sp068a8HqNXoBYDmO99qWukv3ScfW2dHTrDsZ-xOUwZupjRty6_bn1htMfxrytwMjq1Bd2bc-rqRxZ3bZLMwdO5UgpqBvhTH5LqtcHKAdLzNZfx0_TrvbYcO0pBqox.png)
                - ```c
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C
A Deadlock will be detected at T1 all processes will abort.
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C

This process of all processes aborting and restarting will continue.
```
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/FE29KtXxq3a2RPGt-6SQkq_ZmPfUGq4obesyhGD56B1hBGbiGG4E2FMBGdDaxaencwVoGQSKI0QUGaUewM1vpjHwiFFLuMjJKYsDaiHF1uXhuXkMGjBmefVzFzv66yXG.png) 
            - When deadlock is detected, we abort the next thread we operate on and continue. 
            - ```c
T1.L1 // T1 now holds the lock for A
T2.L1 // T2 now holds the lock for B
T3.L1 // T3 now holds the lock for C
A Deadlock will be detected at T1 and T1 will abort
// T2.L2 skipped, no lock for C
T2.L2 // T3 will acquire the lock for A, then release locks for C & A
T1.L1 // T1 acquires the lock for A
T2.L2 // T2 acquires the lock for C, then releases locks for B & C
T1.L2 // T1 acquires the lock for B and then releases locks for B & A
```   
        3. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/vN_VbUS8amAxLCs-AOhqqxAur_W_tYyXlN2WybuBBo5j7uiEavHAl7gChERgXUax844uyMNik7Ls2WjWzgR_JehImsbRLJySqF3P5gUnieydjoYVyYrZJSH95wDSm42u.png)
                - ```c
T1:
	a = A.gb()
	b = B.gb()
	return a+b
T2:	
	A.debit(100)
	B.credit(100)

Interleaving:
A.debit(100)
a = A.gb()
B.credit(100)
b = B.gb()
return a+b

T2: timestamp 1. T1: timestamp 2.
 
A.debit(100)
a = A.gb() // Abort here, as V(T2) < W(A) but final result would have been correct
B.credit(100)
T1 -> Gets new timestamp 3
a = A.gb()
b = B.gb()
return a+b 
``` 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/CPdhUdYYYwwg7iW6ACw3pMXPZmGXASdwc5aRJ4MdLmnuDbdz7WN9ACNex7r5uCM1tbFiRDOHXE4JoVgyk-DNkIAi0G-RnVexfzrWOclPFaUgPI8VyB1G8HHobO6nxjed.png) 
                - TSO can result in situations akin to an even worse spinlock - This occurs when a thread needs a resource a later thread has accessed before it, and thus the thread has to abort, like a spinlock the thread will be restarted but will be spinning over it's entire code contents rather than a single while loop - that is all computation before the abort needs to be recomputed (To to ACID requirements). So, if the mentioned resource is never freed the threads could continually 'spin' over their whole codebase - continually computing the same results and then throwing them away. 
                - Also, for a multiple resource case - a live lock could occur when multiple threads are trying to hold a lock on all the resources:
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gJrEJWDYlmX2Q9E3k9-OCYAzelh1401QHiC5_6LVvhEBgXMmKidk9IVDW15tVHKE1PDebbVxV85pL9ojHgKOXuy31beFjQWPscTcmuqqTOPlGdfMEqvQFX_NTn6yAgno.png) 
                - Case where T1 gets lock of R1, T2 gets lock of R2 - T1 aborts meanwhile T3 gets the lock of R1... This pattern would continue.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/QEfpCL6My-m7761W-3ZbSyaqMfX5WKrbxSg48JYQR1NDZXX__BAGkf5jkASIGBZG2nS7G7XjCNXMmeRvWUhep_U31MN9Ox7KQZ_9L6paneWAQ4_U67n1fdftT672yiRQ.png)
            - ```c
T1: 10
	A.debit(100)
	C.debit(100)
T2: 11
	A.debit(100)
	B.debit(100)
	

T1: A.getBalance() (0,0) 

T2: A.debit(100) ()

T1: B.getBalance()

T2: B.debit(100)

// As OCC distinguishes between write VS reads, while by default TSO doesn't
``` 
            - d.)  OCC executes transactions against local copies of data (‘shadows’) rather than globally visible 3 original copies, which avoids the need to explicitly handle cascading aborts. However, copying all objects at the start of the transaction is problematic if the set of objects to be operated on is determined as part of the transaction itself. Why does on-demand copying of objects complicate transaction validation?  
            - Because using our current system, the previous state that decided on demand the object should be loaded - could have been referring to an earlier version of the item that has since been changed (by another thread). And since we would be copying it on demand (and thus getting it's timestamp when we load it) we would have no way (within this system) of determining if this was the version the state referred to. So the transaction would be valid by our current system, even if the object had been changed to a different (unwanted) object just before we actually loaded it.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/IHsATz-UZGEawcPlhHwr-fQBPo2GeTACbAb6eaeIyZlNZb2M1CPnhclXl_dtuQsY9L01l4AkOEF4_QID_hg0tOnjvjGX8jTB2cjuGwT0SbyXybhL1XMkkyK_ejpfoi_r.png)
                - Because TSO aborts simply when transactions don't follow it's one prescribed schedule, while OCC seeks only to abort conflicting commits. So as TSO aborts more, more live-lock situations will occur when perfectly correct schedules are disallowed.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gslF3mNNmDHVxaPjwqK3JmnsluwJTXFPvI39tdrA2MQg_Sp8cZXQCJVJw3CUryCqRKZ5IWDZml6eoKi6e5KVvT1q-qCptOaRxVa6gA7O_j7To72jCGQVF-Oy2sN6aBYE.png)
                - If a given transaction does a lot of computation in it's body, it may be slower than other threads who use the same resources - in such a case, the thread will continually find that once it's finished computation a faster thread has modified the used resources, forcing us to restart our slow computation. Consider a case where we're performing a statistical analysis of some database, this is a slow operation which will require shadows of multiple different fields - meanwhile one or many fast threads could change the values used in the statistical analysis, meaning once our slow thread has concluded it discovered it's used stale values and must restart. If a database is continually being added to, the slow thread could be starved forever.
        4. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tt68NLsWYZBlsWdYWq-ZfTPlVMtMZMMxIeiiadDE8gkDHP1rrUj30jF_zmobxPhdwmMZ9LYWpyJMFLTYJgpBUFZwBW8QFW9gfS3OShawlETDGMD_se7_T7r6TeG6hnW-.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Fh51IxHMCTYmMkjSu0vg7Zr9psKsZquDCBnOGirStWM76-uwrBGw3Moa17c4hOgwhMUMZOMA0CCOevAty9w_g7YMxf9LjNugU7xThtFkM3Vf8LCSTmKMMXnSbAjFqIcT.png) 
                - Edges represent a "is-before" relationship between nodes.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/h-UuK42dzShBvMy6BZKKVy9nxj85tKJTgxX6fY000655jnaru8NGXJEZ94y2Oc_HSs75GiIB41jfWQcIrJ8M1ViUwOgwAsPRq-8zxfYAbFm13xzd7ivT_XLIPrjuX9B3.png) 
                - A Cycle will be present. I.e. both threads have operations that occur before operations in the other thread - a temporal impossibility.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/k9dHfdy-m5Bm1Eh4nEabAx6LZQo4HfDy5d7XcTZc9ZLOc87gNUEhqyyianbsfSc-0y-QXgxdDKkJ2j7dYa0nlJaeQScECu4ifV3BcNMKri-JIlFhwagPLhzuvDerZvxQ.png) 
                - Isolation & Atomicity
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/lsFX9NuhzszQ6riLY5SF10nNuNddizzb2_KRElUbL73415zKh3CQen490K6g0gEZ4CQiU_un_kVQ4SUV86nbwqyTn4fm5gdJLjSqnvUsIpnjC6DVt5nohO5ezn8spbCN.png) 
                - Serial execution is when threads complete their whole execution before another thread can begin and complete it's whole execution. Serializable is when commands from threads are interleaved, but the result is the same as the serial execution. Serializable executions are a superset of serial executions, as serial executions clearly produce the same results as themselves. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/uXFO19F5I8DmY5Z7OaAZvp1OCZxkVIdYFBPvVU3CH7wsdY0yXABb27KDwQhcXAxFWV2jDo0GdQCURa77rgG7UBmwHX_dZ0c8pnZJL5izrJX03bYhPyPSZjJKqTDaqw3v.png)
                - A dirty read is when a thread reads a value that has been modified by another thread, hear we could read the value of A after it's been debited (a dirty read) and read b before it's credited resulting in a result 'v' less than it should be.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/qvlb9mw6AyME0cDsNXhKYb5hPJHHP8jZCC2YSiNwg5GH8MTA4oIHZkKCLgs7iQ96f0__8rfLHJIt3-RbJyDVpn7OgwFWnWGaM2Q2v11sn02SX-n2KRZcGzsCVF4CdFPm.png) 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Ah4OrMb9r7ElHo9fqdvI3fits0ZlHtYDXNv5C0LxsOnCMi1PEYfKS1j7Gxrpqo-ls1s3qoHqq-PmZrtfhIMZ6mGrOGESeSMf_yJsOOJKTdqEBziY9QtbWTdsHpa_Dadc.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Dq_JxVQqJdUaj6lqnlApNCeWstzIj_u0XzVkiOIVwyfUlxb8htFtTObOn340pTU-tVbtaVwprsSKa6GnLTKzquscQgSw3MDMfWTdDLQY5ql5am_9kJNZvcZ8XAfxDS6D.png)
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/7rCJGSabjZmRl1LewnIgITcgke_b5wYjbn4wOGZI5HDIY7q-QNd6xKWmFnHA_yo6l9c3MpUV-stiEmAP05LuKZyyNJv6K0tPCmly-W2RnHqnq5noQABzyfvk_lr2qOia.png)
                - Not necessarily, after roll back the transactions could travel along the same execution path and cause the same commit error - resulting in livelock. However, there will be some cases which are solved by this addition, at the cost of large overhead of generating and testing this graph.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4KdOPCU5sQRPvkY0iFyRQMmkUlkcPEKxeLPdF1ldpMQ8VgM8VbJyiB3mSW_EUC4-b7hFhKs-EIeE1qpsdhuUYOW6H_Vvp-NE_8HZQhN_QyEdnDO-WFfeJGNuoCI_m9WJ.png)
                - It accepts more, because it will never reject a good schedule. While TSO accepts a single correct schedule as transactions come in.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/43Q_Ib1cOqV0P8xcRYdZMwJmJt1eP3PSh7ie0ZEadmfnt0Vw7ljIT6_I1Z5gf-uOtiOQ2C6u5Q4fk-Gg1ZeKTLjRxm6Yt4v3JnFy0jE7cqgbrX_V-5frhNiPZP7zgCs3.png)
                - This method accepts more schedules, so could result in less cascading aborts resulting in less wasted time. However, this scheme has a huge performance overhead of generating a history graph and checking it for cycles at every step.
        - 
        - 
    - Supervision 1
        1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/sd2R5eXh_2n9qz1rlMJFYdNLd0tG-bE0UaLbKmCsWpDMrlH-pHYl-ZYXdacYEQIOuqaugFW1YRGzMEU9GQ6JOBONxdF-ugR7vRcWjB1AKZSipTorsRhQrosKThDmkULR.png) 
            - 0 - Condition synchronisation where one thread is producing items and another thread is consuming them. Initialising this to zero signifies that there are no items to consume and thus the producer must run. The consumer will wait for items to be produced (S > 0) and will then be signalled (whenever the producer produces an item it will call signal()).
            - 1 - If we have 1 resource available for use between multiple threads, in this case the first thread that arrives get's access to the resource - i.e. only one person can print from a printer at a time.
            - n - If we have n resources available between multiple threads (more than n threads), in this case the first n threads get access to the resource immediately - i.e. only n people can use the n printers at any one time.
        2. ```c
chopsticks = new Semaphore(2);
int chopstick_1, chopstick_2 = 0, 0;
// Thread 1
while (1) {
	if (chopstick_1 == 2) {
		eat();
		chopstick_1=0;
		signal(chopsticks);
		signal(chopsticks);
	} else {
		wait(chopsticks);
		chopstick_1 ++;
	}
}

// Thread 2
while (1) {
	if (chopstick_2 == 2) {
		eat();
		chopstick_2=0;
		signal(chopsticks);
		signal(chopsticks);
	} else {
		wait(chopsticks);
		chopstick_2 ++;
	}
}

// This can result in both threads getting one chopstick and starving
```
        3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/hB68m6SGg36hFL_xPZrweB2Eqg7k_MVpuvzdel9hIGD09WTMEsLGbpsWbnxmyGvH09l_OM7wDs9nDkFSYcrrMckP0b-W4XChfeRFosc3SSgvINuuRlz1TegpO9zNM9qH.png) 
            - Yes, because if we have a context switch anywhere between the weights (including just after the wait command is run) the various producer/consumer threads have different conceptions of the state. For example, if a context-switch occurred (in the case of a producer) before we changed buffer[in] we could resume the thread when the list is full and cause an overflow. Alternatively, we could consume the wrong item by the same means.
        4. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/D19kr_2Pf7_0ZafdDz9-dTMCRWKuzsTeC3BNISA9-vMa91p5xUIbPtkAcO-FvWKG-BOYddEfZNGpxymen8EKKA9v6OFpxc89bqDSu4Y6cYZwpsad_kCWmOu6P2Fstjta.png) 
            - In the implementation of wait & signal presented in the lectures, the problem would be making checking the queue and changing S atomic (for signal) or checking & changing S atomic (for wait) rather than the question posed above. This is because in the version presented in the lecture, only the first and last threads in the door change S.
            - Wait would be unaffected - this is because we only perform a decrement if S > 0 - and we only block a thread when S = 0. This means the two can never be in contention.
            - If signal's integer & scheduler operation were not atomic, we could have a race condition - in between the integer operation and the scheduler operation another thread could call wait on the semaphore and perform a computation. While that thread is running, we would complete our scheduler operation and our awoken thread would perform the same computation - this race condition could lead to anomalous behaviour. Waking up the thread first, and then incrementing the value would solve this.
            - 
        5. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/33akS39qWNR2m71NzOgaRJBQFNkWyVBtTw06nG-8WkaHVY_RldW4gw2BUKle6mpGtR5l7Eizk96IOtfF0m8hj52Aznye1SsP6aGioBc16kDSvqDO1K60vUqc9_FwdWnM.png) 
            - Round-Robin - In a multi-core processor where each consumer thread is on a different core, we would spread the work to different cores to ensure temperatures of an individual core doesn't skyrocket which would result in a slowdown.
            - Prioritized Work - In a multi-CPU architecture where faster CPUs are in more demand for work, faster CPUs would be given a higher priority as they would complete faster and we'd like that time-save when those CPUs are available, while slower CPUs would be given a lower priority. 
            - MRU - If the CPU cores have caches that will have recent data stored in them, if a thread has been used recently it may happen that the required data to perform the computation is already in the cache (addresses of items etc.) meaning time will be saved which would have been spent fetching data from main memory.
        6. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/RdrlWILK0E0bNwSv0LdF4PR9LSwMfofFUuoeUnN2zZ51HMYhG-COY7mcbZQY7g0NXtGGAgopnKwofrjQhkZ-RW5b53cxNVacz10Dj-fph_bN_LdPWE_SrBDgb1eLYKHN.png) 
            - ```c
int buffer[N]; int in = 0, out = 0;
spaces = new Semaphore(N);
items = new Semaphore(0);
producer_guard = new Semaphore(1);
consumer_guard = new Semaphore(1);
// Producer threads
while(true) {
	item = produce();
	wait(spaces);
	wait(producer_guard);
	buffer[in] = item;
	in = (in + 1) % N;
	signal(producer_guard);
	signal(items);
}
// Consumer threads
while(true) {
	wait(items);
	wait(consumer_guard);
	item = buffer[out];
	out =(out+1) % N;
	signal(consumer_guard);
	signal(spaces);
	consume(item);
}
``` 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bPGP_gNXPzszZu0_q37-gatUw0H5dw8izVNFee9drU-pzJ-qJsaKuetdA0NFulnHZLxjr7CjpzZMpGvCJCxYpVZWCmMPIlAGMK-4SQrszI27PiIeOky3BPa_hlCHoaQN.png) 
            - We can consider that the consumer and the producer interact with different sections of the buffer in their "guarded" sections - the consumer deals with out and the producer deals with in. We can then consider that the whole design of the spaces & items was done to ensure the back and front of the list cannot affect each other, that is we can never add to a full list due to spaces and can never detract from a full one due to items. So as in & out are safely independent, we need only protect our consumers from other consumers and producers from other producers. 
        7. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/y6BGMYo6C6AtmnKq8ltCZY67Be2lsy6CI2hVWujhK59XcjEncDNTVw9qCa3N4l3fOIbd_kzM-OmGGOfOdTIkNrFe_W9laL-85ipJVFLlCulSOooNdRFDJ1ZLkqcR-Mw-.png) 
            - Because generally there will be multiple (low priority) consumer threads in the guard queue ahead of the producer thread, they will necessarily be popped from the queue ahead of any producer threads. However, if you were using a mutex:
            - ```c
while (! test-and-set(note));
``` The thread that gets access to the resource, is the thread that runs test-and-set(note) first after the resource is freed - if the producer threads are set to a higher priority by the OS, they are more likely to run the command first.
            - 
        8. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/XtO2e4DqYfpL0B1gbYvMSEYqayEMkA50280I_JG5WD2FiCBcqtGMbZTY-fLOAmdiJLDuTOEe-alLzih8lCUPd9E7G_BCc0Dv_sxyKAGKcJd8IY8mq4XdPT6UXHgvTkhm.png) 
            - One could replace the queue structure with a priority-queue, rather than waking up the next thread in the queue in signal we would call popmin() (where a lower priority number signifies a higher priority) and the higher priority consumers would always go first.
        9. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Wy1sGRze451GrBUFtmUiDbaytnxBlC36EbdEbjjsWFZ2CaSDbQa78plAuoKq4hHoXQ5CslliK5YT_cJkEkuecGzqnKCKst6nEduav4Pibnv5blNuHzndlqfJqDSZCyOg.png) 
            - One solution would be to raise the priority of the producers (to high) whenever there's a high-priority consumer waiting - the wait() commands thus acts similarly to the signal() command, in that it allows another thread to run.
        10. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/cjRL7x0rri8fzqS45tGSxJ_lTt-r8ZbvSkwSlM-jlu96XC0v3j76VAMtqfibLO0JJQMDupkzyO4in-M9lDVC3LpA_f5UZ8DUvR3fXWzaR68yH9UANntExc4So-IiYXSf.png) 
            - Each thread has its own stack, register file and scheduling state, thus there will be two instances of each of these.
            - Threads share the executable program and virtual address space, so there will be only one instance of each of these.
        11. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gSeUH_wE-tW5DLaCuzxk0t7wair3fJw17i5FnYJAVLrFHH8d6hAQtJur1zWRVBjCKb5gsnuUcMNPlui8jIWfaKs-Wys6EhI_8toKLA9B3cFTitBM2p9WMPdN--zIbDxD.png) 
            - Consider the following case: 
            - ```c
if (!beer) {
	// printf(note);
	if (!note) {
		note = 1;
		get_beer();
		note = 0;
	}
}
``` A race condition can occur between checking for beer and checking the note - if another thread is just about to write to the note. However, as printf() takes a non-zero amount of time to execute that added time could result in the second thread changing note  in time, meaning the first thread will check the note once it's been changed (e.g. desired logic flow occurs).
        12. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/r9xDNEUd21vdFWgQV_oBu_b-yT79qFcKluEGCeipA0baCbUXBf4g13mns3lEDnAmLdZwxbOyLpKM8587Ae9iw3K87JXbLdhpE_C6FkpF5JD65RNQAfDJqyiWzg03192u.png) 
            - n! As the OS is (modelled as) non-deterministic, we cannot know the order in which threads will be scheduled and execute thrprint.
        13. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/rOmx9KUE6ei8U0fUQOOJT_dEeaW033n8VTJbWBYfwSH8oESnVDHu_5OpJl-KV63e0zBY8VNTCTXmF_RLMl1F0t5ujdZmkq99WLSKkC8Lk3_AKDNASEYiuUNcygfFIsWc.png) 
            - 1 - As pthread uses signal-and-continue style conditions, the if should be a while loop - as the value of the condition could have changed while the thread was waiting on the condidtion.
            - 2 - We do our printf after unlocking the mutex, this defeats the whole purpose of the safety - another thread could legally access the state and complete it's printf before we've completed ours (this could be due to a context switch or simply another core that's faster).
            - 3 - We never signal ordering_cv to wake up other threads.
            - ```c
int next_thread_id = 0; // Next ID to print
pthread_mtx_t ordering_mtx; // Lock protecting next ID
pthread_cond_t ordering_cv; // next_thread_id has changed

void ordered_thrprint(int thread_id, char *message) {
	pthread_mtx_lock(ordering_mtx);
	while(thread_id != next_thread_id) {
		pthread_cond_wait(ordering_cv, ordering_mtx);
	}
	next_thread_id = next_thread_id + 1;
	printf("Thread %d: %s\n", thread_id, message);
	pthread_mtx_unlock(ordering_mtx);
	pthread_cond_broadcast(ordering_cv);
}
``` 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gcADy-5emy1KJOIoJd595ND9GnD5-ptl-P6YS97lwBJayyx_m-ziHUyQeKJsIrMoEv3TZJd2euOaVtZE15SHtQdEbABINv6eTJNsILmfI65csyku1bmNsxdHQBmVlNKl.png) 
            - We could solve this problem using two additional pieces of state (and associated mutexes), an array of size N (number of threads) and a protected integer that starts as N. Whenever a thread is executed, it would do the following
                - First get control of the buffer and the protected integer
                - Then it would place it's debug message into the buffer at the index of it's thread ID.  
                - Then decrement the protected integer, if that integers value is now 0 print out all the debug messages and associated indexes and we're done.
                - Release the protected integer and the buffer.
    - 
    - 
    - ^^ _Distributed Systems_ ^^ _ _  
    - **Distributed Systems Lecture 1**
        - **Introduction**
            - What 4 advantages are there to make a system **distributed**?  ↓ 
                - Some Systems are **inherently distributed** (text messaging).
                - For better **reliability **- if one node fails others can be used
                - For better **performance **- different nodes for different parts of the world 
                - To solve **Large problems **- some problems consist of such a huge amount of data, can't fit on one computer.
            - The problem with distributed systems is that processes can {{crash }}and {{communications }}can fail without us {{knowing}}. Additionally, these may happen {{non-deterministically. }} 
            - We want **Fault Tolerance, **a system should continue working even if it faces these problems. 
        - **Computer Networking**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/J4ZxKhqnf7YPMc5Ea8liL9bMYQS-goUHpgeoYlVCrKv7VTkhfIle7j8MwYyoAPuOubzU79fQ5RZxTlDG74x2GtG5fd12tWrjFjdZ8LkE9qxWOodDrXj3pIubVuBOE0Ne.png) 
            - The fundamental abstraction of distributed systems is that of {{nodes }}sending {{messages }}to each other.
            - **Latency: **Is↔the time it takes for a message to arrive 
            - **Bandwidth: **Is↔The data volume per unit time
            - **Client-server comms over the web:**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/6IhRlUSXdP3733UVQmOFVDHC6Y0SLe-fYyKuwmLbL3b2U5a2oy4D7ZPz0nHz3m1t06uB3w_2pTNhRk2qpGDvSoLsQpaN92fCXiIZzljH8icC1Qndznxoklb3M_CdU0Df.png) 
                - URLs are separated into the {{server name}} and the {{path of the page}} you'd like to get.
        - **RPC (Remote Procedure Call)**
            - Consider an online shop communicating with a payment service:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/NHXB6R_B2KKd0WN4Dpvtf-FS0i_-AZwnXGdIDp-4KeagopAQLGHJdKnebhFw-cyNVYqG20tL2suIEBVbuKa7_l5sN7OtQ2-A53JtIsVMwGEaIr2-G8yAuLXLB5OzsoV9.png) 
            - We can have a function applied to the shops card object, that is processed on another node/s (that of the payment service). What looks like a function call, is **translated to a network request. ** 
            - **RPC **is used to→invoke a function call from your local machine, on a **different machine** via **network communication**.
            - RPC's are implemented using a **RPC framework:** 
                - RPC frameworks implements **stubs**, which are→function definitions with the same type and arguments as the function to be called via RPC. This stub function sends a message to the other node to process the payment.
                - The RPC framework "**marshals**" and "**unmarshals**" the arguments, this means→it encodes the arguments of the stub so they can be sent over the network, then on the other end the args are reencoded into the function:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/r037lljqIJLOb5QtnsdTRQFyTEq8ssiKFEVmqAV4vYTAhU1BleC9nB8lqX9fcHYH1Y9i0aaPShY4UuPiNLGOOjnppR4QRSBrY-L7djycaZ1vuuIvlWO_AoOhgYd7rpmM.png) 
                - The return value is then sent back, via the same process.![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3fJb_xRoqYCt3dK-TfmYos_wLSknPOsok2cuONek9VDV2yCb_PhIoxuDDhLMbTMX7rvHTUa6KYJJYoBcAB6SOaqktjRaobFagTDvg39xb5-sQ8dAkriVULQGXoWD0j2e.png) 
            - We would like our RPC call to look the same as a {{local function call}}. This is **Location transparency, **the location of resources is hidden. 
            - **RPC in enterprise systems**
                - RPC is used in **enterprise systems** because→these systems can become so large that they cannot be run on a single computer. 
                - A "**Service oriented Architecture**" (SOA)→is the architecture in which a **large service is broken down into microservices** on multiple nodes which **communicate via RPC.** 
                - If multiple services within SOA are **running different languages**, we use→Interoperability (**datatype conversion**) and IDLs (Interface Definition Language).
                - An IDL (**Interface definition language**) is a→Language independent API specification. Method of ensuring datatypes are stored in a method not specific to any one programming language.  
                - Example IDL: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/0xdtpuDkEuhCU8penCtWhT3yg4iFSQacbIje6oM4eGYy5K-eQRmFuyFQ7oE1txO74kASiw2cYLWza3bW8Ho_A9Ur1gMwi_U-gk95VJY_GhJL2GuRgF4IgJ9PpafguiKQ.png) 
        - 
        - 
        - 
        - 
    - **Distributed Systems Lecture 2** **(Models of distributed systems)** 
        - **The two Generals Problem:** 
            - Consider two armies, if they **attack together they win** - but if either one **attacks alone they will lose**. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/kZF5kAjLXMdskp7Es7wh7db6UkMY_9NZcFf9DvSpP-6zUwEsFYgDhPIpmv9ovYPdIQwryWGSfXEzul_ZeP-_trYhNxI-asW1L4n7bEtV62xzcnLhcC1BrwMoEJndrbZj.png) 
            - The two generals can only **communicate via messengers**, however the **messengers may be captured** and the  _**sender could not know**_  (except if they receive a response).
            - Initial message delivered, but the response is captured: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bP57WAkbwWs9MDQXFH0vELMgsOf0iZkhPpGCCu2cYZXMwBbw0BcAZGgMpinj8FVjILtbJtjaWE77MbaPaEcPw4UNaQiW7X86i4TjGhQqxyze-gddSQENt1dJ-Yb57bNI.png) 
This is indistinguishable from the following (**from general 1's POV**): ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Ey46dnl7hwQePgXZ1o7bHuVw7OV6dgmdaS3mxrncvAibJNFQMW2JzRp0Hjg3CHDJdpgQJe1ks_lNrCWzAa0v5pvvzqe3NpjyUCiXLeskxHn_4bkAF0GDD-8UEPlzP54Y.png) 
            - **In the two Generals problem, General 1 has the following two choices**  ↓ 
                - **Choice 1**: **General 1 always attacks**, in this case they may **send lots of messengers to increase the probability of receipt** - then  _if the message is received General 2 knows it's safe to attack_  (even without sending a response).  __**However**__  __, __ if the message isn't received General 1 will die. 
                - **Choice 2: General 1 attacks if a positive response is received**, in this case General 2 is safe **if** a response arrives  __but __  _General 2 is in Choice 1 when they send the positive response._  
            - This can result in an **infinite chain back and forth of communications** where **no absolute certainty of an attack is reached.** 
This is the problem of **No common knowledge **in DS which is→when the only way of knowing something is to communicate it. 
            - An example of the two generals is the following:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/CfPVn-fTG7HNM1XhiINgF1iSMSKSHqv5Rny771BO2iMwu7RG4OxInE0oxC2IjB-5Gx98WFGcN6o2UB-bAvPjpe_fCoomhEBPbPBpRM0qZph8ADP66ZqlNx3rs9kE7IiS.png) 
The reason that this differs from the Two General problem is that→The **charge is a revocable action**, we can always return to the starting point.
        - **The Byzantine Generals Problem:**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/kVjnfDY9vy2AyF3x7MfD3YRsM_q6WT92dlh1O5oVermmNCANiw2qsOklQ7t9MwAEvRVMI8T9RSns63Oxj1ZLVqKrPlOnvNVfpGGtZbJzSsMiyZEUKDmymk_B4C_K77kG.png) 
            - Within the Byzantine Generals problem we make the assumption that communications are {{reliable}} but some of the generals are {{traitors.}} 
            - We further make the assumptions that {{up to }}{{$f$}}{{ generals are}} malicious, that traitorous generals {{may collude and know who the other traitorous generals are}} and that honest generals don't know {{who the traitorous ones are.}} We then require that the honest generals must agree on a plan. 
            - **Generals may lie**:
 ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5y7MCi0wsHxY59MPzWPIY-KL9gZc7jv7vo3MtTd6mxd-w5A8cbXB2dVuqGqFRn7tXBDkPwuSroBGKrMrS6APOTSaJBc47XpUQ7MXSuhSUPoqF40YQTYjbmRoSn0ehD3M.png) 
General 3 cannot tell who is lying!
            - **Theorem**:  _We need _  _$3f + 1$_  _ honest generals to tolerate _  _$f$_  _ traitorous generals._  I.e. $< \frac{1}{3}$ may be malicious 
            - **Cryptography: **Digital signatures help, as we can prove a certain party sent a given message, however the problem is still hard.
            -  _Real life agreement_ :
 ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/OxXWMFBndgJuLV8Z1-F3b7M6MusMgTuaDnq4kdDu1NCuYCwNFYLcf2ZWcy0x7MREMxDxTAFlZBvRqp2KYAy7vk9N5wUx_LGgLiiYJkQp5ge17R3NzXory9ZLFYnxV946.png) 
Customers can act fraudulently, online shops could be fraudulent etc. (could have asymmetric relationship where the payments service is trusted).
        - **System models**
            - We have seen the **two generals problem** in which the {{communication medium}} was faulty and the** Byzantine generals** problem in which {{the nodes}} were faulty. In real networks **both can be faulty**!
            - **Networks are unreliable**, can be damaged by nature.
            - **System Model: Network behaviour**
                - Assume a **bidirectional point-to-point communication** between two nodes. The **three models of such a link are**→a **perfect **link, a **fair-loss** link and an **arbitrary **link.
                - A **perfect link** is→a link where no packets are lost, reordered or damaged.
                - A **fair-loss** **link **is→a link in which some packets can be lost or reordered, however we make the assumption that **if we send a packet enough times** it **will be delivered**.
                - An **arbitrary link** is→a link in which anything can happen. We model this as having **an adversary acting on our communications**. They can replay, block or edit packets as they please.
                - A **Network Partition** is when a **link **between two nodes is **disconnected for a period of time.** 
                - ^^A ^^^^ _fair loss link_ ^^^^ can be converted to a ^^^^ _perfect link_ ^^^^ using^^→^^Continuously resending, and deduplicating at the other end. ^^ 
                - ^^An ^^^^ _arbitrary link_ ^^^^  can (*almost) be converted to a ^^^^ _Fair-loss_ ^^^^ link using^^→^^TLS. An internet protocol to guarantee successful communication has not been tampered with. 
This is only arbitrary, as the adversary could block all packets.^^ 
            - **System model: node behaviour**
                - Under the assumption that each node executes a given architecture, the three types of nodes are→**Crash-stop**, **Crash-recovery **and **Byzantine**.
                - A **Crash-stop** node means→the **node could crash** at any time and **never re-join the network** (dropping phone in toilet). 
                - A **Crash-recovery** node means→The **node could crash** at any time,** lose its memory** state but it **will re-join** the network at some point. 
                - A **Byzantine node** means→A node that **doesn't follow the algorithm** (although it could pretend to).
                - A node is either **correct **or **faulty.** 
            - **System model: synchrony (timing) assumptions**
                - The three types of **synchrony assumptions** about **nodes and networks **are→**Synchronous**, **Partially synchronous** and **Asynchronous**.
                - A **Synchronous connection** means→Message **latency is no greater than an upper bound**. Nodes execute the algorithm at a **known speed**.
                - A **Partially synchronous **connection means→communication has **(finite) periods of asynchronicity **but is synchronous otherwise.
                - A **Asynchronous **connection means→Messages can be **delayed an arbitrary amount of time**, nodes can be suspended an arbitrary amount of time. 
                - Real networks behave in a partially synchronous manner, under such a system an algorithm designed for a synchronous network could fail catastrophically.
                - We can have many **real life violations of synchrony**, within  _**message latency**_  we can have: 
{{message loss}} requiring retry - removing any hope of an upper bound on latency
{{Congestion }}causing queueing
Network/route configuration, meaning a packet could get stuck for long periods of time.

                - Similarly we can have changes in node execution speed:
{{OS scheduling}} resulting in a thread being suspended.
{{Stop-the-world}} garbage collection pauses.
Page faults, swap, thrashing (constant page faults).
                - **Real-time operating systems** (RTOS) can give some scheduling guarantees - however most DS don't use RTOS.
        - **Availability**
            - Online services being offline = losing money. 
            - We can **measure uptimes** using the fraction of time the service is operating correctly. For this we can **use "nines**" 
'Two nines' = 99% up ⇒ down 3.7 days/year
'Three nines' = 99.9% up ⇒ down 8.8 hours/year
...
            - **Service-Level Objective (SLO),** the period of times the service will be up and the response times. "99.9% of requests get a response within 200ms"
            - **Service-Level Agreement** (SLA), a contract specifying some SLO ⇒ there will be penalties for failure to meet the SLO.
            - **High availability: ****Fault Tolerance:** 
                - We have a **Failure **of the system, in which the system as a whole stops working. We have **Faults **where a node is faulty or communication with that node is hampered.  
                - **Fault tolerance** is the design of a system so→a given number of faults does **not **result in a failure.
                - A **Single-point-of-failure **(SPOF) is→a **single point** in the system where a **fault will result in failure**. 
            - A **Failure Detector **is an algorithm that→detects if a given node is faulty.
A **Perfect failure detector **is an algorithm that → says a given node is faulty **IFF **it has crashed. 
            - The **typical implementation** of a failure detector is to→**send **a message to the node, then **wait **a set amount of time for a response. IF the node doesn't respond in that time it will be assumed to have crashed.
                - The problem with this implementation of a failure detector is that→we can't know if that's because the node has crashed, the message was lost or the message/node was only very delayed.
            - **Failure detection in partially synchronous systems**
                - We can only build a **perfect failure detector** in a→**synchronous**, **crash-stop** system with **reliable **links.
                - Instead we have a **Eventually perfect failure detector **this can→**temporarily **label a working node node as crashed or **temporarily **label a crashed node as working. **But, **it will **always eventually reach the truth** of the labelling. 
                - This reflects the fact that detection is not instantaneous **and **we can have long timeouts from a working node. 
    - **Distributed Systems Lecture 3 (Time)** 
        - **Physical Time**
            - Distributed need systems to measure time, used for:
                - Scheduling
                - Performance measurements
                - Log files
                - Data with time validity (e.g. cache entries, TTL)
            - The difference between a **logical **and **physical** **clock **is→Physical clocks count **number of seconds** elapsed while logical clocks count **events **(e.g. messages sent) 
            - **Quartz Clocks**
                - Quartz crystals can be engineered to vibrate at a particular **resonant frequency**, this frequency can then be detected (and fed back into the crystal again to keep the vibrating going). 
                - We use this **quartz vibration** by→counting the number of cycles to measure elapsed time. As we know $f$ 
                - Clock drift is measured in parts per million, meaning 1ppm = 32s/year of drift. 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/acy_5LTVfZi7tnDFZQCnv__uIjFbqSiIwq8P9U5BQXY2cNJN_RXcJM9g1BVOQjjT9FwYNIKdhyhX248FmQyvO9sf7C7HX4nmYpXFVWvK-3_GpHMASP-kA3Al6KhMy0f-.png) 
            - **Atomic clocks**
                - Caesium-133 has a given **resonance** we can measure - about 9 GHz . The second is defined by 9192631770 periods of that signal. We are of by 1 second every 3 million years
            - **GPS as time source**
                - 31 Satellites in space broadcast their **location** and the **time **from their atomic clocks. We then pick that up, and can calculate the time taken for the signal to arrive (via c) and thus get the time.
                - We do need to correct for atmospheric effects and suchlike.
            - **Coordinated Universal Time (UTC)** 
                - **Greenwich Mean Time **is defined by→noon when the sun is in the south, as seen from the Greenwich meridian
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/R9jUYQZGK9nZ6IIhjhW_voek4fxcitDPk3Z3yWTRZj4hvYUVxeEFkbBKxIp1khhsXIy1YwU9mFeTkWVNR9tfhkVwGoKuz0MgWIt7384d0evYj6KJCVM3w2IsCIT7qFv5.png) 
                - **International Atomic Time (TAI (based on French)) is **→ time based on Caesium resonant frequency 
                - **Problem: **Speed of Earth's rotation is not constant
                - Because of the disagreement between GMT and TAI, UTC is→TAI with corrections to account for Earth rotation.
            - **Leap Seconds**
                - A leap second is→a second that can be inserted or removed (typically) twice a year
                - Every year on 30 June and 31 December at 23:59:59 UTC, one of 3 things happen  ↓ 
                    - The clock jumps forward to 00:00:00 without waiting a second (a **negative **leap second) 
                    - The clock continues to 00:00:00 after a second as normal
                    - The clock continues to 23:59:60 after a second, adding a second (a **positive **leap second) 
                - Leap seconds are announced several months in advanced
            - **Most common timestamps**
                - **Unix time: **Which is→the number of seconds since 1 Jan 1970 00:00:00 UTC  _not counting leap seconds_  
                - **ISO 8601: **Which is→year, month, day, hour, minute, second and time-zone offset relative to UTC. E.g. 2020-11-09T09:50:17+00:00
                - Conversion between the two requires **Gregorian calendar** to calculate leap years and **knowledge of past and future leap seconds** 
            - Most software ignores leap seconds, however OS and DistSys require them.
            - **Smearing **is→The  _spreading out_  of a leap second  _over a whole day_ . This helps prevent software that doesn't manage leap seconds from crashing when encountering a discontinuity of a second.
        - **Clock Synchronisation**
            - Computers track physical time/UTC with a quartz clocks - and due to clock drift the error gradually increases.
            - **Clock skew** is the→difference between two clocks at a point in time 
            - A **solution **to clock skew is→periodically get the time from a server with an accurate time (based on an atomic clock/ GPS). Using the **NTP **protocol.
            - **Network Time Protocol (NTP)**
                - An **NTP server** is→A server to give an  _accurate time source_  for computers to sync with. Many OS vendors run NTP servers and configure their OS to use them. 
                - **Hierarchy of clock servers** are arranged into **strata, **these are→ __
Stratum 0__ : atomic clock or GPS receiver. 
 __Stratum 1__ : Something synced with Stratum 0 device
 __Stratum 2__ : Something synced with Stratum 1 device
                - NTP servers may query {{multiple clock servers}}, discard outliers and average the rest. Furthermore, servers are {{queried multiple times}} to remove network error
                - Using NTP we can reduces clock skew to a few {{milliseconds }}in good network conditions, but can be much worse over a {{bad network}} .
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/3H78pNX0DSOHMqLDwyVPqkjGFU7zmOV7K0fZkHoGgXtkzVZAm7wjLcoEQttsBlj3Hrz4FkSwU39_HL7Ev8iQ5-vxPvQlrTV2aG0Uz4DBV2l7p856O5XpanEJArqHOIc2.png) 
                    - The round trip network delay would be→$\delta = (t_4 - t_1) - (t_3 - t_2)$ 
                    - We can't find the time taken for the request and response individually because→the two clocks aren't synchronised. We can only get the time difference between two timestamps of the same clock. 
                    - The **estimated** the **server time** when **client receives the response** would be→$t_3 + \frac{\delta}{2}$ Because  _ __we assume the delay each way is half the total__ _ .
                    - The estimated clock skew would be→$$\theta = t_3 + \delta/2 - t_4$$ 
            - **Correcting Clock Skew**
                - Once the client has estimated the clock skew $\theta$, there are **three options** for changing the time  ↓ 
                    - If $\theta < 125ms$, **slew **the clock. Speed up or slow down the clock very slightly (around 50ppm) so it's correct after a period of roughly 5 mins.
                    - If  $125ms \leq \theta \lt 1000s,$ step the clock - i.e. suddenly reset the clock to the server estimate. 
                    - If  $\theta \geq 1000s$, panic and let the human resolve it.
                - What's wrong with this code? ```cpp
start_time = System.time()
code_to_profile()
print("Function took", System.time() - start_time)
```AND, what is the solution?→ _NTP could have stepped backwards_  while code_to_profile() was running - resulting in a negative time taken or too high of a time.  _Solve this by  using a monotonic clock, who still have slewing but will never jump backwards_  
            - What are **Time-of-day** and **Monotonic clocks** and **how do they differ**?→Time-of-day clocks is the  _time since some fixed date_ . Monotonic clocks are the  _time since some arbitrary point_  (e.g. since system booted up). 
The difference is that Time-of-day clocks can  _suddenly jump forwards_  or backwards subject to leap second adjustments, monotonic clocks  _simply go forward_  at some (near) fixed rate. 
Additionally Time-of-day clocks can be  _synchronised across multiple nodes_ , monotonic clocks  _cannot _ (only good for measuring elapsed time on 1 node).
        - **Ordering of messages**
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/cSyRVfDprWQX6kkONyGuwzXN2cN0oyfX6oT83kiZLRpY4bOkHQ9lOXbG_D-03xvyuC8B0azFM9uvHw7Hj-wBD_IOpw0j4tNwiCrL28Yox_ow4OqhZpM2ERHovfopgoFu.png) 
            - The **problem **with using timestamp ordering→is that $t_2 < t_1$is  still possible if the  _clock skew is greater than the network latency._  
            - **The happens-before relation**
                - An **event **is something happening at {{one node}}. 
                - We say event a **happens before **event b ( $a \rightarrow b$ ) iff  ↓ 
                    - a & b occurred at the  __**same node**__  and a occurred before b in the local execution order.
                    - event a is the **sending** of some **message m,** and event b is the **receipt of said message** (establishing causality)
                    - There exists an event $c$ s.t. $a \rightarrow c \ \text{ and } \ c \rightarrow b$ . Transitive closure!
                - The **happens-before relation is a partial order** - it is possible that neither a or b occur before one another (**i.e. they are unrelated, doesn't mean they occurred at the same time) **this is written→$a||b$** ** 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Bd6o0t7rZ1n8gzSYN0RPPgRQ-0aFu86YR9Wo9EaJDut_cwcndGwgL4ezC2i7DkZo5Ubp0Vma60xmCyP-z5RpbSZEo5C9ann8FL4-JWlOWaD7eTw5jUUabr3rb1uOTdaa.png) 
            - **Causality**
                - When $a \rightarrow b$, a  __might have caused __ b 
                - When $a||b$, a  __cannot have caused__  b 
                - Happens-before relations encode **potential causality.**  ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/E91bglfXDom_vwusocHwkGxcTDNMEX7Moxuhp-TSmcOwQBQSHlCAQmz19vRpVbCNDCsUnbsroqMQYgVVx19c46wt4vhTq1Ri2FbvYSdBOOZgASW6b1C-C2ALIPFo9r19.png) 
        - 
        - 
        - 
    - **Distributed Systems Lecture 4 (Time)** 
        - **Logical Time**
            - Logical clocks are designed to **capture causal dependencies** $(e_1 \rightarrow e_2) \implies (T(e_1)  < T(e_2) )$ 
            - **Lamport clocks algorithm**
                - The Lamport clock algorithm is→```python
# for every node:
t := 0

on event:
	t += 1

send_message():
	t+=1 
	message = (t, m)
	send (message)
	
receive_message(M):
	t', m = M
	t := max(t, t') + 1
	deliver m # to application 
```
                - Within the Lamport clock algorithm, **L(e)** is→the  _time after_  an the  _increment due to e_ .
                - The Lamport scheme has the following Properties  ↓ 
                    - if $a \rightarrow b$ then $L(a) < L(b)$ 
                    - However, $L(a) < L(b)$ does **not **imply $a \rightarrow b$ . We could also have $a||b$. 
                    - We can have $L(a) = L(b)$  
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/NWzGP1UyEkHkO4gREgLixeoi8cOAM4abaB3se7r0ImB-uzVNIeJLEEEilhXwyPSYFctCqAc8cLQLGqg2iXnPG5HF_yYSeGBjEAiTAUxkYYBLtQWAWq5JqrzjIa__JHhu.png) 
                - We can form a unique identifier for an event by→combining the name of the node (the event occurred at) and the time the event occurred $ID = (N(node), L(e))$. 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/xg2IfyouuRbVa9FbkOdHsZXyJrWZxa92DLDPqCaeqaBZR37C6_wCYtchKhkZaF1LKEjOHs1N8x3PyIv-OF-XxQr8SfrNiTL26-8Kc2Qfox0K7qERfYkVDVtK73NpHwmw.png) 
                - The main **problem with Lamport clocks** is→if we have timestamps L(a) and L(b) ^^we can't tell if ^^^^$a \rightarrow b$^^^^ or ^^^^$a||b$^^^^ .^^  _ __Remember, a||b simply means they're unrelated! If no messages have been exchanged all events are concurrent .__ _  __** **__ To solve this we need vector clocks. 
            - **Vector Clocks** 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/UvnFvkZTVzGPxEWZjr_kMUAUiA7FcxrCIors0myTDQknWQy0MOakHVv5DjhY0pPpkSIOxF37OGZ7cqINEulpWsY8VMVsTHrhChFYieuysBBZlfJpbEkqsvS5lL4yem04.png) 
                - The algorithm for **merging vector clocks** is→```python
 T = [0] * n
 i = index of us
 
 on_event():
 	T[i] += 1
 
 send_message(m):
 	T[i] += 1
 	send( (T, m) )
 
 receive_message(M):
 	T', m = M
 	# Max of each element
 	T = [max(a,b) for a,b in zip(T, T')]
 	T[i] += 1
 	deliver m to app
```
                - Example vector clock arrangement:![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Nr5EZypRAEEhXIQ3kVwQIrAtEEzY7-1YKCseaafPouBz8U9SArWl5NBxnYxQ3E1DpzsTK0SW2zXUkMJ6qeaWYvFCBPj4Vv9vAHDxLtiFGC0w6xzAIX0AxjIhzxwrDRwd.png) 
                - The vector timestamp of event e represents→e and all it's causal dependencies: $$t = \{e\} \ \cup \ \{a \ | \  a\rightarrow e\}$$  
So $<2, 2, 0>$ represents the first two events from a, the first 2 events from b and no events on c.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jFFIw1x1E-_MHi9JcaPCEKgEPWcijXTumy-uCOmOWnKEh71Kj14VxJa0iETImwR0bE3qfHN_3vPgy6eXGfP15rhqUhXkak-Iou5cYI6cN6pmwg9CZgfn0wNNlMJuI95r.png) 
                - Two events are **concurrent in vector clocks** iff→**Some **events in T happened before events in T' **and **some events occurred after events in T'. 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/fhN2SFw_h1aP_p7Qcn7UesaVszsVJ1kru10VOP5nlT890pjRlorhlOqw9B5dGM_DcWj7OAQb2rH12_9VM1BYQnevf-mC_886oGi05m1S6IeXHdc-Om81nVkytey9s-TF.png) 
        - **Broadcast ordering**
            - **Broadcast protocols**
                - Broadcast is **group communication** where  ↓ 
                    - One node sends a message, but all nodes in the group deliver messages
                    - Groups can be a fixed or variable size
                    - If one node is faulty, the remaining group members carry on
                - Group communication **can be designed** to be {{best-effort}} (messages may be dropped) or {{reliable }}(non-faulty nodes deliver every message by retransmitting dropped messages). There is no {{upper bound}} on message latency, as we use an Asynchronous/partially synchronous timing model.
                - The layout of a broadcast system is→![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/mFs8TN1pTuSMYFTopeZB2CUFSaNOk2UVEs0gL8tcAuDdaJ1GFrg-gwSi5vUp1M-SvvrldgftFPs3ME__MzkOS4qXyRkFubKjHa6FQzd5bYKziVR0Vn8KHVcD7QaJG9hu.png) 
                - The broadcast algorithm may wait to deliver a message to the application, because→we wish the messages to arrive in a certain order
            - **FIFO broadcast**
                - Note that when a node broadcasts a message, it also sends it to {{itself}}.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/I8jo0cSS3gODTf6w8D-mqHvxH6IBkmHggRtWq7ZQ27V5108wBpOfUFy-f6iFOPAgFvy-xQp4AidZD7C1calXQ5p-qEngwFMCc8X8IREnv5zzoYSww9hYtWmapqTBp2Zb.png) 
                - For **FIFO broadcasts **we **require that**→**messages sent from a given node** are  _delivered in the order they were sent_ . Messages sent from different nodes have no required ordering.
                - Valid orderings of the above diagram are then $$(m_1, m_3, m_2) || (m_1, m_2, m_3) ||(m_2, m_1, m_3)$$ 
            - **Causal broadcast**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/L1nUAnI60q5QqXN8NehbVWovcNwsWgdNcwup_XbfUwGOx-93_iv4GtGP5E_b19fPyGA9SxZC81O5d5FmZTfsJGNX6f-M_wkVxHfnZloOIqmfxL0hY8tOXzgDfChYqMw6.png) 
                - For **Causal broadcasts **we require that→Causally related events are delivered in causal order, concurrent events can be delivered in any order. 
                - The valid orders here are (m1, m3, m2) or (m1, m2 m3). 
                - The **difference **between **Causal **and **FIFO**→If FIFO we could  _technically have m1, m2, m3_ . In Causal broadcasts this would not be allowed. Or m2, m1, m3.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/I8jo0cSS3gODTf6w8D-mqHvxH6IBkmHggRtWq7ZQ27V5108wBpOfUFy-f6iFOPAgFvy-xQp4AidZD7C1calXQ5p-qEngwFMCc8X8IREnv5zzoYSww9hYtWmapqTBp2Zb.png) 
            - **Total order broadcast**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JG3S3CbaHrwr0rjbwr8YSPGYh6GWcWdCw9q_Dt68yE8YD47hQlqUDWyyR6uOeZx-V0qgaufPQlakuX1RNi_zzdC7SRN-ce1ZlUOB9aSbmVIZuuppV0gX5nOdkwNoNUkU.png) 
                - For **Total order broadcast ** we require→that all nodes deliver the messages in the **same order.** This  _includes the nodes delivery to itself!_  
                - The above ordering is for the example m1, m2, m3, but we could just have easily have said  m1, m3, m2: ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/G782ZOFwPUarYj_VHKvoWeHGWkbal8CP8CDza7d5sze5ffFJcnNtmgsUzVj1HvJsjnZtkoE4t0Svhhvf9d-Fug9YQ-x17gBueGzyuzJ0TtUQsUfX0J0meyQAk4v8-jEJ.png) 
            - **FIFO total order-broadcast:**
                - **Fifo total order-broadcast requires **→** **That all messages are delivered in the same order **and **messages from a given node are delivered in the order they were sent
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JLfDCSOtxO_AKEZA9k300iA46WVFHDVBzEUHdfxH2KpbRXALgOjd9Hm1L60e9Jle3lEBqCJ2FLwp08e_Bg1mYDRxoEUVVzEusDhrNLCXjnQ4aRzuYXBJT2xuA5dxeuw7.png) 
        - **Broadcast algorithms**
            - There are two sections for devising a broadcast algorithm  ↓ 
                - Ensuring the **best-effort connection becomes reliable** (retransmitting dropped messages)
Enforce **delivery order atop of the reliable connection** 
            - What is the **problem **with simply retransmitting and deduplicating dropped messages?→A  _node may crash_  in the middle of retransmitting a message, in which case not all nodes in the group will have received the message 
            - **Eager reliable broadcast**
                - Eager reliable broadcast is→![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/P3SNOBLC-Ooeys3gf9H7Qj0ZdDIu890t306QOWR0iqkivcEUNQE7tDaYU0LksM93348Hg3O__KEcRTbsTUpjmMjXGtwOJwLKmEhCdrDgkQbSb-pbnTVKMd4-Ja20jR5J.png) 
                - The **problem **with **eager reliable broadcasts** is→for n nodes, we have $O(n^2)$ messages being sent. 
            - **Gossip protocols** 
                - Gossip protocols works by→![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/AzHyQZqzTUIfVER7QY9jaTCTx-lgQzOZlK8nHdNeWaYKIvhopEjZU7JzK87ameqhPIbJ0HjY3nyWJixFvnQiV4T7PLY-OaTSLRv5NHcDstyN0dTnLbX7JMBuJ-MWsLTM.png) 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_3X3m6GVxLKq8rUjorTbV_cZm4Sb0heFxEEyEPt1EO3EZbOX0o5r7U2QGz2FC9nT_oTen14u9eTrBZcTvud57w6f6uD8MvaFr1i1PTWg3ZgmDZ7hhZ1Q1n88MIVP7jSI.png) 
                - Note: if a node has **already received a message **it doesn't send it again. 
            - **FIFO broadcast algorithm**
                - The **FIFO broadcast algorithm** is as follows→```python
sendSeq, buffer, delivered = 0, [], [0,0,0...,0]
i = ourNodeNumber

send_message(m):
	send(i, sendSeq, m)
	sendSeq+=1

receive_message(msg):
	buffer.append(msg)
	for M in buffer:
		i', sendSeq, m = M
		if sendSeq == delivered [i']:
			send (m)
			delivered [i'] += 1	    
			buffer.remove(M)
```
            - **Causal broadcast algorithm**
                - The **causal broadcast algorithm** is as follows→```python
 sendSeq, buffer, delivered = 0, [], [0,0,0...,0]
 i = ourNodeNumber
 
 send_message(m):
 	dependencies = buffer[:]
 	dependencies[i] = sendSeq
 	# Remember we send dependencies to ourself too
 	send( (i, dependencies, m) )
 	sendSeq += 1
 	
 receive_message(msg):
 	buffer.append(msg)
 	for M in buffer:
 		i', dependencies, m = M
 		if dependencies <= delivered:
 			delivered[i'] += 1
 			send(m)
 			buffer.remove(M)
```
            - **Total order broadcast algorithms**
                - The **single leader** approach is done by  ↓ 
                    - Choosing a single node to be the leader 
                    - All nodes send their messages directly to the leader (FIFO)
                    - The leader sends a FIFO broadcast to all nodes
                - What's the **problem **with the **single leader approach**→If the leader crashes no more message can be sent. Additionally, changing the leader safely can be hard
                - The **Lamport clocks **approach is done by ↓ 
                    - Attaching a Lamport timestamp to every message 
                    - The order messages are delivered in the total order of the Lamport timestamps
                    - But -  _if we get a time stamp T, how do we know we won't in the future get a timestamp < T?_  We need to wait for a timestamp ≥ T from  _**EVERY**_  node! We **need to use FIFO links**
        - 
    - **Distributed Systems Lecture 5 (Replicas)**  
        - **Replication**
            - Replication is keeping a copy of the same data across multiple nodes - could be on a database, filesystem, cache etc.
            - A node that has a copy of the data is called a {{replica}} 
            - There are three main reasons you would want replicas  ↓ 
                - To **spread load** across many replicas (can reboot or change a given node)
                - If **some replicas are faulty**, others can still be used
                - To **reduce latency** in areas far away from nodes
            - Replication is easy if data doesn't change, but becomes harder when it does change.
            - **RAID **is→a **Redundant Array **of **Independent Disks. **It's a method of replication within a single computer.  
            - **RAID** differs from replication of distributed system in two ways→RAID has a **single controller**, in DS each node **acts independently**. In Distributed systems nodes are distributed across the world not just within a single computer.
            - **Retrying state updates**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zAXYaRsuUHc51Km9hbNbnKDDitWvhZ50d3qvoCidJLcm6qeAarPNzPcwvxJcwh6suaom_FCxkHPyNw1aYaIk5-F-BqE7Q66syhUD2JtC9lOAIbxznkqEZL96X64iaxGZ.png) 
                    - To deduplicate this request we would require→that the database stores all requests it's already seen 
                - If the acknowledgement to adding a like to a post never arrives, what's the problem with sending it again?→It could be that the acknowledgement got lost on the way, resulting in two increments.
            - **Idempotence**
                - A function f is idempotent if→$f(x) = f(f(x))$ 
                - The idempotent alternative to incrementing a counter is→creating a set of likes and computing $\text{likeset} = \text{likeset} \cup \{userID\}$.  
            - **Retry-semantics** 
                - **At-most-once **semantics means→the request is carried out at most once, as we don't retry the sending
                - **At-least-once** semantics means→The request is carried out at least once, as we retry until we get a response. This can result in duplication
                - **Exactly-once **semantics means→The request is carried out exactly once, through repetition and deduplication or idempotence.
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/GSRTLxW-vEf4NUqlonf0KbkzGiGE7w-i-tN96YitYC_7leB8q2d6phZmfmFrQCyAAewjT5zeqnyD9EjG4EmX92DPJjK841ZBJpmk0LAPDioiCDBL77Uiyr01RlHFH1YS.png) 
                - What is **going wrong** here?→The request for the like is being sent again because the  _response was lost in the network_  - but in the meantime the user has unliked it (from a different computer) resulting in the  _unlike being cancelled._  
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/uD7MftKfvEoC5LNNYhjyJt-DBpM1_ssxmcNI5GANhHTpQlIW1Xlxnw53rQqoENeT32-aYaWuVefWVsdiKwySbRCjpWVmHve1p6ab5d01cp0USZ-2O5ZGYTio8e6j7zHN.png) 
                - What is the **problem here **→We would like overall operation add x then remove x to be detectably different than not adding x at all. In the above case we cannot tell the difference, so we **can't know which replica is correct**.
            - **Timestamps and tombstones**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gikFIFeyKZoBUH03f_PMFynWpLzcInN7lzSoBpvWv1sDGsezP-H0Sve1OEcxW7a5cwhHWCFGywKNEJePi2OLdQUoVug6X2X82BYJZDWIl8BgO0F-6UQ4E7vaqeP3sKNr.png) 
                - A **tombstone** is→a  _recording that an item was deleted_ , **even if the item is still held.** This is used to hold the fact that the item was once present in the database and has since been delete.
                - Every record has a **tombstone, **and a **logical timestamp.** 
                - Replicas use **tombstones **and **logical timestamps** to come to by→**occasionally communicating** with one another to **check for inconsistencies**. If such an inconsistency is detected a  _**anti-entropy**_  method is computed. The timestamps are compared to decide who's correct and reconcile state.
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Xm41gzLVU0ErhY7SzQFYrxOtGB2mkoEfByN381ekrbHsn80I-k4fjuEGYG9GZ4LofTNezZ9DENA-dB-hKxZZWjuTANfA1TXebT0v4LKRRn5MRcUHGaQ-30Mr3G12GZH9.png) 
            - **Concurrent writes by different clients**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/69MpP4Pxk9RB8R8iIHmNCqbVW3VorxuevBfoCMMVuIVDgqo9AJ2wGe0cLTjKZGPCoeVnb2K-UeY5hvPYftc_IvY3vUt2hHgB3FjAKeQkJlEQf7t-DIWrd8M9XAq4NP3F.png) 
The two approaches for this problem are  ↓ 
                    - **Last writer wins **this uses timestamps with a total ordering (e.g. Lamport clocks) - we choose the option with the larger timestamp, and discard the other one. **Note: Data loss, consider 5 such events occuring **only 1 datapoint will be preserved 
                    - **Multi-value register** - use timestamps with a partial order (e.g. vector clocks) only replace one if one of the timestamps is strictly greater - if t_1 || t_2 we preserve both v1 and v2 (perhaps seek user involvement)
        - **Quorums ** 
            - **Probability of faults**
                - A replica may be **unavailable, **assume the probability p of a replica being faulty is independent of all other faults. 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/XzsAVTwbLE2zEm2HVLKSpuxHwmyeXU4XJBvaIIB55XfoWRqF1qv75w0o4voabdUcUjKa5Ln9Gr_ivmBphhQYwtCeuf7EsOoOqZt2sTYD3UXFX_tzdpapB22NuDTRfHF-.png) 
                - More replicas ⇒ more likely {{at least one replica}} is faulty at a given time
            - **Read-after-write consistency**
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ZV20Kz4WJfsbC1A4_9jWVz_T_VxpPSqOy1snJ6OJEIzvM1eoW62m6A_DUgs46e7W6so5qlh91oECbbg6Tp5-OdOQkPxWA1QAcjrRtRwsu-VaQu1VR-K2FV6ENOYpapKv.png) 
                - The cause of **read-after-write inconsistencies** is→when a client writes to one replica, then reads from another (and the **two have not been synced**). 
                - One solution to **read-after-write** inconsistencies is only allowing {{reads/writes to all replicas}} - if one replica is offline, however {{we cant do any reads/writes}}. 
                - **Quorum**
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bKZieC-unJ2_3dE8Z9rCb3l3UjEZ-uKXpqesXSHJ9puS2MfsrL-ZWYprgf_dsSw2hZLCvuKUtxvLVZi8Au3p5rK2SLNmoQL8ph3W6O953DrelXRRN30iKJ2GAjoyYhmc.png) 
                    - A **Quorum **is→a group of replicas who we compare responses from to decide on correctness. 
                    - What are the **three requirements** for read/write **Quorums**?  ↓ 
                        - **Writes **are acknowledged by at **least w replicas ** 
                        - **Reads **are acknowledged by at **least r replicas** 
                        - **r + w > n **(Think  _pigeonhole principle_ )
                    - **Read/write quorums guarantee**→we'll  _always read the most recent write_ !  
                    - Typically form majority quorums
                - **Read repair**
                    - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/TTTpPyP9EHF65J1DQ0v4KvzdtJ_cLFkv5TW_tNaU6UJyxo16qPIuE57oAKQtztbiKkm4umJi3ryBihS0iifNqH-DvHiujtZ9rJK8JfSBNZIdO1yeKbQZxUIdJSJQheZi.png) 
                    - If we **receive **what we find to be an **out of date value** (via Quorums) then **send the correct value** to all incorrect senders or any replica that didn't send a value.
        - **State machine replication**
            - State machine replication is about using broadcasts to facilitate replication
            - **The Process of state machine replication is as follows ** ↓ 
                1. A FIFO-total order broadcast is used to communicate the state change to all replicas
                2. When a node sends the broadcast it also updates it's own state (so nodes sending the broadcasts will also update)
                3. Applying an update is deterministic
            - An **update being deterministic** in SMR refers to→the  _replicas acting as _  _**state machines**_ **,** they start in an  _initial fixed state_  (usually empty) and  _follow exactly the same state transitions_  in the same order and must then  _end up in the same state_ . 
            - The main limitation of SMR is→can't update state immediately, have to wait for the delivery through the broadcast (has to coordinate with other nodes to decide on order). 
            - Related ideas:
                - Serializable transactions 
                - Blockchains (total order broadcast in the chain), distributed ledgers, smart contracts
            - **Database leader replica** 
                - A leader database replica ensures a total order broadcast
                - Generally have the requirement that write requests can **only **be executed on the leader, read requests can occur on followers. The leader then makes these commits, and communicates these changes with the followers. 
                - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/wNQ5uytq-Djq-0AMvdNtPDVwqO6qipwM-ZwWvCQ0llB-EblhOrX0TmFVQjtZOKh2qKFaLD-cbKFGztrTJdS4i0B_Y_2uP5C2vTAbmLLCPUQo6Icr-1s6-EX9jpTBpIhd.png) 
            - **Replication using causal (and weaker) broadcast**
                - A replica **state update is commutative** iff→$g(f(x)) = f(g(x))$ where g and f are state updates.
                - The** causal broadcast** requires that if a message happens before another, it is communicated first. The **requirement for the state update function** is then→that concurrent updates commute. This with the other requirement ensures determinism. This is a bit like serializing the message.
                - For **reliable broadcasts** we would require that→the system is deterministic and that  _all messages commute._  
                - For **best effort broadcasts** we would require that→deterministic, commutative, idempotent and tolerates message los
            - 
            - 
            - 
        - 
    - **Distributed Systems Lecture 6 (Consensus)**
        - **Consensus**
            - **Fault-tolerant total order broadcast**
                - In our leader follower system, what happens if the leader crashes/becomes unavailable?
                - **Manual failover: **This is→when a human operator manually changes the leader when it's detected the leader has failed. Will need to reconfigure follower nodes. This is fine for planned maintenance. The problem is humans are slow, can take a long time in unplanned outages (consider if this occurred at 3am)
            - **Consensus and total order broadcast**
                - **Consensus is **→several  _nodes coming to agreement _ on a given value.
                - In total-order-broadcasts this would be **the next message to deliver**. So if we can come to a consensus, TOB drops out. e.g. consensus and TOB formally equivalent
                - **Paxos, Multi-Paxos **and **Raft **are consensus algorithms
            - **Consensus system models**
                - Paxos, Raft, etc. assume a **partially synchronous, crash-recovery **system model. 
                - We don't assume a asynchronous system because→there exists **no** consensus algorithm that will **always terminate**! Even in a simple crash-stop system.
                - Paxos, Raft, etc. use clocks only for timeouts/failures however the correctness of the algorithm does not depend on timing.
                - There also exist consensus algorithms for **Byzantine **system models (used in blockchains) 
            - **Leader election** 
                - Use a {{**failure detector**}}** **based on time to determine a suspected leader crash. On a {{suspected crash}} we must then elect a new leader. Crucially, we want to prevent {{two leaders at the same time ("split-brain")!}} 
                - Raft Ensures $\le$ 1 leader per **term **this means→The  _term is an integer variable_  that is  _incremented whenever an election begins_ . Raft ensure that at most 1 leader is elected per **term **and that each  _node votes at most once_  per term. The  _leader is then selected via a quorum._  The quorum gives us the fault tolerance
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/oRKZVQPA2sewgXbqQXQuwNNxXS-hb89JPztSbjtVbzdVfHj2Ym0thNflC38IfB7DFepG9UiDi5zqttzWA3y_uEWDELnWIyMYUzLcXVUDXKAlG6Pnw4QKT9PUia4IYnRe.png) 
            - **Can we guarantee only 1 leader?** 
                - The **system of 1 leader per term **doesn't guarantee 1 leader because→we could have a leader disconnected from it's followers, who is replaced without it's knowledge. So it's the leader of term t and there's another leader of term t+1. I.e. **this method only guarantees on leader per term.
 **![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/V3tUykKyDgLFsDYH6S5IrhXdZQC2D6ubQvp1thFpCZjTFlzCu2vXSTteYMr2Q3DtV4nWWzT84-g0WmATUL0TAToeDTJxZJCInlfXt2xODhLhHvHhT7LE2KYpSXnKPivr.png) 
                - The solution to this problem of a leader being voted out without it's knowledge is→the leader ensures it can send messages via a quorum. 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/CHaFRGF--nZNN8hKVUQbJBTEehN0QFdy0H66cyAhIKONEOuPKt-LRQxotlsC_5hWZE6zGktq-hvjFjCcGptUh06SlQd94k8cxUqPbfTGXAKNFCC-eVGOEZpDlH6NA-yd.png) 
        - **Node state transitions in Raft**
            - The state transitions we will use are always within a certain term. 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/oWqazBP_8nBcIola3uNH5oNL_j0GsbXTAyi9UhFPA0l_JlVCJbTrWk4KelPLQF3Dl_Pr-6bpmqNyzyQMHr4rEL-ASDVNnAoFuthUcVjViShxfQD6bJTk4IARODnl2kQR.png) 
            - Nodes that start-up or crash and then recover always start in the {{Follower state}}. However, we need some node to become a leader and it does this by transitioning to a {{candidate }}(when it suspects {{leader failure}}). If the node then receives enough votes{{ from quorum}}, it will become the leader. Alternatively, it may discover there's a {{new term}} and transition to a follower. Or the election may {{time-out}} in which case the election must be restarted with a {{higher term number}}.
        - **Raft pseudocode Explanations:**
            - ```autohotkey
;; Entering yourself as candidate

on initialisation do
	;; Note that the first 4 variables
	;; need to be stored on disk
	currentTerm := 0; votedFor := null
	log := hi; commitLength := 0
	;; Remaining vars can be lost in a crash
	currentRole := follower; currentLeader := null
	votesReceived := {}; sentLength := hi; ackedLength := hi
end on

on recovery from crash do
	currentRole := follower; currentLeader := null
	votesReceived := {}; sentLength := hi; ackedLength := hi
end on

on node nodeId suspects leader has failed, OR on election timeout do
	currentTerm := currentTerm + 1; currentRole := candidate
	;; nodes vote for themselves
	;; stores votes received as a set
	votedFor := nodeId; votesReceived := {nodeId}; lastTerm := 0
	;; I.e. if we aren't the first leader ever
	if log.length > 0 
		then lastTerm := log[log.length − 1].term;
	end if
	;; Tagged with VoteRequest
	msg := (VoteRequest, nodeId, currentTerm, log.length, lastTerm)
	for each node ∈ nodes: send msg to node
	start election timer
end on
``` 
            - In **RAFT** the **log** is→a list of  _messages with an associated term_ , the term is the term number that the leader sent the given message. It is the  _**total order of messages.**_ 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/VnP_X0y4qd74FjPvg_hresNYjUzjlgDUYiq6sHnVlGWZnzWMPvIAetoO8B7NBf-rY1_hKb43wUquGZ4RwjEl2As6e3wNnfPnJjmu5PiG0AlC7VoEC5w7yCEUJjRN1314.png) 
            - ```autohotkey
;; Voting for a new candidate 

;; c stands for candidate
on receiving (VoteRequest, cId, cTerm, cLogLength, cLogTerm)
at node nodeId do
	;; update our current term if
	;; votedFor=null indicates we've note voted for anyone
	if cTerm > currentTerm then
		currentTerm := cTerm; currentRole := follower
		votedFor := null
	end if
	lastTerm := 0
	if log.length > 0 then lastTerm := log[log.length − 1].term;
	end if
	;; Check if the candidates log is up to date with ours
	;; If their log's last term is greater than ours
	;; or it's equal with their log being at least
	;; as populated as ours
	logOk := (cLogTerm > lastTerm) ∨
			 (cLogTerm = lastTerm ∧ cLogLength ≥ log.length)
	;; if all the log checks are okay and we've not cast
	;; a vote for someone else then vote for this candidate
	if (cTerm = currentTerm) ∧ logOk ∧ votedFor ∈ {cId, null} then
		votedFor := cId
		send (VoteResponse, nodeId, currentTerm,true) to node cId
	else
		;; if we don't vote for them, we must tell them!
		send (VoteResponse, nodeId, currentTerm, false) to node cId
	end if
end on
``` 
            - ```autohotkey
;; Collecting votes at the candidate

on receiving (VoteResponse, voterId, term, granted) at nodeId do
	;; If we're behind in the term we'll have to 
	;; switch back to being a follower
	if currentRole = candidate ∧ term = currentTerm ∧ granted then
		;; idempotent update
		votesReceived := votesReceived ∪ {voterId}
		;; If we have a majority quorum we become the leader!
		if |votesReceived| ≥ cieling((|nodes| + 1)/2) then
			currentRole := leader; currentLeader := nodeId
			cancel election timer
			;; tell everyone we're the leader
			for each follower ∈ nodes \ {nodeId} do
				;; Initialize maps from each node
				;; to the number of messages sent to them
				;; and the number of messages they've 
				;; acknowledged
				sentLength[follower] := log.length
				ackedLength[follower] := 0
				ReplicateLog(nodeId, follower)
			end for
		end if
	else if term > currentTerm then
		currentTerm := term
		currentRole := follower
		votedFor := null
		cancel election timer
	end if
end on
``` 
            - ```autohotkey
;; Broadcasting messages

on request to broadcast msg at node nodeId 
	if currentRole = leader then
		;; add the message to the log which is simply the total
		;; order of messages
		append the record (msg : msg, term : currentTerm) to log
		ackedLength[nodeId] := log.length
		for each follower ∈ nodes \ {nodeId} do
			ReplicateLog(nodeId, follower )
		end for
	else
		;; If we aint the leader, forward the msg
		forward the request to currentLeader via a FIFO link
	end if
end on

periodically at node nodeId do
	;; This acts as a heartbeat, telling them the leader is alive
	;; this also ensures any messages that get lost will be 
	;; redelivered
	if currentRole = leader then
		for each follower ∈ nodes \ {nodeId} do
			ReplicateLog(nodeId, follower )
		end for
	end if
end do
``` 
            - ```autohotkey
;; The ReplicateLog function

function ReplicateLog(leaderId, followerId)
	;; prefixLen the number of log entries we think
	;; we've sent to a particular follower.
	;; suffix is all the entries we've yet to send
	prefixLen := sentLength[followerId]
	suffix := hlog[prefixLen], log[prefixLen + 1], . . . ,
	log[log.length − 1]i
	;; this gets the term number of the last log
	;; entry in the prefix
	;; e.g. the last log entry we think we've sent
	prefixTerm := 0
	if prefixLen > 0 then
		prefixTerm := log[prefixLen − 1].term
	end if
	send (LogRequest, leaderId, currentTerm, prefixLen,
	prefixTerm, commitLength, suffix ) to followerId
end function
``` 
            - ```autohotkey
;; Receiving a log request

on receiving (LogRequest, leaderId, term, prefixLen, prefixTerm,
	leaderCommit, suffix ) at node nodeId do
	if term > currentTerm then
		currentTerm := term; votedFor := null
		cancel election timer
	end if
	;; this is if we thought we were a candidate
	;; or if we thought we were the leader
	if term = currentTerm then
		currentRole := follower; currentLeader := leaderId
	end if
	;; if we aren't actually behind their log
	;; and either the prefix is empty
	;; and their prefix item is the same as what we've got
	logOk := (log.length ≥ prefixLen) ∧
	(prefixLen = 0 ∨ log[prefixLen − 1].term = prefixTerm)
	if term = currentTerm ∧ logOk then
		AppendEntries(prefixLen, leaderCommit, suffix )
		ack := prefixLen + suffix .length
		send (LogResponse, nodeId, currentTerm, ack,true) to leaderId
	else
		send (LogResponse, nodeId, currentTerm, 0, false) to leaderId
	end if
end on
``` 
            - What is the purpose of this code? ```autohotkey
 logOk := (log.length ≥ prefixLen) ∧
	(prefixLen = 0 ∨ log[prefixLen − 1].term = prefixTerm)
```→This is 
            - 
            - ```autohotkey
;; AppendEntries function

function AppendEntries(prefixLen, leaderCommit, suffix )
	if suffix .length > 0 ∧ log.length > prefixLen then
		index := min(log.length, prefixLen + suffix .length) − 1
		if log[index ].term 6= suffix [index − prefixLen].term then
			log := hlog[0], log[1], . . . , log[prefixLen − 1]i
		end if
	end if
	if prefixLen + suffix .length > log.length then
		for i := log.length − prefixLen to suffix .length − 1 do
			append suffix [i] to log
		end for
	end if
	if leaderCommit > commitLength then
		for i := commitLength to leaderCommit − 1 do
			deliver log[i].msg to the application
		end for
		commitLength := leaderCommit
	end if
end function
``` 
            - 
            - ```autohotkey
on receiving (LogResponse, follower , term, ack, success) at nodeId do
	if term = currentTerm ∧ currentRole = leader then
		if success = true ∧ ack ≥ ackedLength[follower ] then
			sentLength[follower ] := ack
			ackedLength[follower ] := ack
			CommitLogEntries()
		else if sentLength[follower ] > 0 then
			sentLength[follower ] := sentLength[follower ] − 1
			ReplicateLog(nodeId, follower )
	end if
	else if term > currentTerm then
	currentTerm := term
	currentRole := follower
	votedFor := null
	cancel election timer
	end if
end on
``` 
    - 
    - GO FROM HERE NEXT: [Distributed Systems 6.2: Raft - YouTube](https://youtu.be/uXEYuDwm7e4?list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB&t=946) 
    -  _Distributed Systems supervision 1 _ 
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
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/qpQ_ydxHmeLCcJOH6RsYAsXfSQmhKyB1tFdamdF6Ap_bDPQSH3D9yXDiDWlMRhPCDIbkBbsV34oweAqelXOk2YakrBsEOBexbuDNPmUFzd2RpaSGhmlB3zKHzVrmj3e5.png) 
            - delta = (t4 - t1) - (t3 - t2) = total network delay
            - skew = (t3 + delta/2) - t4 ^^ Question: should the skew not be the absolute value of this?^^ 
            - This estimate is worst, when the estimate of the time taken for the second response is worst - i.e. when request 2 took the minimum time (according to the speed of light & the distance) $\tau$ and the response took  (t4 - t1) - (t3 - t2) - $\tau$, resulting in a true value of: $$(t_3 + \tau) - t_4  = (t_3 - t_4) + \tau$$ 
            - and an estimated value of:
            - $$(t_3 + ((t_4 - t_1) - (t_3 - t_1))/2) \ = \ \frac{t_2 - t_1 + t_3 - t_4}{2}$$ 
            - Resulting in an error of:
            - $$\frac{t_2 - t_1 + t_3 - t_4}{2}  - ((t_3 - t_4) + \tau)$$ 
            - 
            - $$\text{error} = \frac{t_2-t_1-t_3+t_4}{2} - \tau = \delta/2 - \tau$$ 
        -  _**Exercise 8:**_   ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5S3daW4zY8nipJDU9bb6QDZFwpAKv76GLWXklLBsLwNMaHVyXCyqi6beHbSePSUh2wUUqfIM089PwNg7KdgKAG393iZn0TG3vKoFUqd6uZlbpIj28GT5HfxMznzEsjyk.png) 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JZ0cqETpk4kB-8uo8RsxSXte3C9NVDfOw4vemdbEKxinYe3CqfOPdSUNb_Fpyd4-ye6MCznEIu-9sZu06atSqyFY7bbC1aTgvSUTUTXT9mFmE5HTbSF5PSAVbnrb2wkH.png) 
        -  _**Exercise 9.**_  ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/yjzPiqfzh56oOnjdrWniK1-rmUzLvrJVHdmIi3wGYvHrNK61hUGjfCo6hw7JQp6f_L5YYwSlqfsN8hscm798IJxxy9ynwJuNREyNIPIdegj_vVikP0lJGqiVY31FzpHB.png) 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ob9D3CB9suoCvYxZxqxdjPsKhfoPPSYm6DlccDXCh0NtAPdvEKZA7Lly3ra6n6EQ8nrb-eQAqp-ly0gw__HevRFKuj9ebM1cP9wxXqeeExDvTyWgi-ry8nKXL0kJ1kY9.png) 
        - **Exercise 10.** Given the sequence of messages in the following execution, show the Lamport timestamps at each send or receive event   
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4atqIBUEAzm7OncyN5qB3j5Z5XjQtc_OHDZgMdXZh6kXNeqKApIIRpARrwbyAHUyX7k7ndM-H0MBpStyrugFtkC4DMVZEVYv2pTPR9uWBOaXYXUGmwbk1reIC3dx1sE2.png) 
        - ^^ _**Exercise 11**_ ^^^^. Not really sure what im doing in this Q^^ 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/OLpHgGNm5MfltmNel8M5Q5lLaLiOvEi-XeYkJSwWR2d7kXOaSbkgkSRhko_Iat92Wrqx24q4XCLZlBOuaCfxNSdmG60OZoL9OyAZd8aFGEzVQs2X26dJVDRGVZhjhzk1.png) 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/oBARg9P1D24HOK5JpsjKfxt9BYToaiGQaEFssa4ymDfFEdCvwPFRyS1POKECnRvToCUUSUDiGleDPpD1--KUBhU6sgaQqXCITyKlJIKliumPf_oMLkMtWVPrL2PwqsPV.png) 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_yytoqeaDujPLnHDbTmbdQ8mL45y-VCzC7OtvC2qnqKA8ofMwyZq15n7C4nYTpYnzbyjKVGghpq51wFQGApk_Zsmi4sMKo7jf3lGLupIBvMobBOH_MVgEeECiIBzpoqp.png) 
        -  _**Exercise 12**_ . Given the same sequence of messages as in Exercise 10, show the vector clocks at each send or receive event.  
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/9jwOOpv8Z8WqVwxq7ynfW03XwQFEn7ipkP88FMsmB5DkrGrmrNBuwEUhIDojkOzdAeBx17jEOVmlWrU2whx6-qnXAjz4jqukHzSSGc3F-r53v3Rg82YAzsXevXp8Bh-Z.png) 
        - 
        - 
        - 
        - 
        - 
    -  _Distributed Systems supervision 2_   
        - 
        -  _**Exercise 13**_ . Using the Lamport and vector timestamps calculated in Exercise 10 and 12, state whether or not the following events can be determined to have a happens-before relationship.   
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4atqIBUEAzm7OncyN5qB3j5Z5XjQtc_OHDZgMdXZh6kXNeqKApIIRpARrwbyAHUyX7k7ndM-H0MBpStyrugFtkC4DMVZEVYv2pTPR9uWBOaXYXUGmwbk1reIC3dx1sE2.png)    ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/9jwOOpv8Z8WqVwxq7ynfW03XwQFEn7ipkP88FMsmB5DkrGrmrNBuwEUhIDojkOzdAeBx17jEOVmlWrU2whx6-qnXAjz4jqukHzSSGc3F-r53v3Rg82YAzsXevXp8Bh-Z.png)  
            - Lamport:  
                - Send(m2) ⇒ send(m3) - Yes, because they occurred at the same node, and L(m2) < L(m3) ⇒ $a \rightarrow b$ 
                - Send(m3) ⇒ send(m5) - No, because they didn't occur on the same node, it's not a message from a to b and there's no chain $a \rightarrow x_1 \rightarrow ... \rightarrow x_n \rightarrow b$ . $a||b$ 
                - Send(m5) ⇒ send(m9) - Yes, because we have the chain of events 4 (send m5) ⇒ 5 ⇒ 6 ⇒ 7 ⇒ 8 (send m9) - we can easily prove the happens-before chain is correct as they are all on the same node and all have L(x) < L(x+1) (they are in order in the execution order)
            - Vector: 
                - Send(m2) ⇒ send(m3) - Yes because all values of the vector clock are lesser or equal
                - Send(m3) ⇒ send(m5) - No, they are concurrent as some values are lesser and some are greater between the two vector clocks
                - Send(m5) ⇒ send(m9) - Yes, because all values of the vector clock are lesser or equal
        -  _**Exercise 14:**_    We have seen several types of physical clocks (time-of-day clocks with NTP, monotonic clocks) and logical clocks. For each of the following uses of time, explain which type of clock is the most appropriate: ^^process scheduling^^; I/O; ^^distributed filesystem consistency^^; ^^cryptographic certificate validity^^; concurrent database updates.  
            - **Process Scheduling**: A monotonic timing clock, as each process will be apportioned a time quantum in which they can be processed - It should be monotonic as we don't want any sudden jumps backwards due to NTP corrections. While a logical clock consisting of clock cycles could be considered, this could result in some jobs takin inordinate amounts of time (consider I/O) as they require few clock cycles but take a long time - thus time should be used. 
            - ^^**I/O**^^^^: ???^^ 
            - **Distributed filesystem consistency**: Logical vector clocks (with tombstones), as we want a total order of events to ensure we can compare replicas and decide with certainty who is correct.
            - **Cryptographic certificate validity**: Physical time-of-day clocks with NTP should be used. Physical time because the certificate must be valid for a set of physical days. Time-of-day with NTP because we want the time to be human understandable and because it is the most ubiquitous form of time-keeping. 
            - **Concurrent database updates**: Logical vector clocks. We wish to know with certainty which event arrived last, and we'll choose using FIFO - if an update was issued after it should overwrite. Logical vector clocks provide this. We won't use time, due to clock-drift and leap-second issues. 
        - ^^ _**Exercise 15:**_ ^^^^ Prove that causal broadcast also satisfies the requirements of FIFO broadcast, and that FIFO-total order broadcast also satisfies the requirements of causal broadcast.^^ 
            - 
            --------------------- Portal ---------------------
                - Lecture Notes
 -- Avoided infinite recursion --         -  _**Exercise 16:**_ . Give pseudocode for an algorithm that implements FIFO-total order broadcast using Lamport clocks. You may assume that each node has a unique ID, and that the set of all node IDs is known. Further assume that the underlying network provides reliable FIFO broadcast.  
            - ```python
timestamp = 0
buffer = [ [(None, 0)] ] * N # Initialize all messages, the message is None and the time is 0. Note that each node has it's own FIFO queue, storing messages and timestamps 

def send(message):
    timestamp += 1
    broadcast( tuple(message, timestamp, myNodeNumber) )

def receive((message, msg_t, nodeNumber)): # pattern match on tuple
    timestamp += 1
    if buffer[nodeNumber][0] == (None, 0): # if we aren't holding a message from this node
        buffer[nodeNumber][0] =  ( message, msg_t )
    else:
    	# otherwise add it to the node Queue
        (buffer[nodeNumber]).append( ( message, msg_t) )

def deliver():
    nodeIndex = buffer.getMin()
    item = buffer[itemIndex][0]

    for nodeBuffer in buffer:
        # We know this has the smallest lamport timestamp because it's FIFO:
        message = nodeBuffer[0]

        if message != item:
            if !(message.time < item.time):
                return False # Go back to waiting for a response

    deliver_to_software(item.message)
    # Either promote the next item in the node queue to the head OR
    # Set the item to have lamport 0, so next time we must wait for a value
    buffer[nodeIndex].deleteItem(index=0)
    if len(buffer[nodeIndex] == 0):
        (nodeBuffer[nodeIndex]).append( (None, 0) ) 
    timestamp += 1
    return True

while (input = listen()): # blocks until we get input
    receive(input)
    deliver() 
```
        -  _**Exercise 17:**_  Apache Cassandra, a widely-used distributed database, uses a replication approach similar to the one described here. However, it uses physical timestamps instead of logical timestamps, as discussed here: [ ](https://www.datastax.com/blog/why-cassandra-doesnt-need-vector-clocks)[https://www.datastax.com/](https://www.datastax.com/blog/why-cassandra-doesnt-need-vector-clocks)[blog/ 2013/ 09/why-cassandra-doesnt-need-vector-clocks.](https://www.datastax.com/blog/why-cassandra-doesnt-need-vector-clocks) Write a critique of this blog post. What do you think of its arguments and why? What facts are missing from it? What recommendation would you make to someone considering using Cassandra?
            - The blog post describes problems in Performance, manages siblings and Vector clocks which they seek to solve
                - With regards to **Performance** their implementation will be faster for single field updates - however it may be slower for entire object updates. Consider, in a vector clock system if we go to update an object we need to iterate through a vector clock of size R (number of replicas) - in their system we need to iterate through a "vector clock" of size F (number of fields) as each field has a counter associated with it. So if we wish to update more than R fields in their implementation, that will be slower than in the vector clock implementation. 
                - With regards to **managing siblings** they discuss how LWW can result in lost data, yet their system uses LWW (within specific fields) the only difference is that the overwritten data **may** be smaller depending on how your objects are constructed - as you may just have individual fields overwritten and not the entire object.
                - With regards to **Vector clocks** they say: "Vector clocks are good at helping clients with simple merges like the above user object, but it's important to understand that vector clocks only tell you that a conflict occurred, and not how to resolve it;" - This is a feature not a bug, we **want** user intervention in certain situations in which it's **impossible** to decide what they want - the writer communicates this as a problem, while it results in data being as correct as can be. The downside is the user has to spend time to make this determination, however that is a trade-off  and not a strictly-worse scenario.
            - The blog post makes no mention of leap-seconds, and their impact on timestamp ordering (they provide a dead-link as explanation of how ties are resolved), additionally there is no mention of how they account for clock synchronisation and clock drift which is a large part of the reason for logical vector clocks.
            - This system could be faster for systems whose objects have few fields, and where updates are usually performed on only a few fields at a time. If someone was considering using Cassandra I would urge them to use monotonic physical timers (to protect from leap second problems) and ensure clients are close together (ideally in a single site) and using the same time synchronisation  server (to ensure the tightest clock synchrony and protect from clock-drift).
        - 
        - 
    - 
    - 
    - 
    - 
