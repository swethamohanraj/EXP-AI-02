# EXP02-Implement Breadth First Search Traversal of a Graph

#### NAME: K.M.Swetha
#### REG NO: 212221240055

## AIM:
To Implement Breadth First Search Traversal of a Graph using Python 3.

## THEORY:
Breadth-First Traversal (or Search) for a graph is like the Breadth-First Traversal of a tree. The only catch here is that, unlike trees, graphs may contain cycles so that we may come to the same node again. To avoid processing a node more than once, we divide the vertices into two categories:

1. Visited
2. Not Visited
 
A Boolean visited array is used to mark the visited vertices. For simplicity, it is assumed that all vertices are reachable from the starting vertex. BFS uses a queue data structure for traversal.

#### How does BFS work?

Starting from the root, all the nodes at a particular level are visited first, and then the next level nodes are traversed until all the nodes are visited. To do this, a queue is used. All the adjacent unvisited nodes of the current level are pushed into the queue, and the current-level nodes are marked visited and popped from the queue. Illustration: Let us understand the working of the algorithm with the help of the following example. 

Step1: Initially queue and visited arrays are empty.

![277148319-8acdebf8-ecc2-4d10-a208-45cce441f059](https://github.com/Aashima02/AI02-Implement-Breadth-First-Search-Traversal-of-a-Graph/assets/93427086/bc7e54b8-ed95-4762-bd7e-6d4303265889)

Queue and visited arrays are empty initially. 

Step2: Push node 0 into queue and mark it visited.

![277148352-0e9ce012-8e1f-43d7-b7b9-c0fb19fe0c3f](https://github.com/Aashima02/AI02-Implement-Breadth-First-Search-Traversal-of-a-Graph/assets/93427086/d7c35cea-f3ce-4e9e-8807-4a0d0c34ee8f)

Push node 0 into queue and mark it visited. 

Step 3: Remove node 0 from the front of queue and visit the unvisited neighbours and push them into queue.

![277148379-67d8fa3b-ce9e-46c2-9dd7-089e204e667a](https://github.com/Aashima02/AI02-Implement-Breadth-First-Search-Traversal-of-a-Graph/assets/93427086/c057a0f0-1a33-4789-86e3-da486deaf93c)

Step 4: Remove node 1 from the front of queue and visit the unvisited neighbours and push them into queue.

![277148430-b0cf0fde-8a86-41cb-a054-36875ac24ab0](https://github.com/Aashima02/AI02-Implement-Breadth-First-Search-Traversal-of-a-Graph/assets/93427086/ad2896ce-d3c3-4a8e-ba7e-a799d0ebb1a0)

Step 5: Remove node 2 from the front of queue and visit the unvisited neighbours and push them into queue.

![277148459-8968a163-6b3a-4f7e-8ad4-bbf24f326b9b](https://github.com/Aashima02/AI02-Implement-Breadth-First-Search-Traversal-of-a-Graph/assets/93427086/61df203f-6b93-4b00-8351-c2fc0b7205bc)

Step 6: Remove node 3 from the front of queue and visit the unvisited neighbours and push them into queue. As we can see that every neighbours of node 3 is visited, so move to the next node that are in the front of the queue.

![277148500-7a1c1b16-ea69-497f-a099-8440200f6dc0](https://github.com/Aashima02/AI02-Implement-Breadth-First-Search-Traversal-of-a-Graph/assets/93427086/32f86acd-3d39-42e8-b184-3b0e64076810)

Steps 7: Remove node 4 from the front of queue and visit the unvisited neighbours and push them into queue. As we can see that every neighbours of node 4 are visited, so move to the next node that is in the front of the queue.

![277148529-8e16ffa3-c3d6-4774-822b-6eb84adedad9](https://github.com/Aashima02/AI02-Implement-Breadth-First-Search-Traversal-of-a-Graph/assets/93427086/11252c88-c380-4387-a723-f672348fc1a5)

Remove node 4 from the front of queue and visit the unvisited neighbours and push them into queue. Now, Queue becomes empty, So, terminate these process of iteration.

## ALGORITHM:

1. Construct a Graph with Nodes and Edges

2. Breadth First Uses Queue and iterates through the Queue for Traversal.

3. Insert a Start Node into the Queue.

4. Find its Successors Or neighbors and Check whether the node is visited or not.

5. If Not Visited, add it to the Queue. Else Continue.

6. Iterate steps 4 and 5 until all nodes get visited, and there are no more unvisited nodes.

## PROGRAM:
```python
from collections import deque
from collections import defaultdict

def bfs(graph,start,visited,path):
    queue = deque()
    path.append(start)
    queue.append(start)
    visited[start] = True
    while len(queue) != 0:
        tmpnode = queue.popleft()
        for neighbour in graph[tmpnode]:
            if visited[neighbour] == False:
                path.append(neighbour)
                queue.append(neighbour)
                visited[neighbour] = True
    return path

graph = defaultdict(list)
v,e = map(int,input().split())
for i in range(e):
    u,v = map(str,input().split())
    graph[u].append(v)
    graph[v].append(u)

start = '0'
path = []
visited = defaultdict(bool)
traversedpath = bfs(graph,start,visited,path)
print(traversedpath)
```

### Sample Input and Output:

![image](https://github.com/Aashima02/AI02-Implement-Breadth-First-Search-Traversal-of-a-Graph/assets/93427086/37123abe-dcad-4d6c-a676-2d4ae763dcc5)



## RESULT:
Thus,a Graph was constructed and implementation of Breadth First Search for the same graph was done successfully.
