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
