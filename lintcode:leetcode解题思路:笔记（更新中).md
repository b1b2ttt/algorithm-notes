#Lintcode/Leetcode解题思路/笔记（更新中）

## Notes of Lintcode/Leetcode 


###0. Numbers of Islands


- BFS/DFS都可以，但是DFS容易造成stack overflow,所以采用BFS比较好

- 从左上角开始向右，向下遍历，左上角坐标计为(0,0),并且使用count进行计数，若遇到1，则count加一

- 在成块的“1”区域中，遇到第一个“1”，count就加1，那么如何实现这个“1”周围（上下左右四个相邻的位置）出现的“1”不被重复计数呢？方法是：搜索上下左右四个方向，遇到“1”，将“1”变为0即可

- 注意：要进行边界判断：不能超出边界了

###1. Sequence Reconstruction
- 将seqs中的各序列seq按照其中元素出现的先后顺序建立有向图。例如seqs中的某序列seq = [1, 2, 3]，对应有向图，顶点为1, 2, 3；边为(1, 2), (2, 3)。利用Map<Integer, Integer> indegree记录各顶点的入度（indegree），Map<Integer, Integer> map记录各顶点的后继（边）。
- 然后对图执行拓扑排序，将得到的排序结果与原始序列org作比对即可

###2. Topological Sorting

- using BFS
- STEP 1: count indegree: 
  * initialize：
  
        ``` 
        Map<DirectedGraphNode, Integer> indegree = new HashMap<>();
        for(DirectedGraphNode node: graph){
            indegree.put(node, 0);//初始化
  * counting indegree
     
        ```  
        for(DirectedGraphNode node : graph){
            for(DirectedGraphNode neighbor : node.neighbors){
                // node--neighbor
                indegree.put(neighbor, indegree.get(neighbor) + 1);
            }
        }
  `
       
- STEP 2: topological sorting :put the nodes whose indegree is zero into queue 
- STEP 3: BFS






