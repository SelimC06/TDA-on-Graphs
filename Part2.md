# Topological Data Analysis in Networks
## Part 2

#### **Graph Persistent Homology**

**#Edge Activations**

  Consider the graph below where edge weights indicate distances.
  
  Lets use a Vietoris Rips complex: denoted as $Rips_𝛼(X)$, consists of simplices $[x_0,...,x_k]$ satisfying the condition that the distance between any pair of points, $d_x (x_i, x_j)$, is less than or equal to a for all (i, j).
<center>
![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/a85e3387-a5fe-4faa-b1a0-5ce308dde6f7){width=30%}
</center>
  
  Min scale = 0 (we could start from 0.5 or any other value as well)
  
  Max scale = 100 (we could go longer, but it would not change anything)
  
<center>
  <img width="674" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/95d141c4-6573-4d41-8d06-8a342b6b11bf">
</center>

  Multiple questions:
  
  * Question 1: How do we define a distance based on edge weights? In the previous slide, the edge weights represented distances, eliminating the need for explicit distance definition.
  * Question 2: What happens if the graph is unweighted?
    1. <span style="color:red">Graph resistance distance</span>: In a graph, the resistance between two vertices measures the level of difficulty for electric current to flow between them.
    2. <span style="color:red">Shortest path distance</span> (works with weighted edges as well):  a measure of the minimum number of edges along the shortest path between two vertices in a graph.
    3. <span style="color:red">Ricci curvature</span> (works with weighted edges as well): the concept of Ricci curvature is a generalization of Ricci curvature from Riemannian geometry. It provides a way to quantify the geometric properties of the network based on its connectivity and edge weights.
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/dadd5e49-bc46-4ca9-9e46-993590b38fad){width=70%} |
  |:---:|
  <span style="color:gray">Ni, C.C., Lin, Y.Y., Luo, F. and Gao, J., 2019. Community detection on networks with Ricci flow. Scientific reports, 9(1), pp.1-12.</span>
</center>

  Question 3: What happens if the graph is directed?
  
  * Use distance measures introduced in the first question, but define distances based on incoming <span style="color:red">or</span> outgoing edges only

**#Node Activation**

  Consider the graph below where node features indicate ages.
<center>
  <img width="300" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/1070977a-b11e-4e1d-87df-253e506331a1">
</center>

  We will use sub or super level filtration.
  
  * Sublevel: filtration from <span style="color:green">minimum</span> to <span style="color:red">maximum</span> scales
  * Superlevel: filtration from <span style="color:red">maximum</span> to <span style="color:green">minimum</span> scales
  
  Min scale = 10 (we could start from 15 or any other value as well)
  
  Max scale = 80 (we could go longer, but it would not change anything)
  
<center>
  <img width="674" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/4ea0d648-876c-412b-9ed5-97829f813448">
</center>

  Multiple Questions:
  
  * Question 1: How do we define node activation values? May come from domain: in molecular networks, atomic weights of molecules.
<center>
  | <img width="600" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/90a41eab-2a07-4dec-9e2b-25bb8eb98ee6"> |
  |:---:|
  <span style="color:gray">Image: Wikipedia. Molecular structure of caffeine. Methyl groups are implied, but not visualized.</span>
</center>
  * Question 2: Sub or super level? Usually researchers apply both and concatenate vectorizations.
  * Question 3: On directed or weighted graphs? We need to define node features based on their edges. This is a common issue in weighted blockchain networks.
  
<br>

#### **A few tips and insights for TDA on graphs**

**#Simplex vs Clique**

  Math: Mathematically, a k-dimensional <span style="color:red">simplex</span> is defined as the convex hull of (k + 1) affinely independent points in k-dimensional space. 
  
  CS: In graph theory, a <span style="color:red">k-clique</span> refers to a subset of k vertices in a graph where every vertex is directly connected to every other vertex in the subset.
<center>
  <img width="400" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/24aaf01d-aaa6-4fa9-8e52-d9ddc642f37a">
</center>

**#K-dimensional holes**

  A k-dimensional hole requires vertices with at least degree k+1 (Vietoris-Rips here).

<center>
  | <img width="527" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/16cc7630-a674-4022-a1c6-79511984d4f8"> |
  |:---:|
  | *Node f will never contribute to a k>0 dimensional hole (See our Neurips’22 CoralTDA article)* |
</center>

**#Power of PH**

  Persistent homology is powerful because it allows us to track the birth and death of dimensional features at various scales.
  
  Insight from [Yulia R. Gel](https://scholar.google.com/citations?user=MAFTn7gAAAAJ&hl=en) of UTD Math: This PH information is similar to what we get in graph motif analysis, but with finer granularity. 
  
  * Graph motif analysis is a method used in graph theory and network analysis to identify and analyze recurring patterns or subgraphs within a larger graph.
  * A motif is defined as a small subgraph that appears more frequently in a graph than would be expected by chance alone.
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/f54732bb-5e38-4321-b493-5c512c409919){width=30%} |
  |:---:|
  | *Figure: Three-node graph motifs* |
</center>

#### **Applications of TDA on graphs**

<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/b078772a-fa11-40a0-898a-fca113320141){width=70%} |
  |:---:|
  | Li, Yitao, et al. **"Dissecting Ethereum Blockchain Analytics: What We Learn from Topology and Geometry of the Ethereum Graph?."** Proceedings of the 2020 SIAM International Conference on Data Mining. Society for Industrial and Applied Mathematics, 2020 |
</center>

  Account Based blockchains have two types of "transactions"
  
  1. A transfer of the used cryptocurrency, such as Ether on Ethereum.
  2. Internal transactions, which involve a transfer of smart contract-based tokens

**#Ether transactions**

<center>
  <img width="200" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/b59fe62a-c415-48ae-a7a4-aca2dc0d2e3c"> 
</center>

  Ether transactions involve one input <span style="color:blue">address</span> and one output <span style="color:blue">address</span>. An address spends coins from a balance, keeps the change. Each transaction of an address has an order (called nonce). The nonce is  the number of transactions sent to the network by the address. A later transaction needs to wait for earlier transactions to be mined.
  
**#Internal transactions**

<center>
  <img width="434" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/18f08a1d-1635-4491-90fd-651da2999b93">
</center>

  A transaction can transfer both currencies and tokens. An internal transaction can create multiple edges, although this is rare on Ethereum

**#Trading Tokens - a timeline**

<center>
  <img width="427" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/9b846026-8363-486d-898c-ae033ae499e6">
</center>

**#Token Networks**

<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/9bdbcc20-e0b5-45d6-b2c6-68eca148f1f0){width=65%} |
  |:---:|
  | *The largest connected component in Storj network on 13-1-2018* |
</center>

  We model account based blockchains as directed, weighted, multi-graphs

  The network of a single token is usually sparse and devoid of community structure. Daily networks may contain many disconnected components.
  
**#Topological Data Analysis of Blockchain – Ethereum Case**

  Let 𝐺=(𝑉,𝐸,𝜔) be a weighted graph, with the node set 𝑉 and edge set 𝐸 and $𝜔:𝐸→𝑅^+$ is a function encoding dissimilarity between two nodes connected by an edge. 
  
  To account for dissimilarity between two disconnected nodes, we introduce the weight ̃$𝜔:𝑉×𝑉→𝑅^+$
  $$𝜔_{uv}=\left\{
                \begin{array}{ll}
                  \omega_{uv} & (u,v)\in \mathcal{E}\\
                  \infty & (u,v)\not\in \mathcal{E}
                \end{array}
              \right.$$
  In the context of a weighted network, we define $𝜔_{𝑢𝑣}$ as 
  $$𝜔_{uv}=[1+\frac{(A_{uv}-A_{min})\cdot(a-b)}{(A_{max}-A_{min})}]^{-1}$$
  
  where $𝐴_{𝑢𝑣}$ is the weight of the edge (total amount of tokens traded) between nodes 𝑢 and 𝑣. Values of a 	and b create a scale.
  
  $𝐴_{𝑚𝑖𝑛}$ and $𝐴_{𝑚𝑎𝑥}$ are the smallest and the largest edge weights, respectively.  
  
**#Topological Data Analysis of Ethereum Networks**

  In this context, we introduce a novel notion of Betti functions which relate these counts to the scale parameter viewed as continuum. The Betti-𝒑 function $ℬ_𝑝:𝑅^+→\{0,1,2,3,…\}$, 𝑝=0,…,𝑑, associated with $\{𝒞_𝜖 \}_{𝜖\in𝑅^+ }$ is defined as
  $$ℬ_𝑝:𝜖→ℬ_𝑝(𝒞_𝜖)$$
  Sequence of Betti numbers are finite dimensional realizations of Betti functions.
<center>
  ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/a412809d-d45a-437c-8bbd-e675349b38aa){width=65%}
</center>

  The Betti functions can be regarded as a functional summary statistic of the network’s topological structure. 

  Due to the functional dependency among Betti numbers at different scales, it is important to view $\{\mathfrak{B}_p(\epsilon_k)\}_{k=1}^n$ as a function as opposed to a vector in $𝑅^𝑛$. This point of view allows us to utilize methods from functional data analysis such as a concept of <span style="color:red">functional data depth</span>.
<center>
  ![](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/7bcd49c4-dc81-4914-b4bd-03f5ef69aa13){width=45%}
</center>
 
<center>
  
</center>

Consider Betti functions $\{ℬ_(𝑝,𝑡) \}_(𝑡=1)^𝑇$ associated with an evolving token transaction network over days 𝑡=1, 2,…,𝑇. Although each day visually looks different, some days present a clear anomaly in terms of their shape. 

We use a notion of rolling band depth: 
$$𝑅𝐷_𝑤 (ℬ_{𝑝,𝑡}):=𝑀𝐵𝐷(ℬ_{𝑝,𝑡}|ℬ_{𝑝,𝑡},ℬ_{𝑝,𝑡−1},ℬ_{𝑝,𝑡−𝑤+1})$$. We introduce a concept of Betti signature which is defined as the deepest or most central Betti function. 

<center>
  |![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/70c0ecc6-5d31-4cf7-b10f-953e5983b380){width=50%}|![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/012bc874-349f-4733-b018-5a2c6772dbf6){width=50%}|
  |:---:|:---:|
</center>
<br>

**#Predictive Models**

<span style="color:red">Problem Definition</span>: Given the transaction network of an Ethereum <span style="color:red">token</span> and time series of the token price in fiat currency, predict whether the token price will change more than 𝛿 in the next ℎ days. Identify the maximum horizon value ℎ such that the prediction accuracy is at least 𝜌.

<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/50db0b47-4743-493e-83e1-280650223ad2){width=60%} | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/95a97228-dd93-420c-92ab-b5f8f3ef0c2b) |
  |:---:|:---:|
  | A histogram of absolute price returns of 31 tokens $𝑅_𝑡=(𝑃𝑟𝑖𝑐𝑒_𝑡−𝑃𝑟𝑖𝑐𝑒_{𝑡−1})/(𝑃𝑟𝑖𝑐𝑒_{𝑡−1})$. | Number of (price) anomalous tokens in time. |
</center>

**Predictive Models - A Fusion of Network Analysis and Time Series**

We predict price anomalies in 31 token networks, where a total of 9042 days are predicted as anomalous (Anomaly:true). To predict whether the Ethereum token price will change more than 𝛿 within the next ℎ days horizon, we combine the graph topological features with traditional network summaries. We start by defining the price return of a token on day 𝑡 as 
$$R_t=\frac{Price_t-Price_{t-1}}{Price_{t-1}}$$

Then, we label a day 𝑡 as anomalous if there is a significant change in token’s price. More specifically, if |$R_𝑡$|≥𝛿 where 𝛿 is a user-defined threshold (i.e., magnitude of a price shock), then 𝑡 is considered as an anomalous day. We build one predictive model for each token and examine performance for different prediction horizons ℎ>0. 

Our Random Forest models use 2/3 of a token’s lifetime for training, and the remaining 1/3 for test.
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/00c60556-8f8a-4c8c-b34c-fb5801416993) | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/ccd87297-2621-488e-9eb3-8dbcf638346e){width=50%} |
  |:---:|:---:|
  ||A Venn diagram for the number of predicted anomalies in all token networks (for h = 1). Intersecting regions indicate agreement on predictions|
</center>

$𝑅𝐷_7 (ℬ_𝑝)$: Rolling modified band depth of Betti-p function in the last 7 days.

Edge: Number of edges in the daily token network.

$Price: PN_𝑡=\frac{𝑃𝑟𝑖𝑐𝑒_𝑡}{max{𝑃𝑟𝑖𝑐𝑒_1,…,𝑃𝑟𝑖𝑐𝑒_{𝑇_𝑘}}}$

For up to three-day horizons, all models have accuracy >0.7. The figure shows that compared to other models, the M4 (full) model has the least deteriorating performance as horizon increases from 1 to 7. The accuracy results offer evidence that Betti models are more conservative in making anomalous day predictions, and their accuracy is better than the baseline model M1.

<center>
  |![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/6a515bcb-eb85-4a71-8677-a7902f0acf09){width=65%}|
  |:---:|
  |$Accuracy: \frac{𝑇𝑃+𝑇𝑁}{𝑇𝑃+𝐹𝑃+𝑇𝑁+𝑇𝑃}$|
</center>

<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/0b6fd434-cca2-4415-8870-b11e66cbcc99) |
  |:---:|
  | Abay, N.C., Akcora, C.G., Gel, Y.R., Kantarcioglu, M., Islambekov, U.D., Tian, Y. and Thuraisingham, B., 2019, November. **Chainnet: Learning on blockchain graphs with topological features**. In 2019 IEEE international conference on data mining (ICDM) (pp. 946-951). IEEE.|
</center>

**#Transaction output (TXO) based blockchains**

Next, if  address b wants to spend its received 2B, it needs to show proof of funds:

“Use the 2B I received from Block 1, transaction 1 and to pay 1.5B to c and 0.3B to d”.
<center>
  <img width="700" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/da0ce022-a89b-4d54-88d0-f5e15d549cf2">
</center>

**#Blockchain Graph – Substructure mining**

Rather than individual edges or nodes, we use a substructure as the building block in our Bitcoin analysis. We use the term <span style="color:blue">chainlet</span> to refer to such substructures.
<center>
  | <img width="400" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/1c3fb127-279c-448c-a03f-ddb46afe4845">|
  |:---:|
  |**Forecasting Bitcoin Price with Graph Chainlets**, Akcora et al. PaKDD 2018.|
</center>

Definition [K-Chainlets]: 
Let k-chainlet $G_k = (V_k, E_k, B)$ be a substructure of G with k nodes of type {Transaction}.  If there exists an isomorphism between Gk and G’, G’ ∈  G, we say that there exists an occurrence, or embedding of $G_k$ in G.

If a Gk occurs more/less frequently than expected by chance, it is called
a <span style="color:blue">Blockchain k-chainlet</span>. A k-chainlet signature $f_G(G_k)$ is the number of occurrences of $G_k$ in G.

**#Blockchain Chainlets**

<center>
<img width="350" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/2dc1e57e-e3a7-448c-a746-efec62ee362c">
</center>

Chainlets have distinct shapes that reflect their role in the network. We aggregate these roles to analyze network dynamics.

<center>
  | <img width="700" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/4acec28b-a86e-44cb-97df-323b71d41fe7"> |
  |:---:|
  | Three distinct types of <span style="color:blue">first order chainlets!</span> |
</center>

**#Graph features – occurrence and amount**

<center>
  |![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/6709942a-0b7a-43b0-9bb3-ecf314cbef18) | <img width="250" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/811b836b-54e3-45cf-b7a2-5537b449e9b6"> |
  |:---:|:---:|
</center>

Occurrence: How <span style="color:red">many transactions</span> were created with a given type of chainlet?

Amount: <span style="color:red">How many bitcoins</span> were transferred with a given type of chainlet?

<center>
  | <img width="300" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/d33150e9-384b-4590-bd87-e6ac7794c4aa"> |
  |:---:|
</center>

Let’s take one-to-two chainlets, i.e., c+{1→2}

Occurrence: 2 chainlets occur: $t_1$ and $t_3$.  
Amount: <span style="color:green">7.8Ƀ+6.6Ƀ</span>=14.4 bitcoins are transferred by them.

We can record one occurrence matrix, and one amount matrix per 24 hour window.
<center>
  <img width="608" alt="image" src="https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/4862ed19-b845-4d17-925e-0433f3164203">
</center>

Rows and columns indicate number of inputs and outputs, respectively. 

Information about one-to-two chainlets, i.e., c_{1→2}, are given in the matrix cell [1,2]

**#Topological features**

Topological Data Analysis (TDA) provides methods to systematically study the topological and geometric structure underlying data. These structures are commonly analyzed via the multi-scale-based framework of <span style="color:red">persistent homology</span>. The primary idea is to assess which topological features remain persistent over a larger set of scales and hence are likely to play a significant role in its functionality.

**#Persistent homology for blockchains**

We propose a novel approach that computes the Betti sequences on a network of N × N nodes where N is the size of the <span style="color:red">chainlet matrix</span> A. For each of the $N^2$ unique chainlets (e.g., $C_{2→3}$), we create a node in a new network, where edge distance between two nodes is computed with a suitable ‘distance’ d. 
<center>
  |![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/c96b64ae-d725-4516-b45f-8ac4519bcf52){width=30%}|
  |:---:|
  |*A graph from N2= 400 chainlet nodes*|
</center>

In constructing the new network, we use and hence retain the amount information from the Blockchain network. This way, we combine distance (computed from transferred coins) with edge connectedness while restricting the network size.

We describe the main steps as follows: 

Given a heterogeneous Blockchain network with transferred bitcoins on edges, 

1. All the transferred amounts are converted from Satoshis to bitcoins and log transformed: a’ = log(1 + a/108). 
2. For each chainlet of a given time period, we compute the sample q-quantiles for the associated log-transformed amounts: 
a k-th q-quantile, k = 0, 1,…, q, is the amount Q(k) such that 
$$∑_{𝑖=1}^τ 1_{𝑦_𝑖} <𝑄(k)≈\frac{τk}{𝑞} and ∑_{𝑖=1}^τ 1{𝑦_𝑖} >𝑄(k)≈ \frac{τ(q−k)}{𝑞}$$ , where τ is the total number of transactions. 
3. The (dis)similarity metric dij between chainlet nodes i and j is defined as the quantile-based distance 
$$d_{ij} =\sqrt{∑_(𝑘=0)𝑞[𝑄𝑖(𝑘)−𝑄_𝑗 (𝑘)]^2}$$
4. We construct a sequence of scales $ɛ_1$ < $ɛ_2$ < . . . < $ɛ_S$ covering a range of distances during the entire 365-day period. 
5. For each $ɛ_k$, we build the corresponding VR complex whose 0-simplices are single chainlets and 1- simplices are pairs of chainlets with distance ≤ $ɛ_k$. 

As a result, we obtain the filtration of VR complexes $VR_1$ ⊆ $VR_2$ ⊆… ⊆ $VR_S$
We then compute $x_t = \{β_0(ɛ_1), . . . , β_0(ɛ_S); β_1(ɛ_1),… , β_1(ɛ_S)\}$.

**#Experiment**

**Problem Statement**: Let $x_t$ ∈ R d be a set of features computed on the Bitcoin blockchain. 
Let ($x_1, y_1$),... ,($x_t, y_t$) be the observed data where Y = {$y_1,..., y_t$} are the corresponding Bitcoin prices in dollars. At a time point t, estimate the Bitcoin price $y_t$’ where t’ > t.

We downloaded and parsed the entire Bitcoin transaction graph from 2009 January to 2018 December. Using a time interval of 24 hours, we extracted daily transactions on the network and created the Bitcoin graph. Our Bitcoin price (USD) data is downloaded from blockchain.com which aggregates prices from worldwide online exchanges.

In addition to FL and Betti related features: <span style="color:red">past price</span>, <span style="color:red">transaction count</span>, mean degree of addresses, number of new addresses, mean and total coin amount transferred in transactions and address network average clustering coefficient.  

We used ARIMAx, Random Forest, XGBT, Gaussian Process based Regression, and Elastic Net.

We use a time window-based approach in price prediction. 
<center>
  ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/99c08714-d965-446b-8abe-f77553c1bf44)
</center>

**#Baseline Experiments**

We assess model performance with root mean squared error in the predicted price. 
<center>
  | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/e15b669f-8d3d-4d15-8cd0-c27f6d7ec465) | ![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/19127d6e-ab87-44fe-86c6-dfc55a0bbce3)|![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/fc0b0cd8-a8e7-4123-9881-065c7bc4a630)|
  |:---:|:---:|:---:|
  |Window = 3|Window = 5|Window = 7|
</center>

The simplest baseline for ChainNet can be constructed by training models on past price and past total transaction count in a sliding window prediction scheme.  

**#Experiments**

We report the percentage predictive gain, or decrease in RMSE for a specific machine learning model m w.r.t. its baseline model $m_0$ as 
$∆_𝑚(𝑤, ℎ) = 100 × 1 − (𝑅𝑀𝑆𝐸_𝑚 (𝑤, ℎ)/𝑅𝑀𝑆𝐸_{𝑚_0} (𝑤, ℎ))$, 
where $𝑅𝑀𝑆𝐸_{𝑚_0}(w, h)$ and $RMSE_m(w, h)$ are delivered by a baseline model m0 and a competing model m, respectively.
<center>
  |![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/bc2b5680-ed00-47e1-97d9-902a825ec056) |![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/6979d97f-e612-4d48-a8e0-7ad413c26b15) |![image](https://github.com/SelimC06/TDA-on-Graphs/assets/88677758/ef9214df-d8cc-4417-b3dd-9d2dcd56c80c)|
  |:---:|:---:|:---:|
  |Window = 3|Window = 5|Window = 7|
</center>

Figure: Gain over the best model is given for three windows, and multiple horizons.


<br>


**Next Part**  
>>[**Part 3**](https://selimc06.github.io/TDA-on-Graphs/Part3.html)
