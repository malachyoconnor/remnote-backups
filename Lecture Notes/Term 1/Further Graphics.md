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
