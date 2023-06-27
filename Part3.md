# Topological Data Analysis in Networks
## Part 3

#### **Scaling TDA on Graphs**


**#2.1	Scalability**

  <span style="color:red"> Research QUESTION:</span>  
  How to Compute PERsistent Homology on large graphs?
  
**#2.2	Motivation: What if the network is too Big?**
  
  <span style="color:red">Complexity</span>
  
  * PH has shown promise in various graph learning applications, but prohibitive computational costs of PH constrain its wider usage. 
  * Most PH studies are limited to small graphs with a few thousand vertices at most. 
  * The complexity of the standard PH algorithm is cubic in the number of simplices [10], so one needs to limit homology computations to 0-th and 1-th levels only
  
  
  <span style="color:red">Large graphs</span>  
  Computation of higher-level persistence for relatively large graphs can take days or weeks.


  <span style="color:red">Our approach</span>  
  We aim to address this fundamental bottleneck in the application of TDA to large networks by introducing two new efficient algorithms which significantly reduce the cost of computing persistence diagrams (PD) for large real-world networks:  
	**CoralTDA** and **PrunIT.** 
	
**#2.3	Filtration**

  <span style="color:red">Filtration types</span>  
  PH in a network setting: power filtration or using different complexes (e.g., Vietoris-Rips, Cech complexes) to construct the filtration for a given filtering function [11]. 
  
  We focus on the most common methods to define PH for graphs: sub/superlevel filtrations obtained by a filtering function and the clique (flag) complexes. 
  
  <span style="color:red">Why sub/super level?</span>  
We can inject domain information into the PH process if the chosen filtering function comes from the network domain (e.g., atomic number in protein networks, transaction amount for blockchain networks). 

Our results can be generalized to the persistent homology defined with a filtering function for different complexes. 

**#2.4	Coral Decomposition offers a way (CoralTDA)**

  <span style="color:red">Origins</span>  
  Core decomposition presents a hierarchical ordering of nodes based on edges in communities.

  <span style="color:red">Key idea - CoralTDA</span> 
  
  * The hierarchy can be used to filter-out edges that do not change the topology.
  * (𝑘+1)−core (i.e., $𝐺^{k+1}$) of a graph G is enough to compute the $𝑘^{th}$ persistence diagram (PD) of the graph, i.e.,  
            $𝑃𝐷_𝑘  (𝐺)=𝑃𝐷_𝑘(𝐺^{𝑘+1}).$
  * Core 2 and higher are enough to compute graph loops (i.e., 1-dimensional holes).
  * Core 3 and higher are enough to compute 2-dimensional holes.
  
  <span style="color:red">Illustration - CoralTDA</span>   
  Compute k-core decomposition of nodes, and then select cores to be used
<center>
  ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/b00e2470-03eb-4ae9-b910-86d9f1b775fc){width=30%}
</center>
**#2.4	Coral Decomposition offers a way (PrunIT)**

  <span style="color:red">Origins</span>  
  In algebraic topology, homotopy is a very effective tool to compute topological invariants like homology. If two spaces are homotopy equivalent, then their corresponding topological invariants are the same, i.e.,  
	 $𝑋∼𝑌⇒𝐻_𝑖  (𝑋)=𝐻_𝑖  (𝑌).$
	 
  <span style="color:red">Key idea - PrunIT</span>
  
  * We define dominated vertices in G. We first define the neighborhood  
  of $𝑢_0  𝑎𝑠 𝑁(𝑢_0) = {𝑢_0} ∪ {𝑣 ∈ 𝑉 ┤| 𝑒_{𝑢_0 𝑣}   ∈ 𝐸}$. 
  * In particular, 𝑁(𝑢_0) ⊂ 𝑉 is the set of all vertices adjacent to $𝑢_0$, and $𝑢_0$ itself.
  * A vertex u is dominated by the vertex v in G if $𝑁(𝑢) ⊂ 𝑁(𝑣)$. If there is such a vertex v, we call u a dominated vertex of G
  
  
  <span style="color:red">Example - PrunIT</span>  
  Vertex 3 dominates vertices 1 and 2 because all neighbors of 1 or 3 are neighbors of 3. There are no other dominated vertices.
  
  
  <span style="color:red">Illustration - PrunIT</span> 
  Compute node activations, and then select which nodes are dominated.
<center>
  ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/2399ce0b-6a84-4e90-a3e1-f2ea77bedc89){width=30%}
  </center>
**#2.5	Evaluation - Datasets AND LABELS**

<img width="400" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/398bdf9d-2046-4e7d-b736-d511ae06d6d7">

  <span style="color:red"> TU Datasets (molecular, chemical, biological)</span>
  
  * Small networks representing molecular, biological shapes
  * From https://chrsmrrs.github.io/datasets/

  <span style="color:red">Single Graphs (citation, social, co-authorship)</span>
  
  * Medium sized: Citeseer, Cora networks
  * Large sized: Youtube, Amazon, DBLP
  
![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/877d372e-6754-426d-8afd-a56ba31cd222){width=25%}

  <span style="color:red">Facebook, Twitter ego networks (social)</span>
  
  * Ego networks of users
  
  <span style="color:red">Stanford Open Graph Benchmark Datasets</span>
  
  * OGBN-ARXIV, OGBN-MAG datasets
  
**#2.5	Evaluation - CoralTDA Reduction in Vertices**
<center>
<img width="1000" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/e64279d2-6f9a-4f80-b374-7738e47da156">
</center>
  <span style="color:red">Evaluation</span>  
  CoralTDA vertex reduction in graph and node classification datasets (higher is better). Reduction values are averages from graph instances of the datasets (CORA and CITESEER node classification datasets contain a single graph instance only). 
  
  FACEBOOK and TWITTER datasets are reduced by 10% for k > 4, whereas in other datasets graphs are reduced to empty sets.
  
**#2.5	Evaluation - PrunIT Reduction in Vertices**
<center>
| ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/f0d5c52a-691b-44ac-a38c-b82e72620fb4){width=65%} | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/e587065b-e76b-48f8-9163-eb6799b36914){width=65%} |
|:---:|:---:|
| Vertex reduction by PrunIT algorithm in the superlevel filtration. Results are averages of graph instances from the datasets. | PrunIT reduction in OGB node classification dataset. Each data point is an ego network. Even for large networks, time reduction rates can reach 75% |
</center>
  <span style="color:red">Evaluation</span>  
  The figures show reduction percentages by the PrunIT algorithm. FIRSTMM and SYNNEW datasets are reduced by less than 10%; however, the other 11 datasets are reduced by at least 35%.


**2.5	Evaluation - CoralTDa and PrunIT Reduction**
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/0d9b2222-e9be-4346-9e35-64c88e839be0) | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/bc015b58-f346-4eac-b1f5-3c97387582f2) |
  |:---:|:---:|
  | PrunIt reductions in the number of vertices and edges.| Vertex reduction results for 11 large datasets after the application of PrunIt and CoralTDA algorithms. |
</center>
  <span style="color:red">Evaluation</span>  
  When we apply both CoralTDA and PrunIt on large networks, even for low cores of 2 and 3, the combined algorithms reach a vertex reduction rate of 78%.

**#2.5	Evaluation - new directions with CoralTDa and PrunIT**
<center>
| <img width="1000" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/c5dfdb46-fe83-4c00-bc42-e21df1a91d2e"> |
|:---:|
|Clustering coefficients vs. number of topological features in Facebook and Twitter datasets. Each data point is a graph instance. We observe hundreds of higher topological features in these datasets which can be highly useful for various graph learning tasks|
</center>
  <span style="color:red">Theory</span>
  
  * By Kahle’s seminal result [12], to observe nontrivial Betti numbers for higher dimensions in Erdós-Rényi graphs G(n, p), the average degree must be very high. 
  * For a graph G(n, p), in order to have nontrivial kth-homology in its clique complex, Kahle proved that for $𝑝 = 𝑛^𝛼$, α should be between −1/𝑘 and −1/(𝑘+1).
  * In terms of average degree 𝑛 × 𝑝, this means the average degree should be between $𝑛^((𝑘−1)/𝑘)$  and $𝑛^(𝑘/(𝑘+1))$. For instance, for dimension k = 2, the average degree should be between $\sqrt{𝑛}$ and $\sqrt[3]{n^2}$. 
  
  <span style="color:red">Real world datasets</span>  
  For a graph order of n = 1000, this implies that the average degree should be between 31 and 100 to have a nontrivial second homology in random networks. However, in real-life networks, our results show that higher Betti numbers are prevalent in much sparser graphs.


<br>


**Home Page**  
>>[**Link**](https://selimc06.github.io/TDA-on-Graphs/Topological-Data-Analysis-Project.html)

  

