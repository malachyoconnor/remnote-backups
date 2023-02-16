- **Lecture 1**
    - In Logic Programming, we're describing the result we desire not the procedure to reach that result. Below is a declarative way of finding the sum:```perl
 sum([], 0)
 sum([H|T], N) :- sum(T, M), N is H+M
```
    - To get to user mode to enter facts, use [user]. ctrl + D.
To load a program,  swipl -s program.pl  
    - milestone(X,Y) - prolog will iterate through all the facts where this is true using semi-colon 
    - Terms
        - Constants - like 1, 2, 3.14, tiger ⇐ an Atom, 'Acre Wood' 
        - Variables - strings with capital letters , X, Sticks. Or _ which is the wildcard
        - Compound - likes(dog, bones). We have the top function symbol (likes) and the **arity **which is 2 in this case (number of args).
**Note**, tree(A,B,C) is a different tree from tree(A,B). Arity is important
    - Prolog tries to unify terms:
        - Atoms unify if they're identical - tiger = tiger
        - Variables unify with anything
        - Compound terms unify if the top function symbols and arities match and all parameters unify recursively.
    - Built in relations in Prolog: 
        - You can declare infix operators: op(500, xfx, taller)
Allows for : andy taller ian. andy taller X. X = ian.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7_wHu1Vi1jgou0UMBpawJwRJXdhiDvAENmM-EsWKkfwZIrTC0iaCCTWC2zmJ0jrGEEESb8wMjR3V_UPmI0atnih7WF_JfuZs_EV1iyEEE5vWKI8Q2ztCqFx15Xi6MLLL.png) 
    - Prolog Backtracking
        - Can be interpreted as a tree, try the first rule and if no progress is made try the second etc.
    - THINK DECLARATIVE, len([], 0) asserts that [] and 0 are associated by the len relation. Write declarative comments %.
Good comment, len(L,N) succeeds if L is a list and N is the length of that list.
    - Prolog Execution strategy -
        - First try the first rule, then the second etc. So ```perl
 sum(X, 0) 
``` This will spit out [] and then continue looping over the second rule forever until you stop it.
    - 
- **Lecture 2 **  
    - ```php
house(Nationality, Pet, Smoke, Drinks, Colour).
(H1, H2, H3, H4, H5).

exists(A, (A, _, _, _, _)).
exists(A, (_, A, _, _, _)).
exists(A, (_, _, A, _, _)).
exists(A, (_, _, _, A, _)).
exists(A, (_, _, _, _, A)).

rightOf(A, B, (B, A, _, _, _)).
rightOf(A, B, (_, B, A, _, _)).
rightOf(A, B, (_, _, B, A, _)).
rightOf(A, B, (_, _, _, B, A)).

middleHouse(A, (_, _, A, _, _)).
firstHouse(A, (A, _, _, _, _)).

nextTo(A, B, C) :- rightOf(A, B, C) ; rightOf(B, A, C).

        // Generate candidates
:-  exists(house(british,_,_,_,red),Houses),
    exists(house(spanish,dog,_,_,_), Houses),
    exists(house(_,_,_,coffee,green), Houses),
    exists(house(ukraine,_,_,tea,_), Houses),
    exists(house(_,snails,old_gold,_,_), Houses),
    exists(house(_,_,kools,_,yellow), Houses),
    exists(house(_,_,lucky_strikes,orange_juice,_), Houses),
    exists(house(japanese,_,parliments,_,_), Houses),
    exists(house(WaterDrinker,_,_,water,_), Houses),
    exists(house(ZebraOwner,zebra,_,_,_), Houses),
        // Test candidates and then backtrack
    rightOf(house(_,_,_,_,green), house(_,_,_,_,ivory), Houses),
    nextTo(house(_,_,kools,_,_), house(_,horse,_,_,_), Houses),
    middleHouse(house(_,_,_,milk,_), Houses),
    firstHouse(house(norwegian, _, _, _, _), Houses),
    nextTo(house(_,_,chesterfields,_,_), house(_,fox,_,_,_), Houses),
    nextTo(house(norwegian,_,_,_,_), house(_,_,_,_,blue), Houses),
    print(ZebraOwner), nl,
    print(WaterDrinker).
``` 
    - Consider, what does exists(house(british,_,_,_,red),Houses) actually do?
        - It instantiates a guess at Houses that fit's the exists rule, e.g.:
Houses = (house(british,_,_,_,red), _, _, _, _)
        - Then it continues to  exists(house(spanish,dog,_,_,_), Houses) and will try with the first rule exists(A, (A, _, _, _, _)) - **this will fail! **Then it backtracks and tries another rule to place the Spanish house. Note, it will only backtrack if it runs out of Spanish options. 
        - This is **non-deterministic **behaviour, Prolog backtracks and tries other rules until it finds the correct set. 
    - Rules
        - rule(X,Y)―part1(X), part2(X,Y). 
        - The rule head is true if all of the body is true. Variables can be internal to the rule.
        - Rules can be recursive:
rule3(ground).
rule3(In)―anotherRule(In, Out), rule3(Out).
    - Lists
        - [1,2,3,4]. [H|T], [1,2,3|T] works too. Also [1 | [2,3,4]]
    - Remember try to read declaratively, so read: ```php
last([H], H).
last([H|T], W) :- last(T, W)
```as last with [H] gives H. Last with a list with a head and a tail should give the last value of the tail. 
    - Don't use OR's i.e. semicolons, instead write the two rules separately:```php
R(a,b) :- X(a) ; Y(b) // no, because its too much like imperative programming
// Instead::
R(a,b) :- X(a)
R(a,b) :- Y(b)
``` 
    - Don't think true or false, think succeed or fail - i.e. Prolog will go off and try and find some unification of variables such that the query succeeds - not true or false. 
    - Unification: 
        - Note that 1+1 doesn't unify with 2 - consider what would happen with 1+x, what would that unify with? "is" is specially purposed to have the side-effect of doing arithmetic.
        - X \= Y - tests if X will not unify with Y.
- **Lecture 3**
    - Arithmetic: 1+2 is just infix notation for the compound term, +(1,2). So 1+2 **does not unify **to 3. 
    - The **is **operator: 
        - To do arithmetic we must use the **is **operator,  1+2 is 3. This is a ... with a side-effect.
        - We **cannot have **non-constants in the right-hand term. 3 is B+2 fails. 
        - **NOTE: **only the right hand side gets mathematically evaluated.** So 1+1 ≠ 1+1.** 
    - Using arithmetic we can write things like: ```php
 len([], 0).
 len([H|T], L) :- len(T, K), L is K+1.
```This says, find the len of a simpler list and then come back - and we'll add 1 to that answer and continue. 
Note that with this is construction, we need to remember to come back to it and so our stack space grows linearly. To solve this we could use an accumulator which uses O(1) space: ```php
 len([], 0).
 len([H|T], Acc, Result) :- B is Acc+1, len(T, B, Result)
``` ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vrYLqC0eXQdUNIsQ1TWbhQkydlV55PeheQgh6EVGp-RMtk3jiFek48wE2NdIO8NQV1bzrpaiunwTQrPLgYvqITheaHsdf42K6snwZZPrM-dpOWp1cgO3lxeMZse8OK2t.png) 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/B5Y9LoMVqmV7Vi852HaGnD07TznN0_iA-ly2MmZKWrYrkfwO7uEp2XmPokEnp3X7YGm2NYh8yCPHPSWDC_Mpof3HVFVB9ikczXSbH-xdsgWoDZTKXbVYl4hH1ZAGVrah.png) 
    - Last Call Optimization
        - If the last clause of a rule is a branch, we can forget we were ever interested in the head at all. I.e. there were no other choices, so Prolog will never have to backtrack to test those other choices!
        - Can only do this if the rule is determinate up to this point.
        - Note that last call optimizations and accumulators are distinct concepts - for example the following code will be last call optimized: ```php
 last([L], L).
 last([_|T], L) :- last(T, L).
```As there is no reason to backtrack if last(T,L) fails - we'd have no other choice anyway.
**However: **Accumulators are the only way of finding out what your answer actually is, rather than just finding out if your input fits the mold 
    - Generating a list:
        - ```php
bigList(0, []).
bigList(N, [_|T]) :- M is N-1, bigList(M, T).
```
    - Backtracking:
        - Prolog searches depth-first left to right.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fWGF4FkXHtnFdkxkyh0G0cXeBiPTbDnHo35JqKV30wUClLp6nb5w-DS_axzTYojkXQrWjd0uTLzEdbNLzWhn-Ho1QsFuwKdcOSfzIr2O-DH8UDO_FWgSRCadxvOesPYX.png) 
    - Code for taking values from a list```php
take([H|T], H, T).
take([H|T], A, [H|B]) :- take(T, A, B).
``` results in 1, [2,3] ; 2, [1,3] ; 3, [1,2].
    - When take backtracks, it needs to undo the variable binding that came from the first successful run. We leave a trail of choice-points where we need to backtrack from and work off of. 
    - Note, for > **both sides need to be ground terms. **So we can't do N > 3 if N is a variable. 
    - Comments syntax:
        - + in front of a variable means you expect it to be instantiated - if it's not then all bets are off.
? means you expect it to be a variable or instantiated - note that if you don't instantiate it, Prolog will just go off and do the computation and then unify it with what you gave at the end.```php
 // % len(+List, ?Length)
 len([A], 1).
 ...
```
    - 
- **Lecture 4**
    - Permutation Code:
        - ```php
perm([], []).
perm(L, [H|T]) :- take(L, H, R), perm(R, T).
```
        - We repeatedly take an element of L, and then perm the rest.
    - Dutch Flag implementation, using the **Generate and test paradigm**: 
```php
take([H|T], H, T).
take([H|T], X, [H|T1]) :- take(T, X, T1).
perm([], []).
perm(L, Perm) :- take(L, X, Y), perm(Y, S), Perm = [X | S].
dutch([blue]).
dutch([X | [Y | T]]) :- X=Y, dutch([Y|T]).
dutch([red | [white | T]]) :- dutch([_|T]).
dutch([white | [blue | T]]) :- dutch([_|T]).

dutchFlag(L, Perms) :- perm(L, Perms), dutch(Perms).
``` 
    - Eval implementation: ```php
eval(plus(A,B), C) :- eval(A, X), eval(B, Y), C is X+Y.
eval(times(A,B), C) :- eval(A, X), eval(B, Y), C is X*Y.
eval(A, A).
``` 
Consider evaluating plus(1, times(4,5)) Note that the second possible answer will error, this is because the value times(4,5) will be input to the C is X+Y - which is an error.
Instead we could wrap our query and answer in some gnd term - this **makes our clauses orthogonal - **i.e. we separate our clauses by cases:```php
eval(plus(A,B), C) :- eval(A, X), eval(B, Y), C is X+Y.
eval(times(A,B), C) :- eval(A, X), eval(B, Y), C is X*Y.
eval(gnd(A), A).
``` 
Note: This now requires plus(gnd(1), times(gnd(4), gnd(5)). 
    - Note that this evaluation can be used to add function support. We can flatten an ML function and then eval it after generating the right rules.
    - Prolog does not lack functions, ML functions can always be converted to the equivalent prolog query. Prolog is Turing complete.
    - DONT USE CUT! 
    - 
- **Lecture 5**
    - Cut 
        - ! - stops Prolog from going backwards from it's current decision, pruning out portions of the search tree. This **only occurs when we cross the cut! ** Note that cut only effects it's parent choice point and the current rule being carried out.
        - A green cut is a cut which simply improves execution speed without changing the logic of the program.
        - A red cut changes the logic of the program.
        - The Danger of cut: 
            - Consider: ```php
 a(1).
 a(2) :- !.
 a(3).
 
 b(X) :- a(X).
 b(4).
```
            - a(Y). will give Y=1; Y=2; 
            - b(Y). will give Y=1; Y=2; Y=4;
            -  _a(3). Will give true!!! _ This is because the unification occurs **before **the cut. 
            - The issue being, all of these queries rely on understanding the Prolog execution strategy - the logical query "**Tell me the Y's for which a(Y) is true**" no longer gives the 'correct' answer because If I asked "**Is a(3) true?**" Prolog would contradict itself and say it is.

This creeps up on you in larger programs.
    - Negation
        - Failure using cut : ```php
 foo(A,A) :- !, fail.
 foo(_,_).
``` This fails if A unifies with A and succeeds otherwise.
        - Negation by failure: ```php
 not(A) :- A, !, fail.
 not(_).
``` If A is true the clause will fail and we cannot backtrack.
        - \+A means not A
        - Negation is dangerous! not(expensive(Restaurant)) will always fail - Prolog will find an expensive restaurant and then fail!
    - Databases in Prolog
        - ```php
tName(mro31, 'Malachy OConnor').

tGrade(mro31, '1A', 2.1).
tGrade(mro31, '1B', 1).
tGrade(mro31, 'II', 1).

// Gets all the names
filter_name(N) :- tName(_, N).

// Get all the grades given a name

get_grades(Name, Y, G) :- tName(Crsid, Name), tGrade(Crsid, Y, G).


``` 
    - The **Search Tree **interpretation of Prolog execution, the tree formed is a runtime stack - this tree exists in space but never in time! Parts of the stack will be whittled down and reformed overtime.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5sneLaR5pDg_AJ_FGpbh8aXkzTmJ-TJkkH1VtIrjRAAKhEjoPr8qKgNca1hdCe2gGj6z9v30QUlNMbtpZ2H-IPAkfRKdOwa3uE8QQ15QLe522WLfSYIgTUqR8SgDIRwr.png) 
- **Lecture 6** 
    - Countdown game
        - Select 6 numbers out of (25, 50, 75) and (1,1,2,2,...,10,10) - get as close as possible to a randomly chosen 3 digit number using ( +,-,*,/ ).
        - Strategy: Maintain a list of arithmetic terms, each "iteration" check if the result is on the head (if it is halt) then pick two of the elements of the list and combine them using arithmetic operations and put the result on the head.
        - My solution: ```php
combinations([A | _], [A], A).
combinations([H | T], [Y-H = R | Mem] , R) :- combinations(T, Mem, Y), R is Y - H.
combinations([H | T], [Y+H = R | Mem] , R) :- combinations(T, Mem,  Y), R is Y + H.
combinations([H | T], [Y*H = R | Mem] , R) :- combinations(T, Mem, Y), R is Y * H.
combinations([H | T], [Y/H = R | Mem] , R) :- combinations(T, Mem, Y), R is Y / H.

:-  perm([125, 100, 75, 100, 6, 3], List),
    combinations(List, S, 300), 
    print(List),nl,
    print(S).
```This is inefficient, as we simply generate every possible permutation to solve the inherent issues with the method (i.e. we should be choosing one item and testing the effects of combining that, not all the effects of combining a permutation).  A better solution would use choose.
    - Choose implementation: ```php
choose(1, L, [X]) :- take(L, X, _).
choose(X, [H|T], [H|B]) :- X>1, Y is X-1, choose(Y, T, B).
choose(X, [_|T], B) :- X>1, choose(X, T, B).
``` Took me a while, but is just a case of choosing or not choosing the head (being careful to not decrement the amount to take when you don't choose the head AND being sure that we can't choose 0 of something and that only the choose 1 rule is used when we wish to choose 1).
    - Iterative deepening 
        - Iterative deepening is having some D generated using range() and iterating through that D, allowing a greater distance from the correct answer if no answer with 0 distance is found. 
    - 
    - Not Provable operator:
        - \+ Goal succeeds if the goal cannot be proven, and fails otherwise. Similar to not. 
    - 
    - Graph Searching
        - First we just label each opening in our maze with a vertex, then encode **some **transitions as vertices: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VKN1iTbbEFM9GpAc_YMKrr6rUWEA8zLr7gCeF6P-8_CyDvzoAHXY7dIGD6UmCGIKxDkP9YcAzhFDNgp3iowboFe5WFlOsuyKjm1ynMUK5FN0WaOvJQiHmgMG7kMFIRuU.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gLmnGw_LCMoUTZVnyaBcPZpR-SiJS-ylAp046MxRPN5rvMwvQlpfcggUzuD4uLAT8VzlPfot9Fc1LQnKd-Fsr9txYmko96W7jFg4QZQ6zvTGF5j166OoAOy6K3oPpW-2.png) 
Note that we only choose the ones that we can reach that haven't been reached already, minimizing the number of vertices.
        - Now we can draw our vertices and edges as a graph.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xxg3SB5kA3O7fGK_1wvShsW2LLvwk3z2pmFRAJ0Xemp3RTRZnnLDj-znn-c4O-ae3ORBtNdZe99kcliS1k5KESK54uer02QYD_UpgFlSg2x3jdCYWFCpji7UaDPezmgT.png) 
        - We define this as: ```php
 route(a,g).
 route(g,l).
 route(g, f).
 route(l,s).
 route(a,b).
 route(b,c).
 route(b,h).
 route(c,d).
 ...
 travel(A,A).
 travel(A,B) :- route(A,X), travel(X,B).
```
        - What if we have a cycle in our graph?
            - We can simply add a list storing all the nodes we've been to, and check for membership before we travel to a node.
    - 
- **Lecture 7**
    - Difference Lists
        - First note that the usual method for defining append is O(N) in space and time. Instead we'd like to append without copying:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_qcs22klGdOGRJBlukaFkNxN_rZMKxvbkpOUOf5zdXFHhbBDfWcess8xcyx3ZiZj7_Ll44Yk-5lxYmrdokEGJLiTX_pLjxiEcf2MPS5JcOQTZmAcoijgwfU87H-TzmFP.png) 
We can do this by making our lists have a spare variable at the end, when we want to append we simply append that variable to the second list.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mCBfB1cLpHyhHtnZ385xFlJMMa4NLdoXjyya-qYON_j9FHU-fkgQUMFlmBnqsl4jHgsQXUprmxvyI5789aE3kwJg8neVzsDpyvRzIYziSOZWRG3-2hv2ahRZFQGjeosc.png) 
We can use the syntax $$[1,2,3 | A]$$ 
        - The resulting clause for combining two lists is (Where the T's are pointers to the variable at the end):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Aee4NYU-eDiAN5SCI6r4joCOp_L4Fg072Ztexnemh_jrgqTNFNzCeUgP7Zj3OzC_NeZHFQ28GvtAFR0WFo0jzJLkNrEQb2JS5YL2nvr2RP5YS386LC7Aw1OiUnAKjb12.png) 
This can then be simplified by rewriting L2 as T1 everywhere then L3 as L1... resulting in: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3zE0JRZHvDKPaLgk8GMInKaF9_wdeBTqrOCwvsC1nbPkJyDXcF_lzQZd1Mi4lnImylyRT6I2jbGtjuDKGcRgmrCK8LO6XTkOM0_Ve8M5qh2nkGjR3p4NlLPr3In1Qlpl.png) 
        - We can then form compound terms to represent that the arguments are related (The minus symbol could be any number of different symbols):
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gjAclqBQGngK26Q3Q8gupLHuFcWrNMiaxtJeJWVPK6t3XS2iLVnYswBilWrUqbX74KYH3P7_peoF-CHKpnahDql66iUj2XwmH5JtLq6Y1dR3W9keRKIvcvKfqD1ZXUcB.png) 
        - When writing code  with difference lists, first write it without difference lists and then rewrite that code to include them. Then rewrite and finally simplify using substitution.
    - Empty Difference lists 
        - An empty difference list would then be represented as A-A. 
        - If we try and unify an empty list with a non-empty list, we find that we get an infinite nesting: $$A-A = [1,2,3|B]-B$$
We've matched A such that it contains itself - resulting in [1,2,3|[1,2,3|...]] 
        - Note that if we **ever **try and match an empty list with a non-empty one, prolog will find that that is possible and happily return an infinite term! So for example if we're trying to find the length of a diff list: ```php
 len(A-A, 0).
 len([_|T]-T1, N) :- len(T, M), M is N-1.
 
 :- len([1,2,3|A], X).
``` This will immediately return an infinite term and 0, as the first rule will be matched with successfully.
        - Solutions: 
            - Grounding our difference list: ```php
 len([]-[], 0).
 len([_|T]-T1, N) :- len(T, M), M is N-1.
``` This will match the final variable with [] successfully, destroying our difference list (the final variable can no longer be unified with anything else). This is a destructive but working solution.
            - Forcing an occurs check: ```php
 len(A-A1, 0) :- unify_with_occurs_check(A-A1).
 len([_|T]-T1, N) :- len(T, M), M is N-1.
``` This checks if the unification works, while ensuring the first variable doesn't occur in the second.
            - ALWAYS force an occurs check, set a prolog flag which ensures we always do this occurs check: ```php
 set_prolog_flag(occurs_check, true).
 // Note: can also do this, which throws an error when an occurs error is found
 set_prolog_flag(occurs_check, error).
```
    - 
- **Lecture 8**
- 
-  _Supervision Work_   
    1. Question 1 
        - 2)```php
|tree(tree(tree(1,2),A,B),tree(C,tree(E,F,G)))   
|tree(C,tree(Z,C))

Unify C with tree(tree(1,2),A,B) resulting in:

|tree(tree(tree(1,2),A,B),tree(tree(tree(1,2),A,B),tree(E,F,G)))   
|tree(tree(tree(1,2),A,B),tree(Z,tree(tree(1,2),A,B)))

Unify Z with tree(tree(1,2),A,B) resulting in:

|tree(tree(tree(1,2),A,B),tree(tree(tree(1,2),A,B),tree(E,F,G)))   
|tree(tree(tree(1,2),A,B),tree(tree(tree(1,2),A,B),tree(tree(1,2),A,B)))

Unify E with tree(1,2) resulting in:

|tree(tree(tree(1,2),A,B),tree(tree(tree(1,2),A,B),tree(tree(1,2),F,G)))   
|tree(tree(tree(1,2),A,B),tree(tree(tree(1,2),A,B),tree(tree(1,2),A,B)))

Finally unify F with A and G with B. Resulting in:

|tree(tree(tree(1,2),A,B),tree(tree(tree(1,2),A,B),tree(tree(1,2),A,B)))   
|tree(tree(tree(1,2),A,B),tree(tree(tree(1,2),A,B),tree(tree(1,2),A,B)))
```
        - 3) Either it violates the contains check, that is A is contained in a(A) so cannot be unified with it, OR it could produce a unification where A becomes a(a(a(a(...)))) where the two terms are unified to be the same infinite term.
        - 4) When Prolog unifies a variable with a ground term, you can say it has found the type (in this decision branch) of the variable.
    2. Question 2 
        - 1) ```php
house(Nationality, Pet, Smoke, Drinks, Colour).
(H1, H2, H3, H4, H5).

exists(A, (A, _, _, _, _)).
exists(A, (_, A, _, _, _)).
exists(A, (_, _, A, _, _)).
exists(A, (_, _, _, A, _)).
exists(A, (_, _, _, _, A)).

rightOf(A, B, (B, A, _, _, _)).
rightOf(A, B, (_, B, A, _, _)).
rightOf(A, B, (_, _, B, A, _)).
rightOf(A, B, (_, _, _, B, A)).

middleHouse(A, (_, _, A, _, _)).
firstHouse(A, (A, _, _, _, _)).

nextTo(A, B, C) :- rightOf(A, B, C) ; rightOf(B, A, C).

        % Generate candidates
:-  exists(house(british,_,_,_,red),Houses),
    exists(house(spanish,dog,_,_,_), Houses),
    exists(house(_,_,_,coffee,green), Houses),
    exists(house(ukraine,_,_,tea,_), Houses),
    exists(house(_,snails,old_gold,_,_), Houses),
    exists(house(_,_,kools,_,yellow), Houses),
    exists(house(_,_,lucky_strikes,orange_juice,_), Houses),
    exists(house(japanese,_,parliments,_,_), Houses),
    exists(house(WaterDrinker,_,_,water,_), Houses),
    exists(house(ZebraOwner,zebra,_,_,_), Houses),
        % Test candidates and then backtrack
    rightOf(house(_,_,_,_,green), house(_,_,_,_,ivory), Houses),
    nextTo(house(_,_,kools,_,_), house(_,horse,_,_,_), Houses),
    middleHouse(house(_,_,_,milk,_), Houses),
    firstHouse(house(norwegian, _, _, _, _), Houses),
    nextTo(house(_,_,chesterfields,_,_), house(_,fox,_,_,_), Houses),
    nextTo(house(norwegian,_,_,_,_), house(_,_,_,_,blue), Houses),
    print(ZebraOwner), nl,
    print(WaterDrinker).
``` 
        - 2) exists(house(spanish,dog,_,_,_), Houses)
        - 
        - This generates a candidate house where the occupant is spanish and owns a dog - the composite data-structure Houses previously generated must then be unified to contain this house.
        - 
    3. Question 3 
        - 2) ```php
last([1,2], A).
last([L], L).
last([_|T], L) :- last(T, L).
``` 
        - 3) ```php
append([],A,A).
append([H|T],A,[H|R]) :- append(T,A,R).
``` This should be used to append to lists, the second argument is appended to the first one. This is done by first moving all the items from the first list into a storage list, and then adding the second list to that storage list all in one recursive call.
        - 4) ```php
member(H,[H|_]).
member(H,[_|T]) :- member(H,T).
// or, alternatively
member(X,Y) :- append(_,[X|_],Y).

append([],A,A).
append([H|T],A,[H|R]) :- append(T,A,R).
```
            1. If you view the prolog term append as a "function", one could view this as a partial application as only the 3rd "argument" is specified. However it differs in that the "result" of the "function" is specified which you would not usually be able to do - additionally you would end up with a **new **function with one fewer arguments under partial application, while here you end up with a true or false statement.
            2. While the result would be the same, this would make the code far less readable. 
            3. The first implementation is last call optimized, we can repeatedly tear the head off without needing to come back down the stack frame - meaning we only need a single stack frame. In the implementation of append however, we tack on the head to the result when the nested call to append returns - this means we need to keep track of the values we're going to append in the stack frame. So the stack frame grows in order O(n).
The second implementation does have the advantage of using one less rule.
            4. The first list asks if a value H is at the head of the list, if not then it asks if the value H can be found in the tail of the list. Clearly if H is not in the list this will fail, and if H is in the list it wiwll eventually be at the head of the list to be checked and thus member will succeed.
The second implementation asks if there exists two lists, where the second list has X at the head - such that the two lists appended together results in Y. If X is not in Y, this will clearly not be possible but will always be possible if X is in Y. 
So they both only succeed if their second argument is in the list, hence they are logically equivalent.
        - 5) This checks if a list is sorted in ascending order. We are first given a list to check, we then repeatedly check if the first item in the list is smaller or equal to the next.
        - 6) ```php
b(X,X) :- a(X).
b(X,Y) :- append(A,[H1,H2|B],X), H1 > H2, append(A,[H2,H1|B],X1), b(X1,Y).
```
This sorts an input list. It does this by repeatedly finding a point in the input array where two items in the array are out of order - and then correcting that order. 
    - 
    4. Question 4 
        - 2) Last call optimization is used a branch is only generated in the last portion of a rule, meaning we can know we never have to return to that rule and perform any further calculation - using this fact Prolog does not need to hold onto the stack frame and can simply call the last rule.
        - 4) ```php
// Applies X s( _ )
apply(0, M, M).
apply(X, M, s(R)) :- X>0, Y is X-1, apply(Y, M, R).

prim(X, R) :- apply(X, z, R).

plus(z, B, B).
plus(s(X), B, s(R)) :- plus(X, B, R).

mult(s(z), B, B).
mult(s(s(A)), B, R) :- mult(s(A), B, R1), plus(R1, B, R).
```
        - 5) 
One can always reverse it using the following code or similar: ```php
count(z, 0).
count(s(X), R) :- count(X, R1), R is R1+1.
```
        - 6)
Simply reverse using the above code. Think I'm missing something in this question, it does specifically make "prim" reversible.
        - 7)
1+1 = 2: False, the equals operator does not perform arithmetic - it simply tests to see if the two clauses unify and 1+1 cannot unify with 2 as there is a + separating 1+1.
1+1 is 2: False, is does perform arithmetic but only on the right side - so the 1+1 does not get evaluated.
1 + 1 =:= 2: True, this arithmetic equal performs arithmetic on both sides - but only works with numbers.
One + One = Two: Two = One+One, this unifies when the variable Two has the value One+One.
prim(1, One), prim(2, Two), plus(One, One, Two): One = s(z), Two=s(s(z)), this simply generates primitives for One and Two and then verifies that 1+1=2.
        - 8)
Consider : ```php
 :- prim(3, Three), prim(2, Two), plus(A, Two, Three).
``` We in effect say 3 is 2+A, solve for A. The difference is 
        - 9) ```php
// Without last call optimization
fact(0, 1).
fact(X, R) :- X>0, Y is X-1, fact(Y, A), R is A * X.

// With last call optimization
fact(0, Store, Store).
fact(X, Store, R) :- X>0, Y is X-1, R1 is Store * X, fact(Y, R1, R).

factLastCall(X, R) :- fact(X, 1, R).

// One test to the accuracy would be to observe the ram usage by the two programs during a computation
// A slightly unorthadox method is to first remove the failsafe clauses X>0 :

fact(X, R) :- Y is X-1, fact(Y, A), R is A * X.
fact(X, Store, R) :- Y is X-1, R1 is Store * X, fact(Y, R1, R).

// And then request:
:- fact(-1, Y).
// and
:- factLastCall(-1, Y).
``` 
I found that the non last call recursive version failed in a few seconds reporting:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aG04O-otXj6aytOUF5heispisnNEywihUhVIvnadHwpi6w4iZzhtHXA7Qtcx91Jb8lMAIwU0IoJkbgZNHZSJ6IwcFRZFUUIzH7ll6WZ4rcVPiAWOrXKsWd92NziWEuVF.png) 
While the last call recursive version would happily continue for a lot longer, with the terminal window I was using still using a constant amount of memory while I was watching it:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xn_4zpEMTEs6VbDCAMCy6Za_bEQzEVfLxLhhquq-iANK_JO0tS7TCnRQ62huJRtmuNBttLwbTvb_31HY6v9SBeQcBGOu71tJR6-HhvCUhZmUIMssdrK0_MCmgBw7PhpV.png) 
    - 
    5. 
        - 1)```php
len([], Acc, Acc).
len([_|T], Acc, R) :- B is Acc+1, len(T, B, R).
len(I, R) :- len(I, 0, R).

len(X, 3)

// First we try the first rule and it fails (0 != 3)
// Then we insert a blank into the list we're generating and
// add to the accumulator, we'll then try the first rule and find
// 1 != 0. This will repeat, finally resulting in [_,_,_]
```
        - 2) ```php
take([H|T], H, T).
take([H|T], A, [H|B]) :- take(T, A, B).

take(Y, 1, [2,3]).
// First it'll match with the first rule and return [1,2,3]
// Then it'll match with the second rule and match:
// 1 with A, 2 with H, [3] with B

// Then it needs to prove take(T, 1, [3])
// This will first match with the first rule returning [1,3]
// resulting in backtracking and a new result of [2,1,3]

// For the next value we need to match take(T, 1, [3]) with the second rule
// Resulting in A=1, H = 3, B = []
// The first rule is the only option (the second would fail)
// And we get [2,3,1]

// This gives all the lists you could take 1 from and have [2,3] left
// over
```
        - 3) ```php
append([],A,A).
append([H|T],A,[H|R]) :- append(T,A,R).

append(X,Y, [1,2,3])
// Just from looking at it you can guess it's going to output:
// [], [1,2,3]
// [1] [2,3]
// [1,2] [3]
// [1,2,3] []

// This is because the head will be torn off the input list,
// appended to X and then the first rule will come into effect.
// This will happen again with another item being torn off the head
// and so on.
```
    - 
    6. 
        - 2) ```php
dutch([blue]).
dutch([Y | [Y | T]]) :- dutch([Y|T]).
dutch([red | [Y | T]]) :- Y=white, dutch([Y|T]).
dutch([white | [Y | T]]) :- Y=blue, dutch([Y|T]).

dutchFlag(L, Perms) :- perm(L, Perms), dutch(Perms).
```
        - 5) ```php
 anagramGenerate(Word, R) :- perm(Word, R), Word \= R, word(R).
```
        - 6) 
    - 
    7. 
- Assorted Flashcards
    - What is the FOL expression for ```python
 not(X), case(X).
 and:
 case(X), not(X).
```
