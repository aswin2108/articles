# Biconnected Components
Turns out, biconnected components are one of the most important topic in design analysis of algorithms, data structures and in many competetive exams.
Biconnected components are defined as a maximal biconnected subgraph. 
Lets understand it better!

**Table Of Contents**
1. Prerequisites
    1.1 Graph
    1.2 Articulation Point
    1.3 Biconnected Graph
2. What Are Biconnected Components
3. How To Build A Biconnected Graph
4. Identify Articulation Point In A Graph

# 1 Prerequisites
These are some of the things which you should know before we get to our main topic!

## 1.1 Graph
<p>Graphs can be defined as a mathematical structure which represents a specific function. It is constructed by connecting a set of points using lines.
Each points are known as vertex (node) and the line joining it is known as edges.
In the below graph A,B,C,D and E are known as vertex and the lines joining them are known as edges.</p> 

Fig 1

<p>These graphs have a lot of applications in a lot of different fields like computer science, physics, chemistry etc.
There is even a study called graph theory to learn about the relationship between nodes and edges.</p>
So its a very important concept. The topic biconnected component is a part of this theory. There are a lot of different types of graphs, eg:
Conected graph: If in a graph there is a path between every pair of distinct vertices we can call it a connected graph.

## 1.2 Articulation Point
A vertex V in a connected graph G is an articulation point (cut point) if the deletion of vertex V along with all edges incident to V disconnects the graph into two or more non-empty components.<br> 
Lets demonstrate it with an example:
Fig 2 shows a connected graph

Fig2

Here we can say vertex 2 is an articulation point, because if we remove the vertex 2 along with the incident edges we can observe that the graph splits into two non-empty component.

fig 3

After deleting vertex 2 and the incident edges of vertex 2, the given graph is divided into two non-empty components as in the figure above. 
=> vertex 2 is an articulation point

## 1.3 Biconnected Graph
We can call a graph G a biconnected graph if it contains zero articulation point. 
Example:

fig 4

The above graph contains no articulation point
=> The graph is Biconnected Graph.

# What Are Biconnected Components
A maximal biconnected subgraph is a Biconnected component.
Its really simple if you understand the sentance carefully. Take a biconnected sub-graph of a graph, then keep on adding the neighbouring vertices and edges and take a step back if you find an articulation point. So now you will have a biconnected sub-graph of the given graph with maximum nodes possible such that there are no articulation point.

Note: You might have to read it a couple of times to get the whole idea.
Note From the defenition you might have understood that any biconnected graph can be a biconnected component, as any graph is a sub-graph of itself.

Lets take an example:
 
 fig 5

Here the given graph has 3 articulation points ie, vertex 2, 3, 5, as the graph splits into various parts if we remove one vertex and the edges incident to it.
So the following are the biconnected components in the graph. As you might observe if we take two of them togeher they will have atmost 1 vertex in common and that vertex is none other than the articulation point. Take any pair and check. 

fig 6

# 3. How To Build A Biconnected Graph
**Steps to follow to build a biconnected graph:**
1. Check whether the given graph is biconnected or not.
2. If its not biconnected identify all the articulation point.
3. After obtaining the articulation points, determine the set of edges whose inclusion makes the graph connected in the absence of articulation point.

Now lets look the steps for our graph.
1. The given grapg G is not a biconnected graph, the articulation points are 2,3 and 5.
2. To transform G to biconnected graph new edges are included to te articulation point.

* Edges corresponding to the articulation point 2 are (1,5) and (3,8).
* Edges corresponding to the articulation point 3 are (4,10) and (2,9).
* Edges corresponding to the articulation point 5 are (6,7).
So lets add these edges.

fig 7

The edges added are represented as dotted lines.
After the edition of these lines we can observe that it is a biconnected graph.
