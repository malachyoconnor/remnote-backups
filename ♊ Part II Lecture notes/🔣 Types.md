- 
- Lecture 1 - Review of Type Safety
    - What are Type systems
        - Type systems are both an essential part of programming languages and an essential concept in logic & proof theory. Thus, they form a link between theory and practice.
        - Give some uses of types ↓ 
            - Error detection via  __type checking__  
            - Support for structuring large (or medium) sized programs
            - Documentation
            - Efficiency - if we don't know the type of a variable, if I say x + y, we need to go through a long set of if statements to decide are we adding two integers, are we concatenating two strings etc... (runtime test needed)
            - Safety
    - A language of Booleans & Integers
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tkr5fElVeLYKIQOMUxVMRM94h5UwB5bhAsu6w2DSFxmB_9eDL8n2Ph4h3n4X4IHQMKIg_wKJODvs-kUPtPnu3BV65Jjh7uVIhfaPT7Hei5wgPvmUdMQ1-XXmMbcpNXwd.png) 
        - To ensure our language adheres to our rules, we need to specify types. A boolean type and a natural number type.  $$\tau ::= bool \ |\  \N$$ 
        - Then we make a **typing judgement **like: $$e : \tau$$ 
        - We then define typing rules, that form leaves of a tree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zfVr_AiB3KhveYPS79GlmcMh8mdFNcyB0zaZDBKJBG43CVef_1QxbEk0C62rQ45Ny96JgkRqNEtQT8rxVWbi-VyhYdhXSAqmxZZJ4SPTwz84nYEzpvDme3aAs19xrRvx.png)
        - We can then add variables into our language, what would we add to our terms to add variables?→$$e ::= ... | \ x\  |\  \text{let x = e in e'}$$
This binds x to some expression e in e'. 
        - The typing judgement must know what the variables are - we create $\Gamma$ which associates variables with their type. Note that gamma is just a list (called a **context**): $$\Gamma ::= .\  |\  \Gamma, x: \tau$$
We can then say $$\Gamma \vdash e : \tau$$
What does this mean in English?→This means e has the type $\tau$ under the assumptions $\Gamma$. 
        - We get the following variable rule, ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/F_R1Z6SLETKeffQbS9jODBlMBAK9r6_SJ-QeTf81agJbwXn1sc6xpWJw3DcBqQdvIRT0qRh3iBZ5GJR88ni_8FAgLgp75Dn4y9IBumwpsR_H3DMWr-67YmPBFQyPc0Mr.png) 
    - Substitution
        - We have a host of substitution rules:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7z217o87GnUFzFtn-XugNiGKIyxCBvEoqtXpbhhv4EpEeauV61UYwTXgEdnqiCdZ51p_6w4ud8EFQOrwjLrKdRkM8RQ0fPb1E2jX8MPF5Oy5agjqUI9pbzbBulEKO8eO.png)
        - What should the substitution rules be for these three cases![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iSZ3h9azTciBO8AO3AOgZqD6Kq93o36mpok1qEvb7j2nsFWbLNIRKePhWYIdwY-piK1llCtqzDRp2nm1c-XQKTC4AGOPhpTKJ_xOMaM676hI-rQnjkVjGA32JLdFWxzj.png)↓ ↓ 
            - $$[e/x]e_1 \land [e/x]e_2$$ 
            - $$[e/x]z = \begin{cases} {e \ \text{if z=x}} \\ {z}\  \text{if z != x} \end{cases}$$ 
            - $$\text{let } z=[e/x]e_1 \text{ in } [e/x]e_2$$ 
        - Describe the **Weakening **lemma→Weakening is a lemma that states, if a term typechecks in a context it will also typecheck in a larger context (if the context's do not conflict, assumed to be correct).  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ge7dyBt8lh6pkPn2yPpuAv14S690-il17Jy6yJ47b44thsuygAi8h8npYXPsvjnBocXO2ncs4LJOpQvxBhm77r7EBT0Fn1o8N0lBWwTHh2MjjOfrldJLvJ7Fdw1do5bY.png) 
        - Describe the **Exchange **lemma→Exchange is a lemma that states if a term typechecks in one context, we can exchange different items in the context and the term will still typecheck. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iA7EWKqOSB2lBcFtNHNr5pIGwbZvWzZK-j-qkmCo9ldvFMp3_rkICGyn_uN6JfPkVUa6aFGz7zDU37zsg-7xM4dDPdbIhyfIzXXZ_Ot586UZl19wkFW-_Ufayr8CuGo7.png) 
        - Describe the **Substi****tution **lemma→Substituting a type-correct term for a variable will preserve type-correctness. E.g. adding a type correct variable to the context is the same as substituting a type correct term to the equation 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Zx2KkTdSOmqpVs4yYoCKTyccaJ0OoyxK6utssDsr5Eh6Nj7RUg8-POlRqI4RXDnvTr8dBYzW5ChYSGCsdnC7-_x7RFuRt1rfUtE0gLgyUjFmA01wTjxdPM31N4hVkIA8.png) 
        - How would you prove weakening via  __structural induction__ ? ↓ 
            - For every type rule we start with a derivation of a certain type.
            - We then assume by induction that weakening holds for any subtree. That is, if we are trying to prove $\Gamma, \Gamma' \vdash e: \tau$ then on any subtrees **we assume **$\Gamma, x: \tau'', \Gamma' \vdash e: \tau$ 
            - We then show that if the subtrees hold it holds for the root.
            - For example: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uc-cet6AaDv6D8O4_rAzjfdcO5_c2Gx1L3jjWuHDqBTdldMtvMb8fvxWRSq3zcHKBxPwbnwAE2pNuzSU42UVh0fY2Zsg8XJjyhXmUv24CQyW2HfGxQsWNN8USZWehHTH.png)
        - How would you prove weakening for this type rule (Write out the proof, 5 lines):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dr4xpcqhttvTZdAMlWt6twFFuPhaqKqE7UfBJ4tnaDZEW-Tq0SUBPm3nVmaZqYfWDmq6pLZ6Rm1DGeujpDKi5-R9X6j3z_8XoIMyJkpTGgvmjJpMi7ZN7kId7LBm6P7r.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aDHDd709E9uOHKlxA2aSozhqht3M6B-IvBGMrFEnC0jidc_c4PCQacmC6UEiJWIUxrDEmnAzl45TYmINWxAN8UkvvZgtHRR06ihcOKGO2uDBmVcmB56IDB-lW7SiHfaC.png)
We first apply induction on the sub-derivations, then we use the fact that PLUS carries with it context when it is applied. Consider that this is the same as $x:\tau''$ being inside $\Gamma'$ .
        - How would you prove exchange for this type rule? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wg89SxFoijEEkk58wMVgmcDZUu_s_X4Fe10C7PGNIRFzgH5hhnfVL_eLzmyKRKzawV_bQallFAQim1dLAGL84y_KUEIEzRovDfraXhFH6PZvWUBw1fy9VLnNTNU7HcMn.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-latSCqcXefOwlxsDS22Rpm5VuwM0z7NSaM--_ogc6-GAoYskFK4Lk7h_pE-Nf-YYV1Wr9Tcwsfv9CacHQVfLukrGT0Fa-OfVR0oQ1KJXAUntTPnuQwZltFgY23aQjhy.png)
Note that $\Gamma', z:\tau_1$ becomes an **Extended context**. This means we group it into a single thing and it acts like $\Gamma'$. 
    - Proof of Substitution
        - In broad strokes, how would you prove substitution using  __rule induction__ ?→We start with a proof of $\Gamma, x:\tau \vdash e': \tau'$ **AND** a proof of $\Gamma \vdash e : \tau$ ( __this is what we're going to subsitute for x__ ) - we can then apply substitution on the subtrees by induction and we eventually build the tree that concludes $\Gamma \vdash [e/x]e' : \tau'$ 
    - Operational Semantics
        - We want to define a grammar to find the  __value __ a program computes, this is useful because we can then evaluate our real systems and decide if they obey our operational semantics. 
        - We define a grammar of  __values, __ and a two-place relation on terms $$e \leadsto e'$$
meaning e steps to e' 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tomVW9_1wf7CaPhKzhITenWyZx_ianI0fmZQraDlzNJeY0yud0pj7iEBvJUiZc5WJ7PoVDdjSNxj4Su8BVZ2gKV4dciURe_8thAornQrF6uBr38psiqrJr8gMRH0mQoY.png) 
        - A term e is  __stuck __ if it doesn't result in a value and there are no more reduction rules that can be applied to it. Thus a program is safe if→it never gets stuck. 
        - Describe the **Progress** lemma→If a well program is well typed, then it is never stuck. E.g. If $. \vdash e:\tau$ then either e is a value or there exists some e' such that $e \leadsto e'$. (Note that the dot means that the context is empty) 
        - Describe the **Preservation **lemma→If a well typed program is not a value, then it can always take a step and maintain its type. If $. \vdash e: \tau$ and if $e \leadsto e'$ then $. \vdash e' : \tau$. 
        - How would you prove progress for ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jKdRjXh1DlDTqD2MzEv3N57E-nrBgnoFwL2E8OjF-pQnlYJT4DSipFalZssoCkeugNmoq_mJmQxNGB7Y8jfO39adWaGgACkueE9c3XDg3_qVe-JMnV-l9zmWYqcQkuP0.png)↓ ↓ 
            - We first apply induction on the first subtree, so we say $e_1$ is either a value **or **can step to e1'. E.g. $e_1 \leadsto e_1'$ 
            - Then we approach these two cases, if e1 is a value we can do substitution straight up, resulting in $\text{let }x=e_1 \text{ in } e_2 \leadsto [e_1/x]e_2$  by rule LETSTEP
            - If e1 can step to e1' then the whole let can step: $$\text{let }x=e_1 \text{ in } e_2 \leadsto \text{let }x=e_1' \text{ in } e_2$$
by rule LETCONG (see above) 
        - How would you prove preservation for: E.g. Prove the typing rule. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/x6jlctNzj_MuFuE2I9kOYoP97WgaaitS_ZcSm5X1MHyJMfHzZX1SEZi_2vYrWONnm3c4JKMTB1JEs2ZpS8O4uIjAei_KUlh3RZpNVCLk09VJtUo9vRPXVF4aJwzWDX0F.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZS5_DpxrtgiSw5-P0w3hcXhaUmwZloQKgegWDszAQh0d7KwfazvRIGGNOxqAA_GAntcnzdChNLaE7xdAqTCZL8Kq-s2IfeCYAUlOzjA6SxTUJ9Jxz7m4iPcKHdvSJAs5.png) 
        - 
- Lecture 2 - Curry-Howard Correspondence
    - Natural Deduction
        - After the advent of set theory, many proofs were almost contradictory (natural number set same size as even number set for example), thus mathematicians became worried. As a response to this, the system of natural deduction was invented - where the proof style was  __natural.__  
        - What are propositions?→They are the building blocks of propositional logic (i.e. no quantifiers like $\forall x$ or $\exists x$ ). For example T (true) is a proposition. 
$P \land Q$ is a proposition if P & Q are propositions.
$P \lor Q$ is a proposition if P & Q are propositions.
$P \supset Q$ is a proposition if P & Q are propositions. Meaning P implies Q.
$\bot$ is a proposition.
        - Some claims follow ($P \land Q \supset Q \land P$ ) and some obviously don't ($\bot \supset \top$ ). We decide which claims hold and which don't with **judgements! **Using inference rules. 
        - When does a judgement hold?→If we can build a derivation tree to the proposition under the rules of inference. 
So to prove $P \land Q$ you need to prove that P is true and Q is true, this accords to this rule:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H-wp7laj0m077FKys0UP5v6R9dePvWey2d-Z56LT5u3j70De96ehtaeGhMObaf_arDLiR_izLxbo3cHEOn9K1QtWaNtaGEaHkfStJMLLWlnZ234BALl9E7WzBWMYwhb3.png)
        - What are introduction and elimination rules?→Introduction rules tell you how to form a symbol, and elimination rules tell you how to use it.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pwMIgf9pf6KKVgcNMuQCbMRYL1N4bghVpUj7h6U_bqJlW8mBXQyYKnPj-Iur150Ch2ZL0NrgSGQu7LqUCE0EAyYzUJdgV3ZMqcjPZf4o7Tkd9KvTUS-Bb7O1WM9FX54n.png)
        - To prove P implies Q, we need to assume P and then prove Q. So our system of judgement needs to keep track of the assumptions we've made thus far.
        - What does this inference rule tell us? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/US240hjgU164wT_51TY79IK1IkPUrCBZ32fxmOt6dkOdMSq1LLItk5nlRLQpqw7PbqXHkY5V6V8tALeuiaSLWnF3j45FRHvOD6N6B800vykgOaPesSQJUVIvsT75DzFS.png)→Under the set of assumptions $\Psi$, we judge P to be true. We can judge P is true if ever you've assumed it.
        - What do these two propositional rules tell us? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5RArs7L_zGYIColZ9wvcz0MSdAsPSu27d_8BdO0rM37uWdwz-sLCvs84nGgPqRO-Yvg9eVJe2c_0nGjB0Ezrq9lZRj8xAPGdjvLLsMzqUZiB6u9yc6NS1VxVwqILiQPs.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rZkVbMufjMAH-DFM2pD9C2CwueqvBzdIkEfARZx3EMwvyhdY7qSQYerOVfLg6dYjfYPcaGZiMJ1lGA-D8xJCx0ClQTRJadR6yr0bnF1Y-yqNDOHnOniZbZSzb2m66Pxs.png)↓ ↓ 
            - The first rule tells us that if under $\Psi$ and P - Q is true, then P implies Q is true. This says that if we assume P and prove Q - then P implies Q is true. 
            - The second rule tells us that if we know P implies Q is true under $\Psi$ - and that P is true under $\Psi$, then  __we must __ conclude that Q is true.  
        - What are these type rules telling us? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vPahoJ3VDWwgx6ZaC9muzqCZJKu4BAWkHY3iSp7KzdbQpm_-4AjcxLrqlMCaX41fJqz0BxC87qM79d0ZHspSRj7FzfaW2lqS1Z_56qgdq_mjmgAvFuXJiBcYfyJSIpUV.png)―If we know P or Q is true (i.e. at least one of P, Q is true) and if R is true if either Q or P are true - then R must be true (all of this under our assumptions $\Psi$. 
        - What is this bizarre rule saying? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mEE5dsoAMUnxG3ONX1-b7Tp4rS56NniFTNh3tnNTlDppf0uBKuGpy1tFAOOvaMy-6mgOsjTKQPHUUQGDrHSHY7oQe_Tyd5zAQNX-b33Lcisb3dNI0ZCT-Az4RBldvysx.png)→If you've shown false to be true, you can prove any old shit. From false everything follows. 
        - Example derivation tree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IT85C9SNt6Oh--TJSRDj-w0lSjSBPEPCkTNIbI6oIFFo66zZggoYJCka06escjmDU_dUIi97tr2_sZqPS46jMje_a4FFvrNrZlFNyYsm4_WJjBfjf4DOndAQ0oCZpNRj.png)
    - The Typed Lambda Calculus
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-0B4YVHlM9XMHTqYsb4p08k9v7WmJVqKciQZQkpDNtsubPZxLyNRHj7euZEYUADpNqVDrdqElS0jHnVXGGqParqUE5N3v6eHFVDxB_Y3nPoycRRDGn0XZQ6Er4J--GOj.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ujHHUXBrr2qYtOFePiP-kTezfwAJNdpU4BR-rSioRJsphArc3bC7P27jWUNynVg2awrvnkdotpdTw5owuhgQMDI6bEMrjL7mISK-Rhioi7WauUnv9Gc_lPBCZkTqVe3g.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/htvHYz1UccjC2X_GitP1OfDEApJm5jpU9mTP7OIUKfUT48HG55K66ZPFl7D63ui465yl65YvOCHYGQxRKVGXAUUCfyAyP7xVLtb-u0Itb22GtAvnZsFopgCd66ODf5Hg.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MkUebWZ3KjgIPFRogLgEyy-p3_3SU8H-asNGyf7F8QnkG5r19dceqdwslS8m1pA3yi6vo9dT3thfziFMywmIMXcoijCkRa1hkf2C18UwqqgolgIL6DybDolC96_0bDbb.png) 
        - Explain this typing rule: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4Ia-dar1OvU9RmuDBxkJMk9pefGQYd8v2aSNocEdXToFHO-GSHqhWgPPL6sAxLRf2vXu8Oxl4dUAYjjN1Y5tgS2VIOUQLTqU8ykvVcc0iKDe5x5nqMXSvsLSCuFrFSGn.png)→The unit always has type unit. 
        - Explain these typing rules: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jKO1ZbbSqtq2V2KNfT8qagx6LqOXR_TEGWEJsVRszynb1FAhGyHHQR-sa6GtufaV39rgmZ0aLh32mn2IFjjqA7Db4A4rdPOWPUTMGSbHh0w-hH8iAe7_bdZFbdzZy25X.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HLIirOK_a6m_xkcst0VXoI5TEXmsWOrzcWkh2FfN4XM_Bzre-rvazheRd20qSuNMTU98f2otWoQXagruoq_bcmxdy10Xw2i8rhGmcjiVMKplcBqzuMvJqho11g95Ev0z.png)― ↓ 
            - If you have expressions and you want to form a pair, you can do that given you know the types of your pair's items.
            - Then once you have a pair, you can project out the first or second items.
        - Explain these typing rules ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Q8UspJA_ew_iEf6FIbfDi59IRdEDZANDSncByvzzR7qjxE_fWT0GwQFtOxlYzj2jCcdCHb__nDRPWFJJ3kiBF-uHB55iQ7pRi8Qa6-cKhCKvbmpaAHzOTU-8oNmvXkS4.png)↓ ↓ 
            1. If x has type X in your context, then you can take that as it's type.
            2. If result of an expression, when x is substituted with type X (added to the context), is of type Y - then we can form a lambda function taking an X and the result will be a function from type X to type Y. $X \rightarrow Y$ 
            3. If we hold a lambda function that take's X's and turns them into Y's and we pass an X - we get out a Y.
        - Explain these typing rules ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rPzdSxHx7eggRKkYEysV0HlU6KPjrnghMUwzvltABcFLrADMuz5GYaY9AACpoP2yx4-jqBuDWGbDaNgxP85R7D9grm0d2UAoSaQ1auYJgKXTcVhY3elgMgHCKUBq0FM2.png)↓ ↓ 
            1. If we hold an expression of type X, we can form a disjoint union of type X+Y - noting that the  __payload __ is on the left branch. 
            2. Similarly for Y.
            3. If we hold a disjoint union of type X+Y, and if the result of the expression when X is the payload is Z **and **if the result of the expression when Y is the payload are both Z - then when we case analyse the expression the result will be Z. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YJtsLNGCIzE6Io-uAz1o-Kb2Ct4y3xr869unk22lfna-iU2IszQm4RnsvcSXi0VLBr_zzDHN5whqHeCfWff2Sg8OQlpfk149s3LOcEYJf_hp9h11Im8TFEP3FYmXQNNM.png) If we ever form the empty type, we know we're in some kind of dead code - and we can form any type we like and abort.
    - The Curry-Howard Correspondence
        - States that any idea in programming has a corresponding one in logic and vice versa: Discovered in **1958** and **1969**
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/u9gFcqZtl05LlbZ7_MpIjShxxkun60MvEvIqdOeVYl5BMokLjDxInFB3ido0DC2gbDH3u2_g0n_Ncha08vEllbetGvFwaY4s4f2QueVkq0VPpW3Ls04sel5deZE2scHM.png) 
        - In programming you can run a program, so if we have this correspondence between proofs and programs -  __what does it mean to run a program?__  
        - Rules for evaluating the typed lambda calculus: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mearLg0TbHj13QFvtQEov6MiQ0_BwArofOfplOi4hNIsMh8VAdOLTCcUeBd6Odihg0dfAnG3-o7a6Z16XAx4ORv99TU_vz70XkqH-c9CQtL2LyQR4fkph5_QBPbnnJ1c.png)
        - Voids and sums rules:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9U71fOKb8jvjUGJ2hdYHylQwvu_ypRJuKktCbvFnzB8tYANxV4o2ve_oEE-h0-tetafx4wuLs3S_vwzDvsDwdnFHRFl5JC3MPapf3tpR83zLu2xwFivYTQWNRdhQ-jGq.png)
        - Finally functions:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yKL8JDgjLMAQa38m0ezDjqGBU1QZVg2Oo4BIy-AwM1OXiHDQxhhhZOGdvRaVm9x-vmeeh7Z0WyxzvOgOyeHf8Z5G2IEpH_1dIY7_XlAcXadw7v7Jmplcp-ePG0bfzNkb.png) 
        - Note that in the lambda calculus, expressions are evaluated from {{left-to-right}}.
        - What are  __congruence rules __ and  __reduction rules__ ? ↓ 
            - Congruence rules are rules in which no actual work is done, they simply tell you where to perform the calculation. **Controls evaluation order** 
            - Reduction rules are rules where some actual work is done. **Actually do the evaluation!** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wnPmR8W9CLXMVM8o2sJorvnJSW_SFzX-jOTQz_F-S_9UZRghecrdpAIjHWdZvcs3lcuZAuhmqq8G_tjDjDoU-2ZQS5b7T7FHhB2zWCP9CZC1BswQYxLGkehY0cFvXNqQ.png) 
        - In the case of function reduction:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PGtcJ3uRTGRiNzDnNYF6ZnL5Qj7DYNLXuiVTOwDHPX_lhvAcOGMCDCTsoLCJ8PkybZ6nPGAiyvQsKR4jeGTRE2BCvRnDWqU0CbNUw0y4_eJ1xZCEI7rO2mE8wJmD_Uts.png)
Note that in this typing sequence, we first introduce the lambda and then **immediately **eliminate it. In the reduction relation, we immediately go from the statement to the substitution - removing this **detour**.
        - Every reduction is just such an {{introduction }}followed by an {{eliminator}} . We want to eliminate detours.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CqZ0wwB91YKN5OrWeqEjwbFho8E4MXzbUzuC1iaPM8-NYw0LJGP2dvmyF46ZjdFAOG-r52EMJErZu-HMxiWXwRr_bdBmPknuqFXXw0MjxwN25wPiloDSQMaFGakNFLDp.png) 
        - The values are introduction forms that  __cannot be reduced, __ the process of program evaluation converts an initially complex expression into a normal form of irreducible values. 
Which normal form you get depends on evaluation order.
According to this, what would be the curry howard equivalents of Value, Evaluation and Evaluation Order? ↓ 
            - Values are Normal forms
            - Evaluation would be proof normalization
            - Evaluation order would be Normalization strategy
- Lecture 3 - Consistency & Termination
    - Logical consistency
        - What does it mean for a system to be logically consistent?→There are no proofs of $\bot$. Otherwise we can prove anything, the equivalent in lambda calculus being if we prove the nullary type we can prove anything - $. \vdash e : 0 \implies . \vdash abort(e) : X$ 
        - Note that there are no types with the null type - this in tandem with type safety (Progress and type preservation) means ↓ 
            - Progress (a well-typed expression is either a value or it can take a step) implies that (as no value has null-type) that a null-typed expression must always take a step.
            - Preservation (the type is preserved in a well-typed expression after stepping) means that the null expression will always step to another null expression.
            - Combining the two means that a null-typed expression will loop forever.
    - Proving $. \vdash e : X$ then there is a value $v$ s.t $e \leadsto^* v$ 
        - I.e. prove that every program terminates - to prove there are no closed term of null type.
        - Why does this naïve proof not work in the final step?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iBy-8cMTcej6hyHQ827QDcRjwDqvUk-mFTLrGTi9otnGd_33cH35Wdub48ujH2mLgRx1XpqnNbmz6KYJmwVF5FxRjWO_Oio6QrTjuihb_lGViARacpKR00IG3CIKjxlW.png)→Because you cannot do structural induction when the expression can grow larger than your initial expression (Consider substituting (1,2) into ((x,x), (x,x)) ). We can't do induction on the final expression $. \vdash [v' /x]e'':Y$
The Problem is that knowing a term evaluates to a function tells us nothing about whether that function terminates when given a value! We would need a stronger induction hypothesis
        - A minimal typed lambda calculus:
 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3SiqLFoCAb_tnm2cd8-Va1Xt5E4BhVIjuaomjAM36dQYvEenlsoNrdv5JWAdMoLI-Gwcoi9u_1rqQYSEGXEUNhoVIIxFl9cIoWDRpX6UPo6yhavg16Y5Lg0ZhGGniHh9.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/arYE19Ua-9dZ5qt_9JSSmUbkjMZ7YWTUa-pJn3_k5Ze80_FXUlb9c49f9r7OTtnKG3hXRG_PlPwtkAyokldvjQ52KKXrIs2zrsZaLQHpJuMBiJZ47CdfWMtN9Jngph3T.png) 
        - What does it mean to prove determinacy?→t means we've proved: if $e \leadsto e'$ and $e \leadsto e''$ then $e' = e''$ 
        - A Logical Relation
            1. We say that $\underline{﻿e \text{ halts}}$ if $e \leadsto^* v$. 
            2. We then define a type-index family of set of terms (Remember our simplified lambda calculus only has 1, 0 and $X \rightarrow Y$ for types):

                - $\text{Halt}_0 = \empty$ - there are no expressions which do not halt
                - $e \in \text{Halt}_1$ - e is in Halt1 just when e halts 
                - $e \in \text{Halt}_{X \rightarrow Y}$ - when would this hold? ↓ 
                    - If e halts
                    - And for all t (Which we're going to sub in), if $t \in \text{Halt}_X$ then $(e \ t) \in \text{Halt}_Y$ 
            3. These definitions give us that
$\text{Halt}_1$ halts
$\text{Halt}_{1 \rightarrow 1}$ preserves the property of halting
$\text{Halt}_{(1\rightarrow1) \rightarrow(1\rightarrow1)}$ preserves the property of preserving the property of halting
        - We have now transformed our proof using these logical relations to - $. \vdash e : X \implies e \in \text{Halt}_X$  
        - Proving Closure
            - We first prove that if $e \leadsto e'$ then $e' \in \text{Halt}_X$ iff $e \in \text{Halt}_x$. I.e. we want to prove the halting relation is closed under induction. 
                - Explain this proof of closure line by line
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/C1rO07JGsuyxzvB4pVBg2h6OEizDiDObswonxGZWsi-dozFTgbpxJbVBEB1B8hsj2hqhmWXB_4khOQbanA4xVQOwRVxdrHJ-0zJuJaJr3y2PoIiACTZyTBfjNBa6SIuJ.png)↓ ↓ 
                    1. TODO TODO
                - Explain this proof of closure line by line  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/or3sP3DZxlHQugqsuJl1BTb4xiCiJkF4GDtY75Z799BuaUWq6dk1SF8nTj5cBgbCNL-cWmAqNeGPz0X8E_z9gKmDEJoiSO0ioqJDlpsapQk11ui9Cce0p6EeeC2V8uk-.png)↓ ↓ 
                    1. We assume e steps to e' as it's in our proof statement
                    2. We then assume e' is in Halt$_{Y \rightarrow Z}$ because we are proving the implication from left to right - and we assume the left side of implications then prove the right. 
                    3. We know e' steps to a value by the definition of Halt$_{Y\rightarrow Z}$ 
                    4. Similarly we know that for all expressions in Halt$_{Y}$, substituting into types in Halt$_{Y\rightarrow Z}$ will result in a type Halt$_{Z}$. 
                    5. We know e steps to v, because e' steps to v in n steps - so e must step to v in n+1 steps by transitive closure.
**We then assume t is in Halt Y**
                    6. To evaluate e t, we would first evaluate e which would give e' t - therefore $e \ t \leadsto e' \ t$ by congruence. (He doesn't explain what he means by congruence)
                    7. We know this holds for e' t by 4 and 2. By induction (because Z is a smaller case) we have that if e t ⇒ e' t and e' t in HaltZ then e t in HaltZ
                    8. We already have this
                    9. By definition of halt Y⇒Z
            - Proving the Fundamental Lemma
                - What does the fundamental lemma actually tell you?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EhpEF7881cNYyPj3-6oyGFhbX7TTOG_ZoAUdfolDUDI7w5xUUNY8RKO886PRXKtu93SVSF5HJNU5Js8L4MpZnL3BnLTHR89yWHiXbHmT35Kmp6SxVH-sl-sqaJTOH_Tz.png)→For every well typed term, if you sub in a bunch of terms that are well typed and halt - the result will be in the halting relation. 
                - Explain this structural induction proof of the fundamental lemma:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yu_nSbgixqmIw9jwCfQYrvy_4Plv-6ZTAKq_J2kaifV4iaSkxA4FO2oOTY2CKlKf02I8b5JXQU9o2Et9lsQmRGT4fQbsc_hlpDRRgo8juyp-7YNyXb9OsrajTayaA8Yj.png)↓ ↓ 
                    - NOTE: The arrow means from 1 to n.
                    1. We assume the **overall rule!** 
                    2. Just sub in all the values and we'll get out the one we want
                    3. This is on the left hand side of the implication in the fundamental lemma
                    4. We know $v_j$ halts, and we know it's equal by 2. 
                - Explain this structural induction proof of the fundamental lemma:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vI1md1UhWH7jtCxrUF0NBK014MsK5jpslmc7s_Jp58nND_nA7Yvrs6lC-FqQUs6oLQWJjzU1uhzyKXzSb8-13oMmBCwmZqbQBlFlpl3WT322cX2vOcIftRg0VuKR5MxD.png)↓ ↓ 
                    1. TODO TODO
                - 
- Lecture 4 - Datatypes & Polymorphism
    - Representing basic data types
        - So far we've talked about sum and product types, this is enough to represent basic datatypes
        - Boolean
            - How would you encode Booleans with lambda calculus sums & product types?→We use tagged unions (sums), where left is true and right is false - So $\text{If e then e' else e''}$ becomes:
case(e, L_ ⇒ e', R_ ⇒ e'') 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ND0VXDiUwixx9ux4IFCIG2U67SG67V_yMCI__el4OjYAPKMlRkkjDlZdR21mur0_WhU2TfojndFtM0bS0joMupn41WCvEQ03bwTPs1RvZtcsuUsZdEq7EhCDPlehIkSN.png) 
        - Characters
            - Using these Booleans, we can bundle multiple of them into a product to form characters: (true, false, false, false, false, false, true): 'A'
            - This gives us a representation of data, the ability to do conditional branches on data and functional abstraction on operations. **However**, we  __don't have the ability to do loops.__  
    - Adding Looping
        - The simplest way to add looping, is using recursion
            - Explain what these rules are saying:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6YHDFKWN_1vXRD2wQC-XxcRRfXhV58C5nCUf-9sI-2Me6DtlEvHXGPZJ5SJCJlHVA-7junCoYh-2ChWocx3Lq9ahbd4h9nDZ9DEzR5KCm8ZquaHxFbRbQlPX6RQZveub.png)↓ ↓ 
                1. If you have a function of type X⇒Y ( you need to have it in your hand now, because you may use it in the body of the function), a variable of type X and an expression of type Y - you can bundle that into a function.
                2. First evaluate the argument.
                3. Then if the argument is a value, sub that value into x - **then **to allow for recursion we substitute the whole lambda expression in for the variable f! 
So all the recursive function is doing, is subbing v into the expression  __and then subbing itself into e as well!__ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/G89dsPp44V-MOrP4X6vEQxr55ibC9SiGqpeOXCCct6fYdNdjjCCPm1vbZbn13wKY8OS3fFKd14Z1459Un0X5CUUVQ3Ryr72Z-lHz6w7nwK3fCYSL5iMYYh0CQW0oEw9j.png) 
    - Bounded recursion
        - What if we only had for loops? We do something similar, by adding numbers that will ensure termination
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8b8JpsGf-nYG2MceI7INhwz0rFxUP1qFdvhiNVFi-N1yTWC9ECILmi83QrTjAXHInoI_r3dIphY3lQnJ7gck-_YsYSHQ7gbVp7pEpIK-d7SLVrNfY2SH017XKLPLOqyz.png) 
        - Write code to simulate the iter rule, what other functional programming idea does this resemble? ↓ 
            - ```python
# Here we'll define the natural numbers as the normal number scheme - as opposed to s(s(s(Z)))

def iter(n, e1, e2):
	if n == 1:
		return e1
	else:
		return e2 (iter(n-1, e1, e2))
``` 
            - This is like folding over a number! Think of it thusly: 
iter(n, e1, e2) just says apply e2  __n times__  to e1
        - Using iter, we can build things like:
            - Sum: iter(5, e1, s(x) ⇒ s(x)) = 5 + e1. We just apply the successor 5 times to x 
            - Product: iter(5, e1, s(x) ⇒ 10 + x) = 10 + 10+ 10+ 10+ 10 = 5*10. E.g. apply + 10 5 times to x
            - power: iter(5, e1, s(x) ⇒ 10*x = 10*10*10*10*10 = $10^5$. E.g. multiple 10 with itself 5 times 
    - Data Structures: Lists
        - What does listfold say?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/f76GCTUSo-TdTp1IgXycZQrS0P0zXQfGZxU-gLB3Q_QN7njiXc2IOOVhlgyCeJ-m4NTgNTdHzHtOVPFuIJlgcJRpjipDoM1MXuF0x7d-x_jS_UGZ3FQxdWPqW4cifRMs.png)→If you have a list in your hand, an expression to return once you get to the empty list, and an expression which can take r and x (which is the tail of the list) and return Z - then you can fold over your list.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tFm29AYxstSWs_l9azfDQZ-ZsILRKewi6uQsH0v-dPLY0i9V9CAWMkllaRI3D8jiQwldOiI-1CtGqZPIQHAOCXXVDIBK8Ng7KtKHFtcOZQ7Y6_-Lt4aMFcUme1VdxhlO.png) 
        - How would you append two lists using fold?→$$\lambda xs. \ \lambda ys. \text{concat} (xs, [] \rightarrow ys, r::x \rightarrow r:: x )$$
If we're concatenating [1,2,3] with [4,5,6] this will result in:
$$1::2::3::[4,5,6] = [1,2,3,4,5,6]$$ 
        - How would you map a function over a list using fold→$$\lambda f. \ \lambda xs. \ \text{fold}(xs, [] \rightarrow [], x ::r \rightarrow f(x) :: r)$$
For [1,2,3] this results in $$f(1)::f(2)::f(3)::[] = [f(1),f(2), f(3)]$$  
    - A logical perversity
        - The Curry-howard correspondence tells us to think of types as propositions. But what logical propositions do $\N$ or list X correspond to?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ReKKgOhVVavj6tzw1qmoyqThWmq78YH4rxlW0H_RTX4vQVjA1gNcJZnM5Wa46xeRYXWtNFkzHDoZBbmxzzhyg_c-xEoKcjyp1idOI5ctJMPxhyAt74mqJ9MLR8GmkyzJ.png)
    - A Practical Perversity
        - For our definition of map, we know how to go from a list X to a list Y. However, when writing programs we must re-define map for each pair of types. This is incredibly annoying
    - The polymorphic lambda calculus
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dde_zb95_h1MFa_AEvWpg0cfMFIrqTWBcwoyPLz5Nyr1zPIdzAeH6VvgS-FzaCxEB50x2VAqdgSTre3_q28v39tSGNnPUnzMlCVdqnwsLXpdlBQAfWa0KrASK70t3zsw.png)How would you use the $\forall \alpha.A$ to define polymorphic mapping?→You create a function that has the type $\forall \alpha. \ \forall \beta. \ (\alpha \rightarrow \beta) \rightarrow  \ \text{list}\  \alpha \rightarrow \text{list}\  \beta$ 
        - Well-formedness of types
            - What are these rules saying?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iLz4Tqz4msBwIvKqEFWDHcb68-n14gr3MA2xggI6_m4oVAWKAPo2ejpkfkCRcsw6taPKOC3EffzADgngfcsh43wnlcs_JJLE36Ih2n7GqstlY6DMDZd1kk9i-h-wYeg_.png) ↓ 
                - Type contexts are a list of available type variables.
                - Alpha is a well formed type if it's in the typing context.
                - If A and B are well formed in B then so is A ⇒ B
                - For all $\alpha$ A is well formed in $\Theta$, if A is well formed in $\Theta$** augmented with **$\bold{\alpha}$ 
                - Note that because types can have a free variable, we're checking if the type is well scoped!
        - Well-formedness of term contexts
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sdYcRjaYR_HOF-egREBaE6rWg6tUW_DJd5GPoaIc7RdaA5R8Br4R6S7brcfFV8fkfoQvSZRQJ12MOtkRLnFSQxHAz2W4UzLg-lZwpia-Rc6jzhhf19yum8PG3aGYuyMb.png) 
            - Checking that all the types that appear in the term variable contexts are well formed.→TODO make flashcard 
        - Typing for system F
            - Explain these typing rules![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T17jUN9t5py-G9jrk1cAv-x5PXYzXE2Hc0Egktb5h3uYjD-6v00ugM7z-xzTxMExUOANB1KjQkL_jDL4meJ_N9G00TqBh8sLbb0GMKKi6Xo6T7RgpTTgtUQpPlcWzrMl.png)↓ ↓ 
                1. If x is in the context, run with it brother
                2. If A is well formed in $\Theta$ and if e with x subbed in results in a B - you can form yourself a lambda function son. 
                3. You can apply functions if you're holding the right type of input and the right type of function.
                4. Introducing the forall type: The big lambda $\alpha.e$ has type $\forall \alpha. \beta$ when e has the type B under the additional assumption that $\alpha$ is a free type variable. Meaning we can add variables to gamma that refer to $\alpha$ 
                5. If you have a forall, and you know A is a well formed type - then you can do a type application! We sub in A for alpha **in the type! **This is not in the body of the expression itself! 
        - Proving type safety
            - Now because we have implemented substitution of types, we have to prove type weakening, type exchange and type substitution.
            - What does type weakening say?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4jq3ED2SonNoHulGfNsuOfkJdI2y9UicJhKlINKtc_sxW6XqwiCuSf5O45MsjNC8pc8xU_58lek1DHD_32XHpQqBksj7LNC2Z_uqFv3Yic71090nXc5oxBgmQlPr9u4w.png)
We can add any old type to the definition, doesn't affect anything 
            - What does type exchange say?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NgIjB7LXPkVcqqGEaVG2HaoOhBYZqeiOszNjXnbt9xwE7qvD-ES-CjSX_mhl_Pg4sNSskS5mcZigeE-pALqjq3q3Kk0Mt9cISZXXDZsYMntrNUO3uaK9snsaqKA5ia7R.png)
We can switch types around in the type context - makes no difference. 
            - What does type substitution say?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YqElk5G0ulivnLy-BmXCx5BkU-zwLcs8Hm96t2l-NCqwNoDQBV4gOEmcb7vEwQFaLGXj08FLuenMJUNySfl2pXzY1DBvGsQEcR0_P6mN3AC8XL0ECdjWhWwdMHECj1cv.png)
If A is well typed, we can sub it in for alpha in the B type. 
            - Make flashcards for ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uF1O0FhaZeGMJLRsfGOFE6czyW2YwJxYZu-IDE0EPbgArkK8SpW0daMKBJ0BzA-4MNK7RUjvc_GWG_ZFSYkkzKqFYWz0AW71SgKrNcp4AhrV_hYkemG_HcA2eNJ1x7h9.png)→TODO 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/knxkmNg8nTxZHzMzsuv3GYXMFPJY4X1uxPEsEzPnRF_E4qGFrsqN9o7vKU93dYeQlaLbG2jPD1DOu0nXnc-xHGgZHVGpn6vdoT_aNRGTUU0DhPU2Zcf8wrE-9WT5uTBI.png)→TODO make flashcards for this 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Z2Iw17ZMlLpSk4vla_K6MxzSupiy_eS2KIrZpOeHJ8OhHuRFyKbjnFRNc1dFJu-efUmDZcMrqZHK195GpTYVL4HPv0zRMYytPrudbvHzer1EGrhzMCT8Mq0af4IFBsd_.png)→TODO make flashcard 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ciz9p9mqRvg8Qz-cbQCtclRXElEe-BfmUDrP6HaGc31pb_ZXgzGD6XaphYyenup5Enr-ZD8PL6XRTWIpx4FeR60N90SW8ny2eAlSCWGd8OwR5NFyA66DSVjAzhu7_O6H.png)→TODO MAKE FALSHRACARD 
        - Conclusion
            - Where did the data go in Sytem F? No sums, products etc.
            - 
- Lecture 5 - System F and Church encodings
    - The polymorphic Lambda Calculus
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KfJp3TvqdczuwbfA3TM2RxT8qWE681EMBzN10LFAkPGb5z8x81jbImdyoy4gEm_8NpkqsmcsPn5KKUx2VpWYL4v3C-FcHuokcyPIuyzcws4hxS_MZeO1IXc2184irdIk.png) 
        - What do these rules mean?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/49bVUSzxROQBvR0g15tzkyolYBCr0qL4bztGyJIFy7SBg77p_4vRGt0nSO_W3zQZRUKHMZL39FIpvv2Js5IpbgDezv9tth5C1XmaqK28ZSBzw7SyeGBlfb7rvF1LEUva.png) ↓ 
            1. If $\alpha$ is in the typing context, then $\alpha$ has some type 
            2. If A and B are well formed with respect to $\Theta$, then $A \rightarrow B$ is also well formed w.r.t $\Theta$ 
            3. If A has a certain type under the context $\Theta, \alpha$ then for all $\alpha$ A will have that type. Checking if the type variables are all well scoped.
        - What do these rules mean? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zHLp-pf9zsOKtk81JTJiRSifpw1b4y6U6p6Th8fpSOLuxbKVLzr5hrr9FfHXuDym5RWgkTxAYdbsH6u-r7FZB3xcSJzQNHYTwN7tnhx5IompAWFvvts4-74SZcE42P3f.png) ↓ 
            1. We can instantiate the empty context from an empty $\Theta$. 
            2. If $\Gamma$ and A are well formed under $\Theta$ (as a context and type respectively) then the context with A added is also well formed. 
We need this now because types have a well-formedness condition.  
        - Describe these rules![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i0q5lHrIPLM_32u1Q6681h3yAFcv_V-bUDitb42n5ysEodTy9w-jDMG8cCWTg7-_YauPku_KdLWjVmbM_HNje_cwAmwarKB3pHT3T8sqFm-12PqUnLeSXGHTh2j_kTd7.png) ↓ 
            1. If A well formed under $\Theta$ and e has type B under $\Gamma$ (and $\Gamma$ is well formed under $\Theta$) then we can instantiate a lambda function as normal. 
This is like checking that the progr ammer has put a real type in for A. 
            2. Normal application, while ensuring $\Gamma$ is well formed 
            3. If e has typed B with $\alpha$ included - then when can introduce $\alpha$ with $\land \alpha$ meaning for all alpha. This is a way of binding $\alpha$ to the scope of e.  
            4. If we have an e where for all $\alpha$ it's of type B (for example, for any type of list - counting that list will return an integer) we can substitute that A for $\alpha$ and get the fine grained type of B. 
        - What two value types are there in the polymorphic lambda calculus (one is new)→$$\lambda x:t. e$$
and  $$\bold{\land} \alpha .e$$
These are values because there are times when they evaluate to anything on their own - they need help from outside. I.e. they need to be passed something. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KByNV8OFOhhOq6XiBrHOqwNT5W85Y0MYK23q2KMos3FN91s1DO5ncgHQhcJAW1E7UX0xmSdKJ4Mr1Nmb27byUzG08Vn4_wtPUAKf9Vj7cLEWqPI16fjHwIRJ3Jmv-1jF.png) 
        - What is $\land \alpha .e$?→This is a term. It's an expression which you can substitute in to replace $\alpha$. I.e. $(\land \alpha .e) A \rightarrow [A/\alpha]e$. 
It's the **equivalent for lambda **for types - it's even called lambda. 
        - What is **type **weakening and **context **weaking?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/THqQHqZLq0x4u0HDU7Jg14U8fa6myB6eXfzqC3iw5BhxMAlou9BBQ0aCDF1U5F_xhXYH0kxFjIfX4QnsbdvPliOEIquXGDQB1XxRP97J9dwk1hhhOQWGIIJGGaavqtRJ.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r8V7IfQi3OvxnB0VIKVe4yJzyyeoKalkf8m0m7hSYisy-zzPqtDLYLAReVAubOTHzMeFhlFuH5a9zEe4kMX2s8qrPxwGvPlEWKq_2DnP4Rbvxw4XT37QiMwoDsXYFsKF.png) 
        - What is **type **Exchange and **context **Exchange?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D9z-9MIZPdqxJ06snhArOzIikdTpVPjQ1Ibn3XkZwwtDSezPxslLQGNJACPLQZxVU_8vTZJAhfqabMndKG2vj1YEdJONhI1jbMrpnmiatCEhW6M938dJkcFpyEvA9ZoI.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/M3MsTL5aPWTT9yGx86wj805h1xEp0en7q7xg6HXZXjmtQvFwgnHOTwxl_djsmJlZa8Y8BL64dd13p2Pb2d0CZrAFLVHSVnVOzKzad2zLEMJ33z4WJgGwWnr7kuef0XcW.png) 
        - What is **type **substitution and **context **substitution?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U62u-4iBUAA8HUBcTpa_YNmlHh-12X4xaww-gn6YslZirDB26n2JptBq0gaZIa0KNz-G2GGt_mmGAbUelldhgCqeyeZdYX31p9p0dApMDW19q6ChHqt0LC5vHJR2ChmS.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eVkAdPzA-PabHH1NPNev8EfyiLJ3T2kGyqJXrDI-SqePeEZ3ytfwZ6L5eEZpt-5ebFbtR5GfHiSUyG8AuxpQulGoQdJrD5x9SnPoB_oDOnyI0xJL3NjEmb8nqcyRR9k5.png)
(note the $\Gamma$ should say ctx - typo) 
        - What is the regularity of typing?→Basically, if the context is well formed - then any type that is well formed under the context will be a well formed type under $\Theta$
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UXTW1vAEFCUqjADQr7b_7IyU3bxbRC-N38BDFwfGJepbO0k19O9wYMTcgT-rIJC34pYPe7fYxDUFzVlduAi1S8ghRepyPP7E5Ys2xmlYWQQqOGDlteZsequt2pyYD06v.png)
You prove this by induction on the derivation of $\Theta; \Gamma \vdash e:A$ 
        - Prove regularity for the typing rule
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qrBZSjkzGO4WT_f8lfUIZpaGN5H7V2SI86TlLMB0CvUvoObA3Ns18lmkex0-R0sMqFJcLxnB1doDrz3JRYsGnEfAVrXXb_yurFSEy82pk9DIkoaCxXSX8XvnyBx3sCxY.png)↓ ↓ 
            1. Assume $\Theta; \Gamma \vdash e : \forall \alpha .B$ 
            2. Assume $\Theta \vdash A \ \text{type}$ 
            3. By induction on (1), $\Theta \vdash \forall \alpha.B$ 
            4. By inversion on (3): $\Theta , \alpha \vdash B$ 
Using: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lo_iPjp1a-WIxPRKaREEHqukrgbQ17_uB6AXNourU30iP52axzki70i6bZ5-NWZw3ePJ94Iw2SLJIWKwLzvOxln8wd0f9S972Ku02CkcNdvoiw_x-Ik5JLSlh5jC7ZH5.png)
            5. From type substitution on (2) and (4): $$\Theta \vdash [A/\alpha]B \text{ type}$$ 
        - Prove regularity for  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/msMJdK0tyUayqEpBGQ0HEkNYV3AAkrG5H4J0AmijCAz-pYvCMQ9C5kzmpKTSX4noxiwaakwq2efyCg4YZszHk-WUTuihznIl1e74lhIT1u6791hUFXWUwA5HjS3fKlym.png)→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cV3MxlPkKZ8DERl1r4x_JMIxX3seAMl8NnVce_wHmsd5lADLsXPprsg_m5nGZFL74ZSxfQfotejsqFcOt6r71aRw3PAIo6CvB_9-2th5Jcrf9Y_TgQnI6t4tHhq3dSs0.png) 
We need to show that $\Theta, \alpha \vdash \Gamma \text{ ctx}$ before we can use the induction hypothesis!
    - Church encodings: Representing data with functions
        - How are true and false encoded in church encodings and why? ↓ 
            - Church wanted some way of saying if X then e else e1 - to do this he said Booleans were functions that take two types and return the second ones. E.g. $\forall \alpha . \alpha \rightarrow \alpha \rightarrow \alpha$ 
            - True takes two arguments and returns the first one, false takes two arguments and returns the second
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XlKk_4biAZFIKHmJSNXmLH0IxumyWnoKZCMnd_Ll3UlJjMJwmEpk2IEAtT2dbWSmHF4uPBz5Otte4z_jexbyOR88Q8a65TRBTqIiMWhddmMRaSJ4wpiYOBNhYznbgg4v.png)
            - Then when we have an if:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gX2-NIGE5Y6_03TFA1hmkS_WHBbBcBxvZc13SAX94P3aV3cDxx6V8ALGmCKoGIkLhkfmVmNes4YK4lER-rIz8YRCaOsxvEzlnOBWF6UEWWK-uzQRL1t3Bm5Q9T-FdY4K.png)
If e evaluates to True, then the e' pops out - and if it evaluates to False then e'' pops out as we wanted. The X is subbing a type X in for $\alpha$ - this allows us to do an if then else over any type!
        - How are pairs encoded in church encodings? ↓ 
            - We use the intuition that if we have a pair, I'm allowed to use either value:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tIsKoqo7OvGX0oq5ZXUU42VXIziMiKcTrlhpVUewuHEp63qjE3voo6K9DrxR02113Ukf_GkfEJRgDbW3_ZJfFiUF3XApmFe9UenglzlnZJFRGjdFq3Dau5QTIJncZZ6J.png)
So our pair type takes a function, and applies that function to two expressions that it holds - e and e' are the elements of our pair. 
            - Then fst extracts out the first expression.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SvrHjCd4tGd8VV9l3r5Q5pCeshrGEkDfS0TH7ZtgkO_LhuyXamqPqLKR9KfOi6hXWa2gP-A8V4gVKeaKiXFOMy31XpblYEeAGVXT0c-WxHJKSYvMuAxRI4XWd36UpvyN.png) 
            - And snd extracts the second.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LhIf7kB1DTIqIrdZAo9EF7jpu63l7miyvqqQ1flnBZak0GzBLe_HNrgQTz0FkpjVIrVcRL_GdpP1JHeqm8zJDXxzW03bI69Usx_7n-CGYKP4iF6l3PTcug3Qifpirrqb.png) 
        - How are Sums encoded in church encodings? ↓ 
            - We use the intuition that case matching should return either the first or second component depending on if e is an Le or a Re
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/50oS5Iua5H60y_XVXqlp5M36qXvLUWKR8mJ1XvduSVhiOx7HznQKrvhBHbbz-r0seYMPDqZ8UCHH0iNHImfNpxl1UL2WefCKfQBYccrsahMFmGNvXUOXo6y7pdvBnWh7.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XI9NZEXghGzTLtMlgTEIItlNSHbczJ0famnmVkz5xBQOZkiBJgLzkHH7RJunx6h1IbZPm3wH1xTywA229obZVT4aZiJbmkGhuBpBdT4G-qNoJwioqeVsfRXGjf8IxeYV.png) 
            - So an Le type should take two functions, and as it knows it's an Le it should return the first with e as argument to e1!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VHjypwyK7ejOxXjnX9IwW62bz0m_i5FYYLQ0Arvh4LKuYBkikaH7htzIoPQZChxKHQZRvyDdhrH_wBw6gpTQ5OoiAVyyQx2FVTRz3PpU-_EHQP4UHw9QwNpgCRLyrrY1.png) 
            - Similarly for Re - will end up with $[e/x]e_2$
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uooNfFOUYL63dnGFbPegsUwEq13lYkVywAT3FoUcZdLNXo9xjERur1OnaCLosz7dNMX6vW-b2Yh2xKfDeAqjBXW_aWoPcXx3dtLuypjFpeYrwtTaA6d_5hHVJpRxn7HK.png) 
        - How are natural numbers encoded in the lambda calculus? ↓ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fJMxQzqczsxy0IWaPwvRkyxocGyxF1_IJ-_wjCu5lPdEsMkDGVkJPZ4RaSUWnB3gejBlrvGkKUvO2DTGnr5yxevAxaLONZ_BSi3UwWaH11vBnqNQw861X_3zVU1YH_IN.png)
 The zero type just takes it's input, takes another function and spits out it's initial input.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mKpE6QXaDJjOsATjxlZtJNlLYcNTbQzNMl_Np0WhrEShHNtami4am06pFQSwDeDoJNdKc3K8D93XBOQSgAAOY627LmLP49ZDx3QQ-lGGj-zV9QoJ5ZmJ3rv7zHL6GOLB.png) 
The successor 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZzTu-PhW_oRZIBYWmc-ehXLeu-8E78LIIf6lS8nKPCDDvgCpUPE02E46_jCGvjjza0cRwAMsH4m1Hsp43gBjFlAyewkfC8ixUbsFX7VipSAjr2JbYTDtBkwOHgWiyKJ8.png)
 DONT GET THIS
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/C2C_eRu-ieBeDxNJL2umP6Im4T1zMlhR1EFHaiRo0qTVwsP9Op_fMt12Wb2orDQrdAwTS8DGrPineSu7QkIKrxsQRZs003vZ-xHBJNgqswWCMQ2olSokz2sFRFSUC6qk.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lB5B-5DqydLOTHnhBjXrbN62ejcpnHIPFk2R7cjulP-8gdPJGSorLcDj8QsZB_hDDT8GTkLvhENvajgwv9TtOPUhzr1QtK9LTa_8EkRALCx73ZvHhXpyfPOnauFSqqbz.png) 
        - How do you encode lists with church encoding? ↓ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d79PdggIYp3Z0LPWpOc72YpF4dxmpVtItJwx9UwFMSQTOKPvrir20oLJOrUk2JHrj6CnJ19qLGmvZbZaa-vEct7Yh9itLWETUjjeq_iC6A3hZfCs5aEnpZiD012UyH5v.png) 
            - TODO TODO
    - 
- Lecture 6 - Existentials, Data Abstraction and Termination for System F 
    - Different implementations of booleans
        - Example ML module signature:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Hh1D4yFWFU6aipr960BWVvkFTkG3SsI_NlwVTRvk8wDrKVjTM8_mjsWtJ4akZLsdGO8FgjcW9xxDgoMCGF9URmOsRtHpXgdkLV0BjExbcmvsEdcG0hN-k3opZoCFD_V2.png)
For this abstract type we need a type to store, a yes function and a no function (which returns said type) and a choose type which takes
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2UR8RQRNEoLRs5HIrz6qd6sGESAHM6FGHKF6cD07W_i4s46qZACWDFVohrkJuVUIApMRDXAK7pGZjmjEQmv_B7Fi1lxS88_UKB3SWRIh5OyvnpHMYE3qA_i8wurEO6t0.png)
When we instantiate this signature, we set t to the unit - then we use choose to decide what to do when we're faced with a Some() or a None. Implemented using pattern matching.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c_4PxvCXT7ZevOBSDCctvGV4NhnsHrvbAaXPiU-7SXt23TE_kTv13dBR8XV13oX8MHjI_CR-vqIfmWMWn_iDyCwS6kIVeViCSUiUlMcjHggWMG6VkkYDHMZ8oQcTK7kg.png) 
        - With all these implementations, we're just checking for a value and doing something depending on it's value. From a clients point of view there is no difference because **we get the same behaviour! **
        - Whether we do M1.choose M1.no 1 2 or M2.choose M2.no 1 2 - the output will always be 2. 
And you can't do something like M2.choose 1 1 2 because that's a **different type **the integer is not wrapped up the same as the M2.no 
        - We choose a concrete implementation of an abstract type and implement the interface in terms of that abstract type.
    - Abstract Data Types in System F
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fcmw58aP4yCqUjWSCTFtHMhS0Md05iLU2WX9W-nvrBq02oWPjXzMJyxPrpj52bAskCEHQkWkp5d7SaP7ZzrPuIUb96yOO2mP2Kp0veiuy9HnExfObETswpnjxv4RYMPv.png) Explain these rules and new additions ↓ 
            - $\exists \alpha .A$ is the type of our module, $\alpha$ is the hidden implementation type and A is the body of the module.
            - For rule 1, if we want a module of type B with the hidden implementation type $\alpha$ we need a body of type B when $\alpha$ is replaced with the concrete representation type A - i.e. we implement the operations of the interface depending on the concrete representation.
            - For rule 2, we already have a module so how can we use it?
So if I have a module, I'll get out an alpha and some access to the implementation (x). 
To do this, we have to type check that e is a module, that** e' with that implementation x included comes out with C** and that C is a type.

        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4asiV9S7CBIc4UsJOTy5ZXUu5U2gq8l8gWhx7Tt6UhQVfvaNppTlYeCsqgaN4leRNr0OJ-J01Ib73CZyH4LhFmDZi3tB0p_RHttJmkG9Kznsl7bRezVM3957eevAvQaE.png)
Once everything's reduced down to type, substitute A for $\alpha$ and v for the implementation to be used in e. This is the **same as **M3.choose M3.yes "hello" "world"! We pass the function, pass the value and then it evaluates as normal. 
    - Abstract Type has the universal quantifier
        - Works the same as existential quantification in second-order logic.
        - Thought about initially as the Church encoding for existential types
        - Which part of the rule should you look at to figure out the Church encoding?→**Always look at the eliminator form to figure out how to do the encoding!** 
        - So we examine:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NDeUheEtBLTDwBNILLG-HvI8MBIy403hIyjYLy2M_z0DpUZZq2Ju6BjG2q0y3n6BtQuNmvY0WQedUrtLVx4GJANLut2iSSdYs3YK06yu73AwKKkmWonysqHZkNiCL8Ow.png)
e' has some arbitrary type C which we (Annoyingly) call $\beta$. 
We say, for all $\beta$, give me a continuation that takes a B to a $\beta$ for all alpha we slap into that continuation - and then I'll give you a $\beta$.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qNDqKFNxx-lJIYcCtY8DMy73P-1Cex2OFJBwmt8U8Vx-o41NjVBazfIaDMAw-uz_ZtlsP7wwqFRahMOSoUAacjKUeI87ZOgDrvKGnhqbAxUv4GiA2kGthL6EyXRdndvm.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JzBY_6ulkAhlJLrRU8BPUw0cNFri_mTUF1h4HrBcI11Wt0cwg82xwAu6O7lwdQ2NnIvPnz_FWIIKhpFYurusNn4ZVy3L_0TolCug5L8RKHMs5tdVaH7AM-gI0hkhqJQL.png)
This says, if you give me a type and a function which for any alpha and B gives a $\beta$ (the type you gave me) - then I can apply that function on A and a module. I.e.   so we first apply take A in to k, meaning k has type [A/$\alpha$]B ⇒ $\beta$ - then when we pass e (type $[A/\alpha]$) we get out $\beta$. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iqg0dneOjH6nrhXAenjVnSdAXZxfPHWic92raLhdUoZekQzV86PXVCU8VZ0A25fKZi7NW6YucLrFCH2B4VUuwHYqBnflFGdflSEHgs9Mkbko7gdGwLqEBzvvA6YJn7et.png)
This is just passing things into pack, i.e we just do:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FZrihNnV4uFk8qDxNrTUjcJvBUUGxUMjhA7vby6UGJVYuM40iB37ZaKosvbe6b3niFsuwua3b_jpPwvUtPH1NYS_A1wRm59Oqd8eC5ArXu6FG1t-mxg1mKoCow5ikB2Q.png) 
Working through you get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KkkFja_e-eu4QtdgjdfhxxLL7IzZy4vO4hyHIyH3easzFyD4RF29VQkw7iaSbUujMhr5LL1GJw1PuByWCvQUiXNJozzFFJ06D6XVthVxkqDOl-xXoAeiCn0JcrSSlq1x.png)
    - Proving termination of System F
        - Before we had a family of relations, defined by recursion on the structure of the type - the enforced a 'hereditary termination' property.
So, how do we handle free type variables in a similar way?
        - What is a  __semantic type__ ? ↓ 
            - A set of closed terms X, s.t:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/arezPcBT1yn2ZzrzvSNOz6ad2O4uT_cdztaPKg7mE0YYJMAE5LpBACk0xwIXNvZLLo6JzZcika8NlWdrOFDqNSReGBniREKaE5K0DQ7bKYOPQc4Ct013sCSAd1xeWVgA.png)
I.e. every term in X halts and every term in X steps to another term in X. 
        - We build generic properties of a semantic type into the definition of a type and use this to interpret variables. We say these $\alpha$'s are **any **semantic type. 
        - Semantic Type interpretations
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UiMHLYqy1Rh_DJAJ2YVrQweo7gIFJ0BUg38V7tQiWWu238GfUx76vI_IRy4GQN_K0zzHw7zwwrv5Hu1oAbzZRyRyX_H7NqTA9VHL-fIOVPvcAfipIuzgU-XHwoE2H5rF.png) 
            - Given a type variable context $\Theta$, we define a variable interpretation $\theta$ as a map from $dom(\Theta)$ to semantic types. 
            - Given a variable interpretation $\theta$, we write $(\theta, X/\alpha)$ to mean taking $X$ as extending $\theta$ with the interpretation $X$ for the variable $\alpha$. X is a semantic type!
            - Our interpretation will map every variable in $\Theta$ to **some semantic type.** We don't know which one it is 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R4LYwmlxJ44hClZ-O1sSivudQRMuAGZljK2KIq2ibKAbYjGbRr0qCtoihQjcjGdZxTphflE6AKdd1ZCZ9aFtHB4kRTfhgtpapvSwzRcqx-YBzGhF8xBQiUfIoT7oOm9Y.png)
We have a function which takes a WellFormedType to a VarInterpretation to a SemanticType! The var interpretation is $\theta$. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6ypgloNR7ZqvAcLXCnkPPgpMs4LVZjVgpdLGczT4mWDhs7VvRT_fSdsozrWk4F6tCK8-xrR0SNfpSQXECNdz6bNK7U_XV2aPKrWTiikiQioFb2cpUvUJUClX-eI4WjQA.png)
Here we just look up theta in our variable interpretation, and that is its semantic type. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mHN2nbcET0kOlEIeaI_KAHpmiqxp0aNjfx9mrNoxVd1Oev1OfqxB8okb9Olx3awuSfCft0CxslhgtkKsvgCIpfzAm140lBCwmGy102-j-Gyvu9aigN50t_1CulLLHLiG.png)
e is in the relation for $A\rightarrow B$ when 
   ⇒   e itself halts
   ⇒   For every argument to e' that is in the set of semantic types for A, when you apply e' to e, the result is in the set of semantic types for B.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Hvv05vfIp0g6V6Uv8xqOIRxWlEugXuS40HHp8PvcA5mGURs9fosbj1GGvMN0bw7gs5cnW0hroNoM-0VEZP_Fl0wrPbFq3dMvlm18FwGhlAmvGAvV0c0axeCgtK-s11mY.png)
 e is in the relation for forall alpha B if
 ⇒ e halts
 ⇒ Forall well typed A, and for any Semantic Type X: when you apply A to e, the result is in the set of semantic types for B when $\alpha$ is mapped to X.
So we're mapping our alpha to **any semantic type! **And we want that to still be a correct semantic type for B - so the only way the term can be in this logical relation if it halts for every single semantic type.

You might wonder why do we need X - can't we just use $[\Theta \vdash A]\theta$ to represent find the semantic type interpretation of A and do $[[\Theta \vdash A]\theta / \alpha]$ instead:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ah1PhOUKKiwv1Ixo91ko_0SLZjW6Mkpmhck39zD-UREEmF0CYr-Hl1NG5hyDxt6o9DU8QOg3fEBf6C7N1zkbcJp7Js9FCqskPnpnhTv5DOke6JlLb4IZhWKkf5xPu_Xn.png)
But that is a circular definition, because **A could be bigger than B - **so this could result in infinite recursion. Instead we iterate over all the semantic types and pick a random A.
        - Properties of the Interpretation
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HdVUaBIOy_Ol4OTpfUHhtN4XJvVmS9tebOV81yujWNv3FrUW3hJl7oC3hDLUuYGXBEXAZcfqGz5WWO4KeBzWN_c0i5VrzjdKHg0xlfHQ-IiMttR50Qr9xti2z3eT3_XH.png) 
                - Closure: For all types, it will halt and it will always be in the same set of semantic types.
                - Weakening: Adding a variable that we don't use, doesn't change the interpretation.
                - Substitution: The syntactic definition of substitution is the same as the semantic one, we can pout an alpha in as long as we extend theta to ensure alpha is a semantic type.
        - Proving Closure
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yIePAsOKZkmLW5K6MXEV-sPc6b57ELWIYJKnrz_lhFsXVwtZEoG7wSOcEAHNx6VIwbbTIySPPEWTmvhE2kd_WwZRUYxkQxs6vlGsdNaR2ynsnJHJ-hicK5xgypJd3EOC.png) 
        - Proving Substitution
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/24ce_uLCnCGvZAljaoYLYHbugeAZgCtTjpKWaYDqkAEWYwPTf4ZOcjwgxVfuxBhKmlbcAdQ3WGssvMzAOZupc8tWuVMpmRPmb4XfyZev-94dnLJtXAnpxeb6_O55sfpE.png) 
        - The Fundamental Lemma
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wBav-0Xnp9YwMerNEfN63YBynYqJ8L2DHkFZKtqPW7XO69X2dEdThvr0Lvtj9OATXiwcpiMuwVmMK76zC7eEOP_dea9o3WBOJK3dEp1wtYmzLymulnQE6DniS_LjS91O.png) 
            - If all the e_i's are the semantic type for Ai - then we can sub them all in and come out with the semantic type for B.
- Lecture 7 - Programming with Effects
    - Wrapping up Polymorphism
        - What is the church encoding for a map function?→$\forall \alpha. \forall \beta. (\alpha 
 \rightarrow \beta) \rightarrow \text{list}\alpha \rightarrow \text{list} \beta$. For any alpha and beta type - give me a function from alpha to beta and a list of alphas and I'll give you a list of betas. 
        - Then a function isEven - $\N \rightarrow bool$ 
        - To define a function taking a list of numbers and apply is Even to it, we need to define all the types - giving ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/md_rZt7ZhIL_L222grLfIJG0xTTnwal8IBKWnTdFzPLZGiHXj8XOPH7t_Nhcmi24MXLVPlpNX9RgHQKVzgEpGyClzk18zhHA93fVaciteRlS72PbiqTfhNuB_5ElzwlC.png) 
        - To go a level deeper with a list of lists:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jGZcYPRQgIvIWBG5QomDlWlMkRGJGuiYqAMRWL0O9csQkwsWour7UA6OoAJ5-y2GOA7wPp9vbdFbEIuCm-Om8n04sdmP4SNI5dLVS_3zRTVyLOnmK5ovG4-umrF-exDU.png)
6 tokens of annotations, and 3 tokens of the actual program. Programming practically with System F isn't viable. 
    - Type Inference
        - For languages like Ocaml we don't have to write every type - type inference is used. This uses a type of constraint propagation to find the type.
Introduce a unification variable and incrementally update the constraints.
        - $\text{map isEven}$: Term that needs type inference 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9nOvAv5fRnj-L0X9ohzWpjvaz50FGwFkXeolqdhd2-hyuBsn2htUXaLPclr7Tkk_ti2xV7iQ3aLWgb5441x0L5Y4fgM5onrhy08AanTya-Xv3XfwASJM7xYAGlUnLt6D.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/427aCcIPF8xi6CS07N2Exo8qTTM_WdVUIveQUtiUq-joC-2w2i2kz6Gtm9qVyJN-EuKJGzROAylieVrAHM31Rt5yLsKp7OGdJCe8WorMVcaxOGY8VH-XtqHBQ4yadWBy.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ws3X2yi2dHGsFKxeaCW9DpeadSCxK3hCb_IbTx8cJQIYU2ezu49W3V2UOHzPkhqSF3XTmthCBR0xDHRZRy1jxOOaEC0gsn05vyPex6Bu9bAOYtPTFNDQBhR34DLTbxxa.png)
We're given values for our constraints! So we can propagate back! 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PbbiVELTwSTFk4pKonrMedUmJLTeptQXTIVkoZMHqtmvJfPjvXg-ZXJ65Fgd7vAWApe8rkN-vaSDoSDUANFnaJsHfnAHLBsjZzYMaWvV5Zw511FVda5W0gs9bBGOxF0O.png) 
    - Effects
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nJFe-8ZhIyK9WM9Y60uAa7Zj--n1Y2DVH4AwOqrTlE3mSoHCG2isENJk-8KCKakuE1cdiED88G9PvyeStdWj80yXcNxtCWZZ5jcw6p3NhMMBxpClZ__8t8I4TgefmCfP.png) 
        - Sometimes, we write programs that just take an input and compute an answer.
        - Other times, we write programs to do things - we might want to save a file, update a state, work with I/O, or a robot etc. 
        - This distinction is the difference between **pure **vs **effectful **code! 
        - Two paradigms of Effects
            - State - mutable data structures/ pointers
            - Control - Exceptions, non-determinism (all change the flow of your program)
            - Other effects can be modelled in terms of state and control effects.
        - State:
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zB7fNzpqkP45UTzo4wsdNYXORjvaZGFbVYrlSDgR8Du_ZHxcAaYQyAjTEsEiZt7474nWRu3imzD0sxKqZJ_0YPuqyuPRRS1hjpuDKYY4_-zRSCsrmVs-Ygyu0ZyeiNAu.png) 
            - This means, when we evaluate the same expression twice you don't necessarily get the same answer.
            - We add the following type system:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NOeYMWe0gDV5vM1YYjFExcEvvRlQU_fNbHwOtamTBqca9Gq_JY41bRSm4xf7qz8ROHMJFqHQhOKU9CKheFeqT3kwLlkvnTjYudt7gkZ5R0CuanSmJ86D-fJfIp7oeqHH.png)
 
                - What does $l$ mean?→The literal location of the pointer, e.g. the address 
                - What does $\sigma$ mean?→It's a store that tells us what values at each location.
            - Operational Semantics
                - State gets everywhere:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GBF5Ksfn4i1yPOsG-nYkJt9V6zh4-zfo_XjwgqXgwG4fp7iQgRTes5pFbbthYnaI2LaLD4pmMPZrc1bNLiyMJGWx65LKvFDXNhLFAu5B-ML9AVivJHS9c_HX0hUHsWMC.png)
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/k9iWiW1XLCsjC3Q4peO6PUxvrSF5uEkuRL_wI0Zi5rlncs18DppMLoJwHXByp7dWaViu3VpYplvaxt-8i3VTvmWEYNo8FOdOStHsz_0H5XhBbTpfOJeDbsRPw3OHPM2O.png) 
                - When the allocator runs, it gives us a location - and there's no guarantee that the same location will be given over and over. Meaning the program is now non-deterministic.
            - Typing for Terms
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/B_l4tO6I0Jr42C8YlfNK3ogsbHAClRc--XCyqsTjV0TJPAnJjI9WvbcY4f-PKLBLf8DPqt5OoW8KltsqhBjGqkSPUbPJ6-m4zqpptIZLGazZS-Ayp104wpdar54aZTfx.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9WbMAz6Qfj3TDdrg-tJTARpoo-8FpuPHYzcya-82cJLBW8S8aSByzdihkzeQ3veOJhRjhwvv2hQlPoa4TrdfjHfonciafOstMxzPxxn1fPx9uAuzt4zfXwiLdOotfHyw.png)
We pass the store typing along, and look at it in only the bottom rule. 
Why do we have a bare reference rule? Programmers very rarely have a pointer hard coded in. We do this because of the reduction rules, and new v **creates **bare references even if we didn't have any to begin with. 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zjvWcNGIn0-j8Jsjdu8SXRPcEqasAf6A031-1FXJW6ZhQrc2UNqoCPE-bLh1Cq25nCLk0FThiMX8qbsKvyac-uhofgTI0zJ4xXUZVGsyy_YwYwRtZEQGWaM5DPRWBnaN.png) 
                - Explain this rule
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0Vkytqhm_rLyjO_7VGJe1HKFO4AiNavGqUi8N6rNAL-kaqy24uu1nqplfqs1LBRHfnmediPYiv3m4gP3fShqxvk1mqnPI9SnzYLTHEFZpwpZkbsit3EeQPNssYdkvrr-.png) ↓ 
                    - Remember, $\Sigma$ keeps track of the **types **stored in $\sigma$! Then $\sigma$ has a type that's a subset of $\Sigma$. 
                    - So the top left wants $\sigma'$ to be well typed. 
                    - The top right part says $v$ must have type X under $\Sigma$  
                    - Only then can you slap l : v and l:X into stores and types.
                - Why do we keep the overall types in this $\Sigma$ object, isn't it redundant? Why can't we just represent the same thing in $\sigma$ : $\Sigma$→Consider a loop in a graph - i.e. create a reference two another reference, and update the second reference to point to the first. Then if we dereference the first to get the second - we won't know the type of the first when we dereference the second!
                - Configurations are well-typed if the store and the term are both well typed.
                - Is progress or preservation false when you add references?→Preservation is false, when you add references - creating new references changes the store typing and the type changes 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9epcSJwvdEo5wdpXvrT6xuFL0REUfIFBwqAfRo9uV9f4MbcBRIOTFbct79HxNhey6Vw2BKt-nT3_WGoLMcfJ-kcD2NJAvOHgI8gazfldLry9poSGyxssvQgVzwEvXntq.png)
The heap has **grown!** So the old store typing is no longer suitable
        - Store Monotonicity
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5TDW2wtUnGX4D6pvsbXjFEQqzejFkQaooaInUf-RGo0nOs1vbam3XbUpebUnQF0eotaMC0-rY30k_Du3Q2mwQqMRVWsgqLg1liL_t34KYKP1AelC0QngUWj_kxZwHFUn.png)
I.e. one store has at least as many items as the other - and the smaller one is a subset of the larger one. 
            - What is this lemma saying?:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OavKHXP0VUabZ_hAMoJgdiCDWr_9G0XyAkugMi9lh-3y68rnXF6JS76zAbK0PB52pTT1wpRVSZ0hEVEdGtvrLOAaWlLzkfZofWIM2qw4UF4EbZoMBCcPiGgv-2tLVJ3_.png)→If one type store is bigger than the other, then it can do all the same things as the other one and find the same typings! 
Additionally, that type store will result in the same context!
            - This means **allocating new references never breaks the typeability of a term!** 
        - Substitution and Structural Properties
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3wDn7LL-78zLawJUrjWsLSlRGJ-5d3pKbCidpmyrd2KC_7IWSE5RSqXzjdIgR-9V2QrFo6UUtEcvbwTGSpxTnKJFcNDeNbBAYYFJoB8JkqxQY7UhGqVjs3bLkR8Nt4LU.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZlYY5qtYoEis4TxmHe7K5NnPGO4kCIHrEX-oc929stM4ZK1-VEAXggAXPHVIJH7BMm9eWtCN-qmoYuDzkHQ1gcdqbcCiJICO3U_4GIFy9tnGqEDiPAaZljKQWoPdqwfz.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/I2y8_zBkyFGAP6w_WlpdvYhnfiwC2BAlOJQXSfViz-n9FJHykyXm_tYgwEbBVNlaaYJ_AhsE-i8CUvUQgk5hfN-x1DS5pPpap0YnlK-mfz8FqFV2YjqWtoUJsekqSsiU.png) 
        - A curious higher-order function
            - If we had an unknown function in the STLC (simply typed lambda calc):. Is this true when we add state?
$$f:((1\rightarrow 1) \rightarrow 1) \rightarrow \N$$
What can this function do? ↓ 
                - It can only return some constant n, the same one every time. We cannot alter the function we're given so we have to just suck it up and return some number.
I.e. the argument can never influence the value we get out.
                - This doesn't hold when we add state, we can define a function which goes from unit to unit and increments a counter depending on how many times the function argument is evaluated:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bHUm6MIX1me1CyZQ1aqXQmjpzjWYYF8ij2nk720QrHqx8SJPYsxIO5e7EfNPm6vTlsaf0hM9qUOyTyXnQnvXGsXy_zXZVw7UPVAUXPlU3A-zjndj1Ze_WMNcMtzz1-u3.png)Remember, r:=X returns unit for any X. 
        - Backpatching with Landin's Knot
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9I1Mrsbw3GUzDEubRmMMgRbGR3SWerJrXq7CC4hlVfXU8e2RgpRutfpCwlwuyv2LUX3uqe1r6oORShZED1kmqAD0zr1TtaQsSWiNr12i93rkAfKxPofSvh0_pMHtYw2U.png) 
            - Landin's knot takes a non-recursive function and makes it recursive. A pointer is used to implement a recursive function
        - Another False Theorem
            - Because Landin's knot allows us to implement recursive functions from non-recursive functions - **Termination is no longer a theory! **Functions don't terminate any more. So we can write non-terminating programs.
            - Do we have to choose between state/effects and logical consistency - i.e. is there a Curry-Howard interpretation for effects? Yes, via motherfucking monads.
- 
- 
- Supervision Notes 
    - If we have to prove type safety for VAR: $$\frac{x:X \in \Gamma}{\Gamma \vdash x : X}$$
What problem might we run into and how do we resolve it?→Progress assumes the context is empty - however VAR requires a context with x in it. However, the rule still holds! Type safety says **given **$\cdot \vdash e : t \implies  ...$, our rules still holds as the left part is false so the overall implication is true. (Or you could argue you assume false so you can prove anything you like) 
    - Why is this allowed? $$\frac{v_1 \le v_2}{v_1 \le v_2}$$→Because on the bottom is a **syntactic rule**, in the world of the lambda calculus - while on the top is a mathematical rule in the world of set theory and arithmetic. If we were being proper we would have some symbol around $v_1$ and $v_2$ that say the set theory equivalent to the numbers $v_1$ and $v_2$. 
    - If you want to do structural induction on the shape of a bool type, what must you say?→You're going to go case-wise over true & false, to do that you need to state that "by examining the typing rules, type x can only be true or false".
    - When you're proving things, don't forget to state you're performing structural induction over which rules to prove what.
    - Why does $\pi \rightarrow 0$ mean negation? Give the intuition that **doesn't **rely on propositional logic→This means, if you can prove that the type $\pi$ exists, then that proves a falsehood - clearly this cannot be done. So from this we take that $\pi$ cannot be real, and thus we get that not $\pi$ is true. 
    - Using the correspondence between programs and logic, what can you confirm if a program type checks?→If a program type checks, then the propositional logic formula associate with that formula must be true! 
    - Note that all expressions that halt are in $\text{Halt}_1$ - (1,1) is, 1+4 is, it's all in there okay, okay?!?!  
    - What is this saying ```python
Halt_x = match x with 
| 1 -> ...
| <x,y> -> ...
| (x+y) -> ...
|... 
```→When trying to prove halt_x, it's true if the statement halts and if all its constituent parts are in some halting set. 
    - 
