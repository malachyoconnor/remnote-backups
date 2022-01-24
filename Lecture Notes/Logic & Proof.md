- **Lecture 1** 
    - Logic concerns relationships between statements: satisfiability, entailment,... Logical proofs **supposedly **model human reasoning (symbolic logical AI dead end).
    - **Statements (informal) **are declarative assertions: "The colour of my dog is brown"
    - Schematic Statements - letting variables range over 'real' objects - "The colour of **X **is **Y**" 
    - **Interpretations and Validity**
        - An interpretation→maps variables to real objects. $Y \mapsto \text{coal}$ satisfies the statement, Black is the colour of **Y. **But the interpretation $Y \mapsto \text{strawberries}$ does not! A STATEMENT IS VALID IF...
    - **Satisfiability**
        - A set of statements is satisfiable if→some interpretaiton satisfies **all elements of S at the same time.** Otherwise, S is **unsatisfiable.** 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/w3fzWcKlgdmKEsLXTEjRH3BxEY4A14Pqs4VY6lqw1ppnnwsh7m-4HulXW_KFGSNeKRPj7xppuJAYDSN5YqcV7TRWxuOpU-Y0VUiCgzRTIwk-Un-flkjcmnvJ8FVHEIw8.png) 
    - **Entailment, or Logical Consequence**
        - A set S of statements **entails A **if every interpretation that satisfies S, also satisfies A. We write: TURNSTILE ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/sX9svuHUGCdpgbcNMNqOpCtsjTZIzv2YMEHjld1GsyF6yVkCoytNRpW3H-KwTnobcI6JkSgmRKpPLPvGMlK8ong_5c5lhpUJsm2RhlMfE4nCay8XiXui5MlUYHvzQ8cO.png) 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/JJiC06M_P7NnjUEXujItCK4DOFyV2nR6UdmA6gXgCzgfsnHnqtYRgIaMQ8EGgEDzcMsHcngGBgOrGRwg8Mpv5n_ciSwL3YLrqX6Yi-Qb3WR_H_86p-qGgY5HCLWcdTf0.png) 
        - Last statement true for A being a tautology ok!
    - **Inference Rules** 
        - An **Inference rule **yields→A conclusion from one or more **premises.** ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Qcu-8WH_-qqJNucQyUaQnBBjmiIZYodNQu5JBxlNjSxi1iEqjheRfNXlYgUi8uMRA86F5jlB12I9JAlRlV0VKtRRCtOWP9smI79WkRylEEdxRDhLIb0vujBuIqr6PkYT.png) 
        - A proof using **Schematic Inference Rules **is correct if→it has the **right syntactic form. **Regardless if the premises or conclusions or true.
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
    - What is **Propositional Logic**?→It's traditional **boolean algebra**.
    - **t **means true. **f **means false. P,Q,R,... are propositional letters. **Propositional letters are** **input variables** that can be either true or false.
    - Statement truth tables:
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gwQF7HcduGp11BuKHCpYXzBc2RnEFgMLqXtDhlyf22MrZI2FgQ_GVr1EmZG4KmfXv6SnCsOstz2dGTBiXWJk6JzXJT5XseJJt5wTKYqhh_cWDD6_tv1o_nZ60kRgRPH4.png) 
    - **Interpretations of propositional logic** 
        - An **Interpretation **is→a function **from the propositional letters to 0 or 1**. It's like an  _instantiation of a formula_ . 
        - When does an **interpretation ** _satisfy a formula_ ,  _satisfy a set_  and  _when is a formula valid_ ? ↓ 
            - An interpretation **satisfies a formula** if it **evaluates to true**. 
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/A-x2713LtmHjO0NrCEZd-EplqgvcXFdknIkPBAE8tVJ6fe8xBsQLsDuXyjM460j-8h6BX8in_Sj5B8h1kh-LiXIRuu0mYDew1xJX3Mr9xLAqQKjXXPc7nt5vwd-2-7pU.png) 
            - A set S is **satisfiable **if all elements are **satisfied by an interpretation** 
            - A is valid (a **tautology**) if every interpretation satisfies A. I.e. for all instantiations of the formula it's true.
![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/my8XoQ7hhJ5cmsmlcSJ5ww_luBcrwhE0K4K5nged-gPlXy4aJDGWnGEYcNQJgnIT9r4yJcbs50TIzZTUGT_Xu8SYVTDTP8GAk_qKqm9QNnUHPAZDwYI77lP-l_to5Jjt.png) 
    - **Implication, Entailment, Equivalence** 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/thKW7VRYRg85vxnUsgt-Lan80a3nqILoObMg2fhjX4CYT7Rx23oujOydA-M3EOKqMDf8M2Kzjr_zIi_O5gU3NS4WOHhVx-mvux-d_uGJ-jscbVAVVBEvAC-6NC1UydGL.png) 
        - So in **propositional logic**, $A \rightarrow B$ is false iff→$A=1, B=0$. 
        - What is the relationship between **entails and implies** in **propositional logic** you  _nitwit_ ?→$$A \vDash B \iff \vDash (A \rightarrow B)$$
In other words **A can only entail B if we don't have (A=1, B=0)**. 
^^Entails is more like the implies we know and love^^, e.g. we have $$A \vDash B \iff \vDash_I A \ \ \text{then} \ \vDash B_I \ \text{for every interpretation I}$$ 
        - Although $A \rightarrow B$ is the same as $\neg A \ \lor \ B$ , they have different syntax.  __No shit__  
        - Entails is talking about formulae in the symbolic language of mathematics.
        - The approx equal symbol in equivalence, is saying that the formulas may have different syntax.
    - **Equivalences** 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BZeUSUXzGFY19r_EqkYHJH_Dco2mjSvGnEtjATEYx53m9pGLmVRmd48gG5bX9piyxL4gghDLeomoWeUIIkK0iqVo32JifBIIkuHfB1W0grrAAz8Mej0zMEKiwjGr-gIh.png) 
        - We can exchange $\land$ with $\lor$ and **t** with **f** - and it all bloody holds
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/SjjwTHT_9YFv8dCuUzpyUYH8hA9At-3q78JgJ3CPWtOPLnqxe5YIvnJGlKt5hQv14gfJzDMqJwaBbX3tMjHPNCoBu4Gz0iZndXbWZB9LlWOOgaCPEm5Awet0fK9GHYVl.png) 
    - **Negation Normal Form**
        - What is **Negation Normal Form,** you bloody fool?→Negation normal form is the result of **taking propositional logic** and **removing ****$\leftrightarrow$**** and** $\rightarrow$. Then **adding negation using de Morgan's laws**. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Xobe1WgmgkBqqzUQjOOSvHO8hJFHnHmGar71k2V23AWBaakJnjSIfleMXx0Q5GxTUUaM7czdFXdUWwM9ZZkEsFNphv7Omw_i0Nrx90sjr9jP_trzS5-qrXP4mooIGPNc.png) 
    - **From NNF to Conjunctive normal form** 
        - What is **CNF**→**Conjunctive Normal Form**, remember from Digital Electronics? Load of **formulas ANDed together**, and all the formulas are a **load of** **propositions OR'd together**.![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/jNk7LnaKad2RAY_GBrTmACVKWSSqIqo8lIFMkh2lE6sTOJikEyppFhMJDCJUMiotjkYlrwnWsuV-WX-kOjk9uaZsZDTo7EpX__eVJukCc960keSb6YaKL0dvY1nNO7Gv.png) 
        - We can simplify to reduce huge exponential growth:
            - Delete P and not P in the same disjunction (OR)
            - Delete any disjunction that contains a different disjunction![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/bYVgqnMGfa6vZ8TkWLcWUe47VH1wJ42H_MUS9UAY5JRkydMTMl2W6qcdJJoU32EQYlpUkwVOtKZjZ3JrUGZlz0JH7F3UPJm7dDTZnbX688ivzm3CWWIGVFavhzx8mgg2.png) 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gTX5OIsJ4WkgtyvhXLQspyxwTpuf8HLqLdR4STOt9jryufJY7epQY5S3htNruuGWNo5GZ0-IWhF-zQWhQIXrIIM8ARRrcCp5aHww5a6Iox-vzaxyhKLEWimqO49HUCDx.png) 
    - **Converting a Non-tautology to CNF**
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/LoitiiSr-64lC2Umfdy1orOVlvj6EhUuux5UfCmxGCTudEigbOoTcbS-2Z4tnQY-0ct-CIpo7EGzm1nPEycum2QI8pAmegrpH5nCHhNpQaf-phi1oPUN3T7v4_FmGljk.png) 
        - If it simplifies to True, it's a {{tautology.}} 
    - CNF helpful for theorem solving, we can check each part to find a counter-example.
    - 
- 
