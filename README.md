# Orion Radford
### Walmart
***Walmart*** is located on Main st. It sits in the back of the parking lot infront of it there is three buildings. One is a *bank*, the second is a *gas station* and the last is *burger king*. It is also next door to *bearcat lanes*, the bowling ally.
---
# Airport to Walmart
### how to get from MCI to Walmart
1. turn onto I-29 South from NW 120th St.
2. go untill you reach exit 8 Barry Rd.
3. Follow Barry Rd. North untill Boardwalk Ave. and Walmart will be on your right.
### Some good food at Walmart
- Frozen pizza
- Anything fresh from the Bakery
- Rotisserie chicken

---
# Table of Sports

if you like sports there is sports here you should try.

| Sport | Location | Cost |
| ----------- | ----------- | ----------- |
| Bowling | like 50 bowling allys | $20 |
| hockey | go to someplace that has ice | $10 - $35 |
| soccer | any park or indoor place  | $0 - $20 |
| basketball | find a tall stick with a hoop on it | $0 |

---
# Quotes

> “Be yourself; everyone else is already taken.”  - *Oscar Wilde*

> “Two things are infinite: the universe and human stupidity; and I'm not sure about the universe.” - *Albert Einstein*

---
# Algorithm

> Prim’s Minimum Spanning Tree (MST)    
The idea behind Prim’s algorithm is simple, a spanning tree means all vertices must be connected. So the two disjoint subsets (discussed above) of vertices must be connected to make a Spanning Tree. And they must be connected with the minimum weight edge to make it a Minimum Spanning Tree.

```
import sys # Library for INT_MAX

class Graph():

	def __init__(self, vertices):
		self.V = vertices
		self.graph = [[0 for column in range(vertices)]
					for row in range(vertices)]

	# A utility function to print the constructed MST stored in parent[]
	def printMST(self, parent):
		print ("Edge \tWeight")
		for i in range(1, self.V):
			print (parent[i], "-", i, "\t", self.graph[i][parent[i]])

	# A utility function to find the vertex with
	# minimum distance value, from the set of vertices
	# not yet included in shortest path tree
	def minKey(self, key, mstSet):

		# Initialize min value
		min = sys.maxsize

		for v in range(self.V):
			if key[v] < min and mstSet[v] == False:
				min = key[v]
				min_index = v

		return min_index

	# Function to construct and print MST for a graph
	# represented using adjacency matrix representation
	def primMST(self):

		# Key values used to pick minimum weight edge in cut
		key = [sys.maxsize] * self.V
		parent = [None] * self.V # Array to store constructed MST
		# Make key 0 so that this vertex is picked as first vertex
		key[0] = 0
		mstSet = [False] * self.V

		parent[0] = -1 # First node is always the root of

		for cout in range(self.V):

			# Pick the minimum distance vertex from
			# the set of vertices not yet processed.
			# u is always equal to src in first iteration
			u = self.minKey(key, mstSet)

			# Put the minimum distance vertex in
			# the shortest path tree
			mstSet[u] = True

			# Update dist value of the adjacent vertices
			# of the picked vertex only if the current
			# distance is greater than new distance and
			# the vertex in not in the shortest path tree
			for v in range(self.V):

				# graph[u][v] is non zero only for adjacent vertices of m
				# mstSet[v] is false for vertices not yet included in MST
				# Update the key only if graph[u][v] is smaller than key[v]
				if self.graph[u][v] > 0 and mstSet[v] == False and key[v] > self.graph[u][v]:
						key[v] = self.graph[u][v]
						parent[v] = u

		self.printMST(parent)

g = Graph(5)
g.graph = [ [0, 2, 0, 6, 0],
			[2, 0, 3, 8, 5],
			[0, 3, 0, 0, 7],
			[6, 8, 0, 0, 9],
			[0, 5, 7, 9, 0]]

g.primMST();

```
code is from [GeeksForGeeks](https://www.geeksforgeeks.org/prims-minimum-spanning-tree-mst-greedy-algo-5/)


[About Me](AboutMe.md)