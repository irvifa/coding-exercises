# Find if Path Exist in Graph

```
class Solution {
    
    static class Graph {
        private final List<List<Integer>> g;
        
        public Graph(int[][] edges, int n) {
            g = new ArrayList<>();
            for(int i = 0; i < n; i++) {
                g.add(new ArrayList<>());
            }
            for(int[] edge: edges) {
                addEdge(edge[0], edge[1]);
            }
        }
        
        public void addEdge(int x, int y) {
            this.g.get(x).add(y);
            this.g.get(y).add(x);
        }
        
        public boolean isReachable(int s, int d) {
            if (s == d) {
                return true;
            }
            
            boolean[] visited = new boolean[g.size()];
            Stack<Integer> st = new Stack<>();
            visited[s] = true;
            st.push(s);
            while (!st.empty()) {
                int top = st.pop();
                for (int i = 0; i < this.g.get(top).size(); i++) {
                    int current = g.get(top).get(i);
                    if (current == d) {
                        return true;  
                    }
                    if (visited[current] != true) {
                        visited[current] = true;
                     st.push(current);
                    }
                }
            }
            return false;
            
        }
    }
    
    public boolean validPath(int n, int[][] edges, int start, int end) {
        Stack<Integer> s = new Stack<>();
        Graph g = new Graph(edges, n);
        return g.isReachable(start, end);    
    }
}
```
