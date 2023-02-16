-  _**Lecture 1**_  
    - Text > Compiler > **target **machine 
    - A good compiler should do these 5 things  ↓ 
        - Be **correct**, i.e. **meaning is preserved** - i.e. semantics preserved (source language and target language have different semantics)
        - Produce **good error messages** 
        - Generate **efficient** code
        - Itself be **efficient** 
        - Be **well structured **and **maintainable** - Programming languages evolve and change, should be as easy as possible to upgrade the compiler. 
        -  _The first 2 are REQUIRED, from the last 3 options generally 1/2 of them are achieved. Hard to have quick compilation while deeply optimizing code._ 
    - Pareto frontier of optimization - trade-offs, feasible solution region often common. Changing technology changes this frontier.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XoUFAUYcPtd3q4WN2ics6Z8Fc4ar-9Hc7_3E3s-3v3n2hWiz-r-kBSkC6pJWRPt7Ip1k0J7y_SCsgT5EFZIZ-YN5R1uLAVb2RkAlTifAnGBXIS4QJyjbhjwiC5IkU8jh.png) 
    - Divide and conquer is used in compiler construction by  ↓ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VUV7dcNkXjfhgwniatPtyGOsxPv5_ZX7yRJzMdNa7mYvl6ogT1-ds5rH56U8zXwwBQOezXWMQ-ljzK6Hk5fNqWoqZ9qeedo3l9rgBEqHVKOxL3C4ED6hB-RfR0GXCg69.png) 
        - Front end, checks for errors and warnings.
        - Middle, input is a legal program **in the source language** - the output of the middle end is target independent output, **Not yet in the target language**.
        - Back end, takes the target independent output and moulds it to target a certain VM (e.g bytecode is outputted) or OS etc. Result is the target language. 
    - What are the three parts of the front end, and what do they do?  ↓ 
        - Lexical analysis - code tokenised into lexical tokens. Based on finite automata and regular expressions.
        - Parsing - an AST is formed (an abstract syntax tree). Tradeoff of simple language easy to parse but hard to read for a human. Based on push-down automata and context free grammars.
        - Semantic analysis - enforces the static semantics of the language including type checking, functions etc.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Zi6yDdDhPNQoq5-7mCOVG8-OP02kn_Jsf1Rc3Gy8ZQ3BUv0hBYF_5oDSUnVd7ExsH-uBnyABJ1vPYFuyjUPNfXmURyUzbuQo42No9SL_KWBfdYfjXvcUSxlLDBhxHG_Y.png) 
    - What does the middle of a compiler do?―Takes the AST and other info and converts it to low-level, whilst performing some optimizations. The result is a low level retargetable representation.
    - The back-end takes the low-level {{retargetable }}code and aims it at a certain target machine. Requires intimate knowledge of {{Instruction set and details of target machine}}. Need to understand details of OS interface. {{Target dependent}} optimisations occur here.
    - 
    - 
    - 
    - The middle end also provides {{optimisation }}- with the trade-off that {{more optimizations}} result in a {{slower compiler.}} 
-  _**Lecture 2**_   Lexing
    - **The problem to be solved** 
        - What does a **Lexer **do?―A lexer takes a **stream of characters**, breaks it into **tokens **and **tags them** without any context. It tags them with some datatype/constructor.
        - **Character Sequence**:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TaD32UcLpWln0wjca2pELJ4CCA0QO_gIjRxrKjzOr4bEef9YFYB2-INVyPOf6nrLsYwnkhIggCb2OqK2w297yidr3M6eV9B393j7E9jUV_ItD9iUH7mojdFUxj2tv-qF.png) 
        - Sequence of tokens:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QAOOXh0TiKvQWqr1XI4Xu5DMvlBetnQG4Voxzb2cwdtR_P6T8COG20TzAb84puq5e6AC13lldfixS9ZfIQRf59vlG9o82MaBuaQNlnVAIzhP9-TjIJnbWXEGE2iETgaD.png) 
        - Implemented in some data type:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PCouvqdW5sb9X6DiuBCbI6ag7iI1YYH6eOeTDZEN5ERx-f3EdD4g8BFqGJpFqRLXC0h8l-WhpIaJougOf8Iqb2eSjLndVC2pHRB0Yeo45dSmGTIbMFjigKFDGPnLLYjv.png) 
        - **Whitespace **ignored in this tokenization, as opposed to Python.
        - Having such a specification can be useful for testing, even if you write a faster implementation yourself.
    - **Regular Expressions** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VmIk_F1iXeNXSNyDhKl_RGWd16mvfgRzodqRxhWED8_5_cKOKKZYja7-1Pm6rTSDiF-WcZGZBuL3vPJ7vfvXCkgoYqrvBZmignQgEzUglP0X-0nnpkV3YlxU8UFW0IHp.png) 
        - What does $M(e_1 + e_2) = M(e_1) \ \cup \ M(e_2)$ mean?―This is just saying (for example) the **machine that satisfies** $M(e_1 + e_2)$ **accepts the strings** $M(e_1) \ \cup \ M(e_2)$. So we take e_1 OR e_2. 
        - M is the finite automaton - L(M) is the language accepted by the machine
    - **Finite automata**
        - DFA's have transition rules for every―state for every possible input symbol! E.g.: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GG0rDk6bh05DxAaavPAkjgzMoIQ211g8x2r-rC5h0WvqeYMEVtl0zOnMHx-YzVBE7HvQ52lRJc94ZORZBRrZEUzRwOpPSLAYjmLlQxiaShE6OasQq7mPvc4X3zNjxYFr.png) 
        - What do each of $M(Q, \Sigma, \delta, q_0, F)$ refer to? And what is this machine? ↓ 
            - Q = States 
            - $\Sigma$ = Alphabet 
            - $\delta$ = transition function. It takes the current state and the current symbol and maps to the next state.
            - $q_0$ = Start state 
            - F = final states 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qgMYA7FSfd9GEiQGkNwh5KpUa4_5HsHlHLHZoXf4x2XSLE1CgH2v8AuEMhrxkET0pbhklBmcivmiYN4fcu3ECE0l63ljVr3XKHINQPQtXj8BHGYwWfHAQVgPS02slOf2.png) 
Just says NFA, are DFA with epsilon transitions.
    - **Notation**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1FwrQ6R5ei__2Z7KKalr1whqWa5PZvpPfLJyGZbtDPb1DXzazUrIApR6ix_mzmRc_J3_tRUyPILjzpWCCyDnAKdtsovHTbvawNFq9Ps_4Q76OzGbvt4LMa6L4S9Znk9n.png) 
        - Just notation 
    - **RE ⇒ NFA**
        - We can prove that we can always build an NFA for a {{Regular Expression}}, by rule induction on the rules.
    - **Review of NFA ⇒ DFA**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aasRinDrSoRkEve-i9koOujN9l-DrAoeHoa7SuPw_hZWplVUjwvMVDGLmSTHsFBXmI0TsFlIRxi05B2ymul37zBmaC65lPMYjarijwvOIucSboS2M30anfsYcaSAmKm0.png) 
        - 
    - **How do we compute the **$\varepsilon$-closure(s)? 
        - **What **is the ** **$\varepsilon$-closure?―Similar to transitive closure, say **if there's a q in S that goes to q' - then q' is in **$\varepsilon$-closure: 
$\varepsilon$-closure= $\{q'\in Q \ | \ \exists q \in S, q \rightarrow q' \}$ 
I.e. **if we can reach q' from an element in q** - it's in the $\varepsilon \text{  closure}$ 
        - How do we **compute **the ** **$\varepsilon$-closure?―We just take our elements of S, stick them on a stack - the work through them, checking their transitions and if they're not in S - add them! If we find a value not in our results, stick them back on the stack to be evaluated.
    - **Traditional Regular Language Problem**
        - So if we want to solve the **lexing problem**, that is given a **word w and an regex e **- is w in the Language L(e) - i.e. to find the tokens in our word from our language of tokens.  _ __Can we simply construct an NFA from our expression, then run the NFA on our word to check?__ _ ―No, because what we have is a **collection of regular expressions, each representing a lexical class. **E.g. we have $$\text{given } \ e_1, e_2, ..., e_k  \ \text{  and  } \ w$$
Where one regular expression could represent the "then" keyword. 
        - When given $e_1, e_2, ..., e_k  \ \text{  and  } \ w$ , **what should a lexer output**?―Should output $$(i_1, w_1), (i_2, w_2),...,(i_n, w_n) \text{ where } w=w_1w_2...w_n \\\text{ and each i is a pointer to a regular expression (lexical class)}$$ 
        - In reality we have a **lexical class** for **all our keywords** - we want to break up w into a concatenation of each keyword. We also want to know which of the expression each section of the concatenation matches - also need **specification of whitespace **(might not pass on to the parser)
        - Why do we need a **priority order **of expressions?―need priority to resolve ambiguity! E.g. consider a variable ifif, that could be detected as two ifs. **We want to make the ** _**longest match**_ ** possible. **Results in most specific match. 
    - **Defining Tokens with Regex's**
        - **if: **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VHNu5TeH3fg_klhWwwrOPlmzrxjwU218RA5O4tTMWHXi3EpCGBXOb4_eBrrd3_qKE9Jv-Lo8Fj3Wj3UV7gKBZTZl96SGFM4hpzaiUqTPX_sQLInDHiKpjtt1UEXWdAmZ.png) 
        - **identifiers: **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eMp8Bf4ydWm_fC9N233ZG_XzBmNPxpc8HyVkPgN-8cSHtm4dlJ130fVwexzNNXlB5EjyvjVOyk3TGl72oS1UGwc3TMXiztYKMjmixWzwIR8jLZQ2HNuNPpY1y_KwgOj6.png) 
        - **number: **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/986Qre2nWAnT_cZyBIQo2RxyPyWvPCqyYnJLHHE4d0FCBF_7BVWtiMKfl5znRbcs-MmL0fnvt7_Q1N-3qC35CQFC2mTIG6w4GBsCBFM0Ulnm6fl5ocOKzrgQo_fijRFp.png) 
        - **float: **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ID1epqdeMU2T0_rQF9N3Ng8duyHHKVqypnLD0z-UTuovfRIAo5mmdNx3t7n0xrSCMbzqKo0sSErEx47vKQdbISwiudcQdTskKC1VKdIGqW7FM1Spm59M1Mwqb9lPjzce.png) 
    - **Constructing a Lexer**
        - At a high level, **how do we construct a lexer** given $e_1, e_2, ..., e_k  \ \text{  and  } \ w$?―We construct an **NFA **for the **union of all the lexical classes**, e.g. $e = e_1 + e_2 + ... + e_n$ . Where each $e_i$ is a deterministic machine, **where the final state is associated with the lexical class with highest priority.
**![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CW73Gpxt8FJpJcWKVFJXkRSmmmuMpQPZ63Zjxxe0M0knC1Hzfw8xizCkRTjBHIhG7ixbevuMVJ8I2m-VLAH7EcG2zdF_PifESVQ5tINbIfFw01BTRc5fD4R20zSj4TmT.png) 
        - At each state we store the possible identifier we could be dealing with. The priority rules are "baked-in" to the machine. This eliminates any ambiguity.
        - Algorithm for **Finding longest match** lexical class
            - Start in an initial state 
            - Repeat the following:
      **Read an input until a dead state is reached**, then **emit the last accepting state**.
      Then **reset to the start state**.
            - An example of a dead state would be a space **after **seeing a "then" - this takes us to a dead state. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fYtjPc8TaQ3Br_o2KZvj1ApcTVRs56oNqySfZGbeXFV48zxF3t_-U8sfj2n4Cc-aaSUj1E29N4pkth1mPYexBWv_WpBlchrb7fkmERCe4z-QfUvKSf9VML--6153_Epi.png) 
Note after we RESET, we step backwards one step - notice this is done on Whitespace
            - $ sign indicates end of buffer.
    - 
-  _**Lecture 3**_   Context-free languages
    - **Context-Free Grammars**
        - What does the following represent: $G = (N,T,P,S)$ ↓ 
            - A context free grammar if build formed form the Following:
            - N: A set of non-terminals - syntactic variables
            - T: A set of terminals - elementary symbols. E.g. "+" or "*"
            - P: A set of productions - e.g. rules for building up our language. Combination of terminals and non-terminals
            - S: The start state - it is a non-terminal.
        - **N: **A set of **nonterminals**, these are― __symbols that can be replaced by groups of terminal symbols__  - could say that **nonterminals are syntactic variables**.
        - **T: **A set of **terminals**, these are―the  __elementary symbols of the language__ , **defined by a formal grammar.** 
        - **P: **A set of **productions, **these are―rules for building up the language, consist of a cartesian product of the initial input and the result: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LkxjB5QdhrWKyap3qRU-0SOfBois05g9GOuH3HeqqzikZZ3VmkH5-QvZUPG13vSiVT51Nz6lR3tnPRWZiJLpukqh0pjS5aTD4xX0bcAqEoU4afg2PvSyHhf-GyS6YwWZ.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9QXPQBnemC0c9buEzVZzwgGvbEfjC-kNO4-qlKNG5VH0dTZwoPA4P1Vezu2CSPf9Tt_h0k8f4mjm6qXnB5Rd23ej_7lP9yZgbph465De21vV2mQqsN7jNXgnvBRzP_Tu.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9K0cazjFPi70xnR0P1xDBscBXXuYWf0Cccn-q8YB8CVTQAyXTifnCjsBexYoqdBzZPiuOBD8UV7W1dcm0kc-dNdnEFLkik5ChW-6mSJhZru2_ELKr9X8ZZvj0W1ur9IT.png) 
        - **Example CFG:** 
            - N = { E } 
            - T = { +, *, (, ), id }
            - E ⇒ E+E | E*E | (E) | id
            - Note - the **order **that you present these rules **doesn't matter!** 
        - **When **is a grammar **ambiguous?**―When there is **more than 1 way of deriving a sentence**. 
        - **Derivations**
            - Why is this grammar called **context-free?**―Because when you perform a "derivation step": $$\alpha A \beta \implies \alpha \gamma \beta$$ 
We don't care about the context A is in, we can simply perform the rule.
            - Note: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n3L4AHyrh9GMZNyCCQABaplv6f9c8vuVADavRxTWciVjb-HeXJ9aOiwpWYoOewP4HhZZShq9ifvxHLtBMePg6lgxJUIOiVyxbi2pO-FomBWilyNHmjnKGQpkSWbTH51N.png) 
            - 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/420uLV9nkM6UZE6edLdrjsTNkW7FYsPaHy1W4AOib4GHG1OeBuUhRm0MIJNvC_aINAAAV-SSXkRhp9SWJkuPb8w2fnY_FaN1EmjZ5yV86UW9ql9WAzpNmFyb9rig2ggg.png)
Note the variables, are an instance of an id! 
            - **Leftmost vs rightmost derivation**, work from the left/right until only **terminals **are left.
            - This **derivation **of a **sequence of terminals**, tells us―that **sequence is in the language**.
        - **Derivation Trees** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/orfRuAkuvetSkP97Br3uMm7hylr0NVXQz8P9sszzXWEAKzNASvVQmfsLGx2BPtc3XveaKmJZ8nkWDlY2FUBTSiPZS9tRTeS_43OluqBnYVhe7RfpoaVDVnqt9fA_Bu7M.png) 
            - The difference between a **Concrete and a Abstract Syntax Tree **is―an AST contains only the information needed to generate an intermediate representation.  
Brackets not needed so removed:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SEwDBSLQT_EAIA7AEDAr3JKpdszW1koFg-dD0Vr81UwWkBgE9FsjpQVUu2w-ImLiYGW6nZlBhk6rf8_dFG5t1GB7OGO3BoiJj_-2fCXFtw6q5Rp0qZeNOdAdzwt7IvgC.png) 
        - **The language generated by grammar G** 
            - What does this mean: $L(G) = \{w \in T^* | S \Rightarrow^+ w \}$ ?―It means the language generated by a grammar G, is **equal to all the finite sequences** of **non-terminals** generated by **starting from S** and **following multiple productions**.
            - Note, if we take:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OwvDsNfrYoMyfrV__rDcAxb3GnmpLzh-l4GIzWSXr4Ea9TG8-cTskrbPgursx7T3rR1FGSWQ9MG7osCu5yopn_88mQ-MmMQBEguTgJcJ32q8PoEd_NfkpNiMM1Is-f5a.png)
we get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Zy5gI4f3tMtZFYUHd6h9LPP4WQHFAitFnGVUWY-MEEy61aD1Nx8wWOdEOUOWyTjwZaOLG5wfABTF7fo8iY-vgIzf87QLmBtImbQ0UzW4zOUhC5CryRZwNlGcZO1rXG4N.png) 
This is a language regular languages cannot generate!
        - **Pushdown Automata**
            - What is a Pushdown Automata?―A finite automata augmented with a stack
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ocYPLT91xqkWG2XWxGLgMnCrfH019ND4RitOMZ3AQaNemSSlS_Snk6tvhbyIPyHbDnFCsq0O7PIRe8kY6zjwa47YP94tFYSCdh7KnGzd-4VPwotTDoU9YgjcnjFMu5Eq.png) 
            - What does each element of  $M = (Q, \Sigma , \Gamma, q_0, S, Z)$ represent? Be sure to mention the input to $\delta$.  ↓ 
                - Q : States 
                - $\Sigma$ : Alphabet 
                - $\Gamma$ : Stack symbols   
                - $\delta$ : Transition function - takes the current state, the current symbol being read and the current symbol on top of the stack.
                - $q_0$ : Start state 
                - $Z$ : Initial stack symbol 
            - $\delta (q, a, X) \subseteq Q \times \Gamma^*$  Means―when we see an X on top of the stack, we can non-deterministically move into some other state (Q) with a different stack ($\Gamma^*$). 
            - Pushdown Automata are **nondeterministic**, so everything we do will be a heuristic - as we want our parser to be deterministic.
            - For **Pushdown Automata**, what does $(q', \beta) \in \delta ( q, a, X)$ mean in **English**?―It means, if we're in state q, reading input a and there's an X on top of the stack. We can transition to state q' with $\beta$ on top of the stack. (We pop X and push $\beta$.) 
            - What is an **instantaneous description**?―$(q, w,a)$ It's a description of the automaton in a instant of execution. At state q, reading the first symbol of the word w ($w \in \Sigma^*$), with $\alpha$ on the stack.  
            - **Language accepted by a PDA**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Lm_R-0OHo48effkENxE7LvY2OCRLvO4IbQ-VLLwrkpwU7OQvR9Vjg54s7NiVFHz62S3KQCnFuD3GIRFl3ZGwmSCgTPEv3BhGAWwlXrzEIbemK8qLPZt1bsBlY2-VxUiy.png) 
                - When is a PDA finished computation?―When the input and stack have only the empty string. $$(q, \varepsilon, \varepsilon)$$ 
                - For every Context Free Grammar, there exists a {{PDA }}that accepts it. Also, for every {{PDA }}there is a {{CFG }}that accepts it.
                - The problem is **our PDA is not deterministic.** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/t4MmhDn-MGgk_H81BSIFIDM8OhBPTXwMQs7XRhEqq1YVOBtllBHMjpbgvv-OYoQn7e0BKRZoS2VSaFfhTrM4tWOjz6ynhkci5L6T0tSCdNJm-f9kn6FWwpXTIXzgXqJF.png) 
        - **Modifying grammar to eliminate ambiguity** 
            - Want to say times binds tighter than plus
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qvBsVVcqCz6dFLWHb2gbS1AoPhughxgpSsC9K5OStIlRMSxd8u99PuHVlvoWbjXgpwUMxXsK8G_zFoevtH02udwQr5QlHCdihnMb9i1ud030xXAWS1RJd5QS78CHp0nZ.png) 
            - Add to our non-terminants with a term and a factor. All over the place in Python
            - Note that there are **inherently ambiguous languages! : **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6qAO3aJ3K0Wgs76BFLKPZPeChkSXYX_d4D7l5IZZdn9M39VgVOxKB-0gV1KI-CWP0JAWI-j-w_ARzr0m96fgb-4hEyRVZarBS2Ag0P_UG4GpI9oChCmtvxM9rYtVEDRy.png) 
We would have to guess which of these languages we're in - even though both of those are non-ambiguous.
        - **Top Down vs Bottom up Parsing**
            - Top Down pasting attempts a left most derivation - using recursive decent and predictive parsing. 
            - Bottom-up parsing attempts a right-most derivation backwards. 
    - 
-  _**Lecture 4**_   Top Down Parsing
    - **Recursive Descent Parsing**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vRiR0ZfUV7GlG-rF-mhJlRLWA7dGqqLnMuiASjxTt0NZmxya2nPQd6Km0VzRobIco-gvxOuN4OvXvS5kAvxWhKH5kcrXTTipIVZuuCXTuFqbgd00Dpu2oyNtxJi0F5B9.png)![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/matwjiUUpN4Z_gWqgCSCLS22frtCYIIrb2pco-TSwJ82IYG1NVS0NSk7S1RYilWHR6Ztp1byMyPGTvGT9CW2k8Oj1QxrnaWG4R4JzzH5hnpLvjeFKACRiLHrztv7AmSv.png)  
        - 
    - **Eliminating left recursion**
        - Left recursion $E \rightarrow E+T$ in G_2 will lead to an infinite loop! 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/l8xOcaNeVGJrwKKY0g3IuMGJ9_qxKS_weT3s8iVeIIvPjuGo3YovnWfEy8mjS4rSZa8LF6U0c642zf67-04_2c4JggkQBvAYZfjCwuLrSxxOLWT3DSD6iYD55XJW8G53.png) 
        - We necessarily start with a BETA, followed by some number of ALPHAs.
    - **Recursive descent pseudocode**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/x8_vCjrei9LMET6yq894KYLsppl1CCQHG1bDwQzrESZuJBuQiJqWpnFFdqFG3fAp0dRJlxIdZ22JpLqJG57EBB_tLknoNZ9DfrzY4ilC0p43x1OUZUCHj0UTYb9FS1GF.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/un7DkTxktefxJAbUmLIM_h_rCY4fXT203PXKKJ31Cq0BbNOaMl_YBReakCfHEX9s-qyrYOPWpiCnvJtATPMOf_bt0eyLZOxAKZjq49FBmEJmdGhTA0ajRZHNCftTn-n9.png) 
        - **This pseudocode uses the runtime stack. **And thus a pushdown automata
    - **LL(k) and LR(k)** 
        - LL(k) : Left to right parsing k-symbol lookahead. Must predidct the next production
        - LR(k) : Postpone production until all of the right side has been seen
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RlybpOg2V-AKcMH8TxwIQNyAvMLkG8b228tY-D-g23tZMEt26vHrx4fQpvR-uYoA3KQw5_fSR9HFfW2h9yK-cpEOxKLEyqa-vM8-HIX5PlgArxAu3zBSGEttM4tbG-iC.png) 
    - **Leftmost derivations**
        - The left most non-terminal is replaced
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U54RRF83SgXbbPEbPlm4URcnEzSeAvFxiF5MGr2LoDpAyx0_2BKyVXotFdJl7_N-j8jmGZBBB6ZPV04ugyBUkspVbMTPnOv-KhzK0C-vLKwdElAtb2GDNq06GHN_lCMW.png) 
Where w is the part of the string we've already parsed.
    - **FIRST**
        - Steps backwards through the rules, 
        - It is a function that gives the set of terminals that begin the strings derived from the production rule.  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TiywDcx4Vd_tDwBzHMrRWj2tYDTKY_5Xu7KdADnYFFbuRU6ID8QlAkgEWOm-_6KES8YSnlpIA11Oo9_V-wXb5SNdLCFVXKSTkaqSxyrVOWfcsVTz1MCezWMV1x4sSupl.png)
Should be T U {eps} 
    - **FOLLOW**
        - The set of terminals that can follow an A, in a derivation.
        - In other words, a terminal c is in FOLLOW (N) if c can follow N at some point in a derivation.  
    - **The LL(1) Parsing table M**
        - 
    - **Table M for grammar G_3**
        - 
    - **Nullable**
        - If a string boils down to the empty string - 
-  _**Lecture 5**_   Bottom up parsing Part 1
    - **Non-deterministic Bottom up bloody fucking well parsing **
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/z0kTkFukBbmf4gx6h1YMgJMk9b_0prEfhm-OXBwa8DX1XUoEyCzrbeFizklYUDnp3D8i2jRv8CGC5x-8XPiwJm5CKA08SETWQc4aqXjZgoWJ6s-nVQr7IgLWtbLcY5Jf.png) 
        - E' added so theres a starting production.
    - **Rightmost derivations**
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4gRCBEncNOvG6ofB0upbNMxhH8xudlKHdusqxGQFqPSibK0_Hew82kV1IxDVSqPzqOlnePftMKvGrie-zVBgvsnLNexMQf0WaaNMWrEu1eLUAPm4bK2lDku4OeVXFRfC.png) 
        - What is a **rightmost derivation**?―A rightmost derivation is a derivation in which the completed **collection of terminals** is **on the right**, and we **move in leftwards** applying derivation rules. The left contains terminals and non-terminals.
    - **Bottom up Parsers** 
        - What is a **bottom up parser?**―A bottom up parser **starts with a collection of terminals** and **works backwards** through the derivation rules, **ending with one or more non-terminals**. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hST6opXLlcHJ_i0K1gjXvVgLT3v8yD50iq-pTeYcyh2jOETBaOwUY83IOOMpNnMU0ct0Drs6tUVMRfX8DpheQ1WdprNzQU8CYTNLbfxERralrIH12Ocz6FbsQQEMxeeg.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i-XCjiPfwnOddgg_nwi6AShQVCXZD7-Fnp4WNIL-c5j_136FspYV05bPLn1JxnhzVdvrRs9CyDso9HrzHQPy_vk2Q0vepIvLaTndXEzgQKP0--6bQz8yi3EEt9sZGxh6.png) 
        - We find F⇒(E) when we've seen both parenthesis.
        - reduction other direction to reduction?
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LFC7XiJGo891JiI83PhG_EVXbh6YB7NGayxUPEZE-Dui8zDLkEet1mFlY7uPQ1e6N8GhaNN3KcDxl88Km71CWRjzHDwUYuwQ9Z3KkDYjlvp84dhvT3ZIOvfW1sWlO1hp.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4iv6pmse6cGhoscId8dX7VYvzZ6wPWdJmcXikq9pGUMwYSBJyMcM0vdDsXune1aDYez3qUNH_u9t0S3I6BoXG5UWg0wNuva0eBbiXGGi87NF2wvVxv5sjK5SUS36TXTY.png) 
        - What is a **reduction? **―The **opposite of a production**, move from a collection of terminals and non-terminals to a non-terminal. 
        - **Need an action that ** _**shifts **_ **a terminal onto the stack** 
            - We want to do the reverse of:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7WS-RBqGPEsOCJLOUK6iSVFNLZJNURA_DXbc5qBgLdrC7kd-2Pq7CFK-bB1x7G5MeLPSJYVA0CRt2EyvJEuRsB0NyAJ6STJi8iE3ZRuQPQ06ozu_ryfX6M6veaE3kWnR.png) 
            - So we need to move z **onto the top of the stack**
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ED2UutU9PdYLua9XcxCSzDbWkuj8EgRPml9MXVHCJsvOBsEBJmfb3p-2slQP41z70Z2UKk_3b62ttkJiPety1ORmNf42OBjxiYydtQQD2kJXRTzp_98tgT-3BIFh6b48.png) 
            - Where is the **nondeterminism in a LR parser**?―You **have to decide** **when to stop shifting** and to **reduce**. Note. Shift and reduce can completely reduce any derivation.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HED0s2RIepNj1LVCQOUVzkGvhn52BNAWg0SzevNYHkVFuUy1bQ73oocSO483LoWq9DjS-Z5nCuRE-ushbunxOB3x1PZddsUuJqJAp9DIpmxBg4QVSx8RiCuvkAwBBfrs.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Y0gSgqq5VyJ2IcZevjOmHyHwhDwio5wsl8Lmq71a7_fB0dXSeF0mA_CUHxrXSEkupFtiyN32jU1g4_WVJV3dG1CGFoLkT09G7GU1xlRONbQTC8t7c4m0VKmYiu-qRaHl.png) 
        - **How do we know when to shift and when to reduce?**
            - LR(0) Items:
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a5k3lOB6TaO4KMMIXaI83EBHj1OGzWtMHiIaz_mhvpgFsj_OVI5RswvnpLSoMg2qWxyEiDSd6uy_ivpyPh2jbsb1Yd8wfNkJjZVYPYhAm4---1-zism7jpMh-TrJ2UDD.png) 
                - What are **LR(0) items**? What are they **useful for**?―For an LR(0) item like $$A \rightarrow \beta \bullet \gamma$$ 
this is a way of saying, **we've seen **$\beta$** in our stack - keep an eye out of a **$\gamma$**. If we have **$$A \rightarrow \beta \gamma \bullet$$
it means **we've seen **$\beta \gamma$** and we can reduce to an A**.
They are useful as the **parser can come up with a set of valid actions at each step, limits non-deterministic choices!** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U-WtX4715FMBEeuoChDh2oupKqhdHawp8AMJ3-1FqpHyluFxvVA-X05KErkbirUe0gqAhqdWZGApc0bWlwWx7OkuIoxHSdflIjIhoMjIxGInYE1XfzV1OjGJ2ZN5yBTN.png) 
                - If an LR(0) item is {{**valid **}}that Implies {{**shifting **}}onto the stack is a reasonable thing to do.
            - In the following, **why does **$\bold{ A \rightarrow \beta \bullet B \gamma }$ **disappear? **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wZreS2bydh4vb2nfmL0eWLSADUEuAgcjbLViMDpphhxwI7SX6pBXDEo99UUvHQZBVoOwXkG1XYFHqShAUI1ELsfTYBxKhokvcLOyCP20798bvJs_iZyPF5P4LlrZnAg8.png)―Because **that LR(0) item is no longer valid,** we've no longer got a $\beta$ followed by nothing.  
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zlvo4vorv-zSGWBViwZgpAIQH8p7h930m_mrtUHfIvH3uESxjLcOXFL2uv-xOzp_cgWrf8sZOnLGDuJuXYWtFsantYqXufGeE9_hGLu_WU7ItnZK977CdDzfCYa9CqcH.png) 
        - **The KEY idea in LR parsing**
            - How does our shift/reduce parser obtain these LR(0) items? ↓ 
                - We **augment the parser with a finite automata** that **gives the set of valid items from the current contents** - the parser can then use this (non-deterministically).
                - These LR(0) items then **become our states to move between.** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zakzdPujCx5zzR7nOoCFK9Cjylgd3kPVQANXxx4na3CySIulvgmugEgpJJXtpa3CShcRV7JN7fTAbwu44QB2djZ4N9XPvZqgBhR2EhBlAMS2RqcRYKUtkp4Uxu3UVovh.png) 
        - **Main LR parsing theorem**
            - Looking at the contents of the stack and reading it from the bottom to the top - that language is regular. **This is what allows this system to work - parsing a context free language but the stack holds a regular language.** 
            - Apparently thats what this says??? ?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6A0tc918QZY52ouOuo-wOPAVAMrnoh8gfUQoF_OdaLaaQBEQLtOHyMqMWF_9urmJ_r7dz0vpiQEvO82CzCX9QRsACPa6ULURclXdqMm16a0fRPVXtwkGLvMvokjD0N61.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H1pCf0X6p8y2RxdCEFRG-i9sVbVOpJYx6ejScyxGfWBqFD_w_3dEMDrArN8zat81XoYEwGSoI_2PIr5KIqen8jAJJywxJVaXoA1C-2QNdmR8QZ69_YRFTrtw1gjQQ28V.png) 
        - **Nondeterministic LR Parsing algorithm**  
            - What are the **four (3+1) options** in the **non-deterministic LR Parsing algorithm**? And what order do you check these options in?
                - If $A \rightarrow \beta \bullet$ **then **POP $\beta$ off the stack and push A onto the stack (i.e. reduce). 
                - If $S \rightarrow \beta \bullet$ **AND **no more input, accept and exit. 
                - If none of the above then ERROR!
                - **YOU CHECK THE OPTIONS IN PARALLEL - THIS IS NON-DETERMINISTIC!!!**
                - If $A \rightarrow A \bullet c \ \gamma$  **AND **c is the next input token. Then shift c onto the stack. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ed3SGPN-GNI0ANX1kZe7O-DUchJHvTWB4B-jElLFJWo2F6no15xrv5ymF87HEPsIbezf0w-DktcDYV9dURL9elXEwpP6UitLVLHZo333Om8t3tr64HGZqJ0kQ_eln2QO.png) 
    - 
-  _**Lecture 6**_   Bottom up parsing Part 2
    - **How do we make our LR parsing algorithm deterministic?** 
        - We will examine two heuristics SLR(1) and LR(1). 
        - The 2 things we need to do to achieve determinism are ↓ 
            - Convert the NFA to a DFA (for getting the LR(0) items)
            - When there are shift/reduce or reduce/reduce conflicts, find some way of making a deterministic choice. 
            - To do this we can **peek into the input buffer. ** And use **FIRST and/or FOLLOW.** 
        - **First step NFA ⇒ DFA**
            - First we add a new **starting production, **$\bold {S \rightarrow S'}$ 
            - We then have the NFA start state, $E' \rightarrow \bullet E$ in our dummy grammar. 
            - The DFA start state is the epsilon closure of $E' \rightarrow \bullet E$ , namely:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/E-i9h02pg34m_-tiHbBZ3Jea8wN2jJhSld0sFmwYvn2BPuaKmhPTYoNdBIW9_iPQYZLxTdVt9r8u0_AEQic7JcPsufyD7cnyAVNkGOm0wPcKwC3HtueqoquyvWy6p4ju.png) 
            - **GOTO (I,X)**
                - GOTO computes the epsilon closure for the DFA and finds the new LR(0) items that can be produced from our current ones:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1CiObykv7UrVu0TA6Ari1p9DPSeHhFsxJ9U_JmTcmLYaxcbF4dnsUoWEJLuFWDAMdqpyF1kmHhlNMCkmyJkbKCP38GE4_lAZ0J2RZwUIxXsVhjPRteeXBwK2GhDbplzA.png) 
            - **Some DFA transitions:**
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/khT7pbiVl5tIgymUdYd6LXg3Z8fcSIRw3FL3La7ZLHwmJ3Sep8UK72nnLAFp2TovkywyT80EO76WDdHOT8GI3JdfSff4yY8XB5qaBwAlq_8A1niu-Ba1nqwKDO6J7p7T.png) 
            - **Given the following full DFA: **![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QLvlOjMyNj61xT01v3RIvYeCGmgXXHGt_cWqTqlZnqygRKASe-8B8sv8FA0_d_P2K3g4-y6hyQM4BzBxR2pjZ13Txtdzt9Mj0OT7Xt-EMkeT9n0aZd5pfFpz5anYVi3G.png) 
**Describe the procedure of parsing (x+y) using SLR(1)**  ↓ 
                - We start at I0, and have (x+y) in our input buffer. So first we read a left parenthesis and shift to I4.
                - Then at I4 we read a **id in our input buffer. **So move to I5. 
                - In I5 we have **no transitions, so we transition our id to an F **(We may also have noted that a PLUS CAN FOLLOW A T_) **. **Meaning we have (F on our stack and +y) in our input buffer. **After computing a reduction we return to the start.** 
                - We read a left paren and an F on our stack so we transition to I4 and then to I3. Transition our F to a T and go back to I0. Stack: (T  input: +y)
                - Read left paren and T, so we transition to I4 and then I2. We use **FOLLOW and find + is in the follow set of E, **and see we have no * on our stack - so transition T to E. (E AND +y) 
                - Read left parenthesis and E, so we reach I8. We shift our + to the stack and transition to I6 (We see no right parenthesis in the input so no conflict). STACK: (E+  INPUT: y)
                - From I6 we shift an id onto the stack and transition to I4. We then repeat the previous procedure until we end up with STACK: (E+T   INPUT: )
                - We then transition to I4 ⇒ I8 ⇒I6⇒I9. And our whole stack transitions to an E. STACK (E. INPUT: )  
                - Then (E) ⇒ F⇒T⇒E⇒E' ⇒ ACCEPT
            - Whenever we perform a reduction, we need a {{reason }}to perform that reduction - usually examining the {{follow}} set of the state we're going to change to, and matching that with what's in the {{input buffer}}.
            - **SLR(1)**
                - How does SLR(1) (Simply LR(1)) avoid shift/reduce conflicts? ↓ 
                    - Shift if the token directly after $\bullet$ is the next item in the input buffer. 
                    - Reduce with $E\rightarrow T$ if, the next token in the input buffer is in the **FOLLOW(E)** 
            - Is there a better method to storing the terminals and non-terminals derived on the stack? E.g. is there a better method than having (E+ ⇒ (E+id ⇒ ...―Yes! Instead store the state on the stack, means we don't have to start again each time and work through the derivation. We can just take one step backwards. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LZsARoFdyakEIEdHVWY_MEzGrCGtGzyPI4ucAZGnL4-F0rwDwisc8ouy5nXbG_ZTlpRIUogjMIFrxI1JBmgVsNnjg_CbNZCM7DnWaBlK2e0wKBsvreodVTE86WAUV783.png)  
(This is continuing from left to right)
            - **LR Parsing with DFA states on the stack**
                - Describe what this code is doing: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/O5EGctEiAFIndq3J5tIlwMTZwGnRMdp6V1kCptFPa7und534__JfAcx2ia-5ShHnB8Vxztrz9vO6gmAo6nJtJJPNb0Ds4wdnaUgIpYzFTm8x8q_3JCfe_Wqa9r_GB_ri.png)  ↓ 
                    - ```python
 a = "first symbol of input"
 while (true)
 	s := TOP_PIECE_OF_STATE
 	# If we're at state s reading an a, 
 	# and there's a transition t to another state
 	if ACTION[s,a] = shift t: 
 		push(t)
 		a := "next input token"
 	# Otherwise we can reduce and step back down the states
 	elif ACTION[s,a] = reduce A => B:
 	 	# Step down the states as many symbols as we've popped
 		pop(sizeof(B))
 		t := "top of stack"
 		# GOTO gets the next state
 		# We then push that next state onto the stack
 		push(GOTO[t,A])
 	elif ACTION[s,a] = accept:
 		accept()
 		exit()
 	else:
 		ERROR()	 
```
            - **ACTION and GOTO for SLR(1)** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WIdoKHTtPBGHuRHMTek6LPUDQD_b3qoLNm-RBAPQLE6WQasCOQ47xVFSYt993d4Kxt5OukGKinKV-QVVw4ABqNaQqHMqmiEybzKLwZ_vUU0VW012-IQvsjDAb0JlszRu.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KDLBVJq5R0uKi788OvQo8DiPy0162kREb4mSSgpqTt2sSxigkuEVTDtIe1KQ9EMHYPnZeeWDs8IsWla1BJGmklJ4yXFgRP3w37f0v4Akq9dfs3c3AG-IMUXPPqAXRQg2.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dL0HJX1QDJt5ID-ehcs8sECQd4ADhRPtxbM4_W6NtCeN5sHX0TOyRtQCUh8D1LTAPKIYlZbH3e6JplRGee18r0gpiL7aSoe9Hrqv2diZF4V7i7u5kzbpfkEOo2_T3uWl.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eoSNGMD_X5YNsXA6TlFUlfKnqCe0bjkmyw_fbaGRNj6NgvIBNy9VqlKc6oYckdELH4UxRHqiiVMAdolE5kc-6j4FIZMkYcnRR_Mmo5_iKTQU59GLEHDdR9Mhy7X58FKz.png) 
            - We can have cases like this:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eH6twCP1i6wsOUTUnl15AqGxZK3wjaxnDTcaHetngzCb-i-Gn_JqzFnulw_I8e6JlI2xPRDd3NE1IbttNO0rlSB8p0hFd0e0JRgkKdBLSlBNe31y3zaKTsRUETG4MGP9.png) 
Where = can be shifted, **but equals is in the follow set of R. **So we have a shift/reduce conflict. 
            - **Beyond SLR(1) ⇒ LR(1)**
                - LR(1) parsing has items of the form $$[A \rightarrow \alpha \bullet \beta, a]$$
where a is an explicit look-ahead token 
                - In the SLR parse table, the AST links nodes when we reduce!   
    - 
    - 
-  _**Lecture 7**_   SLANG Compiler Part 1
    - We'll start with a high-level interpreter based on semantics, and **derive **the stack machine by a sequence of semantics preserving transformations.
    - **Parsed AST vs AST** 
        - In the Parsed AST we have locations coming from he Lexer - points to the line and where in the line (of the input code) the token came from.
    - Parser needs to return the type of expr that will be returned e.g. ```haskell
 expr:
 | simple_expr 		{ $1 }
 ...
 // $1 is the AST built from expr 1, $3 is the AST from expr 3
 | expr MUL expr 	{ Past.Op(get_loc(), $1, Past.MUL, $3 }
```
    - Static Analysis type checking easy for Slang: ```haskell
let rec infer env e = 
	 match e with
	 -- bind the type with the expression
	 | Unit _		 -> (e, TEunit)
	 ...
	 | Deref(loc, e) -> make_deref loc (infer env e)
```
    - **High Level interpreter**
        - Built on top of OCaml:
        - ```haskell
type store = address -> value
and value = 
	| REF of address
	...
	-- Uses OCaml functions to build SLANG functions
	-- Note that Slang has assignment which we have to
	-- keep track of 
	-- I.e. we CHANGED the store so return it
	| FUN of ((value * store) -> ( value * store))
	
-- Evaluation environment, bind variables to their values
type env = Ast.var -> value

-- And expression, an environment and a store goes to 
-- some value, and a altered store
val interpret : Ast.expr * env * store -> (value * store) 
```
        - 
        - Actual interpreting: ```haskell
 let rec interpret (e, env, store) = 
 	match e with
 	| Unit 				-> (UNIT, store)
 	| Var x 			-> (env x, store)
 	...
 	| Seq [e]  			-> interpret (e, env, store)
 	| Seq e::rest		-> let (_, store1) = interpret (e, env, store) in interpret (Seq rest, env, store1)
 	...
 	| Assign(e1, e2) 	-> (match interpret(e1, env, store) with 
 							| (REF a, store') -> do_assign a (interpret(e2, env, store'))
 							| v -> complain "runtime error ..."
 							)
 	...
 	| Fst e 			-> (match interpret(e, env, store) with
 							| (PAIR (e1, _), store') -> (e1, store')
 							| (v, _) -> complain "runtime error: Expecting a 				  Pair!"
 	...
 	-- Update the environment to have x in v - then evaluate s with this in place.
 	| Lambda(x,e) 		-> (FUN (fun (v,s) -> interpret(e, update(e, (x,v)), s), store)
 	...
 	| 
```
-  _**Lecture 8**_   Derivation of Interpreters 1 
    - **Datatypes used in SLANG ** 
        - **The basics** 
            - $N$ - set of integers 
            - $B$ - set of booleans 
        - **More interesting** 
            - $A$ - set of addresses 
            - $I$ - set of identifiers (variable names) 
            - $Expr$ - set of L3 expressions 
        - **Most interesting**
            - $E : I \rightarrow V$ - set of environments. Takes identifiers to values 
            - $S : A \rightarrow V$ - set of stores. Takes addresses to values 
        - **Values themselves:**  \
            - $$V = A \ | N  \ | B \  |\{()\} \\ | \ \  V \times V\\|  \ \ (V+V)\\| \ (V\times S) \rightarrow (V\times S)$$ 
    - Need to make sure this is well defined.
    - The M Meaning function, takes a (well typed) expression, a set of environments and a state - and returns the value the expression evaluates to and a state. $$M : (Expr \times E \times S) \rightarrow (V \times S)$$ 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QMEmU5Wlw2JhjlAYC7asW310MWu7rAbFVEH7J510SaHa0dkFrVCQJjFFyCpLeBZ4LmgwyT48IX63aOezaKrA7w7vF2AJ4GrtLBp1-xCEth_9ncPdIz5XG-OSZk_2rDJj.png) 
    - Runtime Stack
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jDmO1mKZTmgd5-AlMDIvON2gJRyi8b1ao_nRmJHiK-6MybB_p-IhaNUOI6Es9oLG79ryjtnTfnG4PEecagVgCosnc-omH7wTlfRyZKDG9Ww6n436zWdFK7eqUW4kjN9r.png) 
        - h calls g calls f. Activation record for each function invocation.
    - Tail Recursion
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jZV4LPJUhv2kiQ40zZqXTuQEEBLkZ08vUM_ky6Mj5g3EnSKgRKOMD8Eh13rjvUntbqnYQRIaVHwx-7FZBa_5MoQySWBMxKWUZJnN04mpJp2js-P2FyWuPIuFoEZnGN3y.png) 
        - **A tail recursive function can be converted to a tight loop** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bAcsOPDbszWT4O17zSzuwdyi73wor519XCrRAzD4Im8JlXbXwGCdAt7jwAQ19z81bOciYqUt1TX4jD3bGtcKDViIfrdG7TlKAGW_G69qrSiL0L1q3HMDK80m9dmCmxFN.png) 
        - **NOT tail recursive**
        - We cannot always convert tail recursive functions to iterative ones automatically, (in complex programming languages **with state involved**). 
        - But for OCaml, we'll consider all tail-recursaive OCaml functions as representing **iterative programs.** 
        - Any recursive program can be converted into a tail recursive program! 
            - We add a **Continuation argument, **containing the **rest of the computation.** This is called the continuation passing style (CPS) transofmration. We'll then defunctionalize these continuations and represent them with a stack. Finally, we obtain a tail recursive function that carries it's own stack as an extra argument. 
    - **Continuation-passing style (CPS)** 
        - A continuation is where a function continues on to. These functions we carry implement a stack. 
    - **CPS transformation of fib**
        - ```python
def fib(m):
	if m <= 1:
		return 1 
	return fib(m-1) + fib(m-2)


def fib_cont(m, cont):
	if m <= 1:
		return cont(m)
		
	# First we figure our fib(m-1), then fib(m-2)
	# finally we need to get the sum of the two
	return fib_cont(m-1, 
		lambda a : fib_cont(m-2, lambda b: cont(a + b))
	) 
```
        - Depends on order of evaluation or +. We assume the left side get's evaluated first.
        - **Note: **This makes the order of evaluations explicit!
        - Need to pass an identity function in the cnt at first.
        - Course-of-values induction needed as we call with m-1 and m-2. Course of values induction means rather than assume some statement is true for all k (and proving that implies it's true for k+1) we assume for all n < m.
        - **Proof by induction of correctness**
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d4nS4A7lMAI5nVjoC8dw_FEEMyn8Wd9UPGjsq3KDPiy8ElByRFwOAfhQUs7bgX2qa9vsBk_A2mliDSWkrEAJhKovT8ko9_JNJ10gxLp1o4vPYw8aTG10gJ87dKcCPpDk.png) 
            - First we define what we seek to prove and find the base case.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qY3cEFR8toYKQJLDs7F18MLaPGdB5j4EdR7F0OcU2AI6jxcWL_7II60h9HPMxCkwrBnTzHYEYyCfa2xRubUAf2Ee4bif7FGxO9bPe3y4qA4SO_cr5xlnujPxwKvZ6m2r.png) 
            - In the last step we apply the induction hypothesis, applying fib(m) to our continuation 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qLz4sxJsXKnXkX0qOYDcNPspIXOZ0t0qxy1nwhavwHvl3Bm1DspU6avkOAeBE42LlwaseN_33jdht5kldxm2b_lPSRN-1ZvvC1eEVYgsdqtT-7koMjETb-DhmYMDRUoh.png) 
            - Line 2 uses the induction hypothesis again. We then pull fib(m-1) into b. By inspection we notice fib( (m+1) -1 ) + fib( (m+1) -2) = fib(m+1)
    - **Defunctionalisation (DFC)**
        - Replace the functions with datatypes. We can do this because the types of functions we're introducing are really simple. 
        - ```python
# (* datatype to represent continuations *) 
type cnt = ID | CNT1 of int * cnt | CNT2 of int * cnt;

# (* apply_cnt : cnt * int -> int *)
let rec apply_cnt = function 
	| (ID, a) -> a 
	| (CNT1 (m, cnt), a) -> fib_cps_dfc(m - 2, CNT2 (a, cnt))
	| (CNT2 (a, cnt), b) -> apply_cnt (cnt, a + b)
	
# (* fib_cps_dfc : (cnt * int) -> int *) 
and fib_cps_dfc (m, cnt) =
	if m = 0 
		then apply_cnt(cnt, 1) 
	else if m = 1 
		then apply_cnt(cnt, 1) 
	else fib_cps_dfc(m-1, CNT1(m, cnt)) 

# (* fib_2 : int -> int *)
let fib_2 m = fib_cps_dfc(m, ID)  
```
        - We form 3 data types that act as tags that tell us the function to compute, namely:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WgI625yRK4dDX5bHFVOT5PuGKm3_iJf6GqCBIzHtOu3sTf-EM6THqXkuJg8HhmTQs70Xr2iNBvo21MmuVB4VHOSSsfo4DKD40iJ4m4EueJ4UQTpXMaBcYPFVyf6w03Ag.png) 
        - We can think of this:```python
type CNT = ID | CNT1 of int * cnt | CNT2 of int * cnt/
``` as a list with two types of cons!!
        - So we can replace the continuations with lists! ```python
 type tag = SUB2 of int | PLUS of int
 
 type tag_list_cnt = tag list
```
        - So our possible tags are the list containing SUB2 and PLUS - the stack becomes more obvious now! 
        - ```python
type tag = SUB2 of int | PLUS of int 

type tag_list_cnt = tag list 

#(* apply_tag_list_cnt : tag_list_cnt * int -> int *)
let rec apply_tag_list_cnt = function 
	| ([], a) -> a 
	| ((SUB2 m) :: cnt, a) -> fib_cps_dfc_tags(m - 2, (PLUS a):: cnt)
	| ((PLUS a) :: cnt, b) -> apply_tag_list_cnt (cnt, a + b)

#(* fib_cps_dfc_tags : (tag_list_cnt * int) -> int *) 
and fib_cps_dfc_tags (m, cnt) =
if m = 0 
	then apply_tag_list_cnt(cnt, 1) 
	else if m = 1 
		then apply_tag_list_cnt(cnt, 1) 
	else fib_cps_dfc_tags(m - 1, (SUB2 m) :: cnt) 

#(* fib_3 : int -> int *)
let fib_3 m = fib_cps_dfc_tags(m, [])  
```
        - **NOTE: **If we have two mutually tail-recursive functions, we can always reduce that to a single tail-recursive function - we simply introduce a datatype indicating which function we're using at the time. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qeIJGGHORRHaqVVHauTI0yTqvbV9IqIP_PpLX2uIX3jn17TOoYVue1EYE6A4X3-mDiRgZ2mFdS1ybY5XZ1P4ywJqZMNXL8C9eDHSAvsMErMEmB8RX5JimUTilcOIEFyT.png) 
        - Finally we obtain the **fibonacci machine:** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oFTKuyK0FJNfyCgKr8dqPIEuCxFT2vmFTwrWC_AcIX0ZJCikHo8Y6usJryxNMMbMUzC-DZa-vpwSrq_kSz_xQAyEMOfoGfjwmHR1cg3RV5EZhvNMsRvDmuZxuKmN1wU2.png) 
- 
-  _**Lecture 13?**_  Garbage collection and simple Optimization
    - **User library management** 
        - Gives garbage collection to higher level languages - but programmers can be too clever and make mistakes.
    - Garbage collection, remove any data in the heap **not reachable **from the root set.  
    - Some languages disallow cyclic datastructures - meaning reference counting can be used.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/v8xsmNF9W7C2IiwBmuu6Kiw3htgcNd93Q1nFiAAwiGYN8gY25DYn5PGiH6yxUkfdC1Lw61UjNJCxtGIjsK010W5o684KNgdMk1Zmjkg6GWu6A_7bycQqTViQRmreEGl3.png) 
    - 
-  _**Lecture 14**_  Static links on the runtime stack
- 
- 
-  _Supervision 1_ 
    1. **Describe the three stages of a typical compiler frontend (lexical analysis, parsing and semantic analysis), including their inputs and outputs.**
        -  _Lexical analysis_ : Given a character stream (written in the source language) and a set of regular expressions defining many lexical classes (in priority order) the lexer deconstructs the character stream into a set of words and outputs a set of tuples containing each word and its corresponding lexical class: $$(i_1, w_1), (i_2, w_2), ... , (i_n, w_n)$$
^^I'm actually a little confused by this - as in the lectures he describes it as above. However, in the Dragon book it says the tuples are the lexical class and a pointer into the symbol table.^^ 
        -  _Parsing_ : Given this set of tokens & lexical class tuples - the Parser forms a **Concrete **syntax tree of the tokens and outputs it. This concrete syntax tree has operations as it's inline nodes and children are arguments to that those operations.
The parser finds if the input set of tokens, is part of the language defined by the formal grammar. It will emit an error if the input set is not.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tbKxJtHiCp3CbBxRlp_EkyQAP1XqKc-OpuMSQjnwUL-rQtkYOd8jufcrGm36SvfsOUtctR4_Gov8suG6V7c0iMfP5dcJ81OUZcyISggeE9MHYqlueMkJH0ExCKUMhooT.png)
This also defines an order of operations. We work bottom up, first performing the multiplication then the + the the =. 
Errors can be detected at this stage and error messages can be produced. E.g. no whitespace between a number and the start of a variable name. 
        -  _Semantic Analysis_ : Semantic analysis takes this AST and tests it for semantic correctness. E.g. are the scoping rules upheld, does each operation have the correct **type **of operands (type-checking). Some **coercions** can also occur here, where a incorrect type is massaged into being the correct type - e.g. an integer is converted to a float when multiplied by another float. The output is a **Abstract Syntax Tree. **The abstract syntax tree has none of the extraneous elements that are not needed to generate the intermediate representation.
Semantic errors can be detected at this stage and error messages can be produced.
    2. **A student proposes doing away with the lexer and writing a parser which operates directly on characters rather than tokens. What advantages and disadvantages might this have?**
        -  _Disadvantages:_ 
            - During recursive descent parsing, we would have a **huge **number of stack frames as every character would result in jumping to a different function. 
            - We would have to have recursive descent parsing functions for each character, with cases for every character. 
        -  _Advantages:_  
            - Don't have the overhead of using or implementing a lexer
    - 
    - REST OF THE WORK IN TXT FILE 
    - 
-  _Supervision 2_ 
    -  _**Tim Questions**_ 
        1. ```cpp
s -> •t
s -> t•
t -> •u
t -> u•
t -> u•->t
t -> u->•t
t -> u->t•
u -> •bool
u -> bool•
u -> •int
u -> int•
u -> •unit
u -> unit•
u -> •(t)
u -> (•t)
u -> (t•)
u -> (t)•
u -> •u re
fu -> u• ref
u -> u •ref
u -> u ref• 
```
        2. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ekdpc2F2HR6gwzZ-Ot_X63u20rCKJU_gy7jdsMGR1Lj-Hn7g_uVkgVnCNV-u6IQryLnI_6VN7GtE6GaN--MFhW2Bb4glXbq3jCqKXHvFLXZP1O86t2qemmp2Ln73p_2M.png) 
        3. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dgGvLkWfTqKT9D52nB0O2dCzuejRS8t1leh9-Y5h9iZ1wcRDXD0DxfqKCdfKrRWZ7oPvy4VbydU79JWAje6a0P38dax3_GgOwa9h-UCgaWz3Qll0kUer4aKg8tSt0InI.png) 
        4. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Irv6di9gs55RekJujLdRwMp31s3XBTnk3JD8jGwn_sR-HcAiQ7iu3D9cEU1F-CGf9p_KWRw5wap1tklKED7F7vZ8kGcg2xEH8TfjHHKOyx-Ifg8dB3alXkORi7XGuSeC.png) 
        5. A reduce reduce conflict is when we could perform two different reductions from the same input character. This SLR parse table contains none of these.
A shift reduce conflict is when we could reduce immediately, but there's a possibility of a different reduction in the future if more items get shifted onto the stack. This SLR parse table contains none of these.
        6. Don't understand this at all. Neither what LR(1) does, nor how to construct a DFA with lookahead 
    - [**2012 Paper 3 Question 4**](../y2012p3q4.pdf.md)** Parts (a) and (b)** 
        - A.) Define the following terms
            - i.) A non-terminal symbol - a non-terminal symbol is a symbol which can be replaced by terminals and/or non-terminals in a derivation step, as ascribed by the grammar rules.
            - ii.) An ambiguous grammar is a grammar which allows for a sentence to be via more than 1 derivation chain.
            - iii.) A production is a rule for transitioning one or more non-terminals into a string of terminals and/or non-terminals
            - iv.) A context-free grammar is a grammar which can be generated by a pushdown automata. The application of the productions requires no outside context other than the string of terminals and non-terminals on the stack currently. Every production rule produces a single non-terminal.
            - v.) A regular grammar is a grammar which can be generated by a Finite State Machine (DFA or NFA). Productions in regular grammars are of these kinds: $A = a \ | \ bB \  | \ \varepsilon$. Where A & B are non terminals and a is a terminal.
        - B.)
            - i.) "cat"+0 
            - ii.) During Semantic Analysis - We've not done that yet in the lectures
            - iii.) ```cpp
Var -> x | y
Str -> "cat" | "dog"
Num -> 0 | 1
Exp -> Str + Str | Num + Num | Var + Exp
S -> Var := Exp | S S
```
            - iv.) Because we would need to create new productions for every function that takes two operands in our language (with every correct combination of types) which would make the grammar massive and unreadable.
    - [2020 Paper 4 Question 4](../y2020p4q4.pdf.md)
        - a.) ```cpp
 S → 
BAb →
BBBb →
BBeb →
BSdeb →
BAadeb →
Bcadeb →
ecadeb
```
        - b.) ```cpp
 S →
BAb →
eAb →
eBBb →
eSdBb →
eAadBb →
ecadBb →
ecadeb
```
        - c.)```cpp
S → Aa | BAb
A → BB | c
B → Sd | e


FIRST(S) = {}

We can have an A first in S, or a B - so it'll be the FIRST(A) ⋃ FIRST(B)

FIRST(A) = {c}
c ⋃ FIRST(B)

FIRST(B) = {e}
e ⋃ FIRST(S)

FIRST(S) = c + FIRST(B) + FIRST(B) = c + e + FIRST(S)
 	     = {c,e}

FIRST(A) = {c, e}
FIRST(B) = {c, e}
FIRST(S) = {c, e}


FOLLOW(A) = {}
Examining all the rules, Aa -> a can follow, BAb -> b can follow.
Next consider Sd, S cannot goto an A alone, so d cannot follow
∴ FOLLOW(A) = {a, b}

FOLLOW(B) = {}
FOLLOW(B) = FIRST(B) + FIRST(A) = {c, e}

FOLLOW(S) = {}
Sd -> d can follow. And it could be the accept so $
∴ FOLLOW(S) = {d, $}

FOLLOW(A) = {a, b}
FOLLOW(B) = {c, e}
FOLLOW(S) = {$, d}

```
        - d.) No, because the grammar is left-recursive. S -> Aa -> BBa -> SdBa
        - e.) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RJPkFSaQ1I1IdMygv68aIVqpofJ2mbcrO0cYBOiVmICWXXsfwfhs6xIccgSxyCHENYvdUDMZTnE4d7ElHrbxUR3Yv2vQQpkUrO38xI67TshlFKolycje4YRjqMZpYfYi.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UtjPh7EYwkhJUQIHcu34fj6wVSXN11A4auLD2RV7grdK-LTvOciskX2vvhDNDMrl5B6PpdhoMz89xWsrbhrbgay9iF-JGvOyE8yj3hI9obsHkoY1e1eSd6QZt-ymJQgi.png)
By inspecting the SLR table we find there are no such conflicts 
            - 
    - TEST FOR SLR CORRECT
        - No 2 reduces (reduce reduce conflict)
        - SHIFT or reduce 
    - 
-  _Supervision 3_ 
    - **Main Questions** 
        1. Continuation passing style makes the current state and the next step of a computation items that are passed over the course of the computation, similar to tail recursion where only the state is passed. It allows us to easily analyse the stack that is being passed, and allows for defunctionalisation where the function being passed is converted to a datatype. But on its own, the possibility of pausing execution and resuming it when you wish allows for greater control over control flow - allowing for the implementation of exception handling, multithreading etc.
        2. ```haskell
let rec gcd (cont) m n = 
	if m == n then cont m
	else
		if m < n then 
			gcd (fun v -> cont (gcd (cont) m v) ) m (n-m)
		else
			gcd (fun v -> cont (gcd (cont) v n) ) (m-n) n;;
``` 
        3. ```haskell
let rec map cont (f) ls = 
	match ls with
	| [] -> cont []
 	| a :: rest -> map (fun v -> cont v @ [(f a)]) (f) rest;;
```
        4. ```haskell
let rec fib m = if m < 2 then 1 else fib (m - 1) + fib (m - 2);;

map (fun x->x) fib [0;1;2;3;4;5;6;7;8;9];;
// this works 
```
        5. Defunctionalisation replaces higher order functions with a data structure - it allows for easier serialization of the program, allowing to split up different actions (allows for splitting computations across different cores/computers) and form a interpreter.
    - 
    - [2014 Paper 3 Question 5](../y2014p3q5.md)
        - a.) The tail recursion eliminates the need to generate a stack frame for each function call - as all the state required for the final computation is carried in each function call. So iteration can be used and only a single stack frame is needed - resulting in less memory being needed and the time walking through the stack frame at the end is no longer needed.
        - b.) ```haskell
 let rec fact n =
	let rec cont m a =
		let counter = ref m in
		let acc = ref a
		in
			(while (!counter > 1 )
			do acc := !counter * !acc;
				counter := !counter - 1;
			done);!acc;
	in cont n 1;;
```
        - ^^c.) Not really sure about this question  ^^
    - 
    - [2016 Paper 3 Question 3](../y2016p3q3.md)
        - a.) Tail recursion is a method of recursion where only a single stack frame is used, and the entire state of the computation is always held by a single function instance. This means the recursion can be replaced by iteration, and we don't need to spend the time winding down the stack nor the memory building up the stack.
        - b.) ```haskell
 let rec foldl (f) l =
	match l with
	| x::y::[] -> f x y
	| head::tail -> f (head) (foldl (f) tail);;
```
        - c.) ```haskell
 let rec is_even n =
	if n = -1
	then false
	else not (is_odd (n - 2))

and is_odd n =
	if n = -1
	then true
	else not (is_even(n - 2))
```
    - 
    - [2017 Paper 3 Question 4](../y2017p23q4.md)
        - ```haskell
let rec eval_cps (cont) e = 
	match e with 
	| Integer n -> cont (INT n)

	| Pair (e1, e2) -> eval_cps 
						(fun n1 -> 
							(eval_cps (fun n2 -> 
										cont (PAIR n1 n2)) e2)
						e1

	| Apply (f, e) -> eval_cps (fun n -> cont (eval_function (f) n)) e;;
``` 
        - 
    - 
    - 
    - [2018 Paper 4 Question 4](../y2018p4q4.md)
        - a.) We will need to use stack pointers which point to the top of the stack, and frame pointers which point to the top of the current frame/computation (i.e. the current function being computed). Then when a function is called a stack  is used to which contains the address to return to and the argument to the function. 
Implementing the stack frame will be made easier as there are only first-order functions, we won't have functions as arguments and functions can only take a single integer argument.
        - b.) For a element of type t we need to allocate the number of ints contained in the datatype. This can be calculated recursively via ```haskell
 to_allocate = function
 	| int -> 1
 	| Prod a b = (to_allocate a) + (to_allocate b)
```
        - c.) The base case of the evaluation of a int is to place it on the top of the stack. For left-to-right evaluation first e1 would be evaluated, then within e1 the left most item would be evaluated (we are computing a depth first evaluation) placing ints on the stack and returning when we meet them.
((1, 2), (3,4)) ⇒ 1 2 3 4 (top of stack)
For right-to-left evaluation the opposite would be the case.
        - d.)
First we would evaluate the value as on c (depending again on left/right evaluation order). We would then shift the stack pointer down to_allocate(e2) positions for fst.
Then for snd we would need to for each item in the top to_allocate(e2) shift them down to_allocate(e1) positions and then shift the stack pointer to_allocate(e1) positions - this would have the effect of overwriting the first values.
    - 
-  _Supervision 4_ 
    - Slightly off topic question, but I read here [Phases of translation - cppreference.com](https://en.cppreference.com/w/c/language/translation_phases) that \n in code results in lines being concatenated - when would this be present? Are they talking about a general newline character?  
    - **Code generation, ASM, linking and loading, ABI, ELF, x86**  
        1. Discuss the advantages and disadvantages of having a single compiler with many target-specific backends vs a compiler that targets a virtual machine which has been ported to the same set of targets.
One can consider a targeted virtual machine to be a separate backend compiled at runtime - this has certain benefits including:
⇒ Runtime security and memory safety checks can be performed on the bytecode, such as array bounds checking or types of garbage collection.
⇒ We don't need to distribute multiple binaries of programs, only multiple VM binaries - and as there will be far more programs than VMs this is worthwhile.
⇒ We don't need to redistribute binaries for all our programs when the backend technologies improve - only the VM need be updated. 
⇒ "It can also provide a foundation for efficiently implementing many dynamic language features." - just parroting this from stack overflow, not 100% sure why this is the case.
It also has downsides including:
⇒ Because the compilation needs to be done at runtime, certain slow and costly performance improvements cannot be performed - this means code may run slower.
⇒ We now have the additional burden of loading the compiler when we run a program, meaning programs are slower to load.  
        2. What is a linker? What are its inputs and outputs?
A linker takes object files as input, and combines them to form a single executable file as output. The object files contain certain data about the program that the linker can use, this includes the symbols to be exported and imported, (not 100% about this) the locations of addresses that must be relocated and constants used in the program (not 100% sure why constants need to be specified). 
        3. Give examples of programmer errors detectable only at link time.
If a programmer writes the wrong name for a method in another file. 
If multiple methods (in different files) have the same name, type signature and parameter types/num parameters. 
Variables defined multiple times in different files. Multiple declarations could throw an error too, depending on the language.
        4. What is a loader? What are its inputs and outputs?
The loader takes an executable program, loads it into memory then runs some preparatory code before passing control to the program code. The loader is part of the OS. 
Dynamic linkers link libraries or files to already running code at runtime, they load files into memory and can thus be thought of as loaders. They take object files.
        5. Give examples of programmer errors detectable only at load time.
If a dynamically linked library is used incorrectly, e.g. incorrect method name or type. If dynamically linked libraries contain additional definitions of methods or variables. 
    1. **Register machines, simple optimisations, OOP, exceptions**
        1.  _What are the _  _**advantages**_  _ and _  _**disadvantages**_  _ of caller-saved vs callee-saved registers?_ 
Caller-saved:
Don't have to worry about the callee messing with your values (even if accidentally). The callee doesn't have to worry about overwriting any values, can just execute their function and use whichever registers they like. Means you have to save all the registers on the stack, even if none of them would get overwritten, this takes time - additionally have to resinstate them afterwards.
Callee-saved:
Caller doesn't have to wrap and unwrap (afterwards) all the registers. 
Callee can only save the registers it would actually overwrite (could be none).
Programmer needs to remember to reinstate the right variables, could cause hard to diagnose bugs if a value gets overwritten.
        2.  _Explain a typical layout in memory of objects in a language supporting single inheritance and dynamic dispatch._   
Objects contain fields arranged in a given order in the object data, and a pointer to a vtable containing their methods to be run (the vtable is the first item in the object data). For subtypes, the fields of its parent types are the first field items followed by its own fields - its vtable contains a pointer to each method and where methods are declared and defined as they could have been overwritten (if there are no overwritten functions then this will just be a pointer to the method). Note the order of methods in the vtable is maintained from the supertype.
These features allow for a pointer to a subtype to be treated as a pointer to the parent type.
        3.  _What complications does supporting multiple inheritance pose at a language level and at an implementation level?_ 
We cannot simply treat subtype pointer as a pointer to its parent type, because the fields will not necessarily be in the same order - i.e. the first field could be from class A, the second from class B and the third (the subtype) from class C. If this object is treated as a B type pointer, the first field will be incorrectly interpreted as a B type field. 
At a language level, we could have multiple definitions of methods from supertypes and not know which one to use.
    2. **Garbage collection and bootstrapping**
        1.  _Can a garbage collected program contain unchecked runtime errors?
_ Yes, depending on if the safe-use rules for the garbage collector are followed. For example, programmers shouldn't obfuscate the pointers being used by XORing them together (or similar) as this could result in the garbage collector trying to access data outside of the allowed bounds or messing up the heap.
        2.  _It is alleged that garbage collected programs can contain no memory leaks—is this true?
_ No, for one there are some garbage collection methods that do not collect detectable leaks. For example if reference counting is used, cyclic objects could be formed which are not garbage collected - these could amass and form a large memory leak. 
Additionally, if an object in the heap is being pointed to from the root set - it is possible that the object will never be used again and is thus garbage, however the logic for this would be very complex and slow to decide and is in general undecidable. Thus, such an object will continue to sit there and if more pile up a memory leak forms.
        3.  _"It is impossible to write the first compiler for language L in language L." Discuss this claim. True or false and why?_   
This is technically False, as you could write a translator which translated the whole of L into some MBC which could be interpreted - then you could simply translate this compiler into MBC, then interpret that and compile your compiler to the base language and use that. However, in general writing such a translator for large languages is extremely difficult - and is not necessary in general. Instead we write a translator for a subset of the language, which we then use to compile L. This compiler is finally used to compiler our desired compiler in L. 
        4.  _A devious hacker wishes to write a compiler for their own language L which adds a security flaw to programs it compiles. They wish their compiler to be open source, so people will easily spot their devious hacks. Suggest a way for the hacker to include the attack, even if the user recompiles their compiler._   
The compiler could change the source code of the compiled program, so whenever it is compiled again that same security flaw exists. 
    - 
    - 1. [2004 Paper 5 Question 7](../y2004p5q7.md) 
        - Consists of function definitions which have bodies containing if-then-else, while-do, assignments and (typed) declarations of variables. Only 1 statement or keyword per line
        - For each of (a)–(d), (i) summarise the main phases of work that are done before execution in each case, giving a brief explanation of the main actions of the main interpreter loop (if any) during execution, and (ii) for each of the following possible erroneous forms, explain whether the error would be found before or during execution: malformed syntax, undeclared variable, type error, division by zero.  
        - Note, by the **typical front end** I mean lexing, then parsing, the type analysis and then semantic analysis - where we come out with an AST with correct type information attached. 
        - **a.) Compiling J to machine code
**We start with the typical front end. Then we must compile this to an intermediate representation, we can then perform some optimizations on this before performing targeted changes to the code to transform it to machine code. This machine code will be machine and OS specific, and different methods of translation will be needed to glean the best performance. During execution the machine code can simply be run, no interpreter is present. Malformed syntax, Undeclared variables and type errors will be found before execution. Divisions by zero will be found during execution.
        - **b.) Compiling J to "interpreted byte code" and then interpreting this**
Again we start with the typical front end, then we compile to this byte code representation which will be interpreted at runtime. We are performing JIT compilation. The interpreter must convert the byte code to machine code on the fly and check for errors - it can also provide types of memory safety like array bounding. Malformed syntax and type errors would be found before execution. Division by zero and undeclared variables would be found during runtime.
        - **c.) Parsing J to a syntax tree, then interpreting this
**Before execution lexing, parsing, type analysis and semantic analysis would have occured - however we still need to convert this to an intermediate representation and then to machine code on the fly. The interpretor would need to walk the tree and compute this. Malformed syntax and type errors would be found before execution. Division by zero and undeclared variables would be found during runtime. 
        - **d.) Keeping J in a text file**
The interpreter would perform the front end on the fly, but only line by line - we could not find multi line syntactic or semantic errors. Then the intermediate representation would be formed before machine code would be generated for the line, the line would then be executed. All of the errors would have to be found during execution
    - 
    - [2. 2011 Paper 3 Question 4](../y2011p3q4.md)
        - a.) The static link method attempts to solve the problem of nested functions, and how a nested function is within the scope of it's parent function and thus needs to be able to access it's variables. The static link points back to the most recent method that statically encloses the holder of the static link. When a function is nested within another function, the static link points to the stack frame of the enclosing function - this is stored in the frame control information. Then if free variable is encountered, we can follow these static links to find the value. This is different to calling a function from a method, as the callee does not then have access to the callers methods. 
        - b.) ?
        - c.) When we come across a handle (say e handle f) command, we first build a special handle frame - then we build up the stack frame for e, if e evaluates normally e handle f evaluates to the normal value. If we come across some raise v', we must evaluate f(v'). We then unwind the call stack and pass the value of v' to the handle frame and f(v') is evaluated.
        - d.) ?
        - 
    - 
    3. [2012 Paper 3 Question 5](../y2012p3q5.md)
        - a.) i.) A variable with global scope (can be accessed anywhere in the program) who's memory is allocated at compile time. Thus it lasts for the lifetime of the program.
ii.) A temporary variable stored on the stack who's lifetime is the same as it's invoker function.
iii.) A free variable is a variable that is not bound by the function/scope which it's immediately in, and is instead bound outside of that scope beforehand.
        - b.) Local variables, as the fields value is destroyed when the object is freed from memory similar to the invoker function.
        - c.) i.) 
Statically allocated global variables are allocated at compile time.
Local variables are allocated for on the stack at runtime.
Free variables are allocated for at compile time, as they are simply normal variables but in a lower scope than they were created.
The linker must computer address relocation for statically allocated variables, as when multiple object files are compiled again the data or code addresses pointed to can have changed. The loader then loads the program into memory and passes control to the program.
        - d.) For statically allocated global variables a pointer must be stored which points to the location of the item in memory where it can be read or changed.
Local variables will be stored in registers and can be quickly accessed from those registers.
A free variable's value will not be directly accessible by the method they're in, as its value/a pointer to it will not be in a register. Some languages (like C) would require this free variable to have been in the global scope (if not in local scope) and you would then search there - other languages would have you incrementally search higher scopes (by traversing up the stack frame from callee to caller) until you find the value of the free variable but htis can be slow.
        - e.) ?
        - f.) Because in strongly typed languages you know which items are pointers and which aren't, so you need only follow the pointers to find live objects.
        - g.) Stack based allocation leads to variable length stack frames, meaning we introduce the overhead of managing **both **stack and frame pointers. The overhead of increasing and decreasing the stack pointer is tiny. Stack allocation is much faster than heap allocation, because the stack is usually in cache and can be accessed extremely quickly - however the stack is small, so should not be used for large objects with long lifespans. The heap has the advantage of being large, and is better for longer lasting objects than the stack as we don't have the same pop system as the stack. 
    - 
    - 4. [2017 Paper 3 Question 3](../y2017p23q3.md) 
        - a.) Otherwise objects can build up in the heap (a memory leak forms) until the heap is full and no more objects can be stored on it - meaning objects that may be needed may be overwritten, or no new objects can be added and execution must halt. Garbage collection (mainly automated, less so explicit as errors can occur) tries to prevent this by deleting any objects on the heap that can never be used again - allowing space on the heap.
These languages may need this heap space to function.
        - b.) Garbage is data that can never be used again (in a perfect world we would remove data that **will **never be used again, but in general that is undecidable). I.e. data that has no pointers to it from the "root set", the root set being the memory accessible locally by the program - e.g. addresses stored in registers or on the stack.
Garbage can be located in memory by first marking all elements reachable from the roots set (mark) then sweeping through memory searching for objects not marked (sweep) and removing them.
        - c.) If a sensible number of bits were used to store the reference count, say 32 this would normally require 2^32 pointers to that object in order for a reference overflow to occur - currently this would be far more objects in the heap that we would generally see (except in specialist programs where 64 bits could be used). Cyclic objects would not produce this behaviour, as we only increase the reference count for each **pointer **not on a traversal of the pointer graph.  
        - d.) It depends if the language has side effects, a language like OCaml includes references which could alter the behaviour of the mapping if g is applied to all elements before f rather than f g being applied to each element in order. If x is some ref, g(v) = (!x = !x+1);v;   f(v) = !x * v;
Clearly this will have different results.
However, we can glean a performance optimization here (Inline expansion and constant propagation could be used) where the composition of the two functions need only be calculated once, then the composition of the functions can be specifically optimized as opposed to optimizing the two functions separately. C compilers often do this. This will of course increase compilation time , but could ideally improve runtime performance.

    - 
- 
- 
- 
