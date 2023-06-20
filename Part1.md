
## Topological Data Analysis in Networks
This tutorial aims to provide a comprehensive introduction to Topological Data Analysis (TDA) on networks specifically tailored for Computer Science, Statistics, and Mathematics students. The tutorial is designed to accommodate students with minimal mathematical background, assuming only a basic understanding of concepts such as graphs, nodes, and edges.

We will introduce the fundamental principles of TDA, enabling students to leverage topological techniques for data analysis and exploration. We will cover essential topics such as simplicial complexes, persistence diagrams, and homology, gradually building a strong foundation in TDA concepts and methods.

The instructional approach emphasizes clarity and accessibility, presenting complex mathematical ideas in an intuitive and digestible manner. By the end of this tutorial, you will have gained a solid understanding of TDA and its applications, equipping them with valuable tools for analyzing and interpreting complex datasets.

If at any point during this tutorial you find yourself feeling lost, please don't hesitate to reach out to us. You can email your concerns or areas that need improvement to cuneyt dot akcora at umanitoba dot ca. Your feedback will be greatly appreciated and will help us enhance the tutorial for a better learning experience.

## Part 1

#### **What is Topological Data Analysis?**

Topological Data Analysis (TDA) serves as the core toolkit utilized by mathematicians in the field of Data Science.

TDA is primarily driven by the belief that topology and geometry offer a robust approach to extracting qualitative and sometimes quantitative information about the underlying structure of data. The objective of TDA is to establish mathematically rigorous, statistical, and  algorithmic methods for inferring, analyzing, and leveraging the intricate topological and geometric structures present in data, often represented as <span style="color:red">point clouds (each dot of the pot)</span> in <span style="color:red">Euclidean</span> or more general <span style="color:blue">metric spaces</span>. 
 
 
 <center>
  
| ![Point Cloud Torus](Images/Point_cloud_torus.gif) | ![Pot](Images/Pot.png) |
|:---:|:---:|
| *The Torus shape given as a point cloud* | *A Pot in the Euclidean (3D) Space* |

</center>

 A metric space (M, ρ) is a set M with a function $\rho ∶M × M →R_+,$ called a distance, such that for any x, y, z ∈ M:
 
  * ρ(x, y) ≥ 0 and ρ(x, y) = 0 if and only if x = y,  
  * ρ(x, y) = ρ(y, x) and,  
  * ρ(x, z) ≤ ρ(x, y) + ρ(y, z).
    
<br>

#### **TDA Process in Machine Learning**

**#1**

  The input data is considered to be a finite collection of points, and there exists a
measure of distance or similarity between these points. This distance can be determined by the metric of the surrounding space, such as the Euclidean metric if the data is embedded in <span style="color=red">$ℝ^d$</span>, or it can be defined by a pairwise distance matrix intrinsic to the data.  

  The specification of the metric for the data is typically provided as an input or guided by the specific application. However, it is crucial to acknowledge that the choice of metric plays a significant role in uncovering noteworthy topological and geometric characteristics of the data

**#2a**

  A continuous shape is constructed to emphasize the underlying <span style="color=red">topology</span> or geometry of the data
<center>
  | ![Pot](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/0f1d5b70-8583-4b3f-932b-115ebc509e54){width=40%} |
  |:---:|
  | *Topology: This looks like a pot!* |
</center>

**#2b**

  This shape is typically a <span style="color:red">simplicial complex</span> or a sequence of nested simplicial complexes known as a filtration, which captures the data's structure at various scales.
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/b12b29db-8b84-4332-8183-e5d50c09325b){width=40%} |
  |:---:|
  | <span style="color:red">*simplicial complex*</span> |
  <span style="color:gray">Image:wikipedia</span> 
</center>

**#2c**

  This shape is typically a simplicial complex or a sequence of nested simplicial complexes known as a <span style="color:red">filtration</span>, which captures the data's structure at various scales.
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/0f793745-5849-4a5b-a2eb-8cbabf97fefc) |
  |:---:|
  | <span style="color:red">Filtration</span> |
  <span style="color:gray">Image: Cavanna, N.J., Jahanseir, M. and Sheehy, D.R., 2015. A geometric perspective on sparse filtrations. arXiv preprint arXiv:1506.03797.</span>
</center>

**#2d**

  Simplicial complexes can be seen as higher-dimensional extensions of neighborhood graphs commonly used in standard data analysis and learning algorithms.
  
  The task at hand is to define these structures in a way that is mathematically proven to reflect meaningful information about the data's structure and can be efficiently constructed and manipulated in practical applications.
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/7e204b00-cb60-48d7-a14b-79115b6a90f9){wdith=20%} |
  |:---:|
  <span style="color:gray">Image: Meng, Z. and Xia, K., 2021. Persistent spectral–based machine learning (PerSpect ML) for protein-ligand binding affinity prediction. Science advances, 7(19), p.eabc5329.</span>
</center>

**#3**

  The structures constructed on the data provide a means to extract topological or geometric information.It may involve generating rough summaries or approximations that require specific methods, such as persistent homology, to extract relevant information.
<center>
   | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/0f793745-5849-4a5b-a2eb-8cbabf97fefc) |
  |:---:|
  | *What do you see in this filtration?* |
</center>

**#4**

  The topological and geometric information extracted offers novel sets of features
and descriptors for the data. These features can enhance the understanding of the data, especially through visualization techniques. They can also be combined with other types of features to enable more comprehensive analysis and facilitate machine learning tasks. Furthermore, this information can be utilized to design data analysis and machine
learning models that are well-suited to the specific characteristics of the data. An essential consideration at this stage is demonstrating the added value and
complementarity of the information provided by TDA tools compared to other
features.

  Understanding how the extracted information complements existing features and showcases its advantages is a key aspect of this process.

<br>

#### **The Language of TDA**

**#Simplicial complexes - 1**

  Simplicial complexes can be regarded as an extension of graphs to higher dimensions. They are mathematical entities that possess both <span style="color:red">**topological**</span> and  <span style="color:red">**combinatorial**</span> characteristics, which makes them particularly valuable for Topological Data Analysis.
  
  Two important aspects of these mathematical objects:
  
  * <span style="color:red">Topological characteristics</span>: Simplicial complexes have a topological nature, meaning they capture information about the connectivity and spatial relationships between their constituent <span style="color:green">simplices</span> (e.g., vertices, edges, higher-dimensional faces). They provide a framework to study topological properties such as connectedness, boundaries, holes, and higher-dimensional structures.
  * <span style="color:red">Combinatorial characteristics</span>: Simplicial complexes have combinatorial properties, which deal with the combinatorial arrangements and relationships between their simplices. These properties involve how the simplices are combined, their intersections, and the inclusion relations between different simplices.
    
**#Simplicial Complexes - 2**

  <span style="color:grey">Given a set $X = \{x_0,···, x_k\} ⊂ R^d$ consisting of k + 1 <span style="color:red">affinely independent points</span>, the k-dimensional simplex $σ = [x_0,···,x_k]$ spanned by X can be defined as the convex hull of X.</span>
  
  Affinely independent points refers to a set of points in a vector space that do not lie on the same affine subspace, except when the set consists of a single point. In other words, a set of points $\{x_0, x_1, x_2,···, x_n\}$ is said to be affinely independent if there is no non-trivial linear combination of the points that results in the zero vector, except when all the coefficiants are zero.
  
  In layman's terms can be understood as a set of points that are not in a straight line or a flat plane.
  
**#Simplicial Complexes - 3**

  <span style="color:grey">Given a set $X = \{x_0,···, x_k\} ⊂ R^d$ consisting of k + 1 affinely independent points, the k- dimensional simplex $σ = [x_0,···, x_k]$ spanned by X can be defined as the  <span style="color:green">convex hull</span> of X.</span>
  
  The <span style="color:green">convex hull</span> of a set of points is the smallest convex shape or region that completely encloses all the points. In simpler terms, it is like finding the "outer boundary" that wraps around a given set of points.
  
  Mathematically, an n-dimensional simplex is defined as the convex hull of (n + 1) affinely independent points in n-dimensional space. In other words, it is the smallest convex shape or region that contains these points. For example, a 1-dimensional simplex is a line segment, a 2-dimensional simplex is a triangle, a 3-dimensional simplex is a tetrahedron, and so on.
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/6515b9b0-26f1-4cdf-a0fe-a372f11dffa2){width=60%} |
  |:---:|
  <span style="color:gray">Image: Robert Laurini</span>
</center>

**#Simplicial Complexes - 4**

   <span style="color:grey">Given a set $X = \{x_0,···, x_k\} ⊂ R^d$ consisting of k + 1 affinely independent points, the k- dimensional <span style="color:red">simplex</span> $σ = [x_0,···, x_k]$ spanned by X can be defined as the convex hull of X.</span>
  
  Mathematically, an n-dimensional <span style="color:red">simplex</span> is defined as the convex hull of (n + 1) affinely independent points in n-dimensional space. In other words, it is the smallest convex shape or region that contains these points. For example, a 1-dimensional simplex is a line segment, a 2-dimensional simplex is a triangle, a 3-dimensional simplex is a tetrahedron, and so on.
<center>
 | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/2f6433c5-29e0-4fee-9681-b127e14b3d92){width=60%} |
 |:---:|
 <span style="color:gray">Image: https://velog.io/@shlee0125</span>
</center>

**#Simplicial Complexes - 5**

  A geometric simplicial complex K in $R^d$ is a collection of simplices satisfying the following conditions:
  
  * Every <span style="color:red">face</span> of a simplex in K is also a simplex in K.
  * The intersection of any two simplices in K is either empty or a common face shared by both simplices.

  The <span style="color:red">face</span> of a simplex refers to a lower-dimensional simplex that is a subset of the original simplex. In other words, it is a subset of the vertices of the simplex that defines a smaller simplex within it.
  
**#Simplicial Complexes - 6**

  For example, in a 3-dimensional simplex (tetrahedron), the faces are triangles, and in a 4-dimensional simplex, the faces are tetrahedra. 

  The faces of a simplex are simplices themselves, but of lower dimension.
<center>
  | ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/7f9a35de-dd0c-4805-b3f1-c989035f8d15){width=40%} |
</center>

**#Simplicial Complexes - 7**
  
  The collection of simplices in a simplicial complex K forms a subset of $R^d$ known as the underlying space of K, which inherits the topology of $R^d$. Consequently, K can be regarded as a <span style="color:green">topological space based on its underlying space</span>. It's worth noting that once the vertices of K are determined, the combinatorial description of the collection of simplices, adhering to certain incidence rules, fully characterizes K.


  * <span style="color:grey">When we say that a simplicial complex K can be regarded as a <span style="color:green">topological space based on its underlying space</span>        , we mean that we can associate a topological structure to K by considering the topology inherited from its underlying space.</span>
  * <span style="color:grey">The underlying space of K is a subset of Rd that contains all the points corresponding to the vertices, edges, faces, and higher-dimensional simplices of K.<span>
    
**#Building simplicial complexes from data**

  There exist many ways to build simplicial complexes. We present here a few classical examples that are widely used in practice. An initial example is an immediate extension of the concept of an a-neighboring graph. 
  
  Suppose we have a set of points, X, in a metric space (M, p), and a real number α ≥ 0. The Vietoris-Rips complex, denoted as $Rips_a(X)$, consists of simplices $[x_0,···, X_k]$ satisfying the condition that the distance between any pair of points, $d_x(x_i, x_j)$, is less than or equal to α for all (i, j).
  
  Each circle (called a <span style="color:green">closed ball</span>) has a data point at its center, and the circle radius is the distance from the data point
<center>
  <img width="499" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/7b961b85-311a-459c-ab7a-f8de1f7c22fa">
</center>
  <br>
  However, it's important to note that in general, even when X is a finite subset of $R^d$, $Rips_a(X)$ may not have a geometric realization in $R^d$. In other words, it may have a dimension higher than d.<span style="color:grey">Can you figure out why?</span>
  
  Closely connected to the Vietoris-Rips complex is the Čech complex, denoted as $Cech_a(X)$. It is defined as the set of simplices $[x_o,···, X_k]$ such that the k + 1 closed balls, $B(x_i, α)$, have a non-empty intersection. It's worth noting that these two complexes are related as follows: $Rips_a(X)$ is a subset of $Cech_a(X)$, and $Cech_a(X)$ is a subset of $Rips_2a(X)$. Additionally, if X is a subset of $R^d$, then $Cech_a(X)$ and $Rips_2a(X)$ share the same 1- dimensional skeleton, meaning they have the same set of vertices and edges.

**#Main Directions in TDA - simplified classification**

  Persistent Homology (PH): study of topological shapes that can fit into your data
  <center>
   | ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/e4d9bb48-f3cc-4db7-ae83-368a6e4e8d71){width=50%} |
   |:---:|
   
   <span style="color:gray">Image: De Lara, M.L.D., 2023. Persistent homology classification algorithm. PeerJ Computer Science, 9, p.e1195.</span>
  </center>
  
  TDAMapper: the overall shape of your data  
  
  * Both have filtrations and distances, but Mapper studies about how your entire data is shaped and deduces insights from that shape.
  <center>
    | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/d19b06f4-af9b-4ee0-8033-99e1ee46febd){width=40%} |
  </center>
  
#### **Persistent Homology in TDA.**

**#What is Homology?**
  
  Homology, in a nutshell, is a fundamental concept in algebraic topology that provides a powerful tool for formalizing and analyzing topological features of spaces or simplicial complexes in an algebraic manner. It enables us to capture and quantify the presence of different-dimensional "holes" within a given space.
  
  In homology, each dimension k corresponds to a vector space $Н_k$, where the dimension of $H_k$ intuitively represents the number of independent features of that dimension. For instance, the O-dimensional homology group $H_0$ describes the connected components of the complex, the 1-dimensional homology group $H_1$ represents the 1-dimensional loops or cycles, and the 2-dimensional homology group $H_2$ captures the 2-dimensional cavities or voids within the space.
  
  Homology provides a rigorous framework for understanding and characterizing topological structures by associating vector spaces to each dimension, giving us valuable information about the presence and properties of various topological features within a space or simplicial complex.
  
  In simple terms, we are defining topological structures (i.e., k-dimensional holes) and counting them in a simplicial complex (SC). 
  
  What are these holes?
  
  * The term "dimensional holes" refers to the topological features captured by the homology groups of a simplicial complex.
  * These holes represent voids or empty spaces of different dimensions within the data.
  * In the context of TDA, the term "hole" does not refer to a literal physical hole but rather to a topological concept.
  * A dimensional hole can be understood as a region or subspace of the data that is missing or empty, characterized by the absence of certain simplices or simplicial structures.
    
  O-dimensional holes are connected components in a SC:
  
  * $K_1$ has 12 0-dimensional holes  
  * $K_2$ has larger balls, but there are still 12 holes.  
  * $K_3$ now has edges between simplices. There are 6 0-dimensional holes.  
  * $K_4$ has just one connected component; 1 0-dimensional hole.
    
  1-dimensional holes are loops in a SC:
  
  * $K_1$ does not have a 1-dimensional hole  
  * $K_2$ has larger balls, but no 1-dimensional holes.  
  * $K_3$ now has edges between simplices, but no 1-dimensional holes.  
  * $K_4$ has a loop now; it has a 1-dimensional hole.

<center>
  | ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/e4d9bb48-f3cc-4db7-ae83-368a6e4e8d71){width=50%} |
</center>

**#Homology**

  To extract summaries of such topological features at a mesoscopic level, we use **Betti numbers**. Betti-p number of a simplicial complex C of dimension d, denoted by $ẞ_p(C)$, is defined as
<center>
  | <img width="499" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/8891bcb0-ae6f-47b0-879a-662c20fcafec"> |
  |:---:|
  | *Betti numbers at increasing dissimilarity scales* |
</center>
<center>
  | ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/dbeec82d-7eb3-4ae0-8c24-7f2fe8fa0979){width=60%} |
  |:---:|
  | Anand, D.V., Meng, Z., Xia, K. and Mu, Y., 2020. Weighted persistent homology for osmolyte molecular aggregation and hydrogen-bonding network analysis. Scientific Reports, 10(1), pp.1-17. |
</center>

**#Persistent Homology**

  We can increase k as much as we want, however we do not see k>2 holes often in our experiments. 
  
  Formal definitions for the holes can be found in works such as
  
  * Edelsbrunner, H. and Harer, J., 2008. Persistent homology-a survey. Contemporary mathematics, 453(26), pp.257-282.  
  * Otter, N., Porter, M.A., Tillmann, U., Grindrod, P. and Harrington, H.A., 2017. A roadmap for the computation of persistent homology. EPJ Data Science, 6, pp.1-38.
    
**#What is Persistent in PH?**
  
  Persistent homology in a nutshell:
  
  1. Given X data points in $R^d$  
  2. Find pairwise distances  
  3. <span style="color:red">Use a filtration threshold on distances from 0 to maximum</span>
      a. Create simplices and a simplicial complex out of them,  
      b. Identify certain topological features - what are they? We need to talk about shapes to answer this question.  
      c. <span style="color:red">Identify which holes persist (i.e., born and survive)</span>   
  4. Use the vectorization in ML tasks
    
**#What is filtration?**
  
  A filtration of a simplicial complex K is a collection of subcomplexes $(K_r)_{t\in T}$ that are nested, meaning that for any $r_0$ and rp in the set T, if r is less than or equal to $r_0$, then $K_{r0}$ is a subset of Kro.
  
  The entire complex K is obtained by taking the union of all the subcomplexes $K_r$ for r in T. In a more general sense, a filtration of a topological space M is a collection of subspaces
$(M_r)_{r\in T}$ that are nested. Similar to the simplicial complex case, if r is less than or equal to $r_0$, then $M_r$ is a subset of $M_{r0}$. The entire space M is obtained by taking the union of all the subspaces $M_r$ for r in T.
<center>
 ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/270009bb-ef99-42e5-8496-82a383d98547)
</center>

**#Persistence Diagrams**
  
  In practical situations, the parameter $r \in T$ can often be interpreted as a scale parameter.
  
  We alternate between scale and distance to refer to r. We mostly use the term distance and use Є or α to refer to the distance threshold in our articles.
  
  Filtration tracks the appearance of shapes along the distance threshold α.
  
  The information gathered through filtration is stored in persistence diagrams (PDs), which consist of a multiset of points supported on the open half-plane $\{(α_b, α_d) \in R^2: α_b <$

**#PD for 1-dimension holes**

<center>
  | ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/76649d35-389d-413b-9608-c0276e6f39ca){width=60%} |
  |:---:|
  
  Krishnapriyan, A.S., Montoya, J., Haranczyk, M., Hummelshøj, J. and Morozov, D., 2021. Machine learning with persistent homology and chemical word embeddings improves prediction accuracy and interpretability in metal-organic frameworks. Scientific reports, 11(1), p.8888.
</center>
<br>

**#Vectorizations for 0 and 1-dimensional holes**

<center>
  <img width="589" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/98675fae-b2c1-40f3-9176-35e565de0ab9">
</center>

