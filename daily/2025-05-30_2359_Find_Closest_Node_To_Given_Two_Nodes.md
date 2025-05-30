# 2359. Find Closest Node To Given Two Nodes

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/find-closest-node-to-given-two-nodes/description/?envType=daily-question&envId=2025-05-30)

## Solution

```python
from collections import deque
class Solution:
    def closestMeetingNode(self, edges: List[int], node1: int, node2: int) -> int:

#####################  BFS #########################

        # def bfs(node:int,egdes:List[int])->List[int]:
        #     noOfNodes=len(edges)
        #     distanceFromTarget=[float('inf')]*noOfNodes
            
        #     distance=0
        #     seen=set()
        #     que=deque([node])
        #     while que:
        #         node=que.popleft()
        #         distanceFromTarget[node]=distance
        #         seen.add(node)
        #         if edges[node]==-1 or edges[node] in seen:
        #             break
        #         que.append(edges[node])
        #         distance+=1

        #     return distanceFromTarget

        # distanceFromNode1=bfs(node1,edges)
        # distanceFromNode2=bfs(node2,edges)
        # print(distanceFromNode1,distanceFromNode2)
#################### Find Min from the Max of the Distance

        # distanceFromNode1=bfs(node1,edges)
        # distanceFromNode2=bfs(node2,edges)
        # # print(distanceFromNode1,distanceFromNode2)

        # res=-1
        # minDistance=float("inf")

        # for i in range(len(edges)):
        #     maxDistance=max(distanceFromNode1[i],distanceFromNode2[i])
        #     if maxDistance<minDistance:
        #         # print(res,i)
        #         res=i
        #         minDistance=maxDistance
        # return res
        
#####################  DFS #########################

        def dfs(node:int,edges:List[int],visited:List[int],distanceFromTarget:List[int])->None:
            visited[node]=True
            ngbr=edges[node]
            if ngbr!=-1 and not visited[ngbr]:
                distanceFromTarget[ngbr]=1+distanceFromTarget[node]
                dfs(ngbr,edges,visited,distanceFromTarget)

        
        noOfNodes=len(edges)
        distanceFromNode1=[-1]*noOfNodes
        visited=[False]*noOfNodes
        distanceFromNode1[node1]=0
        dfs(node1,edges,visited,distanceFromNode1)
        distanceFromNode2=[-1]*noOfNodes
        visited=[False]*noOfNodes
        distanceFromNode2[node2]=0
        dfs(node2,edges,visited,distanceFromNode2)

        print(distanceFromNode1,distanceFromNode2)

            

#################### Find Min from the Max of the Distance
        res=-1
        minDistance=float("inf")

        for i in range(len(edges)):
            if distanceFromNode1[i] != -1 and distanceFromNode2[i] != -1:
                maxDistance=max(distanceFromNode1[i],distanceFromNode2[i])
                if maxDistance<minDistance:
                    # print(res,i)
                    res=i
                    minDistance=maxDistance
        return res    
```

## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:
```
[2,2,3,-1]
0
1
[1,2,-1]
0
2
[4,4,4,5,1,2,2]
1
1
```
