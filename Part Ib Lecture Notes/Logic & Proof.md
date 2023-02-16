- **Lecture 1** 
    - Logic concerns relationships between statements: satisfiability, entailment,... Logical proofs **supposedly **model human reasoning (symbolic logical AI dead end).
    - **Statements (informal) **are declarative assertions: "The colour of my dog is brown"
    - Schematic Statements - letting variables range over 'real' objects - "The colour of **X **is **Y**" 
    - **Interpretations and Validity**
        - An interpretation―maps variables to real objects. $Y \mapsto \text{coal}$ satisfies the statement, Black is the colour of **Y. **But the interpretation $Y \mapsto \text{strawberries}$ does not! A STATEMENT IS VALID IF...
    - **Satisfiability**
        - A set of statements is satisfiable if―some interpretaiton satisfies **all elements of S at the same time.** Otherwise, S is **unsatisfiable.** 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/w3fzWcKlgdmKEsLXTEjRH3BxEY4A14Pqs4VY6lqw1ppnnwsh7m-4HulXW_KFGSNeKRPj7xppuJAYDSN5YqcV7TRWxuOpU-Y0VUiCgzRTIwk-Un-flkjcmnvJ8FVHEIw8.png) 
    - **Entailment, or Logical Consequence**
        - A set S of statements **entails A **if every interpretation that satisfies S, also satisfies A. We write: TURNSTILE ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sX9svuHUGCdpgbcNMNqOpCtsjTZIzv2YMEHjld1GsyF6yVkCoytNRpW3H-KwTnobcI6JkSgmRKpPLPvGMlK8ong_5c5lhpUJsm2RhlMfE4nCay8XiXui5MlUYHvzQ8cO.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JJiC06M_P7NnjUEXujItCK4DOFyV2nR6UdmA6gXgCzgfsnHnqtYRgIaMQ8EGgEDzcMsHcngGBgOrGRwg8Mpv5n_ciSwL3YLrqX6Yi-Qb3WR_H_86p-qGgY5HCLWcdTf0.png) 
        - Last statement true for A being a tautology ok!
    - **Inference Rules** 
        - An **Inference rule **yields―A conclusion from one or more **premises.** ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Qcu-8WH_-qqJNucQyUaQnBBjmiIZYodNQu5JBxlNjSxi1iEqjheRfNXlYgUi8uMRA86F5jlB12I9JAlRlV0VKtRRCtOWP9smI79WkRylEEdxRDhLIb0vujBuIqr6PkYT.png) 
        - A proof using **Schematic Inference Rules **is correct if―it has the **right syntactic form. **Regardless if the premises or conclusions or true.
    - **Consistency vs Satisfiability**
        - An inconsistent system will have a proof for **every statement. **Including 1=2. 
        - Satisfiability is the **semantic counterpart of consistency.** ?????
    - **Richard's Paradox**
        - Consider the list of English phrases that define real numbers (base of the natural log).
            - If we sort this list alphabetically, yielding a series of real numbers
            - Define a new real number, based on the other definitions (diagonalization) 
            - This is a real number not in the list, that we've defined in English - paradox!
    - **Why should we use a formal language** 
        - The smallest positive integer not definable using nine words ⇐ defined using 9 words.
        - This number is so large, it is greater than itself.
        - **A formal language prevents ambiguity**
    - **Different Formal Logics**
        - **Propositional logic **is traditional boolean algebra.
**First-order **logic can say for all and there exists.
**Higher-order** logic reasons about sets and functions.
**Modal/temporal **logics reason about what must, or may, happen.
**Type theories **support constructive mathematics.
All have been used to prove correctness of computer systems.  
- **Lecture 2**
    - What is **Propositional Logic**?―It's traditional **boolean algebra**.
    - **t **means true. **f **means false. P,Q,R,... are propositional letters. **Propositional letters are** **input variables** that can be either true or false.
    - Statement truth tables:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gwQF7HcduGp11BuKHCpYXzBc2RnEFgMLqXtDhlyf22MrZI2FgQ_GVr1EmZG4KmfXv6SnCsOstz2dGTBiXWJk6JzXJT5XseJJt5wTKYqhh_cWDD6_tv1o_nZ60kRgRPH4.png) 
    - **Interpretations of propositional logic** 
        - An **Interpretation **is―a function **from the propositional letters to 0 or 1**. It's like an  _instantiation of a formula_ . 
        - When does an **interpretation ** _satisfy a formula_ ,  _satisfy a set_  and  _when is a formula valid_ ? ↓ 
            - An interpretation **satisfies a formula** if it **evaluates to true**. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/A-x2713LtmHjO0NrCEZd-EplqgvcXFdknIkPBAE8tVJ6fe8xBsQLsDuXyjM460j-8h6BX8in_Sj5B8h1kh-LiXIRuu0mYDew1xJX3Mr9xLAqQKjXXPc7nt5vwd-2-7pU.png) 
            - A set S is **satisfiable **if all elements are **satisfied by an interpretation** 
            - A is valid (a **tautology**) if every interpretation satisfies A. I.e. for all instantiations of the formula it's true.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/my8XoQ7hhJ5cmsmlcSJ5ww_luBcrwhE0K4K5nged-gPlXy4aJDGWnGEYcNQJgnIT9r4yJcbs50TIzZTUGT_Xu8SYVTDTP8GAk_qKqm9QNnUHPAZDwYI77lP-l_to5Jjt.png) 
    - **Implication, Entailment, Equivalence** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/thKW7VRYRg85vxnUsgt-Lan80a3nqILoObMg2fhjX4CYT7Rx23oujOydA-M3EOKqMDf8M2Kzjr_zIi_O5gU3NS4WOHhVx-mvux-d_uGJ-jscbVAVVBEvAC-6NC1UydGL.png) 
        - So in **propositional logic**, $A \rightarrow B$ is false iff―$A=1, B=0$. 
        - What is the relationship between **entails and implies** in **propositional logic** you  _nitwit_ ?―$$A \vDash B \iff \vDash (A \rightarrow B)$$
In other words **A can only entail B if we don't have (A=1, B=0)**. 
^^Entails is more like the implies we know and love^^, e.g. we have $$A \vDash B \iff \vDash_I A \ \ \text{then} \ \vDash B_I \ \text{for every interpretation I}$$ 
        - Although $A \rightarrow B$ is the same as $\neg A \ \lor \ B$ , they have different syntax.  __No shit__  
        - Entails is talking about formulae in the symbolic language of mathematics.
        - The approx equal symbol in equivalence, is saying that the formulas may have different syntax.
    - **Equivalences** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BZeUSUXzGFY19r_EqkYHJH_Dco2mjSvGnEtjATEYx53m9pGLmVRmd48gG5bX9piyxL4gghDLeomoWeUIIkK0iqVo32JifBIIkuHfB1W0grrAAz8Mej0zMEKiwjGr-gIh.png) 
        - We can exchange $\land$ with $\lor$ and **t** with **f** - and it all bloody holds
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SjjwTHT_9YFv8dCuUzpyUYH8hA9At-3q78JgJ3CPWtOPLnqxe5YIvnJGlKt5hQv14gfJzDMqJwaBbX3tMjHPNCoBu4Gz0iZndXbWZB9LlWOOgaCPEm5Awet0fK9GHYVl.png) 
    - **Negation Normal Form**
        - What is **Negation Normal Form,** you bloody fool?―Negation normal form is the result of **taking propositional logic** and **removing **$\leftrightarrow$** and** $\rightarrow$. Then **adding negation using de Morgan's laws**. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xobe1WgmgkBqqzUQjOOSvHO8hJFHnHmGar71k2V23AWBaakJnjSIfleMXx0Q5GxTUUaM7czdFXdUWwM9ZZkEsFNphv7Omw_i0Nrx90sjr9jP_trzS5-qrXP4mooIGPNc.png) 
    - **From NNF to Conjunctive normal form** 
        - What is **CNF**―**Conjunctive Normal Form**, remember from Digital Electronics? Load of **formulas ANDed together**, and all the formulas are a **load of** **propositions OR'd together**.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jNk7LnaKad2RAY_GBrTmACVKWSSqIqo8lIFMkh2lE6sTOJikEyppFhMJDCJUMiotjkYlrwnWsuV-WX-kOjk9uaZsZDTo7EpX__eVJukCc960keSb6YaKL0dvY1nNO7Gv.png) 
        - We can simplify to reduce huge exponential growth:
            - Delete P and not P in the same disjunction (OR)
            - Delete any disjunction that contains a different disjunction![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bYVgqnMGfa6vZ8TkWLcWUe47VH1wJ42H_MUS9UAY5JRkydMTMl2W6qcdJJoU32EQYlpUkwVOtKZjZ3JrUGZlz0JH7F3UPJm7dDTZnbX688ivzm3CWWIGVFavhzx8mgg2.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gTX5OIsJ4WkgtyvhXLQspyxwTpuf8HLqLdR4STOt9jryufJY7epQY5S3htNruuGWNo5GZ0-IWhF-zQWhQIXrIIM8ARRrcCp5aHww5a6Iox-vzaxyhKLEWimqO49HUCDx.png) 
    - **Converting a Non-tautology to CNF**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LoitiiSr-64lC2Umfdy1orOVlvj6EhUuux5UfCmxGCTudEigbOoTcbS-2Z4tnQY-0ct-CIpo7EGzm1nPEycum2QI8pAmegrpH5nCHhNpQaf-phi1oPUN3T7v4_FmGljk.png) 
        - If it simplifies to True, it's a {{tautology.}} 
    - CNF helpful for theorem solving, we can check each part to find a counter-example.
    - 
- **Lecture 3**
    - **A Simple Proof System** 
        - **Axiom Schemes**
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/98wX1oS5FUBaTIhxIac07AKFp2BGLmwcFCHiKoVvVH456WDscqKPe6fq2uAQsG1nRSUhLjc7JdgXD2aQnto4VUliQd1ZWDIEz5pU2oX-QmAMr1jg_zUmj8dHdTyIXlw2.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/igw5iyOMNP-8OQT-IVHYPJa7TJ21zWwhLScqyaPwDKfVVkZ5mhV4Qe26jtxwNJ7rgrl24ECxEasUzSApCFJA1ANSc3HMPVyVHSIpKXBiiT0fwUrN8KnfDyIQDzYSv8bV.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Pwlt-vTqUsra0YrbWcHyICwPaUcUWjKXSOxrzf3Ic_UxQdU-dVoB2ZBeEeROYKjdLo-NQrD3SAnVDl5mp5CDINiktn8Gf_cQjN_upXVfiM0xIjmEqQZN3uXCOsAJ3DXX.png) 
        - **Proof of **$A \rightarrow A$ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aeGM9dUE82EmQg6-jovP705GVCrJlqGirHb-Ib88i_33qaki-IMLDI0AtW0963K_z4MDKaPN39F5YedNs8lPNkH_PDutV00Mtdg9yGbOhgEhs5a-LC-0irN7CrDE5Pb-.png) 
    - **Some facts about Deducibility**
        - A is deducible from the set S, if there is a finite proof of A starting from elements of S. Write: $S \vdash A$. 
        - **Soundness Theorem. **If $S \vdash A$ then $S \vDash A$.  
        - **Completeness Theorem. **  If $S \vDash A$ then $S \vdash A$.  
        - **Deduction Theorem. If **$S \ \cup \ \{A\} \vdash B$ then $S \vdash A \rightarrow B.$ 
    - **Gentzen's Natural Deduction Systems**
        - To deduce $A \rightarrow B$ assume $A$ and go on to prove $B$. 
        - Each logical connective defined independently. We have Introduction and elimination rules:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0cYZlY_NkVpBbk66O2_dKmJGK7Mv-p2VYpTdwpKg19jLD5IZTbpJ8irrdrlqRSABpmuh_CFHVgEUqVV-tgOIJ9cvMkSwTWAVRrSeA_Y5TGfeGf-_vP2O_lnQzYANEyy0.png) 
    - **A Typical Natural Deduction Proof**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/shNrufYnnvXQiKpxTyvDrV-QXRk3r141Eg6YW3V-gv_KsyD31N5EEkuIKRdYM0JVdUmN0VtPB1dINlfBrO4DGJWQ0lw_Opvaxir8fWx-ocwZXUOr_VLpdxGKY-6tci3M.png) 
    - **The Sequent Calculus**
        - If ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Vg-Ff8NEAXnnoW2QjksUIbJ9-az8Rs3DFMNcGcR7iaMiNSYsT7A2R0D-bSah6Ijs3ZEuzO7IQaDU3X3T9AvAMdgyVc11pmzQ85FunyUK4KSDqReJrYDN9LeMk6qSTDoa.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/m2r_lQKtg3xlf6t3FY-uaOdcOX_IpAQcmV94QOGs0BHsOIJwDy1t10Z102DwtdsRq3aLUWUb-5UUKtzxVv6UtmSEGJ9y7gq6X8StSGpAy1d15xVzW9oDxIX_MoNuCFkE.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xl9FiHFJxf7jnlJcDM5r3QiPpfNKme5-5rkr5Xm42keFFRJUHe9_h2Zumcxp0IfTjjp8rvdqlbTG-S-1CpdGtC9yFtUDrjrlidZCZe5Tjqrk_hb0CezyUr5GJtCEXZYq.png) 
        - **Sequent Calculus Rules**
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RxCWq5wVKfY8Ds1wSQONw-4E_5_pbzz-z6hNg_XUpbamkSOrI1SHZuSfZmaoRHuT6xFC8w2by6sYNNi3-onqYcZKZUKbdg9-44B-z7OLjIUCr5Ux4B1rpIcsNuLdULIP.png) 
If we can prove A, we can use it as a Lemma to prove Delta.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6lQtd3KF5qRUBYVIDwTu9eRtCYayY3G-ApFY4fEycb8glzxXnD3s9oBYeN0WhKKpgDAQ3ibgNwXlV5Zrovnw_JtmWRxv6gSpkVjqapGaSK9nM0mxLzFoK91Lr-gAfLoV.png)  
We want to show **delta is the goal that pops out. **So assume not A, and a proof must mean delta is the true goal. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xLmrS8zsoCk9X_K7zWZzSFl8_52ZmtNB4a2lEu7brcB0vwCRA8vMUnqRSR81aq11nIG4RLVmlxfnYZ3MzsByTvgsY1O-foFXK-olYioNZkBi1xMenTR4qDq6CARux_6r.png) 
To Prove not A, it is sufficient to assume A and prove a contradiction
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Gsw4GDUN__EvNMf6cpweZwcg5FpCxG3EF9i6rdTxKlHQGnXseO-kNaygHaWLk5430HuaNKD6QEMCFXhWf2PN1cpSh9fnGVPBHS8fMYhNirYayrRdn_wuNRRZAn-Rf35X.png)
Straightforward. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JnCAXrF6P-eHLm8o1vXRgKP0qlXTCoot8bEM5NAmhCrVR1rr9TOOs9Ij5gc89P0GeNXzWLYrJOVSgf7YvYbMBh73_e_tmJMffSOb-aim4R666pDr5ouIxlNa7NwsyIR6.png)
(delta or a) AND (delta or b) = 
delta or (detlta and b) or (detlta and a) or (a AND b) =
delta or (a AND b) //Think about when the whole thing would be true
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sayFRzBtrTMj4phE2w8sAh0a9A3rM9CuLX3oSLZkbCfO1LNE3td02ztkdW00gDPt6lGKidjodagzZx9dXTZwwYeXcEMBmR_lFHYt6fmUrR_Kan-ShzelsAWkfV8eFmA7.png)
Straightforward.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yhT0awtb4vtMhRtSlKlhzYrV4nA2mJW3l4EqCfUr4SPZT-Tn180U7FzwSP5U8KczqGPWNnGtr4ZscylVUKsaS1yUGAkS5rUJ8nzt6w8zfNXubUgymke5tHe7OK_7RS5Y.png) 
This is simply using less assumptions, can always toss away assumptions
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VfHacf16Omw_4B_dprc_fisJ1tKGrXY6LRQ9rBR_peOPKQe9oA78YCqEPp0LTImvei3CNA1QdknOHqWXLx1CM2ucp5JXuLmkMoRPaakdG9I-YOWjKVMS6t0BfISSlH_x.png)
Assume A - prove B.  
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6lnlyKSjoMXPdQDbL013sUXBZGGWwpd0jpeEV2Gg5puZxYhQNvWWD87nhs32TN_YA9akTVbmqTRrCJLUTMACrtPANppPMcfAu3MlIIbLS2Z1BFE0MONNt98RHrUS-ox_.png)
If we have A, and B can prove delta. Then A implies B can prove delta.
    - **Example Proof**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FH7-DjuDAugv75LfWETVlYTL3jxntapB2P9JCKG0vRVYbhsLXoPPTY2ycrJcFHjW7wSFWm8bk2aRHFUQQkxVVIT1DR-dyrcmMbkI01L1uOg3idqaS-gWpAnJq2fmGcHT.png) 
        - First write the sequent to be proven
        - Then use the sequent rules and step up
        - Work with the outermost symbol at each point
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/69FhkHEateWIh7hBTTwFaOQIXRr0jbUO7xZxcwuavKAEhaYXFBJn466OpE8koCgd2PEcKMgEZclsJf0gIEhJiew6ccXYMfy8wjAS_PGrjiB3pmvXskKS4koIZY7RUj6H.png) 
- **Lecture 4**
    - **Outline of first-order logic**
        - Reasons about functions and relations over a set of individuals
        - Cannot reason about all functions or relations 
    - **Function Symbols; Terms **
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sbitxM-URtE5mW2iTUwtyrjSzOPsQsF7FhOXBvUg0uwFKB6oOV0_YVgfOs7TYhjznWo8jBW0SdNAuxz6lOzNX0koyF3hOAai0NYrOWY0feJRvvum45bnZqkLmP3rpfTc.png) 
    - **Relation Symbols; Formulae** 
        - Each relation symbol stands for a n-place relation 
        - E.g. Equality is the 2-place relation symbol
        - Formula built up from 
    - **Quantifiers**
        - $\exists  \ \ \forall$ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MWflgxSbwZ9Fze0vw3STem3j3heSuyto0cUEeYsQOp3kS1QD_OHnk4p1IoGKJBjnc-ya5DAtp0v0jlrZ7K7K0XOh36NdywZqPFxvA5MJwGbK-hweFQyH9edpbcNZAcCU.png) 
    - **The point of Semantics** 
        - Why not just let 1 mean 1, rather then a complicated symbol that represents 1. Well because an unforeseen usage of a general symbol can be very useful! Think about dot product multiplication. Vector calculus.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TjfwwfmHCJ-AyJT04eAfhKIwittVTA2_wHhQxB3IlBsYwcBkClKS_nfzsnVUh7oWrliyXUz9g9UNXFryZr-smUaZjvoMJQH7ZJUifixtJqM-V3WDPGsHFpOLbFZJG7WW.png) 
    - **Tarski's Truth-Definition**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/33pvB6qWyex4QduJH7JpF833jqbcY7uE6CF4ifF0Ndxy4ChKeLyKREDD1plNISKuMPXgtaFPM8OGdQzZ0wcg8NmWj_nnHIS39GBKZiX_f1VjFX--zy1KdN-yIWWx9L8W.png) 
        - An interpretation and valuation function V specify the truth value of any formulae A
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/srppJ7JDtSURpGwbNptfLBcvslsvcbEvG_4uZkA7h7Bx9hXykCkhYDTqYb-DIldUhe4koPeAuq5TKvV3STlX95fQngP1g7h1GqGKyNAe0b5xs1mgnYuor6MUEfNeXJmH.png) 
        - 
    - 
    - 
    - 
    - 
- **Lecture 5**
    - 
    - 
- 
- **NOTES**  
    - 
    - 
    - 
- 
- **Questions for supo 2**
    - Don't understand the pure literal removal in the DPLL method
    - 
- **Assorted Flashcards**
    - If we have the following in sequent calculus, what does this imply? $$A \implies$$―This means A is necessarily false, as we can step to $$\implies \neg A$$ 
    - How would you solve ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lj8IvKudhXXWEhQnk1xDRXKZIIWe_XMUFYP85IxbA-WHL4NUe8rp5C2-ze95kgOd_u_GFlDx7M3gXD29u6a6PyMoRjzg3flvQRWCfFQhf8ula2dsN7_X5oQ2Y9pfSGcq.png) ?―Put these connectives in terms of existing connectives and do a sequent calculus proof.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wY2QXQTAgUk-oPghScfKYUTjZIKePPEAv9M9SKsxr4MDl3jtTNCdRduNd1ufSMloet8rMPPu-nyv-ctqpe4jkrxRbb_3zOzkOQLzgKgG4uCJIKMqxNkvS4XFaHMfjVhC.png) 
    - What's the difference between linear and general resolution?―In linear resolution you can only use you starting clauses, and the current clause you just generated.
    - For the herbrand universe, applying functions has to be done in a way that is valid. ALSO predicate symbols are seperate from the functions, e.g. < or >. 
    - Do you push in Nots first or skolemize first?―Push the nots in first, then skolemize. Otherwise the quantifiers will be flipped.
    - What do you get if you factor these ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4knpW6zek7HtdVCA-CmLkMsS7M8yO2JH-xowKDAxN9Eq1-XhMV-gpb98IjzcEUwXquGX2LBKGgLha-c9PC9xNnQNJIxAGp9obJ412FtETdFIKU4MnfO9w5T7XDLqXcIy.png)―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pswtBqpep-ekDHtzoqoHlUjRRC4dvFgk8A5MhMVo_8CqRHqmFqbCKkjPKRaEkKcxXTG6q__l4RPhBTtyZ3LlOuN_QnCmkgnGoR86g-ASqAnMMhrTrGOLHVDPtFiliDpl.png)
Always start by factoring if you can, you lose nothing and it just gives you free clauses for free. 
    - Describe the procedure for combining BDDs―Write out your first tree, but when they lead down to 0s or 1s attach your second tree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sxPm1tm3p1PnE-meFGIaERHdopWMMGZM2IwwTA3-XhtuAvrgSpFJm1DOXfuAihD7uIiNHLwFOZNY54reLmuXE6Yx539vYnV3oD36RFNWjTBcD7Q_WEMyirwCdwZKGUc0.png)    IMPLIES  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4hP-neSWPMPjGiupttwjlr2wbQ8joUIGSKEH7jd3v0kXF0emRUa71G_vK5zUFZEgNcXUdZN3w-UMWNhogiIDpI1ZOgJKtyM-2gQaT_gop_Tl-WbRddFMe2bo-hMbKIbC.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BkVbQ4bIz6pzsL7yr6iks9HvRtFQYC57UwwINL5cYUyjnOKhzB5Qw2VM8MApq4TNJzRY8Zkru8ulDVZnXh_zzH6ut35IDPBf9CWqvK49zPv44JJFsS75NEQYRLiLI_1y.png) 
Then simplify
    - How do you know the dual of an operator string equivalence also holds?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/izC8XKFSfTJc-Dv0yZnfovRAL5S-Htovps3kWpWCiwFCR2bMY_cH_fnN_1iG1smjfewz9roLuJRJuyJd1QfGQJTpSGtni2taK3VJ5KkKUN0gteoOqB-hhgnz9bRNjRLf.png) 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/o6vy1vAwO6dsOU1YZec_UVTpr1y8H4Ca5M5VMjNDhZdcVxhGZ88PcIzTW4Xj51uK3jvvB8BZ-e9-z1sQWUJ3qDQJqIvAmvhJCdWWu1RkkOe6bg8ShUe3O7xWnOEewkSL.png) 
