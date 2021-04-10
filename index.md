<h1 style="text-align:center">Graph Convolution Network</h1>



<img src="./1.png" width=560>



> **Tasks on Graphs**
>
> - **Node Classification:** Predict the type of given node.
> - **Link Prediction:** Predict whether tow nodes are linked. 
> - **Commulity Detection:** Identify densely lincked cluster of nodes.
> - **Network Simularity:** Calculating the similarity of two (sub-)graph networks. 



Definition

*Graph Convolution Networks (GCNs)*, because all filter parameters typically shared over all locations in thre graph. The goal is then to learn a function of signals/ features on Graph $\mathcal{G} = (\mathcal{V}, \mathcal{E})$, which takes input as:



#### Symmetric Normalized Laplacian:

<img src="./2.png" height=200>

### Problem Formulation

$$
H^{(t+1)}=\sigma(\hat{D}^{-\frac{1}{2}}\hat{A}\hat{D}^{-\frac{1}{2}}H^{(t)}W^{(t)})
$$

$\mathcal{G} = (\mathcal{N}, \mathcal{E})$



<a href="#loop">where</a>:

- $\sigma$ is activation layer, such as $sigmoid$;

- $\hat{A} = A + I$, $A$ is Adjacency Matrix, and $I$ is a unit matrix;

- $\hat{D}$ is the degree matrix of A, and $D_{ij}=\sum{j\hat{A}_{ij}}$;

- $H^{(t)}$ is feature of layer $t$;

- $W^{(t)}$ is the variable weights of layer $t$;

#### Symmetric Normalized Laplacian:

$$
L^{sym} := D^{-\frac{1}{2}}LD^{-\frac{1}{2}} = I - D^{-\frac{1}{2}}AD^{-\frac{1}{2}}
$$

where
$$
L_{i,j}^{sym} = \begin{cases}1 & if i = j,\ deg(v_i)\not= 0\\[2ex]-\frac{1}{\sqrt{deg({v_i})\dot{}deg({v_j})}} & if\ i\not=j,\ v_i\ is\  adjacent\ to\ v_j \\[2ex]0 &otherwise\end{cases}
$$





**Node Classification[^1]:**
$$
Softmax(Z_ n)
$$
**Graph Classification[^2]:** 
$$
Softmax\left(\sum_N{z_n}\right)
$$
**Link Prediction[^3]:**
$$
P(A_{ij}) = \sigma\left(z_i^Tz_j\right)
$$
Graph Attention Networks[^4]





<div style="text-align:center"><img src="3.png" height=200><img src="4.png" height=200></div>

<div style="text-align:center"><img src="5.png" height=200><img src="6.png" height=200></div>





```
input: [N, D0]
weights: [D0, D1]
adj: [N, N]
layer1 = [N, D1]
layer2 = [N, D1]
```

<div style="text-align:center"> <img src="./7.png" height=250></div>

[^1]: Kipf and Welling etc. (ICLR 2017)
[^2]: Duvenaud et al. (NIPS 2015)
[^3]: Kipf and Welling. Semi-Supervised Classification with Graph Convolutional Networks.(NIPS BDL 2016)
[^4]: Veličković, P., Cucurull, G., Casanova, A., Romero, A., Liò, P. and Bengio, Y., 2018. Graph Attention Networks


