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
