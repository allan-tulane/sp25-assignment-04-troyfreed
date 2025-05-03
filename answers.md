# CMPS 2200 Assignment 5
## Answers

**Name:**Troy Freed



- **1a.**
The maximum depth of a d-ary heap is logd((d-1)n+1)-1, which is O(logd(n))

- **1b.**
if a d-ary heap has a height of O(logd(n))

Insert: at each of at most h levels there is one comparison, and one possible swap with the parent.
this makes the work equal O(log_d(n))

Delete-min: at each of the levels you must scan all up to d children to find smallest then swap down
this makes work = O(d*log_d(n))

- **1c.**

if you are performing |V| delete-min operations, each costing dlogd|V| and
up to |E| insert operations each costing logd|V| you can put these together giving
a new bound on the work = O(d|V|logd|V| + |E|logd|V|)

- **1d.**
d = O(log|V|)

- **2a.**

vith k=0 weight = -2 k=1 weight = 1 k=2 weight = 2 starting at 0: APSP(0,0,0) = 0 APSP(0,0,1) = 0 APSP(0,0,2) = 0 APSP(0,1,0) = -2 APSP(0,1,1) = -2 APSP(0,1,2) = -2 APSP(0,2,0) = 2 APSP(0,2,1) = -1 APSP(0,2,2) = -1

starting at 1: APSP(1,0,0) -2 APSP(1,0,1) = -2 APSP(1,0,2) = -2 APSP(1,1,0) = 0 APSP(1,1,1,) = 0 APSP(1,1,2) = 0 APSP(1,2,0) = 1 APSP(1,2,1) = 0 APSP(1,2,2) = 0

starting at 2: APSP(2,0,0) = 2 APSP(2,0,1) = -1 APSP(2,0,2) = -1 APSP(2,1,0) = 1 APSP(2,1,1) = 0 APSP(2,1,2) = 0 APSP(2,2,0) = 0 APSP(2,2,1) = 0 APSP(2,2,2) = 0

- **2b.**
Yes, when you move k = 1 to k = 2 any new shortest path still avoids vertex 2, or
its length stays APSP(i, j, 1) or it goes through 2 exactly once so length is 
APSP(i,2,1) + APSP(2,j,1), therefore
APSP(i, j, 2) = min(APSP(i, j, 1), APSP(i, 2, 1) + APSP(2, j, 1))

- **2c.**
APSP(i,j,k) = min(APSP(i,j,k-1),APSP(i,k,k-1)+APSP(k,j,k-1))

- **2d.**

there are n choices of k and n^2 pairs, so n^3 sub problems each being O(1) so in total O(n^3) work

- **2e.**

Johnson's algorithm is O(n^2log(n)+nm), compared to our algoirthm O(n^3)
our algorithm wins when the graph is smaller and more dense.

- **3a.**
Yes, an MST also minimizes the maximum edge weight, so any MST solves the MMET problem. An MST minimizes
the weight of the largest edge it uses.  If there were some other spanning tree whose heaviest edge were strictly 
lighter than the heaviest edge in an MST, then swapping that lighter edge in would contradict the cut
optimality property of the MST. Meaning every MST also solves the MMET problem.

- **3b.**
If the MST is unavailable you can find the next best spanning tree by examining each edge not in the tree
for every such edge insert e into the tree, then locate the heaviest edge on the cycle excluding the new edges
and remove it to restore the tree property. Each resulting candidate tree differs from the original, by swapping
new edges in for the original one, and you simply track which candidate tree has the smallest total weight.
The tree with the lowest weight among these swaps is the second best spanning tree.

- **3c.**
The running time is O(VlogV + ElogV) = O((V+E)logV), in any connected graph E >= V - 1,
so E log V dominates VlogV giving O(ElogV)
