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
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fmDPF-dInQpQH71USeyACbGDBgB3nscLlH3JJzNT4er96vIhCtjR1TYQGylX4N1pvTc6Vt6Sr3_pZcqlcEMQgX1KadmjmFAHIMDqaEx9SY8cG9oGrHlHWDcwUI1pK1WI.png) 
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
                - If the assumption that consumers and firms are price takers isn't met, then firms may list items at a price too low where they cannot keep up with demand - while they struggle and battle with the initial throws of this supply and demand curve:     ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4rqcmEIjQt_7SHMQvvfC0rawX7bN5sS307ywCIuC9CtuiDA4SXZ6n-m_2m2tyJjY8jsZmnz5i4uL858ZndmTTYwcLCrjvqOMFW34IqhJP-2knWk6Nca6sixpTfBWWhHs.png)                                                                                           Until they reach the later stages, other firms will be met with a huge decrease in demand - leading to stagnation of growth. Contrarily, if consumers buy the more expensive items when cheaper alternatives exists, competitors will have to change their product or lower prices even further to appear palatable. In regards to the information technology industry, this would be the equivalent of word becoming free to win back users of google docs - or if github started charging for the service and people kept using it.
        - Exercise 1:
            - a.) **  Suppose that we say that an allocation x is socially preferred to an allocation y only if  everyone prefers x to y. (This is sometimes called the Pareto ordering, since it is closely  related to the idea of Pareto efficiency.) What shortcoming does this have as a rule for  making social decisions? [100 words]   ** 
                - Everyone needs to be polled in order to make any small decision, so decision making will be slow and cumbersome. Additionally, If even one person disagrees, no matter how absurd their reason is the idea will be thrown out, and as almost all decisions are likely to have some level of disagreement very few decisions will be accepted. 
            - b.)** A Rawlsian welfare function counts only the welfare of the worst-off agent. The opposite of  the Rawlsian welfare function might be called the “Nietzschean” welfare function—a welfare  function that says the value of an allocation depends only on the welfare of the best-off  agent. What mathematical form would the Nietzschean welfare function take? [100 words]   ** 
                - $\max U_i$  
                - We select for the maximum utility of our population, and try and boost that. ^^Assume we're looking at the utility of a single good^^ 
            - c.) **Suppose that the utility possibilities set is a convex set and that consumers care only about  their own consumption. What kind of allocations represent welfare maxima of the  Nietzschean welfare function? [100 words]** 
                - At face value, improving the utility of the best off person seems to be giving them all the resources. However, then the surrounding agents will suffer and the world around the richest person will degrade. Additionally, due to the convexity of utility functions resources become less desirable the more you have of the resource - meaning more money means less to a rich person than to a poor one. Thus, while some effort must be spent further enriching the best off agent - some money must be spent to maintain their surrounding population so the best off agent needn't witness poverty or drive on broken roads. 
            - d.) ** The ability to set the voting agenda can often be a powerful asset. Assuming that social  preferences are decided by pair-wise majority voting and that the preferences given in the  table below hold, demonstrate this fact by producing a voting agenda that results in  allocation y winning. Find an agenda that has z as the winner. What property of the social  preferences is responsible for this agenda-setting power? [200 words]** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/S1XX-5lu6CMf8Oex4OuNutrHIHl8lA_z2RtN62sSS1UOlyLVRJ7fXN8frGL6TGGjzsMr_YJbGNr_STTvSPBZZuGJtZJmTvClb6EsVz4a2kqikwXXrgbQSJqvtTl9RW_j.png) 
                - ^^Not sure if my understanding of voting agenda is correct^^
                - Obviously, without an agenda the entire vote is a three way tie. If we set the agenda to who wins out of y vs z, we have y winning - as we get to wins for y and one for z. If the agenda is x vs z, we have z winning out with 2 votes to 1. ^^Agenda means, first have a and b fight then have b and c fight^^ 
                - I believe it's the property that people vote for the candidate they actually want to win first, and the following results are murky - especially if given a choice of the top X candidates rather than ranking all candidates. Thus, if specific candidates are chosen the results can vary wildly as less strict rules hold for the last two options.
        - 
    -  _**Lecture 1:**_  
        - Macro vs MicroEconomics―Macro: Performance and structure of global economy or a nation or region.  Micro: Individuals and firms responding to incentives, how market mechanisms fail and circumstances in which markets fail.
        -  _**Prices and Markets**_ 
            - Consider searching for a flat, one bed or house share - people who can afford flats will get them, and others will cycle to far away house shares.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RJdFdwqCAq_YvvqEJmjnukPI87T0GMU2tOel0cVyW8yoJAQxx6SCnpH0QIfVz6MJLmNtUDpXBR3-7ZUCIzErrtZwX-0bvHUkYRsmImVt4wuojOMT32vY-EO8qTHX4Fw3.png) The equilibrium price is where the supply and demand curves corss - e.g. £500
            - Consider if there's rigging - the cartel meet and restrict supply, 800 flats at £700 can earn more than 1000 at £500 - **This is inefficient, houses are left empty for which there is demand.** 
        - **Efficiency:**
            - A monopolist might leave flats empty, despite people being prepared to pay for them.
            - Pareto Improvement―A way to make some people better off, without making anyone worse off
            - A Pareto efficient allocation―Is such that no Pareto improvement is possible
            - Pure monarch and pure communism are **both** pareto efficient.
            - Discriminating Monopolist ↓ 
                - If you know what the person can pay, charge them exactly that, this is pareto efficient and lets you extract the most from the market. The monopolist captures all of the consumer surplus:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i1z7Qw6bTJvxLthQPGUlCWVpvDvoBp5rLqa46oeI4ScBvHRJLeroPu7YnmfCNlFY6GR9u6z00gATNgS873ZixfReC3zNi38M_aOH05ZUcVGhMgjh0HrrSxZ1PfEtQVyj.png) 
                - This is what the IT industry tries to do with different prices of service (microsoft word). 
            - **Consumer Surplus** 
                - Consumer surplus―Is the total amount people saved off their reservation price (What they were willing to pay)
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/O-15rQakD1bu-vSC_cXcj6TSpt-v5tqk6yRcyAdBYwMXKfwTC8k5N7ZwWLTX67VhATkCvqjj4imubQ4tjjQOKA31QHEIX9a6Ll_wioRt23rWQcnf0lPgQfy5oGLVwZ2-.png) 
                - People would have payed 2000 payed only 700. Lost out on A & B. The discriminating monopolist gets the lot 
        - **Basic Consumer Theory:**
            - Consumers choose best bundle of goods they can afford. Most of the time two goods enough, books versus everything else. 
            - Assume a budget constraint m, $p_1 x_1 + p_2x_2 <= m$ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sECy__ijlVN8kbj_fZJR4bWZyWg-uGKgWjhyHCKYxtPsD-0wwqGAl3LhbhkozcnIjzbW3PgidkM-WVKJ5K0AxxozqZvOWKCXdwyGDpeX3FC3TUfOzSNjcp2rbod-3wda.png) Choices lie within this line
            - **Preference:** 
                - Using Indifference curves or isoquants, we plot where a user has no preference between bundle $(x_1, x_2) \ vs \ (x_1', x_2')$. They are indifferent:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Rnc8D1UP6kPGTUwukPeOKun0fV8lBEH4Pz6V5FnQKDiFoq6_cLuS8-Km9zTYqZQLT37RzJxSTJFAGVfvU9vUxXxf4920JH-yUEbBjt8RE_d4VqR7Z4LVW7lvN96wR_dW.png) 
                - We assume they're well behaved and don't cross, **this is the weak axiom of revealed preference**. I.e. If I'm indifferent to having 10 apples and 10 chocolate bars, I'll be happier with 20 apples and 10 chocolate bars.
            - **Perfect Substitutes:** 
                - Perfect Substitutes―Don't care whether I have good 1 or good 2, e.g. sugar from Tesco vs Sainsburys.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RtW4sVt6ZsJ0q8l-QmqUbEUw5Q9eryLcS5Nmn4D30fl0DS-w5BQo2QkEPPSKuqAaimDiKYHLkdB_LUJhkNMkuPJLsjWGQh3y4EiHy9cptDrBpAwQp8itUTiUnYVSdsv3.png) 
            - **Perfect Complements:** 
                - Perfect Complements―Want exact same quantity of good 1 and good 2, left & right shoes for example.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/v0o8b3wdSbHqfQhwfS0ixECIKjMrHcSB7onxgFp8l3iqdca2mLhezud9q8iNgz1_qgaWwYzpn6arhkGmVjkMK_hPuLo29m99yrgEHrbLa6ILYEXnIkSAHhjX-RNr1hHF.png) This indifference curve says, once I have 1 left shoe and 1 right shoe, it doesn't matter if I have 1 left shoe and 300 right shoes.
            - **Bads:**
                - These are goods I'd rather avoid, sometimes I have to consume of the bad in order to have some of the goods.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/M4iSNms1tnx-YOSJMhigTNsGoB6JonMSKNy76ZC2gStAI835LxRgzx6dSJyXqwCj8Fy0f8dlXwTcxoT_z-upEfAFNXbTHk1ptbErRrIgNayhrmjOruwqCN_0Zgmap3Yi.png) 
                - I'm indifferent to getting more sprouts as long as I get more turkey.
            - **Marginal rate of substitution**
                - The tangent to an isoquant gives the marginal rate of substitution. This is the exchange rate at which the consumer will trade the two.
                - Convex curves: You're more likely to trade a good if you have more of it
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7ECMsjYfQPiyz0X6fyHargCzgFHlL44jINYU5fjzGEQRlvSLSC-07qn4Yv5HIkq8o6B5WLRxAb276LOR8M7wg3m49zPeW6AFS_b3Uvm1NaLp7oarKvPhe57wFz4VDhrS.png) 
                - **Diminishing MRS**:
                    - You are less willing to pay for more books if you have less money. 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xdD_GZn9yyeAJ9L-H3Cin_MTBznLB2lJirWVTYvNfZAVBSQFCXjanoE6nI-63ytQbJfOXKTnKPuwCd8IuPO4zmLGld-XmtAn2JTbUuU_JyTAcqtzGiJGsxygUPncLikN.png) 
                - **Utility**
                    - Indifference curves can be parametrised.
                    - Marginal cost―Cost of producing one more good or service
                    - Marginal Utility―Is  MU_1 = dU / dx1 - e.g. the change in utility with respect to a given good.
                    - Then MRS is -MU_1 / MU_2 , utility functions can be useful for describing customer choices. And can be inferred from things like shopping patterns.
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U6CZ7hN8XHwXnTqE3AbKr7UoyFEWUMREiibQn8XtkMKG0s-TWRHFj_hXoRwIZqG7mLqAeX2iNaWLS90BuXcWIAlvmgZCO2VpqCXD6Xv96xFaPQlqE7kltJAJI6nUpc0q.png) 
        - **The Marginalist revolution:**
            - Why is water cheap and diamonds expensive. 
            - The value of the last and least wanted addition to your consumption of a good sets its value to you. 
            - Marginalism asserts that individuals make purchasing decisions on an additional item, based on the added utility it will garner them. This idea shifted thinking from costs of production to demand.  
            - Local coal market has 3 producers and consumers:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-vko3s4LW2USaWft_HrsAWSr10bXcb_C5wmB0s8pFnN531Eb6BWtGhU0l2dMlf523KiyQYq-k3mu56BBm7lQT_sJbEaOgR3Yj3JN8Bv_G87FdEBd-bdGFHRjpQEEBIYY.png) The price of coal will fluctuate between winter and summer with demand. It's determined by the marginal transaction
        - **Demand** 
            - Market demand is the sum of the demand over the consumers. We can get a consumers demand from their utility or vice versa.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dYeW6tK9xXJ8L56YeOFbm-OJiuK9YxaS8lvYvMJKVcB0APpamzdLloeSgDbpOPJSnRrl8IR71jFS7wt2wsZLyAoYzdyYUSo5DJBQMOfksz8TqipMWqFJG9oTi_A41Nmi.png) 
        - **Elasticity** 
            - Elasticity measure the effect on demand of a small change in price. When do people stop buying your product given an increase in price.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vTT7b5HI05V2gkljJuvA-N__lA99IpgPl85EaPEArA7LQI3OBb_14H0vUQULw9QgVAUM_GycldqTKIyHMo2J1HZw3pYRqif6-1eqyzoqtzvSwxdul-yfTPqtZm9LkaoP.png) 
            - 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IwIUmuMf3EuWulCyFKAzRgs5RWZMSx4okIlM-S8wfP39AZrtjtg33kzqwB3dbZ6ETSBR92QD4B0jO2nFDj6mOSD4JMGjeB8dwCIH5gRYg2kPLMRLUdzllgofWY-7Zqsb.png) 
            - Elasticity = 1 means theres likely to be a substitute.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7-y8UFFxlppXF8VuLxiOQsmI4CwPQKhulJqIngb1n74FMQtaiTw18DBRmMqIVadikqJqjN-pHU7e-3nXiz_yNqBa914UqdGRQxCNTVYdm0xd0zL9LJ_6rIueMmNNsF9a.png) 
            - Elasticity = $\frac{\text{Percentage change in quantity}}{\text{Percentage change in price}}$ - so if we have 10%/30% - we have an elasticity of 1/3, meaning that change doesnt have a large effect. 
        - **Supply** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4rqcmEIjQt_7SHMQvvfC0rawX7bN5sS307ywCIuC9CtuiDA4SXZ6n-m_2m2tyJjY8jsZmnz5i4uL858ZndmTTYwcLCrjvqOMFW34IqhJP-2knWk6Nca6sixpTfBWWhHs.png) 
            - Average cost of goods initially falls are more are produced, then something occurs (overtime etc) and costs rice quickly due to capacity constraints. Thus supply curve is typically convex.
        - **Cost Evolution**
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j8i2xcfsdw00xI7OybDEvjmbqTMqFbrib9AoTvvNW9kGwRQP5GxFErq8238MCh1M1BHafGLiIzkfUU1dsuUCP5NgHIVSy4clXG7KGm0JnJHRRI4EUHr_5oLEnz0j8uGf.png) 
            - Firms can build more factories to build capacity constraints, gives nearly constant fixed cost as firm expands.
        - **Firm Supply**  
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0eUwnpy4Evz5Y61Fw6bosytT0EYGJI4OXlf9bJsIBIyAqmN2f9C5U6bnVahOWpTroGe-JTmuDthRyGSI_wtsOKstpmXmGeAZ6iaFnRzpUr6AhGksSFSBl0tfHkJ5Muvt.png) 
            - MC = Average cost
            - In a competitive market, at a price above p* the firm would have no demand and at a price below p* the firm would be faced with all the demand. The firms profit is maximised when it sets output so that its marginal cost equals the price p*.
        - **Putting it all together** 
            - Prices are set where supply and demand curves intersect.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2dG1jmObyO9oF7hWBzX3xm60RFWD5Z-wH5Ue-LJ9e_nn1_fam7JbMvMs266_GAa36ufhBP5oPksvynADsergwaYZE3VMQyVQSlMujO1wKRLkxT0mk-KOLp3fuOLnJSly.png) 
            - p* = marginal cost of marginal supplier.
            - Intrinsic advantages of non-marginal suppliers (good farmlands or easily mined coal) get build into rental values - more expensive. 
        - **Equilibrium** 
            - Supply and demand for 1 good―partial equilibrium analysis
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
            - Arrows impossibility theorem―There is no perfect way to aggregate personal choices into social welfare that's consistent with democracy.
        - **Transaction costs**
            - Trades are not free, time effort comissions bargaining policing and enforcement.
            - External transactions costs higher than internal ones
            - Agency costs within firms also matter hugely
            - Incomplete contracts, opportunistic behaviour comes out.
            - So should tech make firms smaller on average? 
        - 
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
            - The incumbent will strive to maximise switching costs, competitors to minimize them
                - File format wars
                - Loyalty programs 
                - Phone number portability
            - Incumbents promote complementary goods and services that increase lock in, tied printer cartridges to G suite.
            - Asymmetric switching costs, a phone network may supply a phone to win a customer, but keeping them they can simply offer minutes which costs nothing.
        - Network Externalities:
            - Networks more valuable the more people use them.
            - Metcalfe's law―The value of a network is proportional to the square of the number of users.
            - More complex than this, local effects are stronger, but still more than linear.
            - Overall effect - past some threshold, network use takes off rapidly and creates lock-in (telephone takes off as more people have them).
            - Real networks like fax and email, virtual networks like pcs and software. 
            - Most people choose to buy PCs rather than macs because of software. Then people decided pc was winning, so people just developed software for PCs. This pushed microsoft forwards.
            - It works for bads as well as goods, malware writers target windows while mac and linux are also vulnerable.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4zvGoVnMRgE48-8A6GJHCZmDyD5mS0Pkp0xFV_cUPCjZdKgAKmX9BWKFCAaTHMIzYkMqoguOzoC1jDcS5YatuMeEzaDD9zfs-PBtenaEFP3BTJCum_yNmSdrM3d7THgW.png) 
            - Markets with network effects can "tip", one suddenly taking over. Consider rail gauges in the 19th century. Colour TV standards in the 1950s. Paypal vs other payment startups. Facebook vs myspace. Google meet, skype, zoom etc.
        - Strategic issues:
            - High fixed cost + low marginal cost. Significant switching cost due to lock in and network externalities. Tends to lead to a dominant firm market model.
            - Given all three monopoly VeRY likely. 
            - Hence the race for market share when a new product or service market opens. IBM very well engineered, windows ship it tuesday and get it right by version 3. 
            - Is your customer acquisition cost still less than the lifetime revenue.
            - How bad are monopolies? No competition to allow equilibrium, however what if consumers arent paying anything? EU LAW: A fairly-won monopoly is ok, but cant leverage monopoly in one field to another - google cant direct people to their travel service.
            - US - monopoly used to be measured by consumer surplus, doesn't work for google and amazon. 
        - Price discrimination:
            - An efficient monopolist sells to each customer at their reservation price.
            - Pigou's three degrees of price discrimination:
                - Personalized pricing - haggling or loyalty cards
                - Versioning - first class vs economy
                - Group pricing - student
            - Tech increases the motive for price discrimination, have more information about you. Also firms are more likely to have market power.
            - Price discrimination is often unpopular, people don't want to pay more for the same things. 
        - Bundling: 
            - How to conceal discrimination - selling a number of products together.
            - A & B price willing to pay for word and excel:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nbzIJ1zjMLLSUb48JiYJcBC556k1-06cjLSkbAqBf6PyOqKYZbC_s1vV0Ki0-js5medhE1e8q6zaTxUO_7wt7tludXk-1sj8prILOrpRYCUd70Rdg7GhAAmosxXqN4Ts.png)            By bundling word and excel together, they can make £125 per customer, rather than £50 or £75 each.
        - Income distribution:
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b8F_Zq-Rdrxikjw2aDuXGu8KvyP2Pbo09L8OLyDQoIuQ7J4Wtngcz0QSrmWTUCCMnxFFR5mOytEZsC0j1mAA7S3NsuLECBZVm4AE23df2c4a8eGPiOXZlC5-RADWPNWL.png) 
            - The Gini coefficient is used to measure inequality. Gini = A/(A+B) where B is the cumulative income distribution. If Gini = 0 then communism, Gini =1 then the king has the lot.
            - Gini falls with development, rate of violent crime correlates with the Gini coefficient. US has similar Gini coefficient to a 3rd world country. The poor fight harder for welfare than the rich resist them.
            - Democracy is strongly corelated with equality, however cuts both ways. Farm subsidy that gives each farmer £200000 but costs non farmers £200. 
        - 
    -  _**Lecture 3:**_ 
        - The Business Cycle: 
            - Global economic crisis, money out of banks, banks bought out leading to economic debt doubling. The more recent economic crisis was not as deep as the last, but the recover has not been as thorough:
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zoTwERlnGfC_RiVFcJ1dOuWTgSPSSAYBF3IdssGfOc6JqVzNJPfGNqJHhPFTr637zqbghRfc0-vT2-qVgxU6xSlW0wkQn7JM0qezdregQ8wDhc5LhSPxAU-J1aLmdu0K.png) 
            - Pandemic causes greater impact on economy than the 2007 crisis, tech industry doing much better than other industries. 
            - Why the pattern of boom and bust?  
            - Mill and Ricardo argued that: demand for goods + savings = supply of goods + investments. Further savings = investment, so demand = supply. Meaning that the market for money needs to be considered, just the market for goods.
            - Keynes’ liquidity preference: people want a certain level of savings, maybe 3 months salary. In a recession, liquidity preference rises.
            - In a boom, people and firms borrow assets that can be sold later. A bank that takes in £100 pounds in deposits might lend out £94, meaning £6 of capital underwrites £94 of lending. 94/6 = 15.7  
            - In a recession, loans go bad, share prices of banks fall and banks call in loans, capital requirements increase so governments compete for available loans. Money supply contracted leading to large unemployment.
        - Recession and Tech:
            - Booms as people built railways**, Electricity replacing** steam lead to boom, mass production of cars led to a boom. Whole industries replaced with online alternatives, amazon half of book market, newspapers move to online. 
            - Increase in demand of online shopping.
        - Trade:
            - Wealth of Nations - if a foreign country can sell something cheaper, buy it with produce from own industry, employed in a way in which we have some advantage. Was a radical view, previously maximizing exports and minimizing imports.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Pj6uafDRyN_Xgjw4HIGLkLjzqN033NruSKXd6dKINmjEs4wCRkco_Dnr73azj7MY6vrAFk6m1ZVyUsnAmytxBDho2eP6yNvIQNKiK9g2dy49PjKClnxycSM4Yy576RwD.png) 
            - Ricardo, 1817: it’s comparative advantage  that matters, England unit of wheat costs half a unit of wine, while Portugal costs 2/3 a unit of wine.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4IQclGj4j4zfCGoEPFsD7fpo_xlYYips86GGOC2nfPQneZvkEeEGBjrgaYIX8eiTs5Zi5XpdvU69zkTog9TUpcIhQaqb9ljag_MKYQhQzXlIUHuyFl3kvF5vW2ye-TwW.png) 
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
            - Goods/bads that people care about but not traded - typically side effects.
ONLINE DEFINITION: "Costs/boons to 3rd parties as a result of producers". 
            - Consumption externalities include smoking in restaurants, increased education decreases crime. Competitive equilibria are unlikely to be pareto efficient in light of consumption externalities.
            - Can in theory fix with property rights, can only have 100 sheep on the commons.
        - Public Goods:
            - Scientific knowledge is a public good. 
            - Public bad being CO2 emissions, every country affects it equally meaning temptation to free ride.
            - Can **capture benefit from scientific discovery, without contributing**. Need to institute grants, nobel prizes, doctorate programs etc.
        - Club Goods:
            - Traditional communities can limit scale.
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
                - Bad drivers buy volvos to survive - adverse selection (hidden information, the drivers know they can survive in volvos). 
                - Drivers go faster due to increased safety - moral hazard (hidden action, might be subconscious)
            - These are examples of hidden information and hidden actions.  _Adverse selection is a lemons market._  I.e. the information is asymmetric, so the actors with more information participate selectively in trades. "when one party holds information that the other party does not have, they have the opportunity to damage the other party by maximising self-utility, concealing relevant information, and perhaps even lying. Taking advantage in an economic contract or trade of possession of undisclosed information is known as  **adverse selection**  "
        - Behavioural Economics:
            - Classical economics - individuals are rational, they maximise utility with no cognitive limitations.
            - Behavioural economics:
                - Behaviours deviate from this, based on experimental psychology. 
        - Bounded Rationality:
            - People tend to act intuitively rather than rationally, Prospect theory: People offered £10 or a 50% chance of £20 people prefer the former. If it's a loss, they usually prefer the latter.
            - **Framing actions as saving can make them more efficient.** Political marketing with terrorism takes advantage of this.
            - Cyber crime vs terrorism. 
            - Satisfice―People want to make just-good-enough decisions. Stop once meet goals.
            - Hyperbolic discounting, "people disregard far-future events  ",  discount events likely to occur in the future. 
            - The endowment effect―People are more willing to buy an object than sell the same object.
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
            - Classical economics sees institutions as rational, however managers make decisions that improve their **personal** utility as well. 
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
                - Also budgets constraints, revenue equivalent theorem only works for infinite money. 
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
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rZvVd8BnX4p36wkAIOnBIrPmXwuFBJdQxmIh8Qe9GK6s4uUrME6cRllFuxR2NMrCB3yoWAgdgy1N6zL0wUu-KcXkC20MyaUQWYnmTvmuNJyIQOsuDfzhzRisOx-fBZf3.png) 
                - With four people bidding for the first ad position, jerry has the highest rank. And has to pay 1.50 per click - This is calculated by taking Elaine's score divided by Jerry's score multiplied by his bid $\frac{6}{8}\cdot2 = 1.5$ 
                - Each advertiser is paying less than they initially bid, but as their bid affects their ad rank they have an incentive to tell the truth about their valuation. 
                - Ethical Aspects of ad auctions:
                    - Ad quality can easily transform into virality, so if your ad is good as clickbait you pay less. Trump paid less than Clinton.
                    - Many sites then tend to serve more provocative and extreme content, as they have a high quality score.
        - Game Theory:
            - Cooperation or Conflict:
                - If you want something, you can: Make something of value and trade for it - Economics.
                - Just take it, by force or the ballot box - Politics.
            - Game theory is a focus on games of strategy, with problems of cooperation and conflict among independent decision makers.
            - Games of perfect (chess) or imperfect (battleship) information
            - Example matching pennies, if two pennies are different Alice gets bobs penny - else he gets hers. The strategic form is:   ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/E9YwIxeKkXu1lqHplqGdrv_SHFUVKUHeKCQ0LjNFA2RkUPgpGYpM9dx0TQDat9fJSZHyo3ucSbKnSSli5sD1DGJ6U4X0iuD4kGbUSbku1aF_nviqMyBS4KXuRX45cTNQ.png) 
            - Zero sum game―One players gain is anothers loss.
            - Consider this strategic form: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7TKd0Fp1aHGZbdkyQUxKi5Lxr39MDqVSauBOuS5_ILDagnfuq3y8xDZpKU7WO3cUdRUOxI39qP_e_gTMxp77RedwPik8XjbZIJFsO-d9ygFuVS4fwcq-Lq2yktrAgeqf.png)         Bob is always better off playing left, regardless of whatever Alice plays. A strategy is an algorithm - input state and output play.
            - Nash Equilibrium:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/J9BK-4asv8GkG0WFHEGH2Ivz9dwSg2HWDoeAOGFE-aSRAY4bHh3dXjS0Hvr5UV3offClGwlr7A8bhcXq86_K-1AzlFUCkc8C7OIkI1aT2YjaerrHGfYmTPjBsoKQt9Fn.png) 
                - **The optimal strategy depends on what they think the other will do. **
                - Nash Equilibrium―Two strategies are in Nash's equilibrium when A's choice is optimal given B's and vice versa.
            - Pure v Mixed Strategies:
                - Rock paper scissors - has no Nash equilibrium. 
                - Alice plays scissors ⇒Bob plays stone ⇒ Alice plays paper... Fix this using a random algorithm.
                - **Deterministic algorithms called pure.**
            - Prisoners Dilemma:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4_VH7AgZnVE6DQrL2943-HqDL8F7f1NDAfUYJZB-X8mT4VDHQqgzh-JYPMGEf9hLXsKvfxXNcOz9Pvih0aGZU8jv4owcwStUmIe7GRsQcAJ4TUzbhKHfXmC4Q8XcihTI.png) 
                - Both will cheat rather than cooperate, applicable to defense spending - fishing quotas etc.
                - If played repeatedly - Tit for Tat solution. Cooperate at round n, do what other guy did at round n-1.
            - Price Fixing:
                - If it costs x to fly from A to B, to flights compete and spend x + 5, OR collude and charge 2x?
                - Competition laws forbid price fixing cartels. Bug can occur naturally. Try charging 500 and see what other airlines do. If they defect by competing, play tit-for-tat.
            - Stag Hunt:
                - People have to work together to hunt stag, but hares can be caught individually. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/phJ_0IA1kUxgZYTwYfjs5TWPxZiCXUMMC1qx9kAoUpv0roCC9Cls5Rr9qdpSL-CjWTPL2-8RQ6N1tEj2kYlbRduANgpGaXXQL0Tz0-Zyps4fQF0SD6nqGzWru57hCkci.png) 
                - Only chase hare if you believe your buddy will defect.
            - Volunteer's dilemma:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4TatYBq4ak-QZMZdc2hj8oynqq_AaHmyBrGd6Ykw8EoRQLCVM5Nq6tjPAMeWuEZdjr88WrIUBrGCm-gLpzVv4L-qBZ9zWodZffo_2QzfuJLCg4a3_o6ME9AKW6ca1s-P.png) 
                - Leader shows bravery.
            - Chicken:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1ns9L4OCTV0Luda7C0jR0aQ6SMnCZPNYWqJI6637KmuvrYiTGh1Y5Oj-WVYv9J3lkUB7894mIUe5BHvLaViUXT4UVVbs-d1wlaVKF2LXe8ZMd7UNuzY7MxJx0XseT_5p.png) 
                - Iterated version of chicken ⇒ hawk dove game.
            - Hawk Dove Game:
                - Food v at each round, doves share and hawks steal from doves. Hawks fight with risk of death c.
                - If v > c, whole population would become hawks - if c>v then hawks will start to die off and an equilibrium reached.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fmDPF-dInQpQH71USeyACbGDBgB3nscLlH3JJzNT4er96vIhCtjR1TYQGylX4N1pvTc6Vt6Sr3_pZcqlcEMQgX1KadmjmFAHIMDqaEx9SY8cG9oGrHlHWDcwUI1pK1WI.png) 
                - Look along columns, and multiply probability of hawk by your gain - e.g. for a dove if they're a hawk gain is 0, is they're not gain is v/2.
                - $\text{note}: (1 - c)v/2 = \frac{v-c}{2}$ 
                - if v > c:
                    - If one player chooses Hawk, the other should also choose Hawk, as (v-c)/2 > 0
                    - If one player chooses Dove, the other should choose Hawk, for the same reason.
                    - **So hawk dominates.** 
                - if v < c: 
                    - If one player chooses hawk, choose dove.
                    - If one player chooses dove, choose hawk. 
                - Small number of hawks prosper, as most interactions will be with doves. DO THIS: at hawk probability p setting hawk payoff = dove payoff.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xXsTJGAs1j2Rt3ZGXAFFl7tRuvM7ICZf_NUdOoVkV-OjMxssCw1B8-XRpKiWrV3pIf9DIIQ8kF3Ui556E7zsM9rrmUU11er2-fUmGlMbsso-wIczS2xn9-OZyTxDxd9G.png) 
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
                - A guilty mind - if no intent cant be prosecuted.  "  so legal advice or  going to the ethics committee may shield you!  But some offences are ‘strict liability’   
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
            - When you have offers on an online shop, this isn't an offer but an 'invitation to treat'. The customer then makes the offer and the shopkeeper accepts!
            - **This is important if you run out of stock, won't get sued.**  Need to link to terms and conditions.
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
            - Enforcement of foreign judgments not straight-forward, USA is rogue
            - One fix is to specify arbitration - private civil law 
        - Arbitration:
            - Contract can specify binding dispute resolution by an arbitrator
            - Can also specify applicable laws and other things **like** limits on cost
            - Arbitration awards are recognized and enforceable everywhere.
            - **This is a method of optimizing and privatizing the law to settle disputes between companies.** 
        - Costs:
            - US system - Each side pays own costs in suing. Can be expensive for some firms 
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
                - But the economic case is weak, except in the pharmaceuticals - to IT firms, patents are a nuisance many thousands of patents that are said to conflict 
                - Software patents not allowed in Europe **in theory, often discarded by courts. **The court keeps stretching this - not to be believed. 
                - In general innovation in CS very incremental - thousands of ideas in code, as opposed to a blockbuster molecule drug.
                - So far only 4 CS patents earn serious money
                - Microsoft has an open invention network, "trade patents"
            - Trademarks:
                - Marks that distinguish your good or service (IBM)
                - May be registered (®) or not (TM) - registering can make litigation easier. If registered, usually win in domain name disputes
                - Can sue infringers, but have to show misrepresentation **damages your business** 
                - McDonalds used to sue anyone with Mc in the name in catering - too aggressive. 
            - Copyright:
                - Statute of Anne, protects your literary works - extending from novels and drama to art, music. **Beforehand, courts gave monopolies to businesses to write books of particular types. **Oxford making dictionaries 
                - Is the main protection of software - No need to register but asserting copyright can make litigation easier
                - Duration of copyright has steadily increased, lifetime + 70 years. Walt Disney
                - Protects against copying - but fair use and fair dealing get outs from criticism
                - Moral right - **right to be recognized as creator **remain yours even if copyright is sold. Can refuse that your sold work be published if damaged
                - Many orphan works, where author not known. This stalled the Google Books project
                - How to avoid software having thousand of competing claims -  Stallman GPL Licence if you use free work, yours additions must be free too. BSD license allows companies to use as they like
                - Creative commons gives a general framework for sharing 
            - Other IPRs 
                - Specialist rights
                    - Database rights 
                    - US semiconductor chip protection act
                    - Plant breeder's rights
                    - Design rights
                - Rights based on contract
                    - Materials transfer agreements 
                    - Confidential information NDAs
                - Limits - employers cant restrict knowledge that becomes part of the tools of your trade - if become very good at coding at Google, can go elsewhere
            - DRM - Digital Rights Management
                - Copyright owners panicked at printing, internet, cassetes 
                - Huge push to introduce DRM - but shifted power to Apple, Google, Amazon from old-style record companies
                - US law made it illegal to mess with DRM mechanism
                - Lexmark vs SCC case allowed for reverse engineering for compatibility - allowed people to circumvent Lexmaark ink cartridge certification
                - October 2018 - John Deer put software in tractors that made them stop working if taken to unauthorised repairers - **breaking this legal, but selling tools to break it illegal.  **Reverse engineering for compatibility allowed
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
                - Not kept in  a form that identifies for longer than you need it 
                - Processed securely and protected against loss or damage - losing just as bad as having it stolen
            - Extra protection applies for "sensitive personal data" - health, about political affiliation, trade union etc.
            - Requirements to keep internal records of your database:
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
                - The right to erasure - if you have no compelling reason to keep the data, right to remove it. Google has this problem, man was bankrupt 10 years ago and didn't want that to be on Google.
                - Right to data portability - allowed to get a copy to feed it into a different system
                - Right to object - they have to record this, can hold but not process or remove
            - New systems must have data protection designed in - may have to do impact assessment
            - Data breaches must be reported to regulators **within 72 hours - **plus a req to notify data subjects (if data high risk) 
            - Fines can now be much bigger - used to be 500,000 now percentages of world wide turnover! BA got a 1.5% fine got reduced to 20,000,000 as shopping cart got hacked
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
                - Added denial of service of attacks in 2008 - **unauthorised modification to your service.** 
                - Making/distributing hacking tools is illegal since 2008 - confusing when white hats use
            - Case Law is Chequered:
                - Fines often much smaller than damages caused 
                - Only around 20 cases a year, often easier to charge under Fraud act
                - Paul Bedworth got off on an "addiction" defence - couldn't know what he was doing was wrong. " alleged that Bedworth and two others modified code at the Financial  Times share index, and disrupted research work at a European Cancer foundation.   
                - Whitaker convicted (but conditional discharge) for not disclosing a time-lock that froze the software when clients were late on making payments
                - Pile convicted and received custodial sentence for writing virus
                - AMEX case shows multi-level access can matter - not entitled to access part of system so unaurthoised access
                - police officer found to access data on a car parked outside ex-wifes house to find out who it belonged to. **Found to be legal, but subject to disciplinary action** 
                - Wimbledon case, mail bombing with 5 million emails is an s3 offence - test of unauthorised becomes "If I were to ask would they say 'yes'" I.e. Can I send you 5 million emails, No.
                - Cuthbert ("tsunami hacker") convicted of s1 offence for trying out ../../../ URLS. Donated money and poked around in the website, lied to the police.
        - **Electronic Communications Act 2000:**
            - Part II - electronic signatures:
                - Admissible in evidence
                - Creates power to modify legislation to allow the use of electronic communications or storage
                - Not as relevant in practise. Most companies care more about if you have the money, than who you are
        - Investigatory Powers Act 2016: 
            - Replaces RIP Act 2000
                - Much remains the same, but legalises lots of things that Snowden revealed - made to allow GCHQ and the NSA to keep doing what they were doing before
            - Deals with interception - revealing content other than the sender/receiver 
            - Deals with communications Data 
                - Metadata describing communication - length of communication, IPs, etc.
                - Provides for retention regime by ISPs
            - Permits equipment interference (with a warrent) cop put malware on your system
            - Permits bulk initerception, bulk acquisition, bulk equipment interference and collection of bulk personal datasets. Allows GCHQ to access all data coming out of UK, get all database data from Swansea etc.
            - Interception:
                - Tapping a phone, must be authorised by warrant signed by the Secretary of State:
                    - Product is **not currently admissible in court** - would only disclose some of the information, as don't want to show the holes in the collection regime.
                    - GCHQ can scan international communications for "factors" (keywords)
                - Some sensible exceptions:
                    - Delivered data
                    - Permission from both parties
                    - Stored data can be accessed by production order - just a judge
                    - Techies running a network, can intercept for debugging
            - Lawful Business Practise:
                - Regulations describe how not to commit an offence under the RIP/IPA acts. Do not specify how to avoid problems with data protection legislation or other relevant laws.
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
                - E-Commerce Directive also provides key immunities for ISPs:
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
                - John Rawls ‘Theory of Justice’: we should make  moral decisions about a society behind a “veil of  ignorance” of whether we’ll be born high or low  
would you rather be reincarnated in the USA or Portugal - poorer but with better welfare.
                - Aristotle: Consequentialist theories are for beasts, you'd be happier if you were stupid. Prefers people acting in accordance with nature and duty
                - It's not all about the consequence of actions, but the motives as well.
                - The many flavours include Kantian theory of duty - act only on maxims you'd like to be universal, and treat people not as means to an end
                - John Rawls Theory of Justice - should make moral decision based on ignorance, ignorance of whether we'll be reincarnated poor or rich - leads to maximising $W = \min U_i$. 
            - Moral Reasoning:
                - Koglberg's theory of moral development
                - -Pre-conventional:
                    - Stage 1: Punishment and Obedience (greater the harm the greater the wrong, law breaking morally okay if no punishment) - act as if doing wrong earns punishment
                    - Stage 2: Instrumental hedonism (Conformity to gain rewards)
                - -Conventional: 
                    - Stage 3: Conformity, what is right is what your family views as right. Conforming to those rules preserves relationships. Fulfil social roles
                    - Stage 4: Authority and social order, what is right is according to authority and duties 
                - -Post Conventional: 
                    - Stage 5: Morality of contract, individual right and democratically accepted law. Rules based on consensus, lawbreaking alright if based on social justice and preserving human rights. Changing laws preserved to breaking.
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
                    - Acknowledges the speed of distribution of computer science research
                    - Core principles: respect for persons, beneficence (minimze harm, maximize benefits) , justice (risks and benefits distributed fairly) and respect for law & public interest. 
                - Your Part II project may involve human experimental subjects
                    - Independent review by uninvolved scientists greatly reduce risks of civil litigation and criminal prosecution if things go wrong
                    - Pay attention to the procedures for ethics committee approval - if they say no don't do it (unlike Cambridge Analytica).
    - 
- Semantics
    - Semantics Supervision  1
        1. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EWCgcOK-lZJ6GXtKgqpmCeQA2MFAPMXNYxRMBbtq1Xo64BIrKQCe2_wG2RV3mMZDM0vlnXIIDh2jgmHZ7JV5hYlLSXv7Nh7gdgyv65mlLn2cT_dn6BefcHmjX5Q-Un2e.png) 
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
        2. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5Ris8GT10bHMokG27aJov3qS-y0LOsB4EbaA3x1h1pbTkoRyJWK9FX4GYRcTAdUtR-ckWJZ8cnaVcBBGlOy6idjILbTxVkbiAEgSiSujgYSpbiCSXSOq3cc6xGtHBf4x.png)  
            - Assign1: $\langle (skip); (l_1 := (!l_0 + 2)), \{l_0 \rightarrow 7, l_1 \rightarrow 0\} \rangle \rightarrow$ 
            - seq1:      $\langle (l_1 := (!l_0 + 2)), \{l_0 \rightarrow 7, l_1 \rightarrow 0\} \rangle \rightarrow$ 
            - deref:     $\langle (l_1 := (7 + 2)), \{l_0 \rightarrow 7, l_1 \rightarrow 0\} \rangle \rightarrow$ 
            - op+:       $\langle (l_1 := (9)), \{l_0 \rightarrow 7, l_1 \rightarrow 0\} \rangle \rightarrow$ 
            - assign1: $\langle (skip), \{l_0 \rightarrow 7, l_1 \rightarrow 9\} \rangle$ 
            - $\not\rightarrow$ 
        3. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PU6c_xWMwTB5BMOi_AkS3jCdEHAoljIZzyNF1tKO8M5b7SWREeV8y14p8GfIL5rYW4YehyDDK53ae1Lbm1Agt0aUFcc-bcBJTW_NXNnZsDT23rxT1KosrOxxyUvB6YkD.png) 
            - Assign1: $\langle  (skip;0)+(l:=2;0),\{ l \rightarrow 1\} \rangle \rightarrow$ 
            - seq1:      $\langle  (0)+(l:=2;0),\{ l \rightarrow 1\} \rangle \rightarrow$ 
            - op1         $\langle  (0)+(skip;0),\{ l \rightarrow 2\} \rangle \rightarrow$ 
            - assign1   $\langle  (0)+(0),\{ l \rightarrow 2\} \rangle \rightarrow$ 
        - 6)
        - 7)
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Rc4c9TOhFHPbRYzj828cEU4_JRuZDmfE-v24Gu_YmS6y--EURzhWW-PMU88sEU22nb49y_9OYtEjwwEdB_PleXYOnxhWitd-yfqix22QhzlPCYXoVZTXboLjKpahlJJQ.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Jc0qhbdhd-lL9d7htzVB0_f9SqP9bb5cg1QrRt-2_XH6PLNFBcCgD0PslnWjyxw__WxN4QVXJjagXmCzgDniPmUKrGjhscxgVhtRB8CdcFzhVshxtcn2trM9rlsZMn9w.png) 
        - 8) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tphLaWwDL-YsZsNbnqyIY3lPP1hldIbTHJjTmHTf32HFBRl65rLnYtqVRM6pgTP8FCPyBd__LGWK4u1OgePF-XJQuSVxTgMWJ4kxnnMBdwSzgPEuCnol18OwFxHrv_y4.png) 
        4. 9) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qWfnPEWfH_HIYJemqT-IHCZx3cpmYU4lSexlKMO_mKxcgZzZw9j6HqDFubB9XnHoPVzY1gO3e4NRsLSceJ4jPHuDdtlSIX0w8DPVnLA4Z84VFK6YPlm2P36wGpaDocVO.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Vx3Ur63En_V4zF2JiCllUlKE3nqF6yIrgRJgxZDUTiVBZbtgPw95U_0dzJ9ArCj0M2dHGq0ShIQvgEU7-qOfFNlq71eF0K92PslbFFBcAfcdHZe2JftJGAqZdtED7v6t.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/E7T2oUrHiW5yHfKarhk0Rw6izgx2OfDpiJeCAOGa7s0oL6DieyFBMB28SgTmCmvKGdjPiEmjsPbeNy5KSJZaTM30AIA4oJYf3Mu9mm24NPYbMmqtuFjMnQp_SGLdEvp0.png) 
            - N̶o̶,̶ ̶i̶f̶ ̶e̶ ̶i̶s̶ ̶v̶ ̶i̶n̶ ̶v̶;̶e̶2̶v̶;̶ ̶e̶_̶2̶ ̶v̶;̶e̶2̶ ̶​̶ ̶$v; e_2$ ̶ ̶t̶h̶e̶n̶ ̶v̶'̶s̶ ̶v̶a̶l̶u̶e̶ ̶i̶s̶ ̶a̶t̶ ̶f̶i̶r̶s̶t̶ ̶i̶n̶t̶,̶ ̶b̶u̶t̶ ̶u̶p̶o̶n̶ ̶t̶h̶e̶ ̶n̶e̶x̶t̶ ̶s̶t̶e̶p̶ ̶t̶h̶e̶ ̶v̶a̶l̶u̶e̶ ̶i̶s̶ ̶n̶o̶n̶e̶ ̶  - No cant step in a section of a statement.
            - I believe type preservation does still hold, I don't see how assign1 could change that, as the type should be unchanged - and seq1 shouldn't affect the final 'return' type, as we evaluate left to right - meaning our new int value is stuck at the front.
        - 
    - 
    - **Assorted Flashcards** ↓ 
        - What is a transition system?―A transition system is a method of describing changing state. We take a starting configuration, and have a transition relation $\rightarrow$ that goes from that to the next state.
E.g. $c \rightarrow c'$ means c can transition to c'.  
        - When is a configuration stuck?―For a config  <e,s> if e is not a value, and we cannot transition from <e,s>
        - Describe three things about language design we could vary  ↓ 
            - Could make right to left evaluation of ops rather than left to right
            - Could make assigning a value return that value, rather than a skip
            - We can only assign to values when it's already in the domain of the state at the moment, we could change this so we initialize a new l we we assign to it. Or assign everything to 0 initially. 
            - Can only store integers in L1, could change this include booleans, programs etc.
        - What does ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FGsB9CKnsytJMJO9kGgtdJDZbofaYdVyABkS2ofVlkGDUsWqLT2oN_f_np8Flp12NkjY6pN3GqAHPpz3oqGnqrAc8dsGQTyjHmu6-k95-YxQgrjhzrHLnoyq_qRtv71z.png)mean in words?―Means $e$ has type $T$ under the assumptions $\Gamma$ of the types of locations that can occur in e. E.g. $\Gamma$ is the fact that $\text{l1:intref, l2:intref...}$ 
        - What typing rule would you give if checking if $l ::= e : unit$―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V9e4T22_6_Ir_uMLFZi9vC0lDGX1yXPgyDpYaDJSWIs4EPhgQM4WkaGKEzz3h4lcSEmfs4xMqWcjFkMTGBURuar_YZmZJzHK1UmwTHl8e9WFBJBOoCrT_63pBB-Phspc.png) 
        - What is the progress theorem?―For <e,s> If we have ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JukJZtGp45sM6SjvPpmc93WFCkf7FT-glJPkwPNg8m1eYI9w6rV-CMjx0EQ30w_v8cK37uw5A9Qarx_yJ7gddjVcaQ7qxIzIl39tKD3fhY6gc6QOUq9bMF4jLY1yn3eu.png) i.e. The expression e is of type T under the assumptions in Gamma, AND the domain of gamma is a subset of the domain of s. Then either e is a value OR $\langle e,s \rangle \rightarrow \langle e',s'\rangle$. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pgg5f-2Us-DBod_3-Wzwg-jGiwfSVkUk54Mtyz9hJaYyh5f09HPRxUPnlqewNKQZogsqgc3339aPQ-0tVcvkeSjdlQKZ7xedAsKXAwKkUAElnRzJwoiwr0BleOcD8qwC.png) 
        - What is the type preservation theorem―For <e,s> If we have ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JukJZtGp45sM6SjvPpmc93WFCkf7FT-glJPkwPNg8m1eYI9w6rV-CMjx0EQ30w_v8cK37uw5A9Qarx_yJ7gddjVcaQ7qxIzIl39tKD3fhY6gc6QOUq9bMF4jLY1yn3eu.png) i.e. The expression e is of type T under the assumptions in Gamma, AND the domain of gamma is a subset of the domain of s. Then for  $\langle e,s \rangle \rightarrow \langle e',s'\rangle$, the domain of gamma is a subset of the domain of S AND the type is unchanged in e'. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V2a5kIFsh6g61wmDc-I6UpZWjZ0hK0LjXUXZfRS214lap4uus0afHjLg7nVBJ5T8lB_tB1IZjEWDazb0rwCfd3Pblo8QgAfplkDIcj0yonbsrXZDzDD-5mDJwCNTtk99.png) 
        - What is the safety theorem―Basically states well typed programs don't get stuck: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Bn5D8DStQPXLtxSTxcGJugDLZ_GOX6wWFGW3qwyIOZiu3I-cHlzw39y8oZj1AlPZ3WaIRfaPqBIKIHSosnJlM0NM5_DwkPxro7jsueoF2FdhDoBYOZMGAsC9RCqYyAHV.png) 
        - What are the type checking and type inference problems?  ↓ 
            - Given $\Gamma, e, T$ type checking decides if $\Gamma \vdash e:T$ is derivable  
            - Given $\Gamma, e$ type inference decides the type T in $\Gamma \vdash e:T$ if it's derivable or show there is no such type.
        - What is structural induction?  ↓ 
            - To prove a statement $\Phi$ about expressions in a language, it is sufficient to prove it over all leaves of all tree constructors in the language. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PQj8TAUbRs-mDTnkEvfaEc-kfCS4KOMXgVd5TSv1sdRT5RyPwTMnVLwiOf1NqHtRPJIjJwloOntA-OK3tO6D8CVZZRgD7rvJCJll-3kF5THNP_sbcAX7kylbAQmhlYa6.png)
NOTE - if one of our $e_1, e_2,...$ have and expression inside them **we can assume **$\Phi(e)$! 
            - The tree constructors are all the expressions, and the leaves are the expressions within the expressions e.g. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n51vL-XzcfF6JK-LdnTBblSfahhNkDccoQ9b2boGtj0-lA6YiucWDoTtqDmeZWVSYFW8K3db5Dh14oX0hm4gP7Fd1a-a4KHUWcVNZUnHkh9cNFs1F2j69gPTV4fFv0oO.png) 
So for n, need to prove $\forall \Z. \Phi (n)$ - for b, need to prove $\forall k\in \{true, false\}. \Phi(k)$
For e;e need to prove $\forall e_1,e_2. \Phi(e_1) \land \Phi(e_2)$ 
etc.
        - How could you prove: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8697WgBoxCs5V-dwhjdfNp66Zk04tED2t7mWb69wPGu4uOv-eF42w5YalKNVyOh7wyp_rvR4BFprd1At7WRSYCBrQEh_3f2dJQHpE0wEV-SnOSRqsCnug9Hoy6bn2wgS.png)―Given e is a value, it must be one of {skip, n, b}. Look over all the rules, and note for all conclusion <e, s> ⇒ <e', s'> there is no rule where e is a value.
        - What is Rule induction?  ↓ 
            - Rule induction that given a property $\Phi(a)$ of elements and any set of rules that define a subset $S_r$ of A, to prove $\forall a \in S_r. \Phi(a)$ it is enough to prove that $$\{ a| \Phi(a) \} \ \ \ \text{is closed under the rules}$$

            - E.g. for each **CONCRETE INSTANCE **of the rules ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/P1haDTvj1IK-bFi-kGCHgn2JWyFmYiqzPN4I0Nr8NnD_KgM4joAIReTb4Qy8GJFD85_9gl8rqmAGIUtHrl7TapoS6ghrEN8Cr-_UG3duKm5XIloxgC7tLYBV3sx48Qkc.png) we **need to prove**: $$\Phi(h_1) \land ... \land \Phi(h_k) \implies \Phi(c)$$ 
            - A slight variant exists, where the rules inductively define the set $S_r$ 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-8nKIRRTeP08oSzHzlIvkgdX-z3Xwwce2DWLMKe6tlsq4kaB2DVDj8zbfv30beT1K_0p0K9UG_g2fdZcxCaqJvoO1QJrWew8W_W7TlNcESUOQK5BEFxlk2BlE4y73Sne.png) 
        - What is alpha conversion, and how do we calculate it?  ↓ 
            - Alpha conversion is a method of removing name conflicts in function definitions.
            - We would like to be able to rename the variable (and any occurrences of it in e) in a function assignment, e.g. in $\text{fn x :T } \rightarrow \text{e}$ 
We want to be able to replace x with anything we want, **as long as we don't change the binding graph.** 
            - To do so, we build the resulting abstract syntax tree with the new variable and see if it's unchanged from the syntax tree with the old. If the new syntax tree differs, then we've got a name clash.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WXNWBpyOTh-RPMwL_7PONjnlS0bxnFG6p8C03xWed9Qw_PxabCLD-2jrEdkRwJXRpb5_YDZV3ePUHLMDfUispoig0exkLZDmZ5XVDbqZ1DXvgqbBwgqRPThAB1_8BVJI.png) 
        - What would the abstract syntax tree for ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QT63uYn4BkZjk7Qu1tY0jw_ZFZxLlVQPp-DztMtayIT7fpNn2EOXqUacIZQAt49LR0XQw5K0ObWMXS3cCdEu2nfAPnSzP_AAZ92C0fXR8qC5dJFFocoe0zU-OBRyTQeg.png) look like?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-kGuIej1WvA4wk2L78etriqkw_cRFtZZhMBAotirUvQ7R9t-Lr5ifcStdaWXcq4fH7RcP0mM8GskTuQa7b1CaZBFcy4zgKFLDxd4D3FT9M-J7eQt2370tcFnuTWPSz9Y.png) NOTE - we view f(y,y) as a partial function application tree. E.g. First apply z on y, then apply y on the resulting function.
        - What are De Bruijn indices?―Number of fn .:T⇒ nodes we meet while climbing to our one. 
        - What are free variables? When is an expression **closed? **Give three definitions to generate them  ↓ 
            - Free variables are variables in a definition who are not bound by a fn x ⇒ ...
"Say the free variables of an expression e are the set of variables x for which there is an occurence of x free in e."  
            - An expression e is closed iff fv(e) = {}
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iG_fyA0Gy7grdGfSvmggYKa7Ue8zKY81ngwbop4vl5gVxxFbHaLTcbryC64esZMbE0WRDKIGAjUseoPIFEq8Xf73Rxw230eYvTNsVgfKloo8F8A0Kucqrts6hgwQPOhx.png) 
There are many more:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a5W9bn7WFU-2DvQGVAHQMSFFof9IKnN-HFXhQdUdoX4qgX9FeLb4y9rWM7gcqJiz6rbWSr2xDOpvnN_Cp3xtR6-DahplLNAy_eqBWjOJPq-maqkJHp4rHMAT6df9hRTn.png) 
        - What does ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-xhJi9CKqwF5ohkorEVt4TTbT5pwP4UTgzyFl-Djd_mK1w20-gNwoEu-IAdk7fTmE8jO5GGOzDzhJP-6HpP6zcGL7826aNcwkyfa62i_NPF6HBsy3WGdlz2Q9O3jCR5g.png) give you?―It gives you the result of substituting e for every free occurrence of x in $e'$. **NOTE: May need to rename variables to get a good renaming, as in example 3 below.**
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yAn5FUjMhWOj5mAn7XVe5G-sL2zMQZdH5ik66aB0Qq_c9f_5sq3N650LlKn-DdtGA3ZnYkPlfQl4YuhxJXfS3Ag6rHJ8BSs7WYx_ZFH1ukyPjq6TwD38ULefWBCGGI3f.png) 
        - Describe the 3 (discussed) ways of function argument evaluation ↓ 
            - Call by value, evaluate function expression to fn .. ⇒, then evaluate the argument to a value and **then **substitute. 
            - Call by name, evaluate function expression to fn ... ⇒, then subtitute the argument into the function. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UsWGQq5ZwyWU2GV95_fCAf2jPLlc7c_jf76jCzID2xk1Nt4_RMixZxvTVO8Ut0yuhJfY5hsDInzNYav_2Qh5eLaJzXcU9uy_lISUCUh2-KLKpgYiCrVkRXxr61NzHf1w.png) 
            - Full-Beta, evaluate the function or the argument, as soon as the function expression is evaluated down into a fn:... ⇒ then substitute.
        - How must we change $\Gamma$ to allow for variables?―Before we only had $\Gamma_{loc}$ representing the possible types of locations, but now we must account for the possible types of variables in some $\Gamma_{var}$. Note that Gamma is the union of both.
This includes x:int, x: int⇒int etc.  
        - Explain these:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zmgENwoOjtSRE0IbZQ7X9I2qECKpB7ZNT1JtcMz9cRY6dHL36GyZ9BQ4q2klC0W8t75XvR2rhVI22ZsohFVE-WEsg1ZGOursTAab9pMgwM6vyKQubHQoppvmKM9ckXn0.png) 
 ↓ 
            - (fn) is saying, if I'm applying some x to some e, the types are as stated **if** the result of e given x:T is that e is of type T'. 
            - (app) is saying, An application of e2 to e1 has a type T' **if **e1 is a function that takes Ts to T' s and e2 is a type T. 
        - What is the normalization theorem?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AOK7Zlyqk6EfI20FaDd8EfVvL1psbkDdBXTqay4B67RTxvEx1taTQ0tEAR5xWBUMsAcIoRXf2pecNnEpvLrwXUS88IrTZ2HnFr3C1b7StF561RBZkkXQzFG4Eg_igL95.png) 
        - What is ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/24YwxJ5ATq6Y2rbEDDEy3FYE2AUAoSnMDMu0xN7kb7oTvBPifVRzHFPvi7CuRTlr7m3yyi87MgQYrQyYocPQ7ABe4_QYbnu5BU9I4xQS44NiIfAFSW072duAez99r5EN.png) syntactic sugar for?―(fn x:T ⇒ e2) e1
        - Why do we not use this ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DDFqwQ909AoVGEaOO4XKAPRVzI9C3FU5dlm05YbfuAOM-mnJlx8S7sGfPFLDcmPtIQtWRVSnWJzNT-gXzV8hhYJdxS9umbD1EetMWMQ-7vJ09T_PG0nrteK32KLcTYN9.png) to define recursive functions?―Because we can get infinite data structures, but because we're using call by value (not call by name) we'll have to do infinite work before we can use them:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PMzxlbgQyCdyUDjDy4V5O5vdtztZodkfmjcP0vrp8nE1BVbLfLuIV6CGRiYUPvOqpG9EbpB8gwaC2Rr61StPt3uGbRrtrkLqa74UVW8_6g2cVbmNY5gq0HC4NdbPe_7C.png)
We only want to allow recursive definitions of **functions, **not weird infinite data-structures - so we specialize our let rec fn to only allow for function input.
        - What is this saying: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/94kgNR1zF1TeZ0raED9CnCLej63BejH0CfdyOeGFamu6j3b8eTVeqTYsRgDXs8F45St8J2fyLLZDZr5ZPXeC0oPkyXgGKzfPNVifwB67X0453OSQAWa9wWb5If_JXpVl.png)  ↓ 
            - First part means, if we bind x to a function type and y has the same type as the input. Then the result of the function ($e_1$), should be the same type as the return type of that function.  
            - Second part is saying, if x is the function as described - then when subbed into $e_2$ we get the $T$ we would expect. 
        - What does this code do: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SLTMYgMcv1YdZhtkItM0pjlYy7UNhj00LwzYcnjomR0dLFke1vZDG56tqbXsotU4k0bNTNC4QJygqnTagaAaiA5sJ3Juj3to2I2zeRivT2Wdxuj92bv6sBPm_MyfIYN4.png) 
NOTE that **the definition of f isn't that important.**―This takes a function f, and finds the smallest number z s.t. f(z) <= 0. 
        - Explain this, I fucking dare you
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HyLWMoVd6wYvkodTpQWTLLwIuDlbiOOeRGFEPiZvTuSQ0FXgXxa89xx1jmHM_LavHEESNN8jSmPaDVpCIj7Y8fBXz-Von2i4enUNfPn1-in9jIDluTM5c7ZPE6bFEpK4.png)―If e is a Sum (Top line), if the real type stored is $x:T_1$ then substitute that into e1 - if the real type stored is $y:T_2$ on the other hand, substitute that into $e_2$. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8JCr-f2i5Wu2IXmqcSpdqZOu5AIFDpZmA6MjUP_ir3W10UWJMAnowNCVw9DRqCISIS9HD0j6-A6lLHeksYZFLpRuVb1odQRRQzdYqVHtuzmpfC-pp2LKWmugH4eIKIeB.png) 
        - Describe these three equivalences in the Curry-Howard correspondence:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iBv8YLPpYUCOCfLCQPLZqVCH85-XwQLj1mCfZpCFs6mIlZ8Jt2IIqquD3aEe31ApNYC0s71dW9WIPAiVTuCUjSy5nK_K05Saq9f-_duFarxa9t5BoPOpfOqeL55Rc5L7.png) 
 ↓ 
            - (var) Says if you assume P - then you can prove P.
            - (fn) If you assume x is of type T, then you can use that to **prove **that e is of type T'. 
In other words assume P and show P' 
            - (app) If e1 is of type T⇒T', then when we apply a T to it, we get a T'. E.g. if we have P implies P' and P. Then we must have P'.
        - What is this saying ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i2JDmBgsxaToq_IwICqE6_MEvD3c8OjymIbkabeb0Eo4vftoHmYv_2Ln8c8iLoA7K1cUWoZu0ThYv7dHALDA9_mQYk1nqGrwf-_RH0bBkFKRrVau3T7D8ORSJB27wkn2.png)―This is saying we evaluate all the expressions in our record before we can use it. Moving left to right, we evaluate it all haha!
        - Why is the location of a reference typed? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mpHvxqyNuBAVY7ERGHNeUBCHSGUNXKfE0SiNggcJ14aWxUo8MypI31ht0kgCUVTx_1Kz2J6u892GAcVHPZyulWX9C6t816L1za6jWQAHJ42_uExDqNBtMMJ-d9gTY3le.png)No other value is―Because we want to be able to return and pass these around, need to check if it's correctly typed. We want to decompose a e ref, down to a location - like we decompose addition down to an int.
        - What in god's name is this saying:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2Ysd9Mj6Utk66IITzgP0f8d4Sylwg6aN7xcp4Ca13EJpYKZi2VLOzg0MN0qx55D5i_f5TM56h2Dwbv7IC0wysnjI82mZfXoGLxyufpNPj7TjMRnpj5uY2VvCUruvzkQ_.png)―$s$ exists under the assumptions $\Gamma$, if all the locations of f are of type ref according to $\Gamma$- and they are of the same type according to s. 
E.g. all the types of locations mentioned in gamma are compatible with those in s.
        - What is this saying:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/260M0_xJ_XP8J1-s4QsI_Y94UH-uB-QngJb970-30FI6r_VDeLh02eI3NTC_0kKXbkq4hTtMxgoK6QxhiHS65DS8AKCMHxtpb8Q3c1YGbUkEIJOoKW0njE9w9DB_hU7S.png)―When we advance, our gamma needs to change as we store more things. So $\Gamma'$ is the new locations added by this transition. 
        - What is this saying:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gC-CSXA_xVT5DoRU3KB1uPzDySONqpeW2RD-WurosZrWot8mE2vzeg9QHge4TZzdhRxhZWv9rf7T36-Ldt9O1F95e49lDremDSDPwZlo6KJKvVgDakSliPwEwjyMWPsw.png)―It's saying we take $\Gamma \vdash s$ to mean s is a well typed store, if they have the same domains (same reference names) AND for all of the locations in the domain of $s$ they have the same types. 
        - How do you type this? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eMoUmEe2lBynzG4BBzB6qdrRahtV6H1xiSubbPqtHmbVf6VrC0bkwcLDvHAtjktNSHgJYR3LdrmnsxtZ7a7SEHw9JCLJpFMv1Y6jy_8WXt-FROwDHXc5S1KuvlXeoSjV.png)―You can't without polymorphism, even though we're giving the function an argument with **more **information than it needs ({p:int, q:int}) the function is specifically looking for {p:int}.
        - What does this mean![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7mKRu62sVSjq84FzeHgQfrL3VTWThwMPwRJT7tFBSlQvZ6BuQReju40s6af60LnuAZe06RQZK9LfgbxL2WCgk3rP0QrE5lA9yAgmezBNa-2Br2tv8LNnLnnM4rH_v0D1.png), then explain the subsumption rule ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r9s0UVVgEOT67H2DRTmLfLGFZeD0BaNBEa0g9MJuyY1VlXmL7KlzCJwsFmWtK2tFujBMSjziFrroGFpFzvxqmU-38G7XnesPyijmGUuKSbmA77KRCbV2W8nfe1k-8Qqs.png)  ↓ 
            - The subtype relation means that T holds more information than T'. E.g. {p:int, q:int} `<:` {p:int} (I know it's annoying that it's less than...)
            - The subsumption rule says that if we have an object of type T, where T is a subtype of T' - then we can use that type T in place of T'. E.g. we can use Dog in all the places the Animal class can be used.
        - Explain this if you're so smart
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QoN1zYPl_id5ctmepYafvFk9Hk44RDav4J70D_GBj0wHO-A98Fu-L7g7v8AxwyR4bugvlPrK123TG29gRqku8GC1IInxAuZAuSwffYVxL9KqaXnEkLES4HeJvwkvWbHh.png)
 ↓ 
            - The right half is straight forward, if a function T1 ⇒ T2 is a subtype of T1' ⇒ T2' - then then output T2 must be a subtype of T2'. E.g. if our function is a subtype of another, it must output MORE information than the other function
            - The left half says, that our input must have lesser or equal information than our parent function. 
Say we had a function int: double_value(int) and we augmented it so it also outputs how long it took to compute:  (int, float): double_value(int) - This is a subtype of double value, **however **if we augmented it to also take the time to prepare the input:
(int, float): double_value( (int, float) ) 
This is no longer a subtype! Consider, that this can no longer be used where int: double_value(int) could be - we can pick off the float output and use that, but we don't have a float to input!
        - What's the justification for this typing rule? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SnbaQ5631RRuGwlu_SB53QPtV_3AvWLFRgPR37-Vi20oPR0OjaTClfHwD62EOrsN565cCqdq4JUkvCPU85MS6Yt0N1Vk66QgIWoohMRx5lymWof8JtU3w9BS9EyJzqWD.png)―If T ref is a subtype of T' ref, then we can use T ref as a T' ref. Then if someone stores a T' ref into a T ref (when it's being treated as a T' ref) then we need T' to be a subset of T for that store to succeed.
        - When are two expressions the same?―If you can replace one by the other throughout any program without affecting the result
E.g. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WV1nOzM7-JXpFaSb86AvOAO4s-LwHNkOXky3pa7dLqY47kbptQCnbpey8tfSr4cmXvzI2eKKv0yT59naf2SETBCEjwYoWL5JLKh1RI0UnANlgAHWG1cX2u8aVj3mWwOZ.png) NOT THE SAME
We can't smack them into an arbitrary program context and get the same result:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jKk0F-jKwXgg__U3m0SovYjDWmtzUDg4GST2s_-RA8bQv8-xjHzM7s7Ki_YPBYqgEJg6rt1TgzGFOcQ36tG6rX3LkIeyN7UzXObloyuMkht6S8vzWq390h8zN9wTz_DZ.png) 
        - What does this mean? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JHSdqkHoD5o3io8fuCbuwqedkl9tp0D-qEirYooWhxjal4h3p3gKUX5kEbemIgnp-OKltZAr96Tz4t1_d64SbDbcDywOahuschac8JoxKGO-TFOyh5Zfq2cTSnUZj0Jq.png)―If two programs are equivalent, then either they go into an infinite loop - OR they resolve to the same value. This does mean any infinitely looping programs are the "same".
        - What are these congruences useful for? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dmOIhkV1NgFH4-7KNNSxxgkiKrdLVTNyTbJBVtrz9yhLiDQbMH-wLOLgvmk67mV_IyUIWnlXOrErhuXBv4fq0oA-Riwua3dYnotWmWOCdMViwuksf5vJtCjNNLkfjKdG.png)―These define all the places we can plug in an expression, whenever we plug in two congruent expressions - they **must **result in the same output and type. 
        - How do we prove congruence of two programs? ↓ 
            - We need to prove, that when we have two congruent expressions $e_1$ and $e_2$ that either both loop forever, or both evaluate to values with equal stores - We prove that if C[e1] is infinite, then C[e2] is infinite. And if C[e1] is finite, then so is C[e2] and they finish with the same values.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c2ZMEtWWszgazG-3cl7GIz4zGOT-pykDYdLgNUUErfZxbCf6XCyknSNwXY6as3UmB4Mj8WYB7XQ5dutGIeiSguq4laS-_Rt25QhnvkM3sBv8rXcYa5PrLkhUdSkzMLcH.png) 
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
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5RCG5z7hsBmrF-QFWJFCBf4JNmoCJWWx1qb5NumaUsGp05deuEiDNdkSuJLW2PQmSACOmx8S-k1pBEO1jmKnZGBPbRQ-EKVs2a7Oaabi-_-Z4AFpPJW26YzZLt1ZzFnt.png) 
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/G_vvYKWsUWgTdYvAraIN937T7jMUPxJNw3D4J3TBmz3nNBU-JTH7auSCnNNQ5iXccjaU35iQLwfdIXLwOEKOyCo9njrktDsGFCkn_rq7S1kOekWhRvvWFM0VGx6whilm.png) 
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cghRRf1V5S_SBfXGXm3z2enSqJJTBVaVsGimVxqxyFDgShejwOGxpplY3p3TJAtCtYy7roFLeMVgiQ3oZMQJtU-ryvqcMICADe7Yj6ieR2eAocYi6qvgJtE1YDPep0ON.png) 
        - 
        -  _**Question 4:**_ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hYVpdF3g_616zJwKqv979ygzaZOcIulZKc00b9rLC1Q0XfK95UD5FAD1jEM8M_9oY7E_XvZkQZKxynieI8yBYM9FnhwdJmsbCM5OCRB0GyuceMWn4bfnS6JPZB7V2arN.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/buFolL0zHPl78VhEl4Phop6IY4uJk4Ac9lUSJKuUuRLbwKL6oxwf89zKdcsPEMmuA_3amLUO60VeEHNEGdCBB8Fcqfp8paXwlMQr9LX1_UHtiPrQzZ7KFNtbM45rSxB-.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DXf6ni8P8txwwpykxN7UTe8MH86jgdI5DhYhIQitVMSubEMUOyjpPjACyDAXG2qsnmc716I4m-6ywj9P94LEnV8H_zpdZaCq-OsM5dQBRTzlGg42id-QSJqeAMCfPEqy.png) 
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
    - **Assorted Flashcards**
        - How do you solve $$P(X^2 \le Y)$$―$$P(X \in [-\sqrt y , \sqrt y])$$
$$P(X \le \sqrt y) - P(X \le -\sqrt y)$$
Note the **square brackets. **Meaning X is between those values. 
        - State the law of total Probabilities―$$P(A) = \sum_i P(A \ | \ B_i)\ \cdot  \ P(B_i)$$
If you can't find a way to pull out a component, can be useful to range over all the values. Very useful for Gaussian mixed models. 
        - If I have some gaussian mixed models $x_1 \sim Norm(\mu_1, \sigma^2_1), \ ... \ , x_n \sim Norm(\mu_n, \sigma^2_n)$ and the cat function $y \sim Cat([p_1, ..., p_n])$ what is the probability mass function?―$$Pr(x) = \sum_i^n p_n \cdot k \cdot e^{(-0.5 \cdot \frac{x-\mu_i}{\sigma_i})^2}$$
I.e. just the sum of the probability densities of each normal function, times it's probability. 
        - ```php
X = Norm(a,b)
Y = math.ciel(X)
```How would you find the pdf of Y?―Note that Y now has discrete values, and the probability 0 < Y < 1 is $$\int_0^1 \text{pdf}_X(x) \ dx$$
We'd then go from there.
        - If P is some transition matrix, what is $P(X_n = j \ | \ X_0 = i)$?―$$P(X_n = j \ | \ X_0 = i) = [P^n]_{ij}$$I.e. we raise the matrix to some power, and select out the desired item.
        - What are Parametric and non-Parametric modelling? ↓ 
            -  _Parametric_  ⇒ Guess a distribution for the data, then input arguments calculated from measured statistics (e.g. $\lambda$ = mean for Poisson) and then sample from that distribution. 
            -  _Non-parametric_  ⇒ Instead sample from the dataset itself (useful when there are no probability distributions that fit the dataset, think Deep Neural nets and images ).
        - What is the p‒test in hypothesis testing?―The probability of the result or something more extreme.
        - What's the difference between Hypothesis testing and Parametric sampling?―Hypothesis testing assumes the same means, while parametric sampling assumes different means... WHAT DOES THIS MEAN?!?!?!?!
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
            - f.)   Catches take a single argument and allow for the escape of a code block to a predefined location if an error occurs```
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zB0WVJroIQK0RkHQzho8zvjIfCkmXtlmIL3jLz1ZOLw0MoLHOFDLFaEUh1PaKLG-bc64iVhJIajoLCoCy2b996jK4MoffBw6nDR-nU2P_UYxEe8qrzNow4mU46s9QqRk.png)
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
``` ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4EncOulylcP3ibS2i2YvFWOnzfLIxKEKnPaaiubqq7GDBEapF3kAEAU-uD7XBSla7UjDwumB_HkKu4FrEu1z6Zt9XdJ1EG6EnsNg07bjh9XbeYN6QInE3JQbCpm6AdPo.png)
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
``` ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5CvOkCE8ymJEeAFOsAjUVCQ44LCbCUtbJYWKdAgIN0OS8u2Wsy8ILFqk3zp-DPTbnJzLqlTcGVHd5dTnEuRc-4ql_tRA0umkx1Z9W4pm4vhHkDiAUYf7cgRiqiUI5SfJ.png)
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/crzic95YRyiryiMHGIrmxmqkDggUe_2KbJnaftk-5YUTWrhbDsP0rUPfufcy8XmrHUAHD9C9DPDpkqALR3EPC4UDY5wVP-WUnHm3WYEhxJX-Ea59BIvdWIrXP6XKJJO9.png)
            - But wouldn't this mean, If I edit a value on the tree (other than the root) I'm actually editing two? Given that both left & right point to the same node. Sure the tree is build, but it can't be used.
        - 
        - 
        - $$\text{speedup}(n) = n(1-B)+B$$ 
    - Supervision 1
        1. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5x-kpFtSmurzNUmXPlR8GMTKt44S-pGI_uXQn-loC5FTlBbwH2KnTOZb_8vHNtz5Vc-B7ENcAojGyI83lmpHfPa1uVKKFQiiso5afgZZSAndShPRGx_1n1jctwLtBL13.png) 
            - 'a' is a char while "a" forms a string literal - e.g. an array of chars terminated with a null terminator \0.
        2. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Y7TUSDPht8rMMmjwyibGk-4zzDDtqFry6U0sB0wSGHN80olxqx8IhSL4w7q1B7AwdfL5s1F1G8LzJ8q7-K3oTPmuVAZMovFSPG6aKrPGL5mZ2dLldl2lZEglvvYQf7oj.png) 
            - Yes, it will terminate when j equals 5 (e.g. the 5th ASCII character) as long as the two chars were initialized to 0 (which is not guaranteed). This is because you can store integer values in chars, ranging from -128 to 127 for unsigned chars.
        3. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dpZ64aPO1RH5e4EsS1UpUmsF6S1j8sYlwLx6vDShfHV1sW0kweO6ow9QUln0VP0NK6dzaTv2HQGT_siYVBxZQugXD5dBNPaOHMVYXAvK5T_8rvmGEmV0otOOn9oYFKxz.png)
            - ```c
#define SWAP(t,x,y) {\
    t temp = x;\
    x = y;\
    y = temp;\
}
```
        4. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wnEQh3sjj-ggBtFu8O9dNmiI2bL6F-ycmM394KL46Q4W-zJ1YH1L8zb5AuhRQgO0yH7tmlkZoS4jhEaKhz0CZSQcIHphGvCgeGCD5LGCuKrC4Cx7S9oxORSzpGNZE18s.png) 
            - No, the i++ will be evaluated twice - meaning the x in the second line of the macro will differ from the x in the third line of the macro (unless the values of v[i+1] and v[i+2] are the same). Similarly, if f(x) changes when it's called twice we will be getting different indices of w.
        5. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/29dC0HQ66WGsn2vo69u4gNIJZt9N4FnfT5RwFJfM_G3BW7d5EhdsZOHsXWNjWacNu5zL96DZhIyb0C6NbtTEcqJ-TlSKnzxtwO9zn0fVU-ErJJFrKkkTJH3OY9HJb7no.png) 
            - ```c
#define SWAP(t,x,y) {\
    x = x - y;\
    y = y + x;\
    x = -x + y;\
}
``` 
        6. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VjH7bsEoeEXOb-ZAO4st3yXVKrJqqTgta_w8kMyod9Oe22Y2SY3BN4_UwFKmCzzzfdD_XCnzJG4-JQsuy9qVOjbjp3QFCvNPX9JwYgL0iIb2bJSPIhuJLUjEDjsW6djw.png)
            - p[-2] means the value two items before the pointer, this is legal if p is a pointer inside an array - this works because arrays allocate a contiguous block of memory which we can simply step along (pointer-wise) to reach earlier array-items.
        7. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6xCzQuVGM16QjzvbI4VY4CytzsorrFvjZX1148C4R1ovPU0H4YfSVTLPf1cagxhM-sD31wpTXg6cKaq74aQ609n_mIrRaPIb0Yvmv8tjBgN0IUPrbDjxPksgy8rh1VM-.png)  
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
        8. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GtHkEKbpOG6jIjweOng_l6W05H7Yu9StIWUwwxs9dLB2QzAVtBTakVMQh-pHkARbLFo5t3z56QsppajKkhummkk_929JjfaKqROSQEgcZnq0Z_E6z2HzmF_wMr1mqUGD.png) 
            - A const pointer to an int is a pointer that cannot be changed, e.g. it will always point to that integer. However, the integer value itself can be changed. A pointer to a const int means the pointer can be changed to point at something else but the integer value cannot be changed. For a const pointer to a const int, neither the pointer nor the integer value can change.
        9. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ux0pai4I1dl1vDxBhD-cTy9Pz5Ne3eDRwJRRZ6_oW7PPjGjn5gxRXK5Yci7-xFVq4OFPnbgim5O5YHtj-Atp0MF37r5LXuplWnJQLl4xKYwVvp2RaesqucxNl1jgu8zW.png)
            - You could pass the values as const:
            - ```c
int adds_wont_change(const int *x, const int *y) {
    return *x+*y;
}
``` However, this is only an indication not a promise - the function still has it within its power to alter the arguments using casts.
        10. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/q7tzntYJoJxSzhSjxKKL5xo7tQqMM2aUb8ggmcPB4hgSru1O59WOwTIIP62lL9UZ0YPkGiR0WsTifUx0OSi5me7cNjbveENoAqi5HehC-Vkt1tGajaBGdTSkVhekzIGE.png)
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
        11. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0P3QCnLO7m_QReMJWnZiOuxdyR3x8rUtd4bSxrgQch_t8UEhDy3_iGE_cLCbN7043bbQXt9NcOorpBdzmfdQnEzNhkW0RsMTM0Ltx9cSEdIhb1jvO9vaDtXgTKXoCGka.png)
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gcBE6wQaCcIKAs4I7o-7BUREOglWeWiNw8BVM06fB5iiiNPfsSRYKNJn0vki2qk-RDt2nyizBGi96ckZmwg_rQFMd10Tci3VUG2wwnunH84ZH-_MHy6VY6QWxUhE4njR.png)
            - Func1 can pass the pointer to the array to bar as the array still exists while bar runs, however when Func1 attempts to return the pointer to the array it's memory on the stack will be deallocated and thus any local variables will be lost and the values the pointer points to will be undefined - that is it's very possible they will be overwritten.
        12. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KmKDW7D5NUYnv6HW7bY0Ut9L2F_PSp9sxF8ykkzky4_dUrWqcETQTVvt38Ziv905iqB3iSvV7SQEiPUOhrVvgJ79DOcg_jc1y26c4jvSACgavfpB3Sdz3ZP4AHY3UU-C.png)
            - Declaration simply tells the compiler a variable with the given name is going to be defined at some point, while definition allocates an area of memory for the variable. 
        13. 
            - a.) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BlbZtBHf-NMCqx0Ni45FvW9jsJN0z5SnOn0pjG_FusfpndxTwr2s-jl7bfzlokLtRs-Q0rR3NqUjvoXWEm5YZkOonm8F1twD90e2am_nDGl_2sn6oatalYCCy3Zahj_l.png) 
            - **i is the integer value 78 0c 00 00 - which is  c78 which is 8 + 7*16 + 12 * 256 = 3192
            - p⇒c[2] is 62 in hex = 6*16 + 2 - slightly confused by this one, how does the compiler know to move 2 bytes along (as if its working with a char) rather than 9 bytes along (as if it was working with a struct i2c)
            - &(*pps)[1] is 0x18 + 2 = 16+8+2 = 26 (we move 2 forwards because we're dealingiwth a short)
            - ++p⇒i is 3192 + 1 = 3193 
            - 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/01AJtT87kPJuaTX5C5XZt2fkDMlszM_KcOj76VYkPP3spld9TxWz8igbTte2mVcT__CsI1CFlFlr5dQEdpgf-iLHbBo6NlIEVf1o_opvopjYa6F9XEK7M8kOF47i33A5.png)
                - First we cast our manager pointer to an employee pointer, however when we call wage(e) it sill uses the wage calculating function wage_man as the address not wage_em (we never changed the function being pointed to in the cast) - this then casts our pointer back to a manager pointer and calculates 40*10 + 20 = 420.
        14. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8zVLbpTXRupf0NULVKpgctjp9VkjS4ZcHNDQLuTRUyCGgd-edbhLPclwFXnuh2uXkjhKEDkIJdy5lWAaQEGJWZsfd_psK0fXIA_-BxK-hqwe3y9Ljza6RhcTgKYN287h.png)
                - ```c
#define CONCAT(a, b) (a b)
```
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tic3LFyhReYVg9QlQVNVKS7tIwEUZBzjUdDYyiQSwuZ9_n2oEAijrte48htdQ-JcRmPa7VhPCys-1hnYCqOysIGcx4ATPZnLFITqbksPDrIto3T51OM49qsvJWNfTpJj.png)
                - Line 3 would not work, as CONCAT only works by leveraging the fact that string literals next to each other get concatenated in c - e.g. "a" "b" ⇒ "ab". All CONCAT does is paste the values next to each other and let the language do the rest - however CONCAT(b, a) will result in CONCAT("UoCCL", a) and the compiler cannot simply infer the value of a to combine the strings (not a string literal). 
                - Line 4 would not work, as j is not a pointer and you are thus taking the integer value of the pointer that concat(a,b) returns. 
                - concat(a,b) allocates memory on the heap and creates a list of chars, while CONCAT simply places two string literals next to each other (uses stack memory). concat(a,b) returns a pointer to the char array while CONCAT(a,b) will evaluate to the combined string literals. 
        15. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Yc7pDYou5sDFsk8G-vXRMbYZJZkvIvoPnxYzVJzVgAFYuEB1gHaD_VDxY8yvyAernjZfJxRStzCKWnlxhKLebEBiAt38UsEs5HBe0iDRIrJeeAJE7wnMXcHI_ZDczi3L.png)
                - 500 bytes: (4 + 1 bytes) * 100. sizeof(struct Elem) =  5 bytes. long is 32 bits - compiler supports unaligned access, unlike all below.
                - 800 bytes: 32 bit machine, the long is 4 bytes, char is 1 byte. sizeof(struct Elem) =  8 bytes - but as 32 bit machine have to use two 4 byte words. Resulting in 100 * (4 + 4) = 800. 
                - 1200 bytes:  ^^48 bit machine, the long is 6 bytes, char is 1 byte, sizeof(struct Elem) =  12 bytes - but as 48 bit machine have to use two 4 byte words. Resulting in 100 * (6 + 6) = 1200. ^^ - possible answer but more likely: long 64 bits but aligned to 32 bits - 4+4+4 = 12
                - 1600 bytes: 64 bit machine, the long is 8 bytes, char is 1 byte sizeof(struct Elem) =  16 bytes- but as 64 bit machine have to use two 8 byte words. Resulting in 100 * (8 + 8) = 1600. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ep4ntJAbb4n94rCUys5-sCXlO1A_qHTJLLNhp1VaSOwwGa6LU1mKBgnyYGPDlAocg7j39QT7M7vUoPh_zTSCQKRoMdoaB5ne8E74h4aC1Mc6_P7-HdZsak0E_be6VYwQ.png) 
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
            - What are the three primitive types?―Numbers, Characters and pointers
            - Are there primitives of composite types in C?―NO
        - The **Stack **and **static locals** {{are built in}}, the **heap **is implemented {{by a library}}. 
        - Sizing of various types ↓ 
            1. Char―≥8 bits
            2. Int―≥16 bits
            3. Float―6 Decimal digits of precision
            4. Double―Double precision
        - Type operators meaning ↓ 
            1. unsigned―Makes the value unsigned
            2. short―Synonymous to short int, varies but is at least 16 bits
            3. long―8 bytes
            4. const―Informs the compiler that this value will not be changed, can still be changed using pointers though
            5. volatile―Means the storage can change at anytime, compiler must check it every time it's used
        - How do you specify different types of number in C? ↓ 
            - long―123L
            - float―123e10F OR 12.5F
            - double―123e10 or 1.4
            - octal―053
            - hex―0x54
            - 
        - **Enumeration**
            - ```c
enum boolean {TRUE, FALSE};
enum override {TRUE=1, FALSE=5, T=5}
``` One can define Booleans, they are indexed from 0 by default - but this can be overridden. 
            - What items in a enum need to be distinct and what don't―Names must be distinct but values need not be.
        - **Declaration**
            - Variables must be declared before they are definition, where definition means giving them storage. They can be declared, defined and initiated inline.```c
 int i = 5;
 char a, b, c;
```
            - What's the different between Declaring, defining and initiating a variable? ↓ 
                - Declaring―Telling the compiler this variable name will be used
                - Defining―Setting aside storage for a variable
                - Initiating―Putting a value in that variable
            - What does the extern keyword do?―It declares but doesn't define a variable, means the variable will be defined elsewhere - i.e. we allocate it no storage.
            - What does the **static keyword** do in regards to
                - **Static functions**―Usually functions are global, however static functions can **only be accessed within the file they're declared in** 
                - **Static variables**―Static local variables **don't lose their contents when they go out of scope** - so functions can reuse their values when called a multiple time. Static global variables are only seen in the file they're defined in
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
            - What is an expression?―An expression is a formula in which two or more operands are combined with an operator.
            - What is a statement―A statement is an Expression ended by a semicolon
            - What type and value will this expression take on?```c
int x;
short y;
x = 5, y = 3
```―The expression has type short and value 3. (The rightmost expression)
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
```―This results in abcdef, it works because string concatenation is done by default. "abc" and "def" are set to strings using double quotes. This happens at compile time
        - **goto statement**
            - Works but shouldn't be used```c
 some_label:
 	printf("We used a goto")
 goto some_lable;
```
        - 
    -  _**Lecture 2 (Only address space layout)**_   
        - 
        - **Address space layout** 
            - 
            - The **four most important areas of memory** within a **compiled x86 C** program―The **Stack**, the **heap**, the **static variables** and the **C binary code**.
            - Describe the **layout **of the **heap**, the static **variables**, the **stack **and the **C binary** code within the address space of a c**ompiled x86 C program**.―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9EqclGaeJ229axupOmXVqqvMy9SUdPUX7V3UUJKfqAvlQamJKCqsY20bbll3HJaaplmHBKojGNlm-veoZGeWqEKPswm8cEwA_HSec_wpoL4PW054VXI79WQoWA_A92Yu.png) 
Start at 0xffff ffff the top of the address space
The stack grows downwards
The heap Grows upwards
0x0 is often mapped to an illegal address to cause a seg fault if accessed
            - Describe the **features **of the** heap **―The heap is **manually managed**, using malloc and free - it is **generally larger than the stack**.
            - Describe the **features** of the **stack **―The stack is **managed by the compiler** and holds temporary local** variables** **declared in the body of a function** which are freed when they go out of scope. It **grows downwards on the address space**. It grows and shrinks as function calls push and pop their values.
            - Describe the **features **of the **data segment **―The data segment holds **global and static variables** who have a value.  
            - Describe the **features **of the **BSS**―The **BSS **stores **uninitialized **(don't have a value yet) local** **or global variables. Some or all of the bss is set to 0s - this is platform dependent. 
        - **Unspecified behaviour is **―behaviour where the C standard give's 2 or more options of implementations - the implementation chose can be decided by the compiler. It gives more freedom to optimise code for a given architecture. Some examples are whether to implement inline, evaluation order of function arguments, order and contiguity of memory in the heap. Memory layout of storage of function arguments.
        - **Undefined behaviour is**―behaviour not described by the C standard, when a compiler is faced with such behaviour it can do **anything it likes**. An example is modifying a string literal (string literals are in read only memory) or i++ + ++i.
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
            - ^^**Two**^^^^ main components^^ of classes―^^Data members^^ and ^^member functions^^ which act on the data. Both data members and member functions can be static.
            - The^^ 3 access controls^^ of C++ members are―^^private, protected and public^^ 
            - **Class and struct are almost synonyms** in C++, the only difference is―class members are by default private while struct members are private by default.
            - ^^Classes ^^are ^^created ^^with―^^**class or struct keywords**^^**:** 
                - ^^Struct^^ ^^members default to ^^―^^public^^ access 
                - ^^class members default to ^^―^^ private^^. 
            - A ^^constructor ^^is simply a―^^Member function with the same name as the class^^ 
            - C++ supports overloading on both―constructors and member functions
            - A **destructor **is named with―the same name as the class prefixed with a **tilde **(~)**.** 
            - Big differences from Java:
                - ^^Values of class types are^^―^^ ^^^^**not references to objects**^^**, but**^^** the objects themselves**^^**. **
                    - So we ^^access members with C-style . (dot)^^ ( using -> more convenient when we have pointer to objects). 
                - We ^^can create an object of class C,^^ two ways  ↓ 
                    - ^^On the stack by declaring a variable C x;^^
                    - ^^On the heap: new C() ^^^^**which returns a pointer to C.**^^ 
                - If a function is ^^**statically resolved**^^** **it means―the code to execute for a given function name is ^^**generated at compile time (or linked at link time) not runtime**^^.
                - If a function is ^^**dynamically resolved **^^it means―the code to be executed will be ^^**determined at run-time**^^. 
                - ^^Member functions by default are resolved ^^―^^**statically**^^. For java-like code ^^**declare them virtual.**^^ 
                - The virtual tag and the dynamic resolution allows for―runtime polymorphism.
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
            - The preferred form of **constructor** **initialization in C++ **is (somehow). **It MUST BE USED WHEN**...―```cpp
 Complex::Complex(double r, double i) : re(r), im(i) {...}
 
 // You MUST use it when itializing
 // const and reference members
```
            - In java, **constructors only **{{**initialize heap storage**}}** **(which has to be pointed to), only way to update is {{x.f = updated_val}}; 
            - In C++ because objects values are "first-class-citizens"―there are more update behaviours
                - In "C x;" x is initialized using―The default constructor   
                - In "C x = y;" x is initialized using―The copy constructor
                - We need to worry about what "x = y" does. 
                - We split class definitions into separate behaviours and control them to―Preserve **class invariants **(If I can define an object, with no members initialized - certain invariants may not hold) and **object encapsulation** (All the behaviour of the class should be held within the class)
            - **Default Constructor ** 
                - Default constructors are called when―you type "C x;" or if you do "new C();" i.e. with no arguments.
                - If no default constructor is specified―The compiler creates one, with little to no initialization.
                - To disallow users to use the default constructor we―define the default constructor and set it to private.
            - **Destructors **
                - destructor are called―when a stack-allocated object goes out of scope **INCLUDING when an exception causes this to happen**, when a heap allocated object is deleted
                - There can only be {{one}} destructor for a class
                - Make destructors **virtual** when―The class has subtypes or super-types - as we'll want to inherit the destructor
                - Stack allocated objects, with {{destructors}}, are a good way of freeing memory after the scope is exited.
            - **Copy Constructors**
                - ```cpp
// Initialization methods:
Complex c(1,2);
// VS
Complex d = c; // Copy constructor evoked
``` 
                - To augment the default copy constructor use the following syntax―```cpp
class Complex {
	Complex (const Complex& c) {...} 
}
// we don't pass a value
``` This is useful when I have member variables with pointers in for example. Don't just wanna copy everything
                - To **disallow **copying of objects―Make the copy constructor **Private!** Note, can still use assignment );
                - ^^IMPORTANT NOTE:^^ Assignment (d = c) differs from invoking the copy constructor: Complex d = c. **Does not** use the copy constructor.
                - What does copying an object using Complex x = y; do by **default? **―Simply copies any non-static member variables, no constructor called! 
                - 
            - **Assignment operator**
                - By **default **when the assignment operator is used―all the **non-static** members of a class are **overwritten **(x = y;). 
                    - This may not be desirable if the class contains pointers, when I copy a dog I want it to have a pointer to its own dog bowl?
                - You can implement your own assignment operator this syntax (for the class Complex)―```cpp
Complex& Complex :: operator=(Complex& c) {...}
// We take the input to the right hand and return a reference
// e.g in x = y, c = y
``` 
                - We use **reference types** in the assignment operator―Because  if we passed by value the **copy constructor would have to be invoked,** which would be slower. It would also be slower because we would be passing more data.
            - **Constant member Functions**
                - **Member functions** can be declared **const **―This prevents the function from modifying any object members.
                - The syntax for constant member functions is (for a function real in the Complex class )―```cpp
 double Complex::real() const {
 	return this->re;
 }
 // Note that if you declare beforehand you need to include the const:
 double real() const;
```
            - **Arrays and heap allocation**
                - If we want to create an array of objects, the class needs a {{default constructor}}.
                - To create and delete objects on the heap, we use this syntax―```cpp
 Complex* c = new Complex(1.0);
 // To delete them we use
 delete c;
 // This invokes the object destructor !!
```
                - We **need **a method for **array heap deletion** because―C doesn't distinguish between a **pointer to an object**, and a **pointer to an array of objects**. 
                - Array heap deletion is done using the following syntax―```cpp
 delete[] c;
```
                - Deleting objects using the array heap deletion invokes―the object destructor on each object.
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
                    - Consider a class with objects as member variables Complex a, how do we initialize said objects? I.e. how do we call the constructor?―```cpp
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
```―Temporary objects are things such as: ```cpp
 string a("dsadsa"), b("dsadfsadsaadsa");
 // THE TEMPORARY OBJECT BELOW IS FORMED FROM (a+b)!!!
 const char* SCARY = (a+b).c_str();
 // c_str() just returns a pointer to the objects string value
 // HOWEVER, because its temporary the value is lost!!!
 // SCARY don't got nothin' in it
```
                - **Friends**
                    - Within our class, we can define another class to be our **friend, **this means―Code within the other class, can **access the private and protected members** of our class: ```cpp
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
                    - We can even define non-member functions to be friends, this means―that functions defined elsewhere can access our private methods: ```cpp
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
                        - It can be done outside the body of the class, using the following syntax―```cpp
bool operator==(Complex a, Complex b)
	return a.real() == b.real()
		&& a.imag() == b.imag();
``` 
                        - Or it can be done inside the class, in which case we can use the following syntax―```cpp
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
                        - We can use overloading with streams like the built in type using either syntax below: The difference is:―```cpp
const char* s = "Hello World";
cout.operator<<(s);
cout.operator<<(std::endl, s);
// The << operator is overloaded, if we pass one value it behaves differently to two (in this case it would pass &s[0])
```
                - **Inheritance** 
                    - C++ inheritance works much like java
                    - The syntax for C++ inheritance is―```cpp
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
```―The problem is, makeAnimalBark isn't virtual, so the output will be - "Bark" "A noise!". Note this is **only **the case if we pass a pointer - if makeAnimalBark took the value it would work.
                    - Non virtual member functions depend on the {{static type}} of the arguments. 
                    - We need the virtual keyword because―a pointer to a subclass can be cast to the base class, then the base class cannot see the overridden function. 
                    - To get polymorphic behaviour we must―define the function as virtual in the superclass. Then it will be dynamically evaluated at runtime.
                    - **Non-virtual** member functions are called depending on {{the static type }}of the variable, pointer or reference. Since a pointer to a derived class can be cast to a {{pointer to a base class}}, calls at base class do not {{see the overridden function}}. To get polymorphic behaviour, {{declare the function virtual}} in the {{superclass}}. 
                    - To enabe **virtual functions **the C compiler must―generate a "virtual function table" or vtable. This table contains the function to call for **each object instance**. This adds **run-time overhead **as every function call **must go via the vtable.** 
                    - Why does C++ give the option of none virtual overridden functions?―It's a **trade off of performance vs Programmer conceptualization** - dynamically** type checking at run-time can be slow**, so if it's not explicitly needed we don't want to do it. Instead of a function call in machine code, its an indirect function call - While at first glance this is not much slower, the **effect on the cache and branch predictor can be large** 
                    - **Enabling Virtual Functions**
                        - To enable virtual functions, C++ uses―a vtable or virtual function table. These store a pointer to the specific function to call for every object instance. They are slower.
                        - C++ vtables also encode RTTI - runtime type information about the class in question. Can ask if an object has the same type as another.
                - **Multiple Inheritance and Casts (11.3)**
                    - **Abstract Classes** 
                        - Works like java but with a different syntax 
                        - In C++ it is verboten to {{instantiate }}an abstract class.
                        - What is the syntax for C++ abstract classes―```cpp
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
                        - When can a derived class be instantiated?―When all the abstract functions are implemented. If some of them are, you cannot instantiate the class. 
                    - **Multiple Inheritance**
                        - In C++ you may inherit from multiple classes, if you have a name clash you must...―```cpp
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
                        - The Diamond problem with multiple inheritance―Is when a subclass contains two instances of another class. E.g. two sets of the same variables. It can be achieved like so ```cpp
 class A {int someInt;};
 class B : public A {};
 class C : public A {};
 class D : public B, public C {};
 //We can do the following:
 D dInstance;
 dInstance::B.someInt = 3;
 dInstance::C.someIne = 4; 
```
                        - If we have a case of the diamond problem in C++―All variables from the "top" of the diamond, must be chosen explicitly in order to be used. E.g. we need to know which A class to choose from if we have two instances.
                        - **Virtual base classes**
                            - Virtual base classes allow for only {{one instance}} of the "top" class within inherited classes. 
                            - Virtual base classes mean that―any class that **inherits **from multiple classes **containing the same virtual base class**, will share that class instance without ambiguity.
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
                        - In C++ the role of casts and constructors can overlap, casts can be seen as implicit calls to the constructor. Give an example with Complex―```cpp
 double x = 0.1;
 Complex s = x; // Because there is a constructor that take a single double
 
 // Similar to this: (which simply does the cast)
 int a = int(x);
 int b = x; // Implicit cast!
 
```
                        - To disallow ```cpp
 double x = 0.1;
 Complex a = x;
``` we must―Declare the constructor **explicit.** Implicit vs explicit casts.
                        - If I want to allow casts from a class type to a default type I do the following―Overload the operator of the type we wish to cast to, e.g.: ```cpp
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
```―```cpp
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
            - Done just like java, but **throw object values** not object references - the reason for this is―if you **run out of storage**, a reference requires the creation of an object in storage... 
            - The **principal of exceptions** is a given piece of code (**a library**) may  _encounter an error and not know what to do with it_  - the user code may know how to handle it.
            - One portion of code **throw**s an exception, another **catch**es it.
            - If an exception is thrown, the **call stack** is―unwound until a function that can handle the exception is found
            - An uncaught exception results in the program **terminating**.
            - **Throwing Exceptions**
                - Exceptions in C++ are just {{normal values}}, matched by type. Often a {{class}} is used to define a particular error type.
                - An instance of the class can then be thrown, caught and possibly rethrown. The syntax for these is―```cpp
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
                - The syntax for catching multiple errors is the following (also what does catch(...) do?)―```cpp
 try {...}
 catch (errorA) {...}
 catch (errorB) {...}
 catch (...) {} // is a wildcard that catches all exceptions - discouraged, what have I caught?
```
                - Class hierarchies can be used to express errors―e.g. someError > myError. However, this requires runtime-type-information!
            - **Exceptions and local variables**
                - When an exception is thrown, that **stack is unwound** this **differs **from **stepping down the stack** as―all  _local variables we meet call their destructor_ . This plays the role of try - finally (in java finally frees memory)
                - It is **good practise** to wrap locks, open file handles, heap memory etc. in **stack allocated objects** - this is because―when the stack is  _unwound the destructor of the stack allocated object_  will be called and all the  _memory can be freed. _  
                - RAII is―**Resource acquisition is initialisation** (this is a terrible name), actually means  _memory is freed once the object is out of scope_  - done by  _wrapping resources in stack allocated objects_ .
        - **Templates**
            - Templates support **metaprogramming**, this is where―code can be  _evaluated at compile time_  rather than run time
            - Templates support **generic programming**, this is where― _types are_   _parameters _ to a program
            - Generic programming in **void * pointers** has the **disadvantage**―that we lost type-checking
            - **Class templates**
                - The syntax for defining and instantiating a class template is―```cpp
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
                - What is the syntax for setting a specific template type?―```cpp
template<int i> class ... 
```
                - How do you give a template several parameters?―```cpp
 template<typename T, int i> class ...
```
                - How do you declare a subsequent argument with a template argument?―```cpp
 template<typename T, T x> class...
```
                - What's the syntax for a template function with a default value?―```cpp
template<typename T, int x=100> class ...
```
            - **Templates behave like macros**
                - Templated classes are **type checked** when―the template is instantiated. 
                - Template **definitions are often placed** in the―header file, because if we had it in one file and another file used it - we'd end up having to recompile a load of files whenever we updated the template. Additionally, it makes separate compilation impossible.
                - The **difference between java and C++ templates** is―** Java does type erasure** setting all the types to Object, while C**++ works like a macro** where the type is replaced and the new function for that type is added to the binary 
            - **Templated specialisation**
                - What does **Template specialisation allows** **us to do** and what is the **syntax**?―It allows us to define **different definitions of a class** depending on the type parameter passed. 
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
                - The syntax for defining and instantiating a template class is―this:```cpp
template<typename T> void sort(T arr[], const unsigned int& len);

// The type of the template is then inferred from the argument types:
int sam[] = {4, 1, 2};
sort(sam, 3);
sort<int>(a,3); 
``` ```cpp
 
```
                - Unlike template classes, template functions have {{type inference}}. 
                - Two benefits and a negative of using **templates for functions**  ↓ 
                    -  _Better type checking_  than using void *
                    -  _Larger binaries_  if multiple different types of sort() are invoked
                    -  _Potentially faster code_  **than runtime type inference** as we don't have vtables for functions - we know the type of the function at compile time
                - **Overloading templated functions** 
                    - Templated functions can be overloaded with {{templated }}and {{non-templated}} functions. Resolving an overloaded function call uses the "most {{specialised}}" function call
            - **Template specialisation enables metaprogramming** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_qsNY9_ag-ZhMMnJoBIlTBcdNHf3yUahT-AMm2TonL3ay1_mtpzUixn0ACOUbvzuRBBUliHrc1qG9hED_MVdo29srt_WOUI7DZfbgABrzZ47XkYigIPhHplmm7HBr46h.png) 
                - Meaning templates are a Turing complete compile-time programming language! However the type you seek to evaluates value must be known at compile time - like enum or static
            - 
            - 
        - 
    - 
    - **Assorted Flashcards** **for C** 
        - What can the following code result in: ```php
#include <limits.h>
#include <stdio.h>

int main(void) {
	printf("%d\n", (INT_MAX + 1) < 0);
	return 0;
}
```―Don't let them trick you! INT_MAX + 1 results in an overflow, which is undefined behaviour so **anything can happen.** 
        - How do you use an enum?―```c
 // First declare it
 enum boolean = {true=1, false=0};
 // Then create an enum variable that can range over those values
 enum boolean some_value;
 some_value = true;
```
        - What's the different between Declaring, defining and initiating a variable? ↓ 
            - Declaring―Telling the compiler this variable name will be used
            - Defining―Setting aside storage for a variable
            - Initiating―Putting a value in that variable
        - What does the extern keyword do?―It declares but doesn't define a variable, means the variable will be defined elsewhere - i.e. we allocate it no storage.
        - What does the **static keyword** do in regards to
            - **Static functions**―Usually functions are global, however static functions can **only be accessed within the file they're declared in**
            - **Static variables**―Static local variables **don't lose their contents when they go out of scope** - so functions can reuse their values when called a multiple time. Static global variables are only seen in the file they're defined in
        - How are variables passed to functions―Pass by value. 
        - Object files consist of machine code and a list of what?  ↓ 
            - Defined or exported symbols, representing global variables or function names.
            - Declared symbols, e.g. extern variables, or unimplemented functions. Declared but not defined.
        - What does a linker do, and how?  ↓ 
            - A linker combines multiple object files into one executable
            - It does this by combining into a binary, and then adjusting absolute addresses. It also resolves all undefined symbols.  
        - Why are headers needed and what are they useful for?  ↓ 
            - Headers are needed because we want to be able to compile different files at different times and combine them later - but without a header we don't have **declarations **of those functions. So headers can  supply the declarations of functions and variables.
            - They can be used for pre-processor macros.
        - **Address space layout**
            - The **four most important areas of memory** within a **compiled x86 C** program―The **Stack**, the **heap**, the **static variables** and the **C binary code**.
            - Describe the **layout **of the **heap**, the static **variables**, the **stack **and the **C binary** code within the address space of a c**ompiled x86 C program**.―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9EqclGaeJ229axupOmXVqqvMy9SUdPUX7V3UUJKfqAvlQamJKCqsY20bbll3HJaaplmHBKojGNlm-veoZGeWqEKPswm8cEwA_HSec_wpoL4PW054VXI79WQoWA_A92Yu.png)  Start at 0xffff ffff the top of the address space The stack grows downwards The heap Grows upwards 0x0 is often mapped to an illegal address to cause a seg fault if accessed
            - Describe the **features **of the** heap **―** **The heap is **manually managed**, using malloc and free - it is **generally larger than the stack**.
            - Describe the **features** of the **stack **―The stack is **managed by the compiler** and holds temporary local** variables** **declared in the body of a function** which are freed when they go out of scope. It **grows downwards on the address space**. It grows and shrinks as function calls push and pop their values.
            - Describe the **features **of the **data segment **―The data segment holds **global and static variables** who have a value.
            - Describe the **features **of the **BSS **―The **BSS **stores **uninitialized **(don't have a value yet) local** **or global variables. Some or all of the bss is set to 0s - this is platform dependent.
        - **Unspecified behaviour is **―behaviour where the C standard give's 2 or more options of implementations - the implementation chose can be decided by the compiler. It gives more freedom to optimise code for a given architecture. Some examples are whether to implement inline, evaluation order of function arguments, order and contiguity of memory in the heap. Memory layout of storage of function arguments.
        - **Undefined behaviour is **―behaviour not described by the C standard, when a compiler is faced with such behaviour it can do **anything it likes**. An example is modifying a string literal (string literals are in read only memory) or i++ + ++i.
        - Functions and variables can be extern or static, what is the default - what does this mean in the global and static scope for both  ↓ 
            - Functions and variables marked static can't be exported as symbols in the global scope and used in external files. The default is extern, e.g. other files can reference them.
            - Variables marked static keep their value in-between function calls.
        - Describe how the #include directive is used, and how it can be used to generate macros  ↓ 
            - The include directive performs text replacement. E.g. ```c
#define TEST 4.432131
// Note that no semicolon is needed
```
            - It can be used to create macros like this baby:```c
 #define MAX(A,B) ((A) > (B) ? (A) : (B))
 // Need to be careful to put brackets around everying
 // Because any old shite can be replaced in there
``` Note that # before replacement text places it in double quotes, e.g:```c
 #define STRINGIFY(A) #A
```
        - What is array[10] (selecting the 10th array value) equivalent to in pointer arithmetic?―```c
int array[] = {1,2,3,4,5,6,7,8,9,10,11,12}
*(array+10)
//  Note you can treat all pointers to array indexes like this E.G:
int* x = &array[1];
printf("%i", x[2]); // outputs 4
``` 
        - Describe argc and argv, what are they?  ↓ 
            - argc gives the length of the argv list = number of arguments + 1 
            - Argv points to a list of strings, first containing the program name then all the args.
        - How do you pass functions as arguments to other functions―```c
void run_func(int x(int, int)) { 
	printf("%i", x(1, 2)); 
}
int compare(int a, int b) { return MAX(a, b); }

run_funct(&compare)
```
        - Describe the void* pointer―Allows pointing to any type of memory, but not legally functions. Big hole in the type system.
        - What are const and volatile variables?  ↓ 
            - const variables cannot be changed after definition 
            - volatile variables signal that the value could change through hardware - prevent unsafe compiler optimizations.
        - What is Duff's device? What's the point of it?―A method of copying from a memory buffer to an IO device, we iterate over the memory and store a certain number of bytes specified by count:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VqtmdKsQkC1KaufZPQKg_MC8keklC-xIxxV_fFtsoyr2xMotNzwbACWhV-S8GaFG-s_YNl9Lv2hnJjD2HL21UZTaJQW6fR2QkcOfQF2dvFz0BMDvpek6OICapoSx2M1n.png)
Duff's device is a method of loop unwinding, we perform multiple computations before we need to do a branch prediction / test if `--n>0. It falls through the do cases, to the correct case and then works downwards.` 
        - Describe ASan―ASan (address sanitizer) - the leading cause of errors in c is memory corruption. ASan aims to prevent array out of bounds selection, double frees, accessing freed memory, memory leaks and accessing local memory when it's gone.
Add's runtime overhead, so only use while developing. (~2x)
Doesn't catch all errors, i.e. uninitialized memory access.
Compile with -fsanitize=address
Need to recompile code with it.
        - What does MSan do?―Catches uninitialized memory accesses unlike ASan. 
Complie with  -fsanitize=memory
Very expensive! 2-3x slowdown.
Need to recompile code with it.
        - Describe UBSan―Catches undefined behaviour. E.g. division by zero, dereferencing null pointer, **unsigned **integer overflow.
Need to recompile code with it.
Modest overhead, but doesn't catch all bugs. **Seriously consider **using in production
        - Describe Valgrind―A binary that detects undefined behaviour. Adds substantial overhead.
        - Why do you need a visited tag to free a tree?  ↓ 
            - If you recursively free your children and then yourself - if both branches point to the same child a double free will occur.
            - Instead we need to mark and sweep, recursively walk over the tree and add any un"visited" nodes to a list. Then walk over the list and free all the values therein.
        - What is an arena?  ↓ 
            - Instead of recursively freeing tree data structures (or similar) initialize an arena of a certain size, and add each tree to a list within the arena 
            - When we want to free the memory, just free the arena list and then the arena itself.
            - Allows us to make arbitrary graphs without accidental multiple frees.
        - Describe reference counting and how it works―Each node stores the number of "references" to it. We only delete a node when it has no pointers to it (can't be accessed anymore). 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XtX80RyThPaoDIdusNCI6s0iQJpPuZeJLCvlaikx9PJIqqTke3l_e6GmF8NusuKS2rsAmb4yjj0lPXTPx6QYbNKXhYxGZKI1PudzHulTpkWDiSa0zSbU47e-SHv43DCv.png) 
In this graph, n2 needs to be deleted. So we decrement n from the left then the right. We then find n=0 so we recursively free n's children and then free(n).
        - How would you implement dec_ref() for reference counting?  ↓ 
            - ```c
void dec_ref(Node* node) {
	if (node != NULL) {
		node->rc--;
		if (node->rc <= 0) {
			dec_ref(node->left);
			dec_ref(node->right);
			free(node);
		}
	}
}
``` 
        - How do you help prevent errors with reference counting, and why do cycles pose an issue?  ↓ 
            - Careful getters and setters that do the work of increasing and decreasing reference count:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lG6PFf0W5W6M19NFc_FFSw5AmnmsfVY8-zIBveUfBdqbcDyM_cbh7rTkJ3JD3iTjGJE_jzqIae1DX5wnyEpm8NZHL_pEZxyTYmuZEyBKy4u0DhFYMHaFLVcZc1_kMzb0.png) 
            - Even if no other memory points to a cycle, they'll all still have non-zero reference and will stick around in memory:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IGawu447EgCLuDcXsAwMeEIhS8GLIi8hAeD5rMwCpMD4UXFt6nio7CgqTMMENCudH44UD5L-ObA-yzVaOC7qI07rv50AUn-VD0vHcRcyF_Us4BxQuV71T0RL-AQED9jX.png) 
Will both have an rc of 1 even though nothing points to them.
        - Describe mark and sweep for gc  ↓ 
            - We create an allocator with nodes and roots. We add nodes to the node linked list whenever we create them. Nodes are given a mark bit.
            - Mark stage: Then occasionally we iterate over the root nodes and find all the nodes reachable from the roots and **mark them**. 
            - Sweep stage: iterate over the node list and delete all unmarked nodes.
        - Describe what happens in a cache miss  ↓ 
            - The CPU looks up the value in memory, and stores it and the next 64 bytes it in a cache line. 
            - The (address, value) pairs are stored in the cache. Pointers are expensive **because **cache misses are expensive. 
        - What's the difference between intrusive and non-intrusive lists?―Intrusive lists store the data with the list node - rather than having a pointer to some data storage. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_R4lLTSnAORejlRt76NJcyfHa3RTD_2SIVqi1n4Y6tlVsINxUGj7WFSOd7qkpupnLtl_-a5CXclBPNg0x-8gxJuoKDEIeFgeDBOvKUP2EJ9eKOBIF-hBltahYnRKzBUC.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KJvq7K4WPNpTU3jCR_F8Qxldi9IDZHmW5KfOsVWd4SAcSjvnD05zvxwTfGIP4mDqJ3n62Oezc5ig_PEODRqls3vi1xhdpPDfAAWx-nuBY6obTmUIZ1pQTM1RxPURxqtt.png) 
        - Describe list of structs to array of structs―Following pointers on linked list is slow, but linked lists give us dynamic size adjustment. 
Convert your linked list to an array, better cache coherency as we can load lots of items into the cache at once. 
**Need to know size of array beforehand.** 
        - Describe Array of Structs to Struct of arrays  ↓ 
            - If we only want to iterate over one element in a struct, it can be slow to do so as we're loading garbage into the cache line. 
So create a data vector that stores lists of each element
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KrCJi3nhdGwkw37jM0wA40iLnDtmH5fEfPW48w5B2CYt2zD0RI-vi2tdUw4FXhk6syw-O-ysck1tF99Nx3L9ebJZ-CiqVIUkOt4GFt7MOO8CmJlxWV54lEGxz-bsIFW7.png) VS![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yTchK_wqPnhrWBJGhaXRg26lXr1-EjzCsKQOxn2sGfi1KnVr9TDlVM99cWCFJ1V8sZ5aRA5OLmRdCJCnj_TFMeGy3zKhHEjE0AQUU0JJ3_f9a9pYfTs-Ty5aoU7lcquy.png) 
        - Describe what's wrong with this code: ```c
float A[MAX, MAX], B[MAX, MAX]
for (i=0; i< MAX; i++) {
  for (j=0; j< MAX; j++) {
    A[i,j] = A[i,j] + B[j, i];
  }
}
```  ↓ 
            - We iterate over rows of A and columns of B. This is fine for A, as the rows are laid out contiguously:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AeFlGbVYSJM_qMocaYfEU-JPCoMtwn73Cb-0G1O_jhzdZxSp425Pf6arfpB1-giUBP6Jwsz2b_wBk58O64IZ-fo9gp706PF5nMLapdslKDjjWOri4ZMaBODpvFy6XwTu.png)
However, for B we're jumping columns - so by the time we can use the cache for the next item in a row of B, it will likely have been evicted by all the cache-line's generated by A. 
            - We can solve this by making it so a cache miss on one matrix lookup brings data that the other matrix can use.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/z_12bNa40dYDuyhchyDgjhLPt_439oCY9bG_zQDbDEFiITCZJoNVXavs8sBu-6vO17PaYMvycVF1F0bhD52jsPppYvnvLyOkzHp44UHvYbvNbWDH0t3kQ9t4-e_mP33Z.png)
```c
float A[MAX, MAX], B[MAX, MAX];
for (i=0; i< MAX; i+=block_size) {
  for (j=0; j< MAX; j+=block_size) {
    for (ii=i; ii<i+block_size; ii++) {
      for (jj=j; jj<j+block_size; jj++) {
        A[ii,jj] = A[ii,jj] + B[jj, ii];
      }
    }
  }
}

``` 
        - What are regression tests, and where do they fit in the debugging process?―First we note a bug in a unit test. From there we locate the offending code and correct and recompile it. Finally we run a regression test to ensure our update hasn't messed anything else up - e.g. checks if other unrelated unit tests now fail. 
        - How can you use the pre-processor to tidy up source code during debugging―```c
 #define DEBUG 0
 #define print_debug(A, B) {
 	if (DEBUG) {
 		printf(A);
 		printf(B);
 		fflush(stdout);
 	}
 }
 // So if we don't want to debug, all the print_debug calls get 
 // deleted in the object file
``` ```c
 
```
        - How can we find defects other than printing?―Use asserts - ```c
assert(hp != NULL)
```Makes the error message much nicer, and we can quickly find the source of the bug. 
        - What are interpretive debuggers and direct debuggers?  ↓ 
            - Interpretive debuggers execute code statement by statement and allow you to view memory throughout.
            - Direct debuggers require you to place a break point, and stop execution when you reach there and allow you to step forwards. Allows you to inspect program memory. 
        - How does the debugger know which memory is where?―The compiler emits a symbol table, which records the "name" of the variable/function in binary and the associated memory location. E.g. 0x100000f72 could be the printf function.
The debugger then emits more debugging data in the memory so we know which function is which.
This debugging information can also be used to match commands executed with the PC to know which line we're on.
        - 
        - 
    - **Assorted Flashcards for C++**
        - How do you define an enum variable in C++, and what to ways are there to change it's value later?  ↓ 
            - ```c
// Note no = after enum name in C OR C++
enum boolean {TRUE=1, FALSE=0};
enum boolean sam = FALSE;

sam = boolean(1);
sam = boolean(2300);
sam = TRUE;
``` 
        - What are references and what are they useful for?―References are like pointers, with an implicit * added for each use. They allow you to pass by reference, without allowing you to mess around with pointer arithmetic. 
Useful for functions, where you pass a reference to the value you want it to change.
        - Describe the use of const with references, and how it effects type conversion  ↓ 
            - const informs the compiler that the value shouldn't change, and will type check accordingly.
            - const variables also get type converted implicitely, e.g.: ```c
 void func1(const float& sam) {...}
 void func2(float& sam) {...}
 double pi = 3.1415912331324;
 func1(pi); // WORKS float -> double
 func2(pi); // FAILS
```
        - What happens if you overload a function in a different scope?  ↓ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6gCIFGOFBLZuWW1xxZOAviFB7fJ8jJlhAtbhVH3y0AAMCMQCBdcFMvL27dcP5KlpI8pw_Ci8zumxKlUVZrNHJAkE5ihIgzKm7ZCwKaIE__yWRVOFkLDMXIZrcw4_4C5K.png) 
        - Describe how namespaces are used, how do you retrieve specific items from them? Finally describe what you would place in the header file   ↓ 
            - Related data and functions can be grouped in a namespace: ```c
 namespace Stack {
 	int stack_size = 100;
 	int pop() {...}
 	void push() {...}
 	...
 }
```
            - We access items within, by either importing the whole namespace or using `::` to select items. ```c
 Stack::pop(); // 
 if (Stack::stack_size == 3) {...}
 
 using Stack::pop(); //imports Stack
 using namespace Stack; // imports everything
```
            - We stick definitions in the header: ```c
namespace Stack {
 	int stack_size;
 	int pop();
 	void push();
 	... // More definitions
}
``` 
        - What is a namespace?―A namespace is a way of logically collecting related pieces of code, it also allows for managing scope. E.g. values are scoped within their namespace.
You can define the same namespace multiple times.
        - What is the use of extern "C", why do we need it? ↓ 
            - extern "C" allows you to specify parts of the code which are written in C. e.g. ```c
 extern "C" {
 	#include <"some_c_library.h">
 }
```
            - This solves the name-munging issue, because C & C++ give different symbol names to functions. While the C compiler just generates _f for a function, C++ will generate `__Z1fv` to allow for things like multiple definitions of with different argument types - what C++ does for overloaded functions is called name munging.
        - If a library is written in C, how can you allow the library.h header function to be imported by both C & C++ code?  ↓ 
            - Use the #ifdef ```c
#ifdef __cplusplus
	extern "C" void some_func(int);
#else 
#	 include <stdbool.h>
	extern void some_func(int);
#endif
``` 
        - What's wrong with this code?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V9Jk74YQsYumjpJ8sTZAvr2yMZBex3zvVQfGNzIF9mN6gsSXu01i8OdH_paQDmh9A1MP1gvs_4tM9zS3b2agExHmoi3K0A3pX4TUV_FTVnhokXeCkkvyE1DX9Lkr1mtN.png)―We've written C code that takes a compare function for sorting. And we then pass it a **C++ **compare function - this won't work as the C++ compare has a different entry sequence than C. So likely will fail.  
        - What are static member of a class? How do you define them?―Don't vary **per class. NOT PER OBJECT!!!** 
They must be declared **in **the class and declared **outside **of the class: ```c
class Some_Class {
   public:
    static int sam;
    void output() { cout << sam; }
};
int Some_Class::sam = 3;
// Cant define them inside the class okay!
``` 
        - Are values of a certain class references to the class? And are member functions resolved statically or dynamically? ↓ 
            - No, they are the class themselves.
            - Member functions are resolved statically by default, but we can get Java-style resolution using `virtual.` 
        - How are structs copied/assigned?―Either bit copied, or the result is left unassigned.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VUaxQP6qlTiRTse41Vbl38zQDQlt-V4ccWVbpnyPW1AojQJeJMHv15r3ZAKqJmsPRTP5SYecu6ICvBajGXpLzvzAZ1Y5tplVV3DcXC-XRaORYv9cm5KKNvXn2GRM_KKL.png) 
        - How do you disable default constructors?―```c
 class some_class {
 	private: some_class() {}
 };
``` Make it private!
        - What does the default copy constructor do, when is it called and how do you override it?  ↓ 
            - By default, the copy constructor just copies all the fields
            - The copy constructor is called when you define an undefined object with another object: ```c
 MyClass x = ...;
 MyClass y = x;
```
            - Override the copy constructor for a class MyClass using: ```c
 MyClass::MyClass(const MyClass& x) {...}
```
        - What does the assignment constructor do by default, why might that not be desirable and how do we override it?  ↓ 
            - By default the assignment constructor overwrites all non-static members.
            - That might not be desirable, as we might want to clean up some state of the object (e.g. points to some large object in memory). 
            - Override using the following:```c
Complex& Complex::operator=(const Complex& c) {...}
``` 
        - What does declaring a member function constant do?―This means the member function cannot edit any of the contained state: ```c
 double Complex::real() const {
 	// cant modify the complex number in any way
 	return re;
 }
```
        - When can you create a class array like Complex[5], and how do you delete that array?―When the class has a default constructor.
You delete that array using ```c
 delete[] array; 
 // This runs the destructor on all the elements in the array
 // Then deletes the array.
```
        - How do you overload built in operators?―```c
 bool Complex::operator==(Complex b) {
 	return re==b.real() && im==b.imag();
 }
```
        - What are temporary objects?―A temporary object is an object without a name, i.e. an object not bound to anything. A temporary object cannot be bound to a non const reference.
Temporary objects can crop up when functions return objects, e.g.:```c
string a("A "), b("string");
const char *s1 = a.c_str();        // OK
const char *s2 = (a + b).c_str();  // Wrong
```
        - What are the two uses of Friend in classes?  ↓ 
            - Declare functions or operators as friends so that they can access your private fields and methods.```c
 class Matrix {
 	...
 	friend Vector operator*(const Matrix&, const Vector&);
 	...
 };

```
            - Declare other classes as friends ```c
 class X {
 	...
 	friend class Y;
 };
```
        - Would an object of type bicycle be able to access wheels?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dmYyblFLPyK-D8gbCvbbPK0E04_4DeRz7cnujKuyI-ovmphwzAkRzRhX-O1AcrWOLw3VqkyN3voae4ic_j1zz2EbYr04xjrBF_p8AwnBiAIuIP7ymHWZLCGGb6jFxQdh.png)―No bro. Wheels is private, we can't get at it. We could do the following though:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QUymn6Nps420kbCbB9gVng4k5kKnmkOLV-wusylbZT2oTfr1HJP44M--dBbHOxqnZ2snAxAicaND5a739uinm2_o-jLjyMeUUetjTf0RjyLzDSMM6NSfq8KBSca9Hvh1.png) 
And then we could access wheels using get_wheels().
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Uo7oYk2fU-eELpUrdTBUQxMmfuqnhJOWrhgcKfA7KnHlQrJbgh_9rp9bSTx5XBolfrjAD4EOITvDvX4shuWh0UZMkHPGxw5SuGe5d4pQ-nvwyqI93QBHVl_sUmS1rDkv.png)
What would this print, if both vehicles and bicycles have a maxSpeed function (bikes = 12, vehicles =60), **and why**  ↓ 
            - This would print 60 12. 
            - This is because C++ doesn't use java type vtable function selection by default - instead the function relies on the static type of the object. 
To get java-style, you have to declare a function virtual.
        - How are virtual functions made possible?―The compiler generates a vtable, this points to the correct function for every object instance.
These indirect function calls are slower than direct calls.
        - What do virtual functions allow for?―Non-virtual member functions are called depending on the static type of the variable, pointer or reference. Since a pointer to a derived class can be cast to a pointer to a base class, calls at base class do not see the overridden function. To get polymorphic behaviour, declare the function virtual in the superclass:  
        - What is an abstract class in C++, how do you define one?  ↓ 
            - An abstract class is a class with one or more abstract methods. They are needed because sometimes a base class simply isn't definable (how do you define an Animal?). When you inherit from an abstract class, you may implement one or more of the methods - only when you have **implemented ALL of the methods** can the class be instantiated into an object. 
            - ```c
class Shape {
	public:
		int virtual sides() = 0;
};
``` 
        - How do you deal with function name clash when a class inherits from multiple parent classes?―Specify exactly which class implementation you'd like to use E.g. For a class ShapeAnimal which inherits from Shape and Animal - and inherits size() ```c
 ShapeAnimal x;
 x.Shape::size();
```
        - Is this (Multiple instances of base class) legal? If so how do I access B's version of A? Finally, how could we change this so we had only one instance of the base class?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5D7MLqn2xRZGQtpGrduAOyeefEc5cRrI3w5KRtxPtVHCAUHCaxbp6-po7CYO2XYHF8lf3qjwGra0v8w-U7L7VbyukDyMEuAn_68VMjPEYpXO1_DjO6_vQe54vBfgCuY0.png)  ↓ 
            - This is legal! (EXCEPT VAR SHOULD BE PUBLIC TO USE) We store to versions of A, because B and C could change them in different ways
            - ```c
D d;
d.B::var;
d.C::var;
``` 
            - If we made A virtual. E.g. convert to: ```c
 class A {
   public:
    int var;
};
class B : public virtual A {};
class C : public virtual A {};
class D : public B, public C {};
```
        - How do casts play a similar role to constructors? How can enforce that casts from a Complex to a double must be explicit?  ↓ 
            - When casting from a type to a class, we have to construct a new object from the given type. E.g. ```c
double Y = 3.14;
Complex x = Complex(Y); //Normal
Complex x = Y; //Implicite cast
``` 
            - Overload double() in the class declaration: ```c
 class Complex {
 	...
 	explicit operator double() const () {
 		return real;
 	}
 
 };
```
        - What are the downsides of C++ casts, and what does C++ provide to combat this?  ↓ 
            - Hard to find and classify in a text editor AND they do no type checking.
            - C++ offers multiple different types of casts for different scenarios which are easier to search for and can provide type checking.
            - ```c
dynamic_cast<T>(e); // Does runtime type checking when casting pointers
static_cast<int>(3.14); // Normal C casting, quick
const_cast<int>(const_int); // Lets you remove const (or volatile) from a type, even though the type system says you can't
reinterpret_cast<some_struct>(some_other_struct); // Reinterprets a bit pattern as another type.
```
        - Why is casting to a supertype with C-style casts like this dangerous with multiple inheritance? ```c
static_cast<Class *>(pointer);
//equivalently:
(Class *)pointer;
```―Because under multiple inheritance, we might need to change the underlying data structure to cast it to a parent. In Java this would require no work, but as we could be storing multiple copies of a multipley inherited type - we might need to get rid of one. 
We would also need to check all the virtual function definitions are correct.
        - What is stack unwinding, and how does it relate to RAII? What happens to the call stack when an exception is thrown? ↓ 
            - When the stack is unwinding, stack allocated objects (that aren't const or volatile) that have been created within the try{} block have their destructors called. However, any heap allocated objects won't have their memory cleaned up. 
Thus, RAII wraps heap allocated objects in stack allocated ones - so when they go out of scope they are removed. The constructors of those heap allocated objects do the necessary allocation, and the destructors do the necessary freeing. Note that stack unwinding happens at the end of {} blocks as well.
            - The stack is unwound until we find a function which can handle the exception.
        - What can you throw as errors in C++?―You can throw any type, and then match the type in the catch block ```c
try {
    someClass c = someClass();
    throw(c);
} catch (SomeClass err) {
    cout << err;
}

//Or you can catch a double - any old shit works

try {
    double x = 3.14;
    throw(x);
} catch (double error) {
    cout << error;
}
```
        - How do you multiple exceptions, and finally catch any exceptions?  ↓ 
            - ```c
try {//something}
catch(Err1 e) {}
catch(Err2 e) {}
catch(...) {}

// The catch(...) catches all errors
``` 
        - If you're using class hierarchies to represent different types of errors, what do the functions associated with catching them need to be?―They need to be virtual, i.e. you need run time type information to know which type of function you should be running for the error. Because we'll catch the **parent class **and run a function that the child class augments.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QpV1OxWlPhhuA_jZCB9DeeDIPrhaO9wgwfDn7xgmWbUpWCLpxpgCqPtAENl3sryvXqeiBmQjy6X4LLUeNGt2LZA_KOOQXIjY5U_KDa-ElpbqUNw-MYAfAQkLOxja2MEX.png) 
        - Describe templates, how do you template a class or a function? How do they differ from Java Generics?  ↓ 
            - Templates allow you to do generic programming, where a set of functions and data structures can be repurposed to work on a variety of types. They allow you to specify type **and **value for a given type - e.g. we specify the type of the array AND it's max length below in SomeClass below. We can use the values to specify anything we like, as in SomeOtherClass
            - ```c
template<typename T> void sort(T arr[], int size) {
...}
template<typename T, int max> class SomeClass {
	public:
		T[max] arr;
};
template<class T, int max> class SomeOtherClass {
	public:
		T val;
		int array[max]; 
};


//Note that we can write class in the space of typename,
// makes no bloody difference mate!! haha!!
``` 
            - Java Generics require parameters to be Java reference types. In C++ parameters may be of other types, e.g. integers, compare: ```c
template<Class c, int n> struct Buffer { C[n] buf; int size; } 
class Buffer { public C[] buf; };
``` 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/v-2hvHxzmcwdzIQCZL1q9Ju2uFCIGAglL6aULboUOQtcXdBRFLgqYg2SSSv73hw57QC9t-W5pTWIuq8OhUKOe0_U02wbAgG-J1iK5jL-lut1XKgbUGuL05KDRBwig7O_.png) 
            - C++ also includes template specialisation, where we can write code which is used on a specific type - Java don't have this. E.g. We might want the code to work one way in general, but do something different when encountering int's: ```c
template <typename T>
void fun(T a) {
    cout << "The main template fun(): " << a << endl;
}

template <>
void fun(int a) {
    cout << "Specialized Template for int type: " << a << endl;
}

// This will behave differently for int's than any other types
```
            - In C++ we can specialize on int, doubles etc while in Java the special type cannot be a primitive type.
        - How do templates behave like macros?―At compile time, the T in the class or function get's replaced with the relevant type. This results in a larger binary, as the compiler needs to create a new definition for each instantiation.
        - How does a template function know what type it's using when it's called? How is this an improvement on void*? ↓ 
            - It infers it from the arguments, using ML style type inference.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sgw36WlbT8mwxVnm39zcv99MLFSDZaUF0w0-veKL6p-eykQuVRsCLULAm8ZJ46Ne9JScArshS5Qy9-WJZCgndItp7DxUWsCj0vvMei1O2e-ywo6Vg64w2CrGL-9PmzrZ.png) 
            - Better than void*: ↓ 
                - Allows for type inference 
                - Possibly faster code (no function pointers in vtables)
                - **However**, does result in larger binaries 
        - Give three examples of cases where a C program can vary in execution on different hardware. What is the benefit of this ↓ 
            - sizeof applied to 32 vs 64 bit pointers - both give 1
            - Stack direction - which can affect parameter evalutation
            - Big vs little endian
            - Primary advantages are efficiency arising from not having to respect uniformity and machine-specific low-level access.  
        - 
    - 
    - **Combined Flashcards**
        - What can the following code result in: 
        - ```php
#include 
#include 

int main(void) {
	printf("%d\n", (INT_MAX + 1) < 0);
	return 0;
}
```
        - ―Don't let them trick you! INT_MAX + 1 results in an overflow, which is undefined behaviour so **anything can happen.**
        - How do you use an enum?―
        - ```c
// First declare it
 enum boolean = {true=1, false=0};
 // Then create an enum variable that can range over those values
 enum boolean some_value;
 some_value = true;
```
        - What's the different between Declaring, defining and initiating a variable? ↓ 
            - Declaring―Telling the compiler this variable name will be used
            - Defining―Setting aside storage for a variable
            - Initiating―Putting a value in that variable
        - What does the extern keyword do?―It declares but doesn't define a variable, means the variable will be defined elsewhere - i.e. we allocate it no storage.
        - What does the **static keyword** do in regards to
            - **Static functions**―Usually functions are global, however static functions can **only be accessed within the file they're declared in**
            - **Static variables**―Static local variables **don't lose their contents when they go out of scope** - so functions can reuse their values when called a multiple time. Static global variables are only seen in the file they're defined in
        - How are variables passed to functions―Pass by value.
        - Object files consist of machine code and a list of what? ↓ 
            - Defined or exported symbols, representing global variables or function names.
            - Declared symbols, e.g. extern variables, or unimplemented functions. Declared but not defined.
        - What does a linker do, and how? ↓ 
            - A linker combines multiple object files into one executable
            - It does this by combining into a binary, and then adjusting absolute addresses. It also resolves all undefined symbols.
        - Why are headers needed and what are they useful for? ↓ 
            - Headers are needed because we want to be able to compile different files at different times and combine them later - but without a header we don't have **declarations **of those functions. So headers can  supply the declarations of functions and variables.
            - They can be used for pre-processor macros.
        - **Address space layout**
            - The **four most important areas of memory** within a **compiled x86 C** program―The **Stack**, the **heap**, the **static variables** and the **C binary code**.
            - Describe the **layout **of the **heap**, the static **variables**, the **stack **and the **C binary** code within the address space of a c**ompiled x86 C program**.―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9EqclGaeJ229axupOmXVqqvMy9SUdPUX7V3UUJKfqAvlQamJKCqsY20bbll3HJaaplmHBKojGNlm-veoZGeWqEKPswm8cEwA_HSec_wpoL4PW054VXI79WQoWA_A92Yu.png)  Start at 0xffff ffff the top of the address space The stack grows downwards The heap Grows upwards 0x0 is often mapped to an illegal address to cause a seg fault if accessed
            - Describe the **features **of the** heap **―** **The heap is **manually managed**, using malloc and free - it is **generally larger than the stack**.
            - Describe the **features** of the **stack **―The stack is **managed by the compiler** and holds temporary local** variables** **declared in the body of a function** which are freed when they go out of scope. It **grows downwards on the address space**. It grows and shrinks as function calls push and pop their values.
            - Describe the **features **of the **data segment **―The data segment holds **global and static variables** who have a value.
            - Describe the **features **of the **BSS **―The **BSS **stores **uninitialized **(don't have a value yet) local** **or global variables. Some or all of the bss is set to 0s - this is platform dependent.
        - **Unspecified behaviour is **―behaviour where the C standard give's 2 or more options of implementations - the implementation chose can be decided by the compiler. It gives more freedom to optimise code for a given architecture. Some examples are whether to implement inline, evaluation order of function arguments, order and contiguity of memory in the heap. Memory layout of storage of function arguments.
        - **Undefined behaviour is **―behaviour not described by the C standard, when a compiler is faced with such behaviour it can do **anything it likes**. An example is modifying a string literal (string literals are in read only memory) or i++ + ++i.
        - Functions and variables can be extern or static, what is the default - what does this mean in the global and static scope for both ↓ 
            - Functions and variables marked static can't be exported as symbols in the global scope and used in external files. The default is extern, e.g. other files can reference them.
            - Variables marked static keep their value in-between function calls.
        - Describe how the #include directive is used, and how it can be used to generate macros ↓ 
            - The include directive performs text replacement. E.g.
            - ```c
#define TEST 4.432131
// Note that no semicolon is needed
```
            - It can be used to create macros like this baby:
            - ```c
#define MAX(A,B) ((A) > (B) ? (A) : (B))
 // Need to be careful to put brackets around everying
 // Because any old shite can be replaced in there
```
            - Note that # before replacement text places it in double quotes, e.g:
            - ```c
#define STRINGIFY(A) #A
```
        - What is array[10] (selecting the 10th array value) equivalent to in pointer arithmetic?―
        - ```c
int array[] = {1,2,3,4,5,6,7,8,9,10,11,12}
*(array+10)
//  Note you can treat all pointers to array indexes like this E.G:
int* x = &array[1];
printf("%i", x[2]); // outputs 4
```
        - Describe argc and argv, what are they? ↓ 
            - argc gives the length of the argv list = number of arguments + 1
            - Argv points to a list of strings, first containing the program name then all the args.
        - How do you pass functions as arguments to other functions―
        - ```c
void run_func(int x(int, int)) { 
	printf("%i", x(1, 2)); 
}
int compare(int a, int b) { return MAX(a, b); }

run_funct(&compare)
```
        - Describe the void* pointer―Allows pointing to any type of memory, but not legally functions. Big hole in the type system.
        - What are const and volatile variables? ↓ 
            - const variables cannot be changed after definition
            - volatile variables signal that the value could change through hardware - prevent unsafe compiler optimizations.
        - What is Duff's device? What's the point of it?―A method of copying from a memory buffer to an IO device, we iterate over the memory and store a certain number of bytes specified by count: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VqtmdKsQkC1KaufZPQKg_MC8keklC-xIxxV_fFtsoyr2xMotNzwbACWhV-S8GaFG-s_YNl9Lv2hnJjD2HL21UZTaJQW6fR2QkcOfQF2dvFz0BMDvpek6OICapoSx2M1n.png) Duff's device is a method of loop unwinding, we perform multiple computations before we need to do a branch prediction / test if `--n>0. It falls through the do cases, to the correct case and then works downwards.`  
        - Describe ASan―ASan (address sanitizer) - the leading cause of errors in c is memory corruption. ASan aims to prevent array out of bounds selection, double frees, accessing freed memory, memory leaks and accessing local memory when it's gone. Add's runtime overhead, so only use while developing. (~2x) Doesn't catch all errors, i.e. uninitialized memory access. Compile with -fsanitize=address Need to recompile code with it.
        - What does MSan do?―Catches uninitialized memory accesses unlike ASan.  Complie with  -fsanitize=memory Very expensive! 2-3x slowdown. Need to recompile code with it.
        - Describe UBSan―Catches undefined behaviour. E.g. division by zero, dereferencing null pointer, **unsigned **integer overflow. Need to recompile code with it. Modest overhead, but doesn't catch all bugs. **Seriously consider **using in production
        - Describe Valgrind―A binary that detects undefined behaviour. Adds substantial overhead.
        - Why do you need a visited tag to free a tree? ↓ 
            - If you recursively free your children and then yourself - if both branches point to the same child a double free will occur.
            - Instead we need to mark and sweep, recursively walk over the tree and add any un"visited" nodes to a list. Then walk over the list and free all the values therein.
        - What is an arena? ↓ 
            - Instead of recursively freeing tree data structures (or similar) initialize an arena of a certain size, and add each tree to a list within the arena
            - When we want to free the memory, just free the arena list and then the arena itself.
            - Allows us to make arbitrary graphs without accidental multiple frees.
        - Describe reference counting and how it works―Each node stores the number of "references" to it. We only delete a node when it has no pointers to it (can't be accessed anymore).  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XtX80RyThPaoDIdusNCI6s0iQJpPuZeJLCvlaikx9PJIqqTke3l_e6GmF8NusuKS2rsAmb4yjj0lPXTPx6QYbNKXhYxGZKI1PudzHulTpkWDiSa0zSbU47e-SHv43DCv.png)  In this graph, n2 needs to be deleted. So we decrement n from the left then the right. We then find n=0 so we recursively free n's children and then free(n).
        - How would you implement dec_ref() for reference counting? ↓ 
            - ```c
void dec_ref(Node* node) {
	if (node != NULL) {
		node->rc--;
		if (node->rc <= 0) {
			dec_ref(node->left);
			dec_ref(node->right);
			free(node);
		}
	}
}
```
        - How do you help prevent errors with reference counting, and why do cycles pose an issue? ↓ 
            - Careful getters and setters that do the work of increasing and decreasing reference count: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lG6PFf0W5W6M19NFc_FFSw5AmnmsfVY8-zIBveUfBdqbcDyM_cbh7rTkJ3JD3iTjGJE_jzqIae1DX5wnyEpm8NZHL_pEZxyTYmuZEyBKy4u0DhFYMHaFLVcZc1_kMzb0.png)
            - Even if no other memory points to a cycle, they'll all still have non-zero reference and will stick around in memory: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IGawu447EgCLuDcXsAwMeEIhS8GLIi8hAeD5rMwCpMD4UXFt6nio7CgqTMMENCudH44UD5L-ObA-yzVaOC7qI07rv50AUn-VD0vHcRcyF_Us4BxQuV71T0RL-AQED9jX.png)  Will both have an rc of 1 even though nothing points to them.
        - Describe mark and sweep for gc ↓ 
            - We create an allocator with nodes and roots. We add nodes to the node linked list whenever we create them. Nodes are given a mark bit.
            - Mark stage: Then occasionally we iterate over the root nodes and find all the nodes reachable from the roots and **mark them**.
            - Sweep stage: iterate over the node list and delete all unmarked nodes.
        - Describe what happens in a cache miss ↓ 
            - The CPU looks up the value in memory, and stores it and the next 64 bytes it in a cache line.
            - The (address, value) pairs are stored in the cache. Pointers are expensive **because **cache misses are expensive.
        - What's the difference between intrusive and non-intrusive lists?―Intrusive lists store the data with the list node - rather than having a pointer to some data storage.  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_R4lLTSnAORejlRt76NJcyfHa3RTD_2SIVqi1n4Y6tlVsINxUGj7WFSOd7qkpupnLtl_-a5CXclBPNg0x-8gxJuoKDEIeFgeDBOvKUP2EJ9eKOBIF-hBltahYnRKzBUC.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KJvq7K4WPNpTU3jCR_F8Qxldi9IDZHmW5KfOsVWd4SAcSjvnD05zvxwTfGIP4mDqJ3n62Oezc5ig_PEODRqls3vi1xhdpPDfAAWx-nuBY6obTmUIZ1pQTM1RxPURxqtt.png)
        - Describe list of structs to array of structs―Following pointers on linked list is slow, but linked lists give us dynamic size adjustment.  Convert your linked list to an array, better cache coherency as we can load lots of items into the cache at once.  **Need to know size of array beforehand.**
        - Describe Array of Structs to Struct of arrays ↓ 
            - If we only want to iterate over one element in a struct, it can be slow to do so as we're loading garbage into the cache line.  So create a data vector that stores lists of each element
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KrCJi3nhdGwkw37jM0wA40iLnDtmH5fEfPW48w5B2CYt2zD0RI-vi2tdUw4FXhk6syw-O-ysck1tF99Nx3L9ebJZ-CiqVIUkOt4GFt7MOO8CmJlxWV54lEGxz-bsIFW7.png) VS![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yTchK_wqPnhrWBJGhaXRg26lXr1-EjzCsKQOxn2sGfi1KnVr9TDlVM99cWCFJ1V8sZ5aRA5OLmRdCJCnj_TFMeGy3zKhHEjE0AQUU0JJ3_f9a9pYfTs-Ty5aoU7lcquy.png)  
        - Describe what's wrong with this code:
        - ```c
float A[MAX, MAX], B[MAX, MAX]
for (i=0; i< MAX; i++) {
  for (j=0; j< MAX; j++) {
    A[i,j] = A[i,j] + B[j, i];
  }
}
```
        -  ↓ 
            - We iterate over rows of A and columns of B. This is fine for A, as the rows are laid out contiguously: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AeFlGbVYSJM_qMocaYfEU-JPCoMtwn73Cb-0G1O_jhzdZxSp425Pf6arfpB1-giUBP6Jwsz2b_wBk58O64IZ-fo9gp706PF5nMLapdslKDjjWOri4ZMaBODpvFy6XwTu.png) However, for B we're jumping columns - so by the time we can use the cache for the next item in a row of B, it will likely have been evicted by all the cache-line's generated by A.
            - We can solve this by making it so a cache miss on one matrix lookup brings data that the other matrix can use. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/z_12bNa40dYDuyhchyDgjhLPt_439oCY9bG_zQDbDEFiITCZJoNVXavs8sBu-6vO17PaYMvycVF1F0bhD52jsPppYvnvLyOkzHp44UHvYbvNbWDH0t3kQ9t4-e_mP33Z.png)
            - ```c
float A[MAX, MAX], B[MAX, MAX];
for (i=0; i< MAX; i+=block_size) {
  for (j=0; j< MAX; j+=block_size) {
    for (ii=i; ii
```
            - ` `
        - `What are regression tests, and where do they fit in the debugging process?→First we note a bug in a unit test. From there we locate the offending code and correct and recompile it. Finally we run a regression test to ensure our update hasn't messed anything else up - e.g. checks if other unrelated unit tests now fail. `
        - `How can you use the pre-processor to tidy up source code during debugging→`
        - ```c
#define DEBUG 0
 #define print_debug(A, B) {
 	if (DEBUG) {
 		printf(A);
 		printf(B);
 		fflush(stdout);
 	}
 }
 // So if we don't want to debug, all the print_debug calls get 
 // deleted in the object file
```
        - 
        - `How can we find defects other than printing?→Use asserts - `
        - ```c
assert(hp != NULL)
```
        - Makes the error message much nicer, and we can quickly find the source of the bug.
        - `What are interpretive debuggers and direct debuggers? `
        - `How does the debugger know which memory is where?→The compiler emits a symbol table, which records the "name" of the variable/function in binary and the associated memory location. E.g. 0x100000f72 could be the printf function. The debugger then emits more debugging data in the memory so we know which function is which. This debugging information can also be used to match commands executed with the PC to know which line we're on.`
        - `  `
        - How do you define an enum variable in C++, and what to ways are there to change it's value later?  ↓ 
            - ```c
// Note no = after enum name in C OR C++
enum boolean {TRUE=1, FALSE=0};
enum boolean sam = FALSE;

sam = boolean(1);
sam = boolean(2300);
sam = TRUE;
```
        - What are references and what are they useful for?―References are like pointers, with an implicit * added for each use. They allow you to pass by reference, without allowing you to mess around with pointer arithmetic.  Useful for functions, where you pass a reference to the value you want it to change.
        - Describe the use of const with references, and how it effects type conversion ↓ 
            - const informs the compiler that the value shouldn't change, and will type check accordingly.
            - const variables also get type converted implicitely, e.g.:
            - ```c
void func1(const float& sam) {...}
 void func2(float& sam) {...}
 double pi = 3.1415912331324;
 func1(pi); // WORKS float -> double
 func2(pi); // FAILS
```
        - What happens if you overload a function in a different scope? ↓ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6gCIFGOFBLZuWW1xxZOAviFB7fJ8jJlhAtbhVH3y0AAMCMQCBdcFMvL27dcP5KlpI8pw_Ci8zumxKlUVZrNHJAkE5ihIgzKm7ZCwKaIE__yWRVOFkLDMXIZrcw4_4C5K.png)  
        - Describe how namespaces are used, how do you retrieve specific items from them? Finally describe what you would place in the header file ↓ 
            - Related data and functions can be grouped in a namespace:
            - ```c
namespace Stack {
 	int stack_size = 100;
 	int pop() {...}
 	void push() {...}
 	...
 }
```
            - We access items within, by either importing the whole namespace or using `::` to select items.
            - ```c
Stack::pop(); // 
 if (Stack::stack_size == 3) {...}
 
 using Stack::pop(); //imports Stack
 using namespace Stack; // imports everything
```
            - We stick definitions in the header:
            - ```c
namespace Stack {
 	int stack_size;
 	int pop();
 	void push();
 	... // More definitions
}
```
        - What is a namespace?―A namespace is a way of logically collecting related pieces of code, it also allows for managing scope. E.g. values are scoped within their namespace. You can define the same namespace multiple times.
        - What is the use of extern "C", why do we need it? ↓ 
            - extern "C" allows you to specify parts of the code which are written in C. e.g.
            - ```c
extern "C" {
 	#include <"some_c_library.h">
 }
```
            - This solves the name-munging issue, because C & C++ give different symbol names to functions. While the C compiler just generates _f for a function, C++ will generate `__Z1fv` to allow for things like multiple definitions of with different argument types - what C++ does for overloaded functions is called name munging.
        - If a library is written in C, how can you allow the library.h header function to be imported by both C & C++ code? ↓ 
            - Use the #ifdef
            - ```c
#ifdef __cplusplus
	extern "C" void some_func(int);
#else 
#	 include 
	extern void some_func(int);
#endif
```
        - What's wrong with this code?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V9Jk74YQsYumjpJ8sTZAvr2yMZBex3zvVQfGNzIF9mN6gsSXu01i8OdH_paQDmh9A1MP1gvs_4tM9zS3b2agExHmoi3K0A3pX4TUV_FTVnhokXeCkkvyE1DX9Lkr1mtN.png)―We've written C code that takes a compare function for sorting. And we then pass it a **C++ **compare function - this won't work as the C++ compare has a different entry sequence than C. So likely will fail.
        - What are static member of a class? How do you define them?―Don't vary **per class. NOT PER OBJECT!!!**  They must be declared **in **the class and declared **outside **of the class:
        - ```c
class Some_Class {
   public:
    static int sam;
    void output() { cout << sam; }
};
int Some_Class::sam = 3;
// Cant define them inside the class okay!
```
        - Are values of a certain class references to the class? And are member functions resolved statically or dynamically? ↓ 
            - No, they are the class themselves.
            - Member functions are resolved statically by default, but we can get Java-style resolution using `virtual.`
        - How are structs copied/assigned?―Either bit copied, or the result is left unassigned.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VUaxQP6qlTiRTse41Vbl38zQDQlt-V4ccWVbpnyPW1AojQJeJMHv15r3ZAKqJmsPRTP5SYecu6ICvBajGXpLzvzAZ1Y5tplVV3DcXC-XRaORYv9cm5KKNvXn2GRM_KKL.png)  
        - How do you disable default constructors?―
        - ```c
class some_class {
 	private: some_class() {}
 };
```
        - Make it private!
        - What does the default copy constructor do, when is it called and how do you override it? ↓ 
            - By default, the copy constructor just copies all the fields
            - The copy constructor is called when you define an undefined object with another object:
            - ```c
MyClass x = ...;
 MyClass y = x;
```
            - Override the copy constructor for a class MyClass using:
            - ```c
MyClass::MyClass(const MyClass& x) {...}
```
        - What does the assignment constructor do by default, why might that not be desirable and how do we override it? ↓ 
            - By default the assignment constructor overwrites all non-static members.
            - That might not be desirable, as we might want to clean up some state of the object (e.g. points to some large object in memory).
            - Override using the following:
            - ```c
Complex& Complex::operator=(const Complex& c) {...}
```
        - What does declaring a member function constant do?―This means the member function cannot edit any of the contained state:
        - ```c
double Complex::real() const {
 	// cant modify the complex number in any way
 	return re;
 }
```
        - When can you create a class array like Complex[5], and how do you delete that array?―When the class has a default constructor. You delete that array using
        - ```c
delete[] array; 
 // This runs the destructor on all the elements in the array
 // Then deletes the array.
```
        - How do you overload built in operators?―
        - ```c
bool Complex::operator==(Complex b) {
 	return re==b.real() && im==b.imag();
 }
```
        - What are temporary objects?―A temporary object is an object without a name, i.e. an object not bound to anything. A temporary object cannot be bound to a non const reference. Temporary objects can crop up when functions return objects, e.g.:
        - ```c
string a("A "), b("string");
const char *s1 = a.c_str();        // OK
const char *s2 = (a + b).c_str();  // Wrong
```
        - What are the two uses of Friend in classes? ↓ 
            - Declare functions or operators as friends so that they can access your private fields and methods.
            - ```c
class Matrix {
 	...
 	friend Vector operator*(const Matrix&, const Vector&);
 	...
 };
```
            - Declare other classes as friends
            - ```c
class X {
 	...
 	friend class Y;
 };
```
        - Would an object of type bicycle be able to access wheels? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dmYyblFLPyK-D8gbCvbbPK0E04_4DeRz7cnujKuyI-ovmphwzAkRzRhX-O1AcrWOLw3VqkyN3voae4ic_j1zz2EbYr04xjrBF_p8AwnBiAIuIP7ymHWZLCGGb6jFxQdh.png)―No bro. Wheels is private, we can't get at it. We could do the following though: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QUymn6Nps420kbCbB9gVng4k5kKnmkOLV-wusylbZT2oTfr1HJP44M--dBbHOxqnZ2snAxAicaND5a739uinm2_o-jLjyMeUUetjTf0RjyLzDSMM6NSfq8KBSca9Hvh1.png)  And then we could access wheels using get_wheels().
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Uo7oYk2fU-eELpUrdTBUQxMmfuqnhJOWrhgcKfA7KnHlQrJbgh_9rp9bSTx5XBolfrjAD4EOITvDvX4shuWh0UZMkHPGxw5SuGe5d4pQ-nvwyqI93QBHVl_sUmS1rDkv.png) What would this print, if both vehicles and bicycles have a maxSpeed function (bikes = 12, vehicles =60), **and why** ↓ 
            - This would print 60 12.
            - This is because C++ doesn't use java type vtable function selection by default - instead the function relies on the static type of the object.  To get java-style, you have to declare a function virtual.
        - How are virtual functions made possible?―The compiler generates a vtable, this points to the correct function for every object instance. These indirect function calls are slower than direct calls.
        - What do virtual functions allow for?―Non-virtual member functions are called depending on the static type of the variable, pointer or reference. Since a pointer to a derived class can be cast to a pointer to a base class, calls at base class do not see the overridden function. To get polymorphic behaviour, declare the function virtual in the superclass:
        - What is an abstract class in C++, how do you define one? ↓ 
            - An abstract class is a class with one or more abstract methods. They are needed because sometimes a base class simply isn't definable (how do you define an Animal?). When you inherit from an abstract class, you may implement one or more of the methods - only when you have **implemented ALL of the methods** can the class be instantiated into an object.
            - ```c
class Shape {
	public:
		int virtual sides() = 0;
};
```
        - How do you deal with function name clash when a class inherits from multiple parent classes?―Specify exactly which class implementation you'd like to use E.g. For a class ShapeAnimal which inherits from Shape and Animal - and inherits size()
        - ```c
ShapeAnimal x;
 x.Shape::size();
```
        - Is this (Multiple instances of base class) legal? If so how do I access B's version of A? Finally, how could we change this so we had only one instance of the base class? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5D7MLqn2xRZGQtpGrduAOyeefEc5cRrI3w5KRtxPtVHCAUHCaxbp6-po7CYO2XYHF8lf3qjwGra0v8w-U7L7VbyukDyMEuAn_68VMjPEYpXO1_DjO6_vQe54vBfgCuY0.png) ↓ 
            - This is legal! (EXCEPT VAR SHOULD BE PUBLIC TO USE) We store to versions of A, because B and C could change them in different ways
            - ```c
D d;
d.B::var;
d.C::var;
```
            - If we made A virtual. E.g. convert to:
            - ```c
class A {
   public:
    int var;
};
class B : public virtual A {};
class C : public virtual A {};
class D : public B, public C {};
```
        - How do casts play a similar role to constructors? How can enforce that casts from a Complex to a double must be explicit? ↓ 
            - When casting from a type to a class, we have to construct a new object from the given type. E.g.
            - ```c
double Y = 3.14;
Complex x = Complex(Y); //Normal
Complex x = Y; //Implicite cast
```
            - Overload double() in the class declaration:
            - ```c
class Complex {
 	...
 	explicit operator double() const () {
 		return real;
 	}
 
 };
```
        - What are the downsides of C++ casts, and what does C++ provide to combat this? ↓ 
            - Hard to find and classify in a text editor AND they do no type checking.
            - C++ offers multiple different types of casts for different scenarios which are easier to search for and can provide type checking.
            - ```c
dynamic_cast(e); // Does runtime type checking when casting pointers
static_cast(3.14); // Normal C casting, quick
const_cast(const_int); // Lets you remove const (or volatile) from a type, even though the type system says you can't
reinterpret_cast(some_other_struct); // Reinterprets a bit pattern as another type.
```
        - Why is casting to a supertype with C-style casts like this dangerous with multiple inheritance?
        - ```c
static_cast(pointer);
//equivalently:
(Class *)pointer;
```
        - ―Because under multiple inheritance, we might need to change the underlying data structure to cast it to a parent. In Java this would require no work, but as we could be storing multiple copies of a multipley inherited type - we might need to get rid of one.  We would also need to check all the virtual function definitions are correct.
        - What is stack unwinding, and how does it relate to RAII? What happens to the call stack when an exception is thrown? ↓ 
            - When the stack is unwinding, stack allocated objects (that aren't const or volatile) that have been created within the try{} block have their destructors called. However, any heap allocated objects won't have their memory cleaned up.  Thus, RAII wraps heap allocated objects in stack allocated ones - so when they go out of scope they are removed. The constructors of those heap allocated objects do the necessary allocation, and the destructors do the necessary freeing. Note that stack unwinding happens at the end of {} blocks as well.
            - The stack is unwound until we find a function which can handle the exception.
        - What can you throw as errors in C++?―You can throw any type, and then match the type in the catch block
        - ```c
try {
    someClass c = someClass();
    throw(c);
} catch (SomeClass err) {
    cout << err;
}

//Or you can catch a double - any old shit works

try {
    double x = 3.14;
    throw(x);
} catch (double error) {
    cout << error;
}
```
        - How do you multiple exceptions, and finally catch any exceptions? ↓ 
            - ```c
try {//something}
catch(Err1 e) {}
catch(Err2 e) {}
catch(...) {}

// The catch(...) catches all errors
```
        - If you're using class hierarchies to represent different types of errors, what do the functions associated with catching them need to be?―They need to be virtual, i.e. you need run time type information to know which type of function you should be running for the error. Because we'll catch the **parent class **and run a function that the child class augments. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QpV1OxWlPhhuA_jZCB9DeeDIPrhaO9wgwfDn7xgmWbUpWCLpxpgCqPtAENl3sryvXqeiBmQjy6X4LLUeNGt2LZA_KOOQXIjY5U_KDa-ElpbqUNw-MYAfAQkLOxja2MEX.png)  
        - Describe templates, how do you template a class or a function? How do they differ from Java Generics? ↓ 
            - Templates allow you to do generic programming, where a set of functions and data structures can be repurposed to work on a variety of types. They allow you to specify type **and **value for a given type - e.g. we specify the type of the array AND it's max length below in SomeClass below. We can use the values to specify anything we like, as in SomeOtherClass
            - ```c
template void sort(T arr[], int size) {
...}
template class SomeClass {
	public:
		T[max] arr;
};
template class SomeOtherClass {
	public:
		T val;
		int array[max]; 
};


//Note that we can write class in the space of typename,
// makes no bloody difference mate!! haha!!
```
            - Java Generics require parameters to be Java reference types. In C++ parameters may be of other types, e.g. integers, compare:
            - ```c
template struct Buffer { C[n] buf; int size; } 
class Buffer { public C[] buf; };
```
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/v-2hvHxzmcwdzIQCZL1q9Ju2uFCIGAglL6aULboUOQtcXdBRFLgqYg2SSSv73hw57QC9t-W5pTWIuq8OhUKOe0_U02wbAgG-J1iK5jL-lut1XKgbUGuL05KDRBwig7O_.png)  
            - C++ also includes template specialisation, where we can write code which is used on a specific type - Java don't have this. E.g. We might want the code to work one way in general, but do something different when encountering int's:
            - ```c
template 
void fun(T a) {
    cout << "The main template fun(): " << a << endl;
}

template <>
void fun(int a) {
    cout << "Specialized Template for int type: " << a << endl;
}

// This will behave differently for int's than any other types
```
            - In C++ we can specialize on int, doubles etc while in Java the special type cannot be a primitive type.
        - How do templates behave like macros?―At compile time, the T in the class or function get's replaced with the relevant type. This results in a larger binary, as the compiler needs to create a new definition for each instantiation.
        - How does a template function know what type it's using when it's called? How is this an improvement on void*? ↓ 
            - It infers it from the arguments, using ML style type inference. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sgw36WlbT8mwxVnm39zcv99MLFSDZaUF0w0-veKL6p-eykQuVRsCLULAm8ZJ46Ne9JScArshS5Qy9-WJZCgndItp7DxUWsCj0vvMei1O2e-ywo6Vg64w2CrGL-9PmzrZ.png)  
            - Better than void*: ↓ 
                - Allows for type inference
                - Possibly faster code (no function pointers in vtables)
                - **However**, does result in larger binaries
        - Give three examples of cases where a C program can vary in execution on different hardware. What is the benefit of this ↓ 
            - sizeof applied to 32 vs 64 bit pointers - both give 1
            - Stack direction - which can affect parameter evalutation
            - Big vs little endian
            - Primary advantages are efficiency arising from not having to respect uniformity and machine-specific low-level access.
    - 
    - 
- Further Graphics
    - Supervision 2
        - 
        - 13. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/17Edkai7g7Fd5qebWHcQ8u-c8mqJ2t8Fs2Ps0S0XNiNz-twUM2aCW9oIReBYPPF2Cto8FtoPALxoC4LxgpSmCdjF9_jYSw8tvh9oxWqE9eDXMeb-25IcpWVuPCf42kkW.png) 
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Mq6Ih2CBkUzLCkQyVPcARUSPbWA6pB8Tx2ap3czxbNB39-2BElzVEn-sQqUY2Abm2zJV7mPGLGoUryKQhjmg7CdBsroRlPL1VLb3dvK0cJ0XTQPVHHQzjVrJs84SUWmx.png) 
            - We can separate them into three dual quaternions, one rotation about the z axis, on translation along the x axis with zero rotation and finally a translation along the y axis with zero rotation. Finally, if we multiply the three quaternions the resulting quaternion will represent our translation.
        - 
        1. ) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/w07UOHSZFJMNCuTGrCebgQaTJV7bJwcW8lc7f3lkThFZ9tvE24CUQy14UjfmU-vqgixnNwzUYgd2Rk0h58wPwTalUJxfvxAYa-hLaoGcvdfSxOvGQumLsnyiGlJaLG2H.png) 
            - Caustics - The interaction of light & curved surfaces or glass - e.g. the refraction of light. 
            - Subsurface scattering - Light entering and being scattered by a translucent material, e.g. skin.
            - Soft shadows - point lights cannot create soft shadows, as the incident intensity is the same everywhere (varying only with distance & angle) - there are not points in which light from multiple  points on a light source combine and a gradient of luminance is formed. 
            - >1 bounce lighting - light that arrives after performing 2 or more bounces is not accounted for. 
        2. In areas of low curvature, less sampling needs to be done as the effect of reflections and bouncing will be less pronounced. In areas of high curvature we should have more samples, as there is likely to be more occlusion of objects and more light bouncing effects.  
        3. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/13sI92Gd6ULRrF3ccPF88UmC8s1hGEqwULrVuPoak71HfJUjMn6D7XHAlHHjXgdk90XoI3P1xnGUd_2N5jAE4Qz3klTtLoto7vfoBu1AmZQgqY7GT9wmxvjcHZjkdki5.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OezAp8d-MEVVCvNOfirN596uGuWLFVCq-Qg469KNo8-qjZs-dQBnLijynE-hDCBtH4-veMjI8wafwqHl1ulMM-65UFO81bz-DlRNfgguqThRLWfV3Lr4-kethFFQ5BPk.png) 
        4. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wLzNg5gjNt3K68OaClfqbigNmPNV1-RdDY6KrQ0XOSSVr9m1HtRmrghguA5E7wOKx0SqNXOkot5n8MkJCmMEbVvta_N6SoFV-nYRTXAFJ-djLIY9CqYjYROLcXJlLSc6.png) 
            - c.) b shows that using importance sampling, we can still get a high quality approximation while sampling a smaller area - in reality we use monte carlo integration rather than analytical integration. 
            - d.) Using cosine we sample more light values at a greater angle to the surface, giving perpendicular light a higher weight. We assume that light is coming from all angles for this to work, however if light is coming from a more acute angle - less of it will be sampled resulting in a lower quality image.
        - 
    - Supervision 1
        1. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gTK4JW5ryukfyXXqdHoX4VyrjOWKeMBIZR0MErPyy_mHWLsDjfYI4zrgxLoRfwEXncPqwwfL72zuQswpGmhrs_N-qTprQFaoxHUWpdUPJ19TiARF_nwV6yK5JSa4Afkv.png) 
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
        2. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7GDDM58Km_D6S_B7eTNJRuJuvQZ2lcJOW9WMCy-vyKsvkWTCPlVnMA6ULHFbsRn96NOYlogLBgaD02NrPdWYGVujgdOh2Tqld1J27kRYT0EL28IH24B7GaUblTqK91q-.png) 
            - $x^2+y^2=e^{2t}$
            - $R = e^t$
            - This describes a spiral centred at (0,0) where the distance from the origin is $e^t$
            - 
        3. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZmkyinQzH326IJwFAzKQAtsa4DjUaZkSKgdGN2ILCYoWxNMSz5LfKPKDRhxI_gCOzrpjNX9XzgBFrSJiE0U-q9q4g_AeCGpt8esliS1FG8NREOTPRZmrnrXCzhnFudMq.png) 
            - a.) First you must compute $S_u = \frac {\partial (s(u,v))}{\partial u}$ and $S_v = \frac {\partial (s(u,v))}{\partial v}$ , one can then compute the normal via $\frac{S_u \times S_v}{||S_u \times S_v||}$.
            - b.) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jWzZl4lN7321QOkwuLl-rQjLyrCTQHHloFpCA7i31xJ_aiViYTlSBWgQyh430XaZCzVQv66zT4atPR-jzFKdo7K03icYTVX3q89WQ2nMKXqS7V0XdJ91BT71WGRyLY7v.png)![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VRgybaadKrIWnFcRLL4KuG_nZMVq3eWkG6IL2aQutOuyYrgkyEvqiFJU3oT9xTxH0x2R38Xxel-F-ld7kyFgLW0TZZU2xa_AmUc8RwNGFJxE3sQEZETk4hW9PkO_sv3H.png) 
        4. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8UIPYfQEqMSbTmQI5-FBIbJ3mtNHi6yluVkNxBaGrWKOV4ToxB-e_ludB-kOIn7TCdZatDLxcfuDn0nKUG8cba9JGVYW53vTW4zqYDOWv0gesXcwuPRq0u60MoGIUHuf.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4sG-KtYTLnDXew39MLnWTljXM61KRrHhOyT_C5lSh3n9Md2ceefb3bBHHYowjiMzHZBdc5k3UTxMvcUreaIc7IonOk7PBVFy3yzNxMWlExbjp4LdhqwUbhPb4S7n5a8i.png) 
            - 
        5. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XOvvZeCJvrhpTcf7nXIMF8k55A6mrKyG3U296WFcv6gSIkPOHkH2Rc602pUZH_Whj4Lj79-n9FjqHOAxdkqtHkHJVl9ZxW8L5qDGP6d1HBFnar1KZ11BscqFF1tl2WdS.png) 
            - This implicit function will comprise all (x,y) coordinates where either x, y or both x&y are zero, meaning the function will be a plus sign on the xy plane. The result will be at (0,0) there are infinite possible surface normals, while at every other point there are two equally plausible surface norms.
        6. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_Avg0u7PgJxITQwfaoK-ZxNT52GGyof6YJk5QVE2BQfM5c-Yblz20LZ2GAdY4Ataq4mGQTFU-a_MaFFfvf9iVgHvOmqToxKhKC7QR_ayMi_JHBQoteu2v9_IpU64ziYx.png) 
            - Triangle meshes store two separate lists, a list of vertices (containing the x, y and z of each vertex) and a list of faces containing **indices** of sets of three vertices. E.g:
            - v = [(2,1,4), (2,4,6), (1,4,6), (2,4,5)]
            - f = [0, 1, 2, 0, 1, 3]
            - From these lists surface normals and other factors are calculated later.
            - b.) The geometry would be the list of vertices, while the topology is the faces - while the topology deals with the more abstract concept of the connections between vertices, the geometry is the actual coordinates in $R^3$.
        7. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5b-NrE_NjGIA3t1Pie8OKt4e2vKrQb0aGEiVYC18feWaJh1s4lBqocECCpVNjNl_kwKR7TgVZvI4ohGBSyx6JDtNIiWWCQAL3keyYAyPjwOiSm0iBdf--8-p2QTxT7wV.png) 
            - For normal triangular meshes this is vital for a number of reasons ↓ 
                1. The order of the neighbouring vertices decides the direction of the surface normal, without that ordering the resulting vertex can be facing the wrong way.
                2. The choice of neighbouring vertices decides the size and direction of each face.
                3. The neighbouring vertices of a given vertex cannot simply be calculated by finding the 2 closest vertices, using this method can result in areas of the mesh being devoid of triangles (a see through part of the mesh) or alternatively an area where triangles overlap. 
            - Point set surfaces instead do away with triangular meshes and use dishes oriented in the direction of the normal. With a large enough number of dishes, we can cover the whole surface and remove the need for storing neighbouring vertices.#
        8. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-VeCFokgTj5THyvZ9IIAPBfs_rDbc2vueDR3P-iZKsbBo85CCQRpSbltC7kceuyif3ffjF3SdUKohuqzmg2NaaFNWw6MMhX426EWBs3ckHEEeNzNbU5r5Wk_zIcKXFe7.png)  
            - A manifold is a topological space that is locally Euclidean, that is for every point there's a neighbourhood around that point that is topologically the same as a closed ball in $R^n$. This differs from a manifold with boundaries, where every point is either topologically the same as the closed ball or a half ball in $R^n$.
        9. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PEM-naJb74Gs19Jh3tbbGf2pnLbzQiIt9rIYBLAV4Bm8XlmA5QrjfRs-XJIO8331tIU_0KcwatDz0JKNb5bsf_SFNwup9jx5DvQMkV1MxrUlo281wdNat3crFfkZt3pL.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nbpdkz3g0QTGfwXYz_2uyTwCzjPTci0hfo3j38PyEvqyPA088yUhPZ5S8DYrtRSILq_vxGpcjNg3QkMwnv9-36llrfMzauxSAe6suBcpPtRlTBnX8wVFVC2XpyvvoG00.png)![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/owCO8hXdTgMd1Uu6nRgpsMYjlfdPbQauA2SNjhsFi1qT1KChWZiOPWQ2wc5lGVQVMQfdRKSeiCi2lVIamb2ajAhP8GWy0CXh2qxqp4VqS5VpasWB9bJvmHrx62VmNRU4.png)![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HWlUsLlt6unQe7NVpUwo4q0Gc5-_adujByQFIgxpjRBtUIkqtYtoSZD4PsLTo83IXYPrZJz6VV1TXFel9HN352HXyVBeMcMXFmX7ZLz2DNAjQHozIymb-KxK7D4UyiOL.png) 
            - 
        10. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uIcH7WGA54QIVhJ0azN-JgKybCDazS3nb53Q8fSnOopK2AxZLIDjzNsZ8VpCt9qxZ7HhT50ZzvhMiKJ2Q7rWt_E34F9u_1Rrt8J9_pg8SHGHp-QrlBvN1sC46gpxcP5G.png)![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_MYCKA-U6uo18yOOH0vg0MJCh-VbzUD6JEaBhkdeMkUAuIFH7rWS059UxTsrSIjNBY3opRO67MSX7fzCVwzptVrt_8P5eDMYc_Bqa4NNvjThGIKDg6RhF692uBzCV3iV.png) 
        11. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XXtkOh1iTv2VMWTab58JYFEVXFb0HN5cExyDfPZfweVMW7f-nE2JzM6UBNkxSJXBkftd9ZKZl27snfG1dDvMMdfygheG4SRalotI6yU5B46hgRzMJAUQGI6Geyy3yzsi.png) 
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jij8LnlRdQqRvRBAWGGdAQMBmBAFtnPIX84u1QnPQlrCKIOQJnD1KbTRNX_glroP69oKsNKhXOxi2qyMepdHfb5THuZ-07L1y9AX7YuqIzediVK3zAVFe-NmwQ3Zo6m9.png) 
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
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/f2zAZKGcOtm5cobCTsjFhv6Fdm2jafuCJtEazRN8u1fwJ-e9yv5kPMD2VnxBSWfibY_v5A0z5U25qKn968rSEQSoLLgcS-WlC503hNYuG9Jh5b6R0Bw6lWPaEtU2jpaU.png) 
                - 
            - **Bezier Curve**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/G_qXB6PERNCbBzvO_5ofEPkcZqZFNcDgss5N4PEJVEToDvw1xg3rlBXbOhEpkB5WGi2vVuIbiEib8fR3WkzywVfW-yDihEDZLk6dR69RHs9kkcb7UV_a6svTZ0dsUKFV.png) 
                - $s(t) = \sum_{i=0}^{n}{P_i B_n^i(t)}$ 
                - $B_n^i(t)={n \choose i}t^i(1-t)^{n-1}$ 
                - Allows for moving smoothly from point to point
            - **Bezier Surface**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZE9Z9UBBbLbpiGj7UYd_gZSWf4HHEub6Iy-TWItU3QlrIOG8lGMYJ88XNuqV1tkLO5g7oZjcl2yQ3-PG_SQIaGAeSRLNXd9Dm_mUloD7Yyxb2l5pPC57N7sGLddAKmaz.png) 
                - $$s(u,v)=\sum^m_{i=0} {\sum^n_{j=0}} 
 \space P_{i,j} \space B^i_m(u) 
\space B^j_n(v)$$
                - Where B is shown above and P is the height of the control point of each vertex
                - A Bezier surface will always lie within the convex hull formed by its control points
            - **Normal and Tangent Planes:**
                - Give the equations used to calculate the basis vectors and normal vector for a parametric surface ↓ 
                    - $S_u = \frac {\partial (s(u,v))}{\partial u}$, $S_v = \frac {\partial (s(u,v))}{\partial v}$
                    - 
                    - $\frac{S_u \times \ S_v}{||S_u \times \ S_v||}$ ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/W0TDCq4d8uKp1i4ptIwB4wG8Py776569voOeqwE7HOAHqgZZaUPDZP1UraYIbiGfYAnrbnfVn7igdp5jIkBk3bUNu7BPxu1MVWxn8UKeFuK_QjoVzgOrqCm4rk3Klk-x.png) 
            - **Volumetric Representations**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aFvD3btV7B1EOl8_jCMjS4vvfbnDY2LWxNnfD92VeckX4W_4Ot5HcSN6IKF_zCESGAGAJNJsngr2EWqySoex2RoWPyZ4F0LQIhelvG00OOGt56pDBpqC-xwoAZeLfFD9.png) 
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pVRbFTJiQ_QCs6i4Y2_KVqFIlF1n5sOjiJUwECTh8Q0OvPRz104EIuSfphvZzmsxnem5MnmDMlP8p2bPcy8ryFn6wYD8cGll_AEfCN99ozHuK-kN_QyLeLqXuckNysxI.png) 
        - **Implicit Curves and surfaces**
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OSyZL75cz9VCR7NvHHYyt6cgxA0xiF5C_u2ZT_qyb3PRulP0uzR6tO_6ftdws0WHs_aeJf3hrDffa-uPV9Z2CgFcu8lQT0v4XW1cqKxz_U7HJB-6MSxcbYvDCffYIl7n.png) 
            - What are implicit Curves?―Curves that satisfy a given property $f.$
            - What are the two Fundamental equations of implicit curves and surfaces ↓ 
                1. $$f: R^m \rightarrow R$$
                2. $$S = \{x \in R^2 \space| \space f(x) = 0 \}$$ 
            - What three things can our implicit function tell us? And what is this useful for? ↓ 
                - $f(x) > 0$  Then we're outside our surface
                - $f(x) = 0$  Then we're on our surface
                - $f(x) < 0$  Then we're inside our surface 
                - Useful for collision detection
            - Example usage:
                - Give the implicit function for a circle―$f(x) = x^2 + y^2 - r^2$
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ezsxBHc9t5yBc3GfDoiccHryfozIxDjLE0beSaveN-VUt20FKhBkAs5eExIE-WxU_eiVIDWLodZpPCx_36B9SR0uV72ZJHl2OuTGf8zNaLc86vYCDi3F_FVQV2RFOMKl.png) 
            - Point cloud ⇒ a surface, end with the analytic form
            - What type of data can you use for point-set surfaces?―Only point wise data (position, colour and sometimes normals).
            - Approximate measures ⇒ Smooth surfaces
            - What is the process of determining if a point is on a point set surface? ↓ 
                - First examine a region around the query point and map a simple proxy surface (line, plane, hyperplane) to that region![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LVdEODyX7e5rr0D7IF1K5ENp7bN0Kyw8pclpQI6MfUzQYeFxTzxaXwRJcISTG2WXVc0263NC9bHnLz1I_s_PS6HIc1Hn3R8T5qUr-WgaHwTbkLGBqw7fjI_z9muuF2uH.png) 
                - Then if the point lies on that line it is on the surface
            - How can we project onto our point set surface?―Using our proxy surface, we can get the line between said surface and our point and then project it onto our shape. Using this we are guaranteed to end up on the surface.
            - What is the resulting function after generating a point set surface?―The result is an implicit function ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b-PQYvFpJ5nOnDjLgeClezXc7nPGedb19FXDjcDJWKB4kWYIbghJQpzk80BlZ0thAfuLJ-knQPv3kSJzpA-hFdAhF9i7FT4vne5YUlO7olHcjeb5mrTHb7p_K5A_j4Dr.png)
            - Give three important features of Point Set surfaces ↓ 
                - They are robust to noise.
                - You can do direct rendering with them - can do rasterization using disks and surface normals around the points, rather than triangle meshes disks are used.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hyf4-cGTIQB6M2_d20tHFIOEzJvtBcr7Zgfan8pnO_GBVSlOHPq8BNUSCxImeIDVsfhtz7od8HgcDY_Y7wBmPPV0wiUEh3y6gBNHfUaFvHzOESlZ1W9_yauMI6OsPCa_.png) .
                - You can convert them to meshes.
            - What are the Pros of Point set surfaces? ↓ 
                - Easy to determine if inside/outside the surface
                - Easy to generate points on the surface
                - Easy to determine if on the surface
                - Can use real world data - robust to noise
                - Can render in real time
            - What are the cons of point set surfaces?―Not efficient to use in some modelling tasks
    - **Lecture 2** **Discrete Differential Geometry** 
        - **Manifolds**
            - What is a manifold? ↓ 
                - A manifold is a topological space that is locally Euclidean (around every point there's a neighbourhood that's topologically the same as a closed ball in $R^n$) 
            - What is a closed 2-manifold?―A surface is a closed 2-manifold if it is locally homeomorphic to a plane everywhere
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dKte5l_PI2Zm2NUj4i-Z275X5hPPeV15rfocqZmS4pNznAKURVu-dJQ2rAU7xMNx2qlXRw_CLYmWsIrF8KmhCQPr1XGGEMbbHj9Pmt7-7trIAjl1wahOzEvawX__l_4u.png) 
            - What does homeomorphic mean?―One surface being homeomorphic to another surface, means it can be deformed (without piercing or pinching the surface) to become that second surface.
            - Math definition: 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/51gnM6JUfXL6wRogOH_bI-CTnPszmLiWWgdsmrRPopAai2XtfQNxsRA7iOgBdkiCa-0VrIV5i9ShHb5oXojk7G2DE0WZQmX3xXW0L1TUE7ZjZvsWmpBS-RkFGHi9YF2s.png) 
                - I.e. we create a volume sphere and get the intersection of the sphere and the surface and we can map it to a circle.
            - Manifolds with Boundaries:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/f2sNy5DHFQ7BmN09_acYPmqzWsLvEGCdqgS9iV3wZNBBAQQUVMT4ME-vUoYFStvFbVnmHlfLXVX6HIAdol28njMdslDyhepZIAIxn2geKpKkvIp2aITuRpK37fU_s1Nu.png) 
                - Each boundary point is homeomorphic to a half disk
            - We treat local areas on the shape as mappings to a 2d plane, we can then compute differentials. We get a continuous 1-1 mapping:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3Tz91ygPntWjdga7fwAFjx81uL3qA3c1t13TsPymjw-mfTnaWO3xYQ4xO0KXuR5NhuNVGSVfS2d8GLjz0NrFSMI2j2ZGapybMTT-pwzw5oMVF-cj-Y8ijaJNyf6q0w6p.png) 
            - 
        - **Local Coordinates**
            - After mapping from an area of the curve to a 2d plane, we can define local coordinate systems and thus a surface normal.
            - $$p(u,v) = \begin{bmatrix} x(u,v) \\ y(u,v) \\ z(u,v)  \end{bmatrix}$$
            - $$p_u = \frac{\partial p(u,v)}{\partial u}$$ 
            - $$p_v = \frac{\partial p(u,v)}{\partial v}$$
            - Having created this orthonormal basis, which is a linear approximation to the surface - we can then find the surface normal $n = {\hat{p_u}\times \hat{p_v}}$ where  $\hat{p_u} = \frac{p_u}{||p_u||}$ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JaLVopTxOR2dzfUFnUOAOtId0SwnHmuJmT-7lhnt8yN2DJAjWt_wtUdElqImTuZj0gOI5yp8Cia9yXs5ZRUbQCU0TXOOfD6FsEH0aISXFn9pb41wauxQFsdRp4r4L-Ms.png) 
            - We can then define a vector t rotated within the local coordinate system $$\hat{t} = \cos(\phi) \space \hat{p_u} + \sin(\phi) \space \hat{p_v}$$
            - Finally we can use the plane defined by t and n which will cut the surface:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-8Brlr1ugBaqXwEtdburKdWwts5IXK0KGgKbn3JTXIkCuBsuALdoLB-HJtlPx9gVII5CYpRLMP2RKb_8N5sgKdCvDA71542HKTaTYdAjrYe-BZSKmbS3JbhLBINtZCEZ.png) 
            - The curve $\gamma$ is the intersection between the curve and the surface, ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/B-hT4tHdYddzp1HPoRVNY0Sk0zJvW7pxz1QU3aHbpGz0ZUxT8cBJXYttuWf-vVuY4E69oB21phun1HRg6SuThqqaMbL9iA_q3Ol15hFj7gFww_hI7bKujdxHLz8HqBTi.png) 
            - What is this curvature we use for minimum and maximum curvature calculations? ↓ 
                - The curvature is the change in the tangent lines of the function as we move along it: $$||\frac{dT}{ds}||$$
                - Which is the second derivative.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8EL3m2BKkI4-UtrtZGo2GDfHjMyNC-d7qJMKBCBS5_yz-HVrEPAsVnFXHwhlUwkZHANreEdZVGid5-uIEwaBcvFnqR78IsvKridxLnHBXt8pNc2tFi3ey4ZblmatvC8b.png) 
            - What are the principal Curvatures? ↓ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zZFXEjt9KTY2MuWviuyzubq7nOxf_dddcS-iYeMJSJIX_O7bA5kcs8V-LEruq0dxKkcO6VNAKQec0ydo5f9huOYiLjoYKW5m34irU67gDY3WITlo-vq0LMAuy_5HsUmX.png) 
            - What is the mean curvature? ↓ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uI9S-7wP_kjtF1oI7_N8nF77BGS9FclFmtA2voIl9QU5qvMIAj0bnLKTLLcQMTEBZ6KTAU2yGCHuesvHm6qa6uNOUAksFQfKS2Boor5cLkUwycNlhjCaD-M12JwSrOy5.png) 
            - What is the Gaussian Curvature?
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/o_Of_U-l_rzIc_3dsrGGLIYZl-jFKCSXe7CMOq7Tv-5QbSl2F7eEzU2_emGPVC541PXjfc5DbNAzonYQD8Xzo3B-CAKN1ojRsnADJiW9zCHamXlLx1wdc29bgBDg0AIk.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qFKiqndLatwB-2qb8juCneDmGFXkBxx3RHtzZMeLIjm6KPKlTVtSheQJ_SPB0dJNuGuwfm8RTHTxe0hdHLuFUUXsV8RV9sW4u1eIQd2h5qEntL2riDd9c-nF6QUU35Xv.png) 
            - What is Euler's Theorem? ↓ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/znH-YE5uWUdRs5GdzTaPML-Buo2lQr7pdPjhaGS5PodRGR0Zhtw9KtKbQC9xYuiULnQqIaBjXcNzCul6Mb7anjnxG_JwSHmavEqZRW7BLhWzVcH3aLpspPerOjC8Bhkj.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bkQksDnoG9sHaytQuyOCfQ9BG44Nw1-It0AFWYaLUHGiwPHrILob9f5rTwc-UwZfvXeKovInsNag_oD4ZnyS_K1MKHJczu4tLotflOfABWSrRfcCmGOMYXQwTxonm-QP.png) 
        - **Local Shape by Curvature:**
            - Isotropic : Same in all directions
                - Facts about Spherical ↓ 
                    - k1, k2 > 0, k1=k2
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FXocmZ9XYMUx3J4DnvFroQRfK_jpMQESHrLrGV7r3UX11vX4nr7kWRtEX8ff9gHWRPjoCXtxNUTUVqXYmp21lu63eW7Dc5zRD80mTldzbdEExc9QJCMfmb2LGvHgnZpN.png) 
                - Facts about **Planar** ↓ 
                    - k1, k2 = 0
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UXK5d_EUdwEUhlAAV5jaJ0ZzN3QfBKikVGFUiAIbXKvm5fNZ9urNR3Zbe3zl3TdDF0bQ154zHoCVL9l6c_sRK-UP8eR7z3UJQEUfJxRZeQP2jyRgdL1RrD-oP_aeiBZm.png) 
            - Anistropic : 2 distinct principal directions
                - Facts about elliptic ↓ 
                    - k1 > 0, k2 > 0
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/01C4IoMzLHL7XbEetHy9hOFKX-09xE6GDIBQabk1hQRnznxdnX3c2xpTOrU8f4vnur9IdlUjkPzbLaUjP6tQzGjm85BfknmvwIpVlSRKqY3i2XLqiYzByNWCBsUrHat7.png) 
                - Facts about parabolic ↓ 
                    - k1 = 0, k2 > 0
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/l_M41qvVCPcHecuIqpu2eSHL2K18NgRPTJqGk3pjVyNrH80jKdNtp8rbqobl4KlLhJwd9N9Y-UmQteMGKX9RjH6DDLLABaJvh2qcwwIs4aYpl5pvNx_-W4FONFZ501tP.png) 
                - Facts about hyperbolic ↓ 
                    - k1 < 0, k2 > 0
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TLMhicO-U_9gxvd_t7-n6su7GwssPb5gPXqF6D8jBSqafojBsoo2_1go-LkNay2dgbUyLhMuI_I35Df-nj9eTFMLFawOaqpofYT13UXhpzrXxClFU0BqvFpasOvVtpgu.png) 
        - **Discrete Differential Geometry**
            - What two main approaches are there for approximating surface normal & curvature? ↓ 
                - Local surface approximation
                - Global surface approximation : discrete Laplace-Beltrami
            - What is the Laplace operator? Describe using its composite parts ↓ 
                - $f : R\rightarrow R^3$ $\Delta f : R\rightarrow R^3$ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AQHspVFkjdkY5T4ATL_BfZKdol8X_jMbzpuLIjbUuKxcf6Oo9tCuV4DF7a4coqV884PPL-ZuWo9K03tHeseRp3D4abrrdaZpPoIsHbXAg3Rv7Wap-4296ID9uncwVxHb.png) 
                - Grad f points towards the areas of most rapid increase, e.g. pointing towards a peak and away from a trough![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Cp5sUp1Hglr13hoB9ygBDhUrilQ9bG29O20JunrwdmmCrY_Aj2QOWdAvWlFyabxHXB9DZggBIqabgNCrlk8_jRg9q7K22hk0MFnR6ktGcegzlnmRQIcK1cEeXGQvBT-r.png) 
                - divergence can be imagine to be if we dropped particles and imagine how they would behave under the vector field, positive divergence meaning they would move out of the area and negative meaning they would move into the area.
                - So the Laplace operator can be thought of as a 3d differential, higher if the curve is increasing and lower if it's decreasing in an area.
            - What is the equation for divergence? ↓ 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LnvQlR7K5uT3b4I8jx-vuUE1HxoOwDx2SJLvpXCeQhWo1hXyngmN_KeybHpBtPNkxJRDb0Nt30GCYnKoRKPZCdrFS91NUZeLl3Ksp8VXUoGtnUu6b8MVvmy-5IFpePFF.png) 
            - What is the Laplace-Beltrami operator? ↓ 
                - The laplace beltrami is the extension of the laplace operator to manifold surfaces.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YdVLZ1lEJZ9Op8zdiQyq3hw1JdjASQ6LSmwPLXbzTQ7XRgKOp8VxaaRqD8bo7s6xU3SYZBLfszxVo4HeFqiJxhGJb-OgNE-9irDsr7gFBrfMbWqDc94rLP4IbMx__P_P.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sK3lbCjN0RoQpKxLtelEvmg76R0hYeT7VN_UzuYMNrmmRSO_GCT_cGk3RpnM90cX7oNC7_Nnb2EKkKubwdazvWRabafL4GTizZ8T0Pe0KVL0dER8s_8NAYNIEqwz8qpn.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/icIUVjGxKotBfFMTmkn5KlfQAOSbeYJhF0q-L382TejUVBsRX1D9EtJbUIlSjwfQsFzZjxoSRUiBZ1vp9dAV_RXzGU8Z1TPwLfO3zq-ik-auC30qpDIEoFwqLjmtRS9F.png)
            - The Laplace-Beltrami for coordinate functions gives us -2 times the mean curvature times the surface normal. This is useful as we can calculate the Laplace-Beltrami discreetly and then use that to calculate the surface normal.
            - **Discrete Laplace-Beltrami:**
                - Method 1:
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mJlIrYRU2cGwqnA_93w1-6enQHprSmwvnFO-sCxo-pjtU6nmRuatH_cXcgkJle9fFdeFQvtRpcx7P7GXBAQW459Nv1-9Zqosop9eiJsGk6MYHgipTlbrbOS3AorXAEJR.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JiZp0sH3O03p-BLspz-B9xdanb7G6o4ewv8lxHu_uvL_DLo0KmTu_yJZMGTJHatHeBVKoaV7wZhtUIP6pd6zO7uK4wDg4VAejEix7w8_mjeOD-H6d4C4D2PMgzo1QgLq.png) 
                    - The first method of calculating the Laplace-Beltrami is to calculate the average vector from a given point to all it's neighbours.
                    - Resulting in:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IZd6ZDPxYXxMUwir1wc1ozsRmDAS0kj991y1VryOoxd9_YRZmUTc13bcNeV0eypOVHSbvTaRU_y_MGiNmlqyHnVpJS8FnTL41N20YEPVb8twbFEFrvl7yKuI5PpXNG32.png) 
                - Method 2:
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3JHJT7Qjw9p_4Cdb4ZCv6fIZJqNlR1Pkw96JrtIG2b6CxzFaGjYOs5jTcffMWnJbrQQiXBqbDkTH-JZfx0vY4QQmRnFHL5RKZUW2qYuXgwWa1XPV72pTqPoC9H3xmGHe.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Kj_TKwMNKF7tIRV3pZWpJybJD9MNftNvHDilcnmXGJY37r1BLjukV5ABnUlyH6CCTKvIXQkYvPv9_pllWlAmiXzALGG-Km7LDaUKu9vlV0zDGxdVVBzn9W_syqU4t-CG.png) 
                    - First take your neighbourhood and flatten it to a plane - then find the circumcenters (or just place the point on the edge if the angle is more than $\pi/2$) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/coHWS9QvP0MY3wzL4WUmItishrY7ZDgBwZG0UxMNPtCRuTyQRZAz1W_E-PYBqChf7bLXgXbag64QykG9dXk3jH303anW8DI_kBagt8xeL_UuVswtNWoCPmxEBxL7Lutj.png) 
                    - We then get the weights which is the area inside the triangles:
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rH9vm-MWTQv0PYxKOJIHC6wgrJTMN1HmHcmIxLAcLsSkOO9xbJpFnwhs2FOIvluPkJE_wMi7qOGSNIPt-MCWJCdQsyWtN7ekEwJJMsjpHbEbnheTe2dvx1_uim7kcSSI.png) 
                    - We can then compute:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/t4VYeXmxmvcIvYdZB31dwCImYhbr3l99RF0EypNX_nlLza4n4M2PK_OtXoV34GMqokBvQhZE2dUkrD55b85kAvDCPjyDrRr_9uN-zVRnZnhoixvOUf5scICT_DMNd_6i.png) 
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D1X9bGGmh6f7AaUXpVjB_zROuWvwBXu98EF92mptAPmYyAF51si5aYMAOz2okeODANFw5EbES_QZ8luji2C6A4nHSCkTtlbHAw4MpOmVnnjnz6TgpxaVH8WwakPufh0W.png) 
    - 
- Distributed Systems
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
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/J4ZxKhqnf7YPMc5Ea8liL9bMYQS-goUHpgeoYlVCrKv7VTkhfIle7j8MwYyoAPuOubzU79fQ5RZxTlDG74x2GtG5fd12tWrjFjdZ8LkE9qxWOodDrXj3pIubVuBOE0Ne.png) 
            - The fundamental abstraction of distributed systems is that of {{nodes }}sending {{messages }}to each other.
            - **Latency: **Is―the time it takes for a message to arrive 
            - **Bandwidth: **Is―The data volume per unit time
            - **Client-server comms over the web:**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6IhRlUSXdP3733UVQmOFVDHC6Y0SLe-fYyKuwmLbL3b2U5a2oy4D7ZPz0nHz3m1t06uB3w_2pTNhRk2qpGDvSoLsQpaN92fCXiIZzljH8icC1Qndznxoklb3M_CdU0Df.png) 
                - URLs are separated into the {{server name}} and the {{path of the page}} you'd like to get.
        - **RPC (Remote Procedure Call)**
            - Consider an online shop communicating with a payment service:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NHXB6R_B2KKd0WN4Dpvtf-FS0i_-AZwnXGdIDp-4KeagopAQLGHJdKnebhFw-cyNVYqG20tL2suIEBVbuKa7_l5sN7OtQ2-A53JtIsVMwGEaIr2-G8yAuLXLB5OzsoV9.png) 
            - We can have a function applied to the shops card object, that is processed on another node/s (that of the payment service). What looks like a function call, is **translated to a network request. ** 
            - **RPC **is used to―invoke a function call from your local machine, on a **different machine** via **network communication**.
            - RPC's are implemented using a **RPC framework:** 
                - RPC frameworks implements **stubs**, which are―function definitions with the same type and arguments as the function to be called via RPC. This stub function sends a message to the other node to process the payment.
                - The RPC framework "**marshals**" and "**unmarshals**" the arguments, this means―it encodes the arguments of the stub so they can be sent over the network, then on the other end the args are reencoded into the function:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r037lljqIJLOb5QtnsdTRQFyTEq8ssiKFEVmqAV4vYTAhU1BleC9nB8lqX9fcHYH1Y9i0aaPShY4UuPiNLGOOjnppR4QRSBrY-L7djycaZ1vuuIvlWO_AoOhgYd7rpmM.png) 
                - The return value is then sent back, via the same process.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3fJb_xRoqYCt3dK-TfmYos_wLSknPOsok2cuONek9VDV2yCb_PhIoxuDDhLMbTMX7rvHTUa6KYJJYoBcAB6SOaqktjRaobFagTDvg39xb5-sQ8dAkriVULQGXoWD0j2e.png) 
            - We would like our RPC call to look the same as a {{local function call}}. This is **Location transparency, **the location of resources is hidden. 
            - **RPC in enterprise systems**
                - RPC is used in **enterprise systems** because―these systems can become so large that they cannot be run on a single computer. 
                - A "**Service oriented Architecture**" (SOA)―is the architecture in which a **large service is broken down into microservices** on multiple nodes which **communicate via RPC.** 
                - If multiple services within SOA are **running different languages**, we use―Interoperability (**datatype conversion**) and IDLs (Interface Definition Language).
                - An IDL (**Interface definition language**) is a―Language independent API specification. Method of ensuring datatypes are stored in a method not specific to any one programming language.  
                - Example IDL: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0xdtpuDkEuhCU8penCtWhT3yg4iFSQacbIje6oM4eGYy5K-eQRmFuyFQ7oE1txO74kASiw2cYLWza3bW8Ho_A9Ur1gMwi_U-gk95VJY_GhJL2GuRgF4IgJ9PpafguiKQ.png) 
        - 
        - 
        - 
        - 
    - **Distributed Systems Lecture 2** **(Models of distributed systems)** 
        - **The two Generals Problem:** 
            - Consider two armies, if they **attack together they win** - but if either one **attacks alone they will lose**. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kZF5kAjLXMdskp7Es7wh7db6UkMY_9NZcFf9DvSpP-6zUwEsFYgDhPIpmv9ovYPdIQwryWGSfXEzul_ZeP-_trYhNxI-asW1L4n7bEtV62xzcnLhcC1BrwMoEJndrbZj.png) 
            - The two generals can only **communicate via messengers**, however the **messengers may be captured** and the  _**sender could not know**_  (except if they receive a response).
            - Initial message delivered, but the response is captured: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bP57WAkbwWs9MDQXFH0vELMgsOf0iZkhPpGCCu2cYZXMwBbw0BcAZGgMpinj8FVjILtbJtjaWE77MbaPaEcPw4UNaQiW7X86i4TjGhQqxyze-gddSQENt1dJ-Yb57bNI.png) 
This is indistinguishable from the following (**from general 1's POV**): ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ey46dnl7hwQePgXZ1o7bHuVw7OV6dgmdaS3mxrncvAibJNFQMW2JzRp0Hjg3CHDJdpgQJe1ks_lNrCWzAa0v5pvvzqe3NpjyUCiXLeskxHn_4bkAF0GDD-8UEPlzP54Y.png) 
            - **In the two Generals problem, General 1 has the following two choices**  ↓ 
                - **Choice 1**: **General 1 always attacks**, in this case they may **send lots of messengers to increase the probability of receipt** - then  _if the message is received General 2 knows it's safe to attack_  (even without sending a response).  __**However**__  __, __ if the message isn't received General 1 will die. 
                - **Choice 2: General 1 attacks if a positive response is received**, in this case General 2 is safe **if** a response arrives  __but __  _General 2 is in Choice 1 when they send the positive response._  
            - This can result in an **infinite chain back and forth of communications** where **no absolute certainty of an attack is reached.** 
This is the problem of **No common knowledge **in DS which is―when the only way of knowing something is to communicate it. 
            - An example of the two generals is the following:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CfPVn-fTG7HNM1XhiINgF1iSMSKSHqv5Rny771BO2iMwu7RG4OxInE0oxC2IjB-5Gx98WFGcN6o2UB-bAvPjpe_fCoomhEBPbPBpRM0qZph8ADP66ZqlNx3rs9kE7IiS.png) 
The reason that this differs from the Two General problem is that―The **charge is a revocable action**, we can always return to the starting point.
        - **The Byzantine Generals Problem:**
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kVjnfDY9vy2AyF3x7MfD3YRsM_q6WT92dlh1O5oVermmNCANiw2qsOklQ7t9MwAEvRVMI8T9RSns63Oxj1ZLVqKrPlOnvNVfpGGtZbJzSsMiyZEUKDmymk_B4C_K77kG.png) 
            - Within the Byzantine Generals problem we make the assumption that communications are {{reliable}} but some of the generals are {{traitors.}} 
            - We further make the assumptions that {{up to }}$f${{ generals are}} malicious, that traitorous generals {{may collude and know who the other traitorous generals are}} and that honest generals don't know {{who the traitorous ones are.}} We then require that the honest generals must agree on a plan. 
            - **Generals may lie**:
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5y7MCi0wsHxY59MPzWPIY-KL9gZc7jv7vo3MtTd6mxd-w5A8cbXB2dVuqGqFRn7tXBDkPwuSroBGKrMrS6APOTSaJBc47XpUQ7MXSuhSUPoqF40YQTYjbmRoSn0ehD3M.png) 
General 3 cannot tell who is lying!
            - **Theorem**:  _We need _ $3f + 1$ _ honest generals to tolerate _ $f$ _ traitorous generals._  I.e. $< \frac{1}{3}$ may be malicious 
            - **Cryptography: **Digital signatures help, as we can prove a certain party sent a given message, however the problem is still hard.
            -  _Real life agreement_ :
 ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OxXWMFBndgJuLV8Z1-F3b7M6MusMgTuaDnq4kdDu1NCuYCwNFYLcf2ZWcy0x7MREMxDxTAFlZBvRqp2KYAy7vk9N5wUx_LGgLiiYJkQp5ge17R3NzXory9ZLFYnxV946.png) 
Customers can act fraudulently, online shops could be fraudulent etc. (could have asymmetric relationship where the payments service is trusted).
        - **System models**
            - We have seen the **two generals problem** in which the {{communication medium}} was faulty and the** Byzantine generals** problem in which {{the nodes}} were faulty. In real networks **both can be faulty**!
            - **Networks are unreliable**, can be damaged by nature.
            - **System Model: Network behaviour**
                - Assume a **bidirectional point-to-point communication** between two nodes. The **three models of such a link are**―a **perfect **link, a **fair-loss** link and an **arbitrary **link.
                - A **perfect link** is―a link where no packets are lost, reordered or damaged.
                - A **fair-loss** **link **is―a link in which some packets can be lost or reordered, however we make the assumption that **if we send a packet enough times** it **will be delivered**.
                - An **arbitrary link** is―a link in which anything can happen. We model this as having **an adversary acting on our communications**. They can replay, block or edit packets as they please.
                - A **Network Partition** is when a **link **between two nodes is **disconnected for a period of time.** 
                - ^^A ^^^^ _fair loss link_ ^^^^ can be converted to a ^^^^ _perfect link_ ^^^^ using^^―^^Continuously resending, and deduplicating at the other end. ^^ 
                - ^^An ^^^^ _arbitrary link_ ^^^^  can (*almost) be converted to a ^^^^ _Fair-loss_ ^^^^ link using^^―^^TLS. An internet protocol to guarantee successful communication has not been tampered with. 
This is only arbitrary, as the adversary could block all packets.^^ 
            - **System model: node behaviour**
                - Under the assumption that each node executes a given architecture, the three types of nodes are―**Crash-stop**, **Crash-recovery **and **Byzantine**.
                - A **Crash-stop** node means―the **node could crash** at any time and **never re-join the network** (dropping phone in toilet). 
                - A **Crash-recovery** node means―The **node could crash** at any time,** lose its memory** state but it **will re-join** the network at some point. 
                - A **Byzantine node** means―A node that **doesn't follow the algorithm** (although it could pretend to).
                - A node is either **correct **or **faulty.** 
            - **System model: synchrony (timing) assumptions**
                - The three types of **synchrony assumptions** about **nodes and networks **are―**Synchronous**, **Partially synchronous** and **Asynchronous**.
                - A **Synchronous connection** means―Message **latency is no greater than an upper bound**. Nodes execute the algorithm at a **known speed**.
                - A **Partially synchronous **connection means―communication has **(finite) periods of asynchronicity **but is synchronous otherwise.
                - A **Asynchronous **connection means―Messages can be **delayed an arbitrary amount of time**, nodes can be suspended an arbitrary amount of time. 
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
                - **Fault tolerance** is the design of a system so―a given number of faults does **not **result in a failure.
                - A **Single-point-of-failure **(SPOF) is―a **single point** in the system where a **fault will result in failure**. 
            - A **Failure Detector **is an algorithm that―detects if a given node is faulty.
A **Perfect failure detector **is an algorithm that → says a given node is faulty **IFF **it has crashed. 
            - The **typical implementation** of a failure detector is to―**send **a message to the node, then **wait **a set amount of time for a response. IF the node doesn't respond in that time it will be assumed to have crashed.
                - The problem with this implementation of a failure detector is that―we can't know if that's because the node has crashed, the message was lost or the message/node was only very delayed.
            - **Failure detection in partially synchronous systems**
                - We can only build a **perfect failure detector** in a―**synchronous**, **crash-stop** system with **reliable **links.
                - Instead we have a **Eventually perfect failure detector **this can―**temporarily **label a working node node as crashed or **temporarily **label a crashed node as working. **But, **it will **always eventually reach the truth** of the labelling. 
                - This reflects the fact that detection is not instantaneous **and **we can have long timeouts from a working node. 
    - **Distributed Systems Lecture 3 (Time)** 
        - **Physical Time**
            - Distributed need systems to measure time, used for:
                - Scheduling
                - Performance measurements
                - Log files
                - Data with time validity (e.g. cache entries, TTL)
            - The difference between a **logical **and **physical** **clock **is―Physical clocks count **number of seconds** elapsed while logical clocks count **events **(e.g. messages sent) 
            - **Quartz Clocks**
                - Quartz crystals can be engineered to vibrate at a particular **resonant frequency**, this frequency can then be detected (and fed back into the crystal again to keep the vibrating going). 
                - We use this **quartz vibration** by―counting the number of cycles to measure elapsed time. As we know $f$ 
                - Clock drift is measured in parts per million, meaning 1ppm = 32s/year of drift. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/acy_5LTVfZi7tnDFZQCnv__uIjFbqSiIwq8P9U5BQXY2cNJN_RXcJM9g1BVOQjjT9FwYNIKdhyhX248FmQyvO9sf7C7HX4nmYpXFVWvK-3_GpHMASP-kA3Al6KhMy0f-.png) 
            - **Atomic clocks**
                - Caesium-133 has a given **resonance** we can measure - about 9 GHz . The second is defined by 9192631770 periods of that signal. We are of by 1 second every 3 million years
            - **GPS as time source**
                - 31 Satellites in space broadcast their **location** and the **time **from their atomic clocks. We then pick that up, and can calculate the time taken for the signal to arrive (via c) and thus get the time.
                - We do need to correct for atmospheric effects and suchlike.
            - **Coordinated Universal Time (UTC)** 
                - **Greenwich Mean Time **is defined by―noon when the sun is in the south, as seen from the Greenwich meridian
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R9jUYQZGK9nZ6IIhjhW_voek4fxcitDPk3Z3yWTRZj4hvYUVxeEFkbBKxIp1khhsXIy1YwU9mFeTkWVNR9tfhkVwGoKuz0MgWIt7384d0evYj6KJCVM3w2IsCIT7qFv5.png) 
                - **International Atomic Time (TAI (based on French)) is **― time based on Caesium resonant frequency 
                - **Problem: **Speed of Earth's rotation is not constant
                - Because of the disagreement between GMT and TAI, UTC is―TAI with corrections to account for Earth rotation.
            - **Leap Seconds**
                - A leap second is―a second that can be inserted or removed (typically) twice a year
                - Every year on 30 June and 31 December at 23:59:59 UTC, one of 3 things happen  ↓ 
                    - The clock jumps forward to 00:00:00 without waiting a second (a **negative **leap second) 
                    - The clock continues to 00:00:00 after a second as normal
                    - The clock continues to 23:59:60 after a second, adding a second (a **positive **leap second) 
                - Leap seconds are announced several months in advanced
            - **Most common timestamps**
                - **Unix time: **Which is―the number of seconds since 1 Jan 1970 00:00:00 UTC  _not counting leap seconds_  
                - **ISO 8601: **Which is―year, month, day, hour, minute, second and time-zone offset relative to UTC. E.g. 2020-11-09T09:50:17+00:00
                - Conversion between the two requires **Gregorian calendar** to calculate leap years and **knowledge of past and future leap seconds** 
            - Most software ignores leap seconds, however OS and DistSys require them.
            - **Smearing **is―The  _spreading out_  of a leap second  _over a whole day_ . This helps prevent software that doesn't manage leap seconds from crashing when encountering a discontinuity of a second.
        - **Clock Synchronisation**
            - Computers track physical time/UTC with a quartz clocks - and due to clock drift the error gradually increases.
            - **Clock skew** is the―difference between two clocks at a point in time 
            - A **solution **to clock skew is―periodically get the time from a server with an accurate time (based on an atomic clock/ GPS). Using the **NTP **protocol.
            - **Network Time Protocol (NTP)**
                - An **NTP server** is―A server to give an  _accurate time source_  for computers to sync with. Many OS vendors run NTP servers and configure their OS to use them. 
                - **Hierarchy of clock servers** are arranged into **strata, **these are― __
Stratum 0__ : atomic clock or GPS receiver. 
 __Stratum 1__ : Something synced with Stratum 0 device
 __Stratum 2__ : Something synced with Stratum 1 device
                - NTP servers may query {{multiple clock servers}}, discard outliers and average the rest. Furthermore, servers are {{queried multiple times}} to remove network error
                - Using NTP we can reduces clock skew to a few {{milliseconds }}in good network conditions, but can be much worse over a {{bad network}} .
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3H78pNX0DSOHMqLDwyVPqkjGFU7zmOV7K0fZkHoGgXtkzVZAm7wjLcoEQttsBlj3Hrz4FkSwU39_HL7Ev8iQ5-vxPvQlrTV2aG0Uz4DBV2l7p856O5XpanEJArqHOIc2.png) 
                    - The round trip network delay would be―$\delta = (t_4 - t_1) - (t_3 - t_2)$ 
                    - We can't find the time taken for the request and response individually because―the two clocks aren't synchronised. We can only get the time difference between two timestamps of the same clock. 
                    - The **estimated** the **server time** when **client receives the response** would be―$t_3 + \frac{\delta}{2}$ Because  _ __we assume the delay each way is half the total__ _ .
                    - The estimated clock skew would be―$$\theta = t_3 + \delta/2 - t_4$$ 
            - **Correcting Clock Skew**
                - Once the client has estimated the clock skew $\theta$, there are **three options** for changing the time  ↓ 
                    - If $\theta < 125ms$, **slew **the clock. Speed up or slow down the clock very slightly (around 50ppm) so it's correct after a period of roughly 5 mins.
                    - If  $125ms \leq \theta \lt 1000s,$ step the clock - i.e. suddenly reset the clock to the server estimate. 
                    - If  $\theta \geq 1000s$, panic and let the human resolve it.
                - What's wrong with this code? ```cpp
start_time = System.time()
code_to_profile()
print("Function took", System.time() - start_time)
```AND, what is the solution?― _NTP could have stepped backwards_  while code_to_profile() was running - resulting in a negative time taken or too high of a time.  _Solve this by  using a monotonic clock, who still have slewing but will never jump backwards_  
            - What are **Time-of-day** and **Monotonic clocks** and **how do they differ**?―Time-of-day clocks is the  _time since some fixed date_ . Monotonic clocks are the  _time since some arbitrary point_  (e.g. since system booted up). 
The difference is that Time-of-day clocks can  _suddenly jump forwards_  or backwards subject to leap second adjustments, monotonic clocks  _simply go forward_  at some (near) fixed rate. 
Additionally Time-of-day clocks can be  _synchronised across multiple nodes_ , monotonic clocks  _cannot _ (only good for measuring elapsed time on 1 node).
        - **Ordering of messages**
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cSyRVfDprWQX6kkONyGuwzXN2cN0oyfX6oT83kiZLRpY4bOkHQ9lOXbG_D-03xvyuC8B0azFM9uvHw7Hj-wBD_IOpw0j4tNwiCrL28Yox_ow4OqhZpM2ERHovfopgoFu.png) 
            - The **problem **with using timestamp ordering―is that $t_2 < t_1$is  still possible if the  _clock skew is greater than the network latency._  
            - **The happens-before relation**
                - An **event **is something happening at {{one node}}. 
                - We say event a **happens before **event b ( $a \rightarrow b$ ) iff  ↓ 
                    - a & b occurred at the  __**same node**__  and a occurred before b in the local execution order.
                    - event a is the **sending** of some **message m,** and event b is the **receipt of said message** (establishing causality)
                    - There exists an event $c$ s.t. $a \rightarrow c \ \text{ and } \ c \rightarrow b$ . Transitive closure!
                - The **happens-before relation is a partial order** - it is possible that neither a or b occur before one another (**i.e. they are unrelated, doesn't mean they occurred at the same time) **this is written―$a||b$** ** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Bd6o0t7rZ1n8gzSYN0RPPgRQ-0aFu86YR9Wo9EaJDut_cwcndGwgL4ezC2i7DkZo5Ubp0Vma60xmCyP-z5RpbSZEo5C9ann8FL4-JWlOWaD7eTw5jUUabr3rb1uOTdaa.png) 
            - **Causality**
                - When $a \rightarrow b$, a  __might have caused __ b 
                - When $a||b$, a  __cannot have caused__  b 
                - Happens-before relations encode **potential causality.**  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/E91bglfXDom_vwusocHwkGxcTDNMEX7Moxuhp-TSmcOwQBQSHlCAQmz19vRpVbCNDCsUnbsroqMQYgVVx19c46wt4vhTq1Ri2FbvYSdBOOZgASW6b1C-C2ALIPFo9r19.png) 
        - 
        - 
        - 
    - **Distributed Systems Lecture 4 (Time)** 
        - **Logical Time**
            - Logical clocks are designed to **capture causal dependencies** $(e_1 \rightarrow e_2) \implies (T(e_1)  < T(e_2) )$ 
            - **Lamport clocks algorithm**
                - The Lamport clock algorithm is―```python
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
                - Within the Lamport clock algorithm, **L(e)** is―the  _time after_  an the  _increment due to e_ .
                - The Lamport scheme has the following Properties  ↓ 
                    - if $a \rightarrow b$ then $L(a) < L(b)$ 
                    - However, $L(a) < L(b)$ does **not **imply $a \rightarrow b$ . We could also have $a||b$. 
                    - We can have $L(a) = L(b)$  
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NWzGP1UyEkHkO4gREgLixeoi8cOAM4abaB3se7r0ImB-uzVNIeJLEEEilhXwyPSYFctCqAc8cLQLGqg2iXnPG5HF_yYSeGBjEAiTAUxkYYBLtQWAWq5JqrzjIa__JHhu.png) 
                - We can form a unique identifier for an event by―combining the name of the node (the event occurred at) and the time the event occurred $ID = (N(node), L(e))$. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xg2IfyouuRbVa9FbkOdHsZXyJrWZxa92DLDPqCaeqaBZR37C6_wCYtchKhkZaF1LKEjOHs1N8x3PyIv-OF-XxQr8SfrNiTL26-8Kc2Qfox0K7qERfYkVDVtK73NpHwmw.png) 
                - The main **problem with Lamport clocks** is―if we have timestamps L(a) and L(b) ^^we can't tell if ^^$a \rightarrow b$^^ or ^^$a||b$^^ .^^  _ __Remember, a||b simply means they're unrelated! If no messages have been exchanged all events are concurrent .__ _  __** **__ To solve this we need vector clocks. 
            - **Vector Clocks** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UvnFvkZTVzGPxEWZjr_kMUAUiA7FcxrCIors0myTDQknWQy0MOakHVv5DjhY0pPpkSIOxF37OGZ7cqINEulpWsY8VMVsTHrhChFYieuysBBZlfJpbEkqsvS5lL4yem04.png) 
                - The algorithm for **merging vector clocks** is―```python
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
                - Example vector clock arrangement:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Nr5EZypRAEEhXIQ3kVwQIrAtEEzY7-1YKCseaafPouBz8U9SArWl5NBxnYxQ3E1DpzsTK0SW2zXUkMJ6qeaWYvFCBPj4Vv9vAHDxLtiFGC0w6xzAIX0AxjIhzxwrDRwd.png) 
                - The vector timestamp of event e represents―e and all it's causal dependencies: $$t = \{e\} \ \cup \ \{a \ | \  a\rightarrow e\}$$  
So $<2, 2, 0>$ represents the first two events from a, the first 2 events from b and no events on c.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jFFIw1x1E-_MHi9JcaPCEKgEPWcijXTumy-uCOmOWnKEh71Kj14VxJa0iETImwR0bE3qfHN_3vPgy6eXGfP15rhqUhXkak-Iou5cYI6cN6pmwg9CZgfn0wNNlMJuI95r.png) 
                - Two events are **concurrent in vector clocks** iff―**Some **events in T happened before events in T' **and **some events occurred after events in T'. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fhN2SFw_h1aP_p7Qcn7UesaVszsVJ1kru10VOP5nlT890pjRlorhlOqw9B5dGM_DcWj7OAQb2rH12_9VM1BYQnevf-mC_886oGi05m1S6IeXHdc-Om81nVkytey9s-TF.png) 
        - **Broadcast ordering**
            - **Broadcast protocols**
                - Broadcast is **group communication** where  ↓ 
                    - One node sends a message, but all nodes in the group deliver messages
                    - Groups can be a fixed or variable size
                    - If one node is faulty, the remaining group members carry on
                - Group communication **can be designed** to be {{best-effort}} (messages may be dropped) or {{reliable }}(non-faulty nodes deliver every message by retransmitting dropped messages). There is no {{upper bound}} on message latency, as we use an Asynchronous/partially synchronous timing model.
                - The layout of a broadcast system is―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mFs8TN1pTuSMYFTopeZB2CUFSaNOk2UVEs0gL8tcAuDdaJ1GFrg-gwSi5vUp1M-SvvrldgftFPs3ME__MzkOS4qXyRkFubKjHa6FQzd5bYKziVR0Vn8KHVcD7QaJG9hu.png) 
                - The broadcast algorithm may wait to deliver a message to the application, because―we wish the messages to arrive in a certain order
            - **FIFO broadcast**
                - Note that when a node broadcasts a message, it also sends it to {{itself}}.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/I8jo0cSS3gODTf6w8D-mqHvxH6IBkmHggRtWq7ZQ27V5108wBpOfUFy-f6iFOPAgFvy-xQp4AidZD7C1calXQ5p-qEngwFMCc8X8IREnv5zzoYSww9hYtWmapqTBp2Zb.png) 
                - For **FIFO broadcasts **we **require that**―**messages sent from a given node** are  _delivered in the order they were sent_ . Messages sent from different nodes have no required ordering.
                - Valid orderings of the above diagram are then $$(m_1, m_3, m_2) || (m_1, m_2, m_3) ||(m_2, m_1, m_3)$$ 
            - **Causal broadcast**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/L1nUAnI60q5QqXN8NehbVWovcNwsWgdNcwup_XbfUwGOx-93_iv4GtGP5E_b19fPyGA9SxZC81O5d5FmZTfsJGNX6f-M_wkVxHfnZloOIqmfxL0hY8tOXzgDfChYqMw6.png) 
                - For **Causal broadcasts **we require that―Causally related events are delivered in causal order, concurrent events can be delivered in any order. 
                - The valid orders here are (m1, m3, m2) or (m1, m2 m3). 
                - The **difference **between **Causal **and **FIFO**―If FIFO we could  _technically have m1, m2, m3_ . In Causal broadcasts this would not be allowed. Or m2, m1, m3.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/I8jo0cSS3gODTf6w8D-mqHvxH6IBkmHggRtWq7ZQ27V5108wBpOfUFy-f6iFOPAgFvy-xQp4AidZD7C1calXQ5p-qEngwFMCc8X8IREnv5zzoYSww9hYtWmapqTBp2Zb.png) 
            - **Total order broadcast**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JG3S3CbaHrwr0rjbwr8YSPGYh6GWcWdCw9q_Dt68yE8YD47hQlqUDWyyR6uOeZx-V0qgaufPQlakuX1RNi_zzdC7SRN-ce1ZlUOB9aSbmVIZuuppV0gX5nOdkwNoNUkU.png) 
                - For **Total order broadcast ** we require―that all nodes deliver the messages in the **same order.** This  _includes the nodes delivery to itself!_  
                - The above ordering is for the example m1, m2, m3, but we could just have easily have said  m1, m3, m2: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/G782ZOFwPUarYj_VHKvoWeHGWkbal8CP8CDza7d5sze5ffFJcnNtmgsUzVj1HvJsjnZtkoE4t0Svhhvf9d-Fug9YQ-x17gBueGzyuzJ0TtUQsUfX0J0meyQAk4v8-jEJ.png) 
            - **FIFO total order-broadcast:**
                - **Fifo total order-broadcast requires **―** **That all messages are delivered in the same order **and **messages from a given node are delivered in the order they were sent
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JLfDCSOtxO_AKEZA9k300iA46WVFHDVBzEUHdfxH2KpbRXALgOjd9Hm1L60e9Jle3lEBqCJ2FLwp08e_Bg1mYDRxoEUVVzEusDhrNLCXjnQ4aRzuYXBJT2xuA5dxeuw7.png) 
        - **Broadcast algorithms**
            - There are two sections for devising a broadcast algorithm  ↓ 
                - Ensuring the **best-effort connection becomes reliable** (retransmitting dropped messages)
Enforce **delivery order atop of the reliable connection** 
            - What is the **problem **with simply retransmitting and deduplicating dropped messages?―A  _node may crash_  in the middle of retransmitting a message, in which case not all nodes in the group will have received the message 
            - **Eager reliable broadcast**
                - Eager reliable broadcast is―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/P3SNOBLC-Ooeys3gf9H7Qj0ZdDIu890t306QOWR0iqkivcEUNQE7tDaYU0LksM93348Hg3O__KEcRTbsTUpjmMjXGtwOJwLKmEhCdrDgkQbSb-pbnTVKMd4-Ja20jR5J.png) 
                - The **problem **with **eager reliable broadcasts** is―for n nodes, we have $O(n^2)$ messages being sent. 
            - **Gossip protocols** 
                - Gossip protocols works by―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AzHyQZqzTUIfVER7QY9jaTCTx-lgQzOZlK8nHdNeWaYKIvhopEjZU7JzK87ameqhPIbJ0HjY3nyWJixFvnQiV4T7PLY-OaTSLRv5NHcDstyN0dTnLbX7JMBuJ-MWsLTM.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_3X3m6GVxLKq8rUjorTbV_cZm4Sb0heFxEEyEPt1EO3EZbOX0o5r7U2QGz2FC9nT_oTen14u9eTrBZcTvud57w6f6uD8MvaFr1i1PTWg3ZgmDZ7hhZ1Q1n88MIVP7jSI.png) 
                - Note: if a node has **already received a message **it doesn't send it again. 
            - **FIFO broadcast algorithm**
                - The **FIFO broadcast algorithm** is as follows―```python
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
                - The **causal broadcast algorithm** is as follows―```python
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
                - What's the **problem **with the **single leader approach**―If the leader crashes no more message can be sent. Additionally, changing the leader safely can be hard
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
            - **RAID **is―a **Redundant Array **of **Independent Disks. **It's a method of replication within a single computer.  
            - **RAID** differs from replication of distributed system in two ways―RAID has a **single controller**, in DS each node **acts independently**. In Distributed systems nodes are distributed across the world not just within a single computer.
            - **Retrying state updates**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zAXYaRsuUHc51Km9hbNbnKDDitWvhZ50d3qvoCidJLcm6qeAarPNzPcwvxJcwh6suaom_FCxkHPyNw1aYaIk5-F-BqE7Q66syhUD2JtC9lOAIbxznkqEZL96X64iaxGZ.png) 
                    - To deduplicate this request we would require―that the database stores all requests it's already seen 
                - If the acknowledgement to adding a like to a post never arrives, what's the problem with sending it again?―It could be that the acknowledgement got lost on the way, resulting in two increments.
            - **Idempotence**
                - A function f is idempotent if―$f(x) = f(f(x))$ 
                - The idempotent alternative to incrementing a counter is―creating a set of likes and computing $\text{likeset} = \text{likeset} \cup \{userID\}$.  
            - **Retry-semantics** 
                - **At-most-once **semantics means―the request is carried out at most once, as we don't retry the sending
                - **At-least-once** semantics means―The request is carried out at least once, as we retry until we get a response. This can result in duplication
                - **Exactly-once **semantics means―The request is carried out exactly once, through repetition and deduplication or idempotence.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GSRTLxW-vEf4NUqlonf0KbkzGiGE7w-i-tN96YitYC_7leB8q2d6phZmfmFrQCyAAewjT5zeqnyD9EjG4EmX92DPJjK841ZBJpmk0LAPDioiCDBL77Uiyr01RlHFH1YS.png) 
                - What is **going wrong** here?―The request for the like is being sent again because the  _response was lost in the network_  - but in the meantime the user has unliked it (from a different computer) resulting in the  _unlike being cancelled._  
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uD7MftKfvEoC5LNNYhjyJt-DBpM1_ssxmcNI5GANhHTpQlIW1Xlxnw53rQqoENeT32-aYaWuVefWVsdiKwySbRCjpWVmHve1p6ab5d01cp0USZ-2O5ZGYTio8e6j7zHN.png) 
                - What is the **problem here **―We would like overall operation add x then remove x to be detectably different than not adding x at all. In the above case we cannot tell the difference, so we **can't know which replica is correct**.
            - **Timestamps and tombstones**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gikFIFeyKZoBUH03f_PMFynWpLzcInN7lzSoBpvWv1sDGsezP-H0Sve1OEcxW7a5cwhHWCFGywKNEJePi2OLdQUoVug6X2X82BYJZDWIl8BgO0F-6UQ4E7vaqeP3sKNr.png) 
                - A **tombstone** is―a  _recording that an item was deleted_ , **even if the item is still held.** This is used to hold the fact that the item was once present in the database and has since been delete.
                - Every record has a **tombstone, **and a **logical timestamp.** 
                - Replicas use **tombstones **and **logical timestamps** to come to by―**occasionally communicating** with one another to **check for inconsistencies**. If such an inconsistency is detected a  _**anti-entropy**_  method is computed. The timestamps are compared to decide who's correct and reconcile state.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xm41gzLVU0ErhY7SzQFYrxOtGB2mkoEfByN381ekrbHsn80I-k4fjuEGYG9GZ4LofTNezZ9DENA-dB-hKxZZWjuTANfA1TXebT0v4LKRRn5MRcUHGaQ-30Mr3G12GZH9.png) 
            - **Concurrent writes by different clients**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/69MpP4Pxk9RB8R8iIHmNCqbVW3VorxuevBfoCMMVuIVDgqo9AJ2wGe0cLTjKZGPCoeVnb2K-UeY5hvPYftc_IvY3vUt2hHgB3FjAKeQkJlEQf7t-DIWrd8M9XAq4NP3F.png) 
The two approaches for this problem are  ↓ 
                    - **Last writer wins **this uses timestamps with a total ordering (e.g. Lamport clocks) - we choose the option with the larger timestamp, and discard the other one. **Note: Data loss, consider 5 such events occuring **only 1 datapoint will be preserved 
                    - **Multi-value register** - use timestamps with a partial order (e.g. vector clocks) only replace one if one of the timestamps is strictly greater - if t_1 || t_2 we preserve both v1 and v2 (perhaps seek user involvement)
        - **Quorums ** 
            - **Probability of faults**
                - A replica may be **unavailable, **assume the probability p of a replica being faulty is independent of all other faults. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XzsAVTwbLE2zEm2HVLKSpuxHwmyeXU4XJBvaIIB55XfoWRqF1qv75w0o4voabdUcUjKa5Ln9Gr_ivmBphhQYwtCeuf7EsOoOqZt2sTYD3UXFX_tzdpapB22NuDTRfHF-.png) 
                - More replicas ⇒ more likely {{at least one replica}} is faulty at a given time
            - **Read-after-write consistency**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZV20Kz4WJfsbC1A4_9jWVz_T_VxpPSqOy1snJ6OJEIzvM1eoW62m6A_DUgs46e7W6so5qlh91oECbbg6Tp5-OdOQkPxWA1QAcjrRtRwsu-VaQu1VR-K2FV6ENOYpapKv.png) 
                - The cause of **read-after-write inconsistencies** is―when a client writes to one replica, then reads from another (and the **two have not been synced**). 
                - One solution to **read-after-write** inconsistencies is only allowing {{reads/writes to all replicas}} - if one replica is offline, however {{we cant do any reads/writes}}. 
                - **Quorum**
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bKZieC-unJ2_3dE8Z9rCb3l3UjEZ-uKXpqesXSHJ9puS2MfsrL-ZWYprgf_dsSw2hZLCvuKUtxvLVZi8Au3p5rK2SLNmoQL8ph3W6O953DrelXRRN30iKJ2GAjoyYhmc.png) 
                    - A **Quorum **is―a group of replicas who we compare responses from to decide on correctness. 
                    - What are the **three requirements** for read/write **Quorums**?  ↓ 
                        - **Writes **are acknowledged by at **least w replicas ** 
                        - **Reads **are acknowledged by at **least r replicas** 
                        - **r + w > n **(Think  _pigeonhole principle_ )
                    - **Read/write quorums guarantee**―we'll  _always read the most recent write_ !  
                    - Typically form majority quorums
                - **Read repair**
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TTTpPyP9EHF65J1DQ0v4KvzdtJ_cLFkv5TW_tNaU6UJyxo16qPIuE57oAKQtztbiKkm4umJi3ryBihS0iifNqH-DvHiujtZ9rJK8JfSBNZIdO1yeKbQZxUIdJSJQheZi.png) 
                    - If we **receive **what we find to be an **out of date value** (via Quorums) then **send the correct value** to all incorrect senders or any replica that didn't send a value.
        - **State machine replication**
            - State machine replication is about using broadcasts to facilitate replication
            - **The Process of state machine replication is as follows ** ↓ 
                1. A FIFO-total order broadcast is used to communicate the state change to all replicas
                2. When a node sends the broadcast it also updates it's own state (so nodes sending the broadcasts will also update)
                3. Applying an update is deterministic
            - An **update being deterministic** in SMR refers to―the  _replicas acting as _  _**state machines**_ **,** they start in an  _initial fixed state_  (usually empty) and  _follow exactly the same state transitions_  in the same order and must then  _end up in the same state_ . 
            - The main limitation of SMR is―can't update state immediately, have to wait for the delivery through the broadcast (has to coordinate with other nodes to decide on order). 
            - Related ideas:
                - Serializable transactions 
                - Blockchains (total order broadcast in the chain), distributed ledgers, smart contracts
            - **Database leader replica** 
                - A leader database replica ensures a total order broadcast
                - Generally have the requirement that write requests can **only **be executed on the leader, read requests can occur on followers. The leader then makes these commits, and communicates these changes with the followers. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wNQ5uytq-Djq-0AMvdNtPDVwqO6qipwM-ZwWvCQ0llB-EblhOrX0TmFVQjtZOKh2qKFaLD-cbKFGztrTJdS4i0B_Y_2uP5C2vTAbmLLCPUQo6Icr-1s6-EX9jpTBpIhd.png) 
            - **Replication using causal (and weaker) broadcast**
                - A replica **state update is commutative** iff―$g(f(x)) = f(g(x))$ where g and f are state updates.
                - The** causal broadcast** requires that if a message happens before another, it is communicated first. The **requirement for the state update function** is then―that concurrent updates commute. This with the other requirement ensures determinism. This is a bit like serializing the message.
                - For **reliable broadcasts** we would require that―the system is deterministic and that  _all messages commute._  
                - For **best effort broadcasts** we would require that―deterministic, commutative, idempotent and tolerates message los
            - 
            - 
            - 
        - 
    - **Distributed Systems Lecture 6 (Consensus)**
        - **Consensus**
            - **Fault-tolerant total order broadcast**
                - In our leader follower system, what happens if the leader crashes/becomes unavailable?
                - **Manual failover: **This is―when a human operator manually changes the leader when it's detected the leader has failed. Will need to reconfigure follower nodes. This is fine for planned maintenance. The problem is humans are slow, can take a long time in unplanned outages (consider if this occurred at 3am)
            - **Consensus and total order broadcast**
                - **Consensus is **―several  _nodes coming to agreement _ on a given value.
                - In total-order-broadcasts this would be **the next message to deliver**. So if we can come to a consensus, TOB drops out. e.g. consensus and TOB formally equivalent
                - **Paxos, Multi-Paxos **and **Raft **are consensus algorithms
            - **Consensus system models**
                - Paxos, Raft, etc. assume a **partially synchronous, crash-recovery **system model. 
                - We don't assume a asynchronous system because―there exists **no** consensus algorithm that will **always terminate**! Even in a simple crash-stop system.
                - Paxos, Raft, etc. use clocks only for timeouts/failures however the correctness of the algorithm does not depend on timing.
                - There also exist consensus algorithms for **Byzantine **system models (used in blockchains) 
            - **Leader election** 
                - Use a {{**failure detector**}}** **based on time to determine a suspected leader crash. On a {{suspected crash}} we must then elect a new leader. Crucially, we want to prevent {{two leaders at the same time ("split-brain")!}} 
                - Raft Ensures $\le$ 1 leader per **term **this means―The  _term is an integer variable_  that is  _incremented whenever an election begins_ . Raft ensure that at most 1 leader is elected per **term **and that each  _node votes at most once_  per term. The  _leader is then selected via a quorum._  The quorum gives us the fault tolerance
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oRKZVQPA2sewgXbqQXQuwNNxXS-hb89JPztSbjtVbzdVfHj2Ym0thNflC38IfB7DFepG9UiDi5zqttzWA3y_uEWDELnWIyMYUzLcXVUDXKAlG6Pnw4QKT9PUia4IYnRe.png) 
            - **Can we guarantee only 1 leader?** 
                - The **system of 1 leader per term **doesn't guarantee 1 leader because―we could have a leader disconnected from it's followers, who is replaced without it's knowledge. So it's the leader of term t and there's another leader of term t+1. I.e. **this method only guarantees on leader per term.
 **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V3tUykKyDgLFsDYH6S5IrhXdZQC2D6ubQvp1thFpCZjTFlzCu2vXSTteYMr2Q3DtV4nWWzT84-g0WmATUL0TAToeDTJxZJCInlfXt2xODhLhHvHhT7LE2KYpSXnKPivr.png) 
                - The solution to this problem of a leader being voted out without it's knowledge is―the leader ensures it can send messages via a quorum. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CHaFRGF--nZNN8hKVUQbJBTEehN0QFdy0H66cyAhIKONEOuPKt-LRQxotlsC_5hWZE6zGktq-hvjFjCcGptUh06SlQd94k8cxUqPbfTGXAKNFCC-eVGOEZpDlH6NA-yd.png) 
        - **Node state transitions in Raft**
            - The state transitions we will use are always within a certain term. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oWqazBP_8nBcIola3uNH5oNL_j0GsbXTAyi9UhFPA0l_JlVCJbTrWk4KelPLQF3Dl_Pr-6bpmqNyzyQMHr4rEL-ASDVNnAoFuthUcVjViShxfQD6bJTk4IARODnl2kQR.png) 
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
            - In **RAFT** the **log** is―a list of  _messages with an associated term_ , the term is the term number that the leader sent the given message. It is the  _**total order of messages.**_ 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VnP_X0y4qd74FjPvg_hresNYjUzjlgDUYiq6sHnVlGWZnzWMPvIAetoO8B7NBf-rY1_hKb43wUquGZ4RwjEl2As6e3wNnfPnJjmu5PiG0AlC7VoEC5w7yCEUJjRN1314.png) 
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
```―This is 
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
    -  _Distributed Systems supervision 2_   
        - 
        -  _**Exercise 13**_ . Using the Lamport and vector timestamps calculated in Exercise 10 and 12, state whether or not the following events can be determined to have a happens-before relationship.   
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4atqIBUEAzm7OncyN5qB3j5Z5XjQtc_OHDZgMdXZh6kXNeqKApIIRpARrwbyAHUyX7k7ndM-H0MBpStyrugFtkC4DMVZEVYv2pTPR9uWBOaXYXUGmwbk1reIC3dx1sE2.png)    ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9jwOOpv8Z8WqVwxq7ynfW03XwQFEn7ipkP88FMsmB5DkrGrmrNBuwEUhIDojkOzdAeBx17jEOVmlWrU2whx6-qnXAjz4jqukHzSSGc3F-r53v3Rg82YAzsXevXp8Bh-Z.png)  
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
                - Part Ib Lecture Notes
        -  _**Exercise 16:**_ . Give pseudocode for an algorithm that implements FIFO-total order broadcast using Lamport clocks. You may assume that each node has a unique ID, and that the set of all node IDs is known. Further assume that the underlying network provides reliable FIFO broadcast.  
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
