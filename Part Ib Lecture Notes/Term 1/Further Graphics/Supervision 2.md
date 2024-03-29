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
