### BFS (Breadth-First Search)  
Breadth-First Search is a graph traversal algorithm that explores all nodes at the current depth level before moving to the next level. It uses a **queue** to keep track of nodes to visit, ensuring a level-by-level traversal.



https://github.com/user-attachments/assets/ded46567-d988-4f94-840a-e76a488353fa

### BFS Implementation
```cpp
vector<int> bfsOfGraph(vector<vector<int>> &adj) {  
    int n = adj.size();  
    queue<int> q;  
    vector<bool> visited(n, 0);  
    vector<int> bfs;  

    q.push(0);  
    visited[0] = 1;  

    while (!q.empty()) {  
        int node = q.front();  
        q.pop();  
        bfs.push_back(node);  

        for (auto ele : adj[node]) {  
            if (!visited[ele]) {  
                q.push(ele);  
                visited[ele] = 1;  
            }  
        }  
    }  

    return bfs;  
}

```
### DFS (Depth-First Search)  
Depth-First Search is a graph traversal algorithm that explores as far as possible along a branch before backtracking. It uses either:  
- A **stack** (iterative implementation)  
- **Recursion** (implicitly uses the call stack)
  
https://github.com/user-attachments/assets/617a7f46-8d96-4f23-819d-224c9bfdcba4


```cpp
private:
    void dfsCheck(int node, vector<int> &visited, vector<int> &dfs, vector<vector<int>>& adj){
        visited[node] = 1;
        dfs.push_back(node);
        
        for(auto ele: adj[node]){
            if(!visited[ele]){
                dfsCheck(ele, visited, dfs, adj);
            }
        }
    }
  public:
    vector<int> dfsOfGraph(vector<vector<int>>& adj) {
       
       int n = adj.size();
       vector<int> dfs;
       vector<int> visited(n,0);
       
       int start = 0;
       visited[0] = 1;
       dfsCheck(start, visited, dfs, adj);
       return dfs;
    }

```

