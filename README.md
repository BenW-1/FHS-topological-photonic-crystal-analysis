No AI was used in this project. This represents my work with Dr Alex Song and Mr Hector Hu.

Important note: the module 'legume' is used for photonic crystal construction and eigenmode computation. Confusingly, on conda and pip, 'legume' is the name of an unrelated python UDP library. Having both this and the 'real' Legume library within your environment will give conflicting results upon calling 'import legume' depending on what was installed first.

The 'real' Legume module can be found [here](https://github.com/fancompute/legume) and [here](https://pypi.org/project/legume-gme/).

# FHS meathod for Berry curvature:
As described by [Chern Numbers in Discretized Brillouin Zone: Efficient Method of Computing (Spin) Hall Conductances](https://journals.jps.jp/doi/pdf/10.1143/JPSJ.74.1674) (FHS stands for the authors Fukui, Hatsugai, Suzuki).

This method and my implementation work for both the single-band Abelian case and the band-multiplet non-Abelian case.


# Results for: 2D Valley hall crystal
(Crystal as described in [Valley-contrasting physics in all-dielectric photonic crystals: Orbital angular momentum and topological propagation](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.96.020202))

The photonic crystal is constructed as the paper outlines. PWE is then used to find the eigenmodes and photonic band structure:

<img width="583" height="433" alt="download" src="https://github.com/user-attachments/assets/62e7ea96-4706-408c-a70f-8ba0f97cad21" />

As Xiao-Dong Chen et al. also show, eigenmodes at the K and K' points carry +1 and −1 orbital angular momentum, respectively, around the unit cell. This orbital angular momentum flips across the domain boundary, which is created by swapping d_a and d_b during crystal construction, or by changing the analysed band (between m=0 and m=1).

<img width="533" height="433" alt="download" src="https://github.com/user-attachments/assets/bf76de07-4647-4ddf-a3bb-ca2a4e9b58cb" />
<img width="533" height="433" alt="download" src="https://github.com/user-attachments/assets/e7d74729-667a-4065-a50b-b913cd32932b" />

Performing the FHS method over a rhombic Brillouin zone shows a respective maxima and minima of Berry curvature around the k and k' points respectively, and these switch upon flipping across the domain boundary or analysed band. This result is also shown for the hexagonal (Wigner-Seitz) Brillouin zone.

<img width="410" height="452" alt="download" src="https://github.com/user-attachments/assets/9ff3bdc3-6159-48f5-99c7-0dad872f05d3" />
<img width="415" height="435" alt="download" src="https://github.com/user-attachments/assets/45dafea2-88cd-48c5-964a-5ea3ce28b0f6" />


As expected, the Chern number for the whole band is zero. However, summing the peak and trough constructively yields the topological index -1.16, close to the theoretically correct value of -1.

# Results for: 2D Spin hall crystal
(Crystal as described in [Scheme for Achieving a Topological Photonic Crystal by Using Dielectric Material](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.114.223901))

As before, the crystal is constructed and undergoes 2D PWE using legume to obtain eigenmodes and band structure. The phase of the crystal is defined with the ratio a/R (2.9 is considered topological,  3 is the traansition point, 3.125 is non-topological):

<img width="616" height="453" alt="download" src="https://github.com/user-attachments/assets/fcaa01ff-919a-41af-8f9d-29f641181056" />
<img width="616" height="453" alt="download" src="https://github.com/user-attachments/assets/aa3807c0-5689-485f-a463-d356e36e9e8f" />
<img width="616" height="453" alt="download" src="https://github.com/user-attachments/assets/43d37a51-9844-45af-a3d7-70c3b5eb1c8d" />

Since this case must be treated as non-Abelian (see the band crossings), the Berry curvature and phase must be computed over a multiplet of the bands of interest, by constructing a matrix of eigenmode inner products (an overlap matrix) and taking its determinant, as described by Fukui et al. Here, the bands of interest are m = 1 and m = 2 (orange and green). For this multiplet, the Chern number integrated over the Brillouin zone is 0; a shallow peak and sharp trough cancel each other out.

<img width="407" height="418" alt="download" src="https://github.com/user-attachments/assets/e90a4471-8431-4115-b2f1-f30bb074dd1d" />
