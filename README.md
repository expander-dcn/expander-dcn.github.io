# Expander Data Center Networks

This site is a compendium of resources on random graphs and, more generally, expander graphs, for data center networks.

# Research Papers

* [Jellyfish: Networking Data Centers Randomly](https://www.usenix.org/conference/nsdi12/technical-sessions/presentation/singla). Ankit Singla, Chi-Yao Hong, Lucian Popa, and P. Brighten Godfrey. 9th USENIX Symposium on Networked Systems Design and Implementation (NSDI), April 2012.
  * Introduced the idea of using a random graph as the data center network topology, leading to better throughput and greater flexibility in construction compared to Clos networks (fat trees). In particular, the paper showed 25% higher throughput than Clos networks for the workloads it considered, and 60% lower incremental expansion cost for a particular model of incremental expansion, and better resilience to failed components.
  * Compared throughput with degree-diameter optimal (Moore bound) graphs, as a benchmark of an optimal topology, finding Jellyfish comes within 10% of their throughput. (See discussion of Moore graphs elsewhere on this page.)
  * Proposed routing with k-shortest paths, and simplifying cabling via physical switch placement, patch panels providing the random matchings, and clustering with fewer cross-cluster links and bundling cables

## Theoretical Background

* [Approximate Moore Graphs are good expanders](https://dl.acm.org/doi/10.1016/j.jctb.2019.08.003). Michael Dinitz, Michael Schapira, and Gal Shahaf. Journal of Combinatorial Theory Series B, Vol. 141, No. C, 2020. An earlier version appeared in ESA 2018.
  * Two major measures of topology optimality are (1) graph expansion and (2) approaching the Moore bound, which bounds the maximum number of nodes for a given degree and diameter. These have served as inspiration or explanation for data center and HPC network topology design.
  * This paper showed that the two major measures of optimality are actually fundamentally connected: it is easily seen that good expanders have low diameter; here it is shown that graphs with low diameter (for a given number of nodes and degree) are also good expanders.

# Talks and Lecture Slides

# Simulators
