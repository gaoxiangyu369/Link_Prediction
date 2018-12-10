# Link_Prediction
## Problem Description 
The social network is commonly represented by a network topology graph, which is formed by nodes and edges connecting the nodes. The nodes stand for people and the edges represent associations among people. By knowing the current graph, we can predict the growing trends of the network or the likelihood of association among certain group of people in the future by analysing the features hidden in the network. This can be identified as the link prediction problem.

## Data Format
In this project, an incomplete snapshot of Twitter network is given as the training set. The data is in raw text, where each node refers to a real-life Twitter user and each line stands for a one-to-many relationship. The first node in every row is noted as the source node and the rest nodes are target nodes. For example:

<p align="center">1 2</p>

<p align="center">2 3</p>

<p align="center">4 3 5 1</p>

represents the network illustrated in Figure 1.

<div align=center>
  
![Network diagram for the adjacency list example](https://github.com/gaoxiangyu369/Link_Prediction/blob/master/images/Screenshot%202018-12-10%2012.19.23.png)

</div>

Each relationship has a direction indicating the source node person follows the target node person. However, some relationship or edges of the network is missing, which adds in uncertainty between two unconnected nodes. The main task to predict whether two randomly chosen nodes have a connection in real life through constructing directed social network topological structure, extracting features and training current dataset.

## Methods

### Data
The original graph contains N = 4,867,136 Twitter users joined by 23,416,061 edges. Even the training network is a subgraph of the entire network, it still cannot run on the whole training graph due to the processing limits. Besides, it is hard to decide whether two nodes can make up a true edge or not as some edges are withheld from the training graph. Considering these two constraints, it is a competition setting with limited time to implement and run the entire graph.

Therefore, we adapt a more practical way to generate our dataset and treat this project as a supervised classification problem.
For potential edges that do not appear at the graph, we label them 0 to identify their state as temporary unlinked or fake edges. These already existed edges are Label 1 to indicate true edges. The final model tuning randomly chooses 40,000 true edges and 40,000 fake edges respectively.

### Algorithm
As for our final approach, we decided to employ multi-layer perceptron as our prediction model. We think the task is a real world problem and it is feasible to adapt artificial neural network to solve the non-linear and complex relationship (link prediction) problem. 

We also try to apply other methods such as support vector machine (SVM) and NodeToVec as our other approaches to the problem. However, the process time it costs is enormous even for only 10,000 samples and we think it is not feasible with our equipment for this project.

### Features
Since the tendency for nodes that share more connections in a social network, they are more likely to be connected (Coursera, 2017). The natural alternative to computing the similarity between two nodes is to process the union set and the intersection of their neighbors. More features (Zhou, Lü, & & Zhang, 2009) are extended based on this fact and shown as below:

<div align=center>
  
![Description of the Features](https://github.com/gaoxiangyu369/Link_Prediction/blob/master/images/Screenshot%202018-12-10%2012.44.36.png)

</div>

## Evaluation metrics
In this work, we use the area under the receiver operating characteristic curve (AUC) as our evaluation method since it is our project standards. A 0.5 AUC represents random predictions and better model has higher value.

## Results and Analysis

**Individual Feature Performances**

AUC | CN | JC | RAI | AAI | PA | Salton
------------ | ------------- | ------------- | ------------- | ------------- | ------------- | -------------
AUC in own test set | 0.886515 | 0.801724 | 0.888501 | 0.888378 | 0.999435 | 0.872503
AUC in competition test set | 0.82766 | 0.79329 | 0.84973 | 0.81786 | 0.55666 | 0.84283

**Feature combination performance**

AUC | CN + RAI | CN + Salton | RAI + Salton | CN + RAI + Salton | CN + JC + RAI + AAI + PA + Salton
------------ | ------------- | ------------- | ------------- | ------------- | -------------
AUC in own test set | 0.882315 | 0.873475 | 0.889123 | 0.902315 | 0.772539
AUC in competition test set | 0.80523 | 0.72483 | 0.84236 | 0.85894 | 0.71322

