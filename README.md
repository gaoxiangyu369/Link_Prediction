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
  
![Network diagram for the adjacency list example](https://github.com/gaoxiangyu369/Link_Prediction/blob/master/Screenshot%202018-12-10%2012.19.23.png)
</div>

Each relationship has a direction indicating the source node person follows the target node person. However, some relationship or edges of the network is missing, which adds in uncertainty between two unconnected nodes. The main task to predict whether two randomly chosen nodes have a connection in real life through constructing directed social network topological structure, extracting features and training current dataset.

