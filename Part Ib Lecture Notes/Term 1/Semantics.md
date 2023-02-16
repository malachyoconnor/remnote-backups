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
