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