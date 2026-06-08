# Expander Data Center Networks

This site is a compendium of resources on expander graphs, in particular including random graphs, for data center networks.

# Research Papers

* [Jellyfish: Networking Data Centers Randomly](https://www.usenix.org/conference/nsdi12/technical-sessions/presentation/singla). Ankit Singla, Chi-Yao Hong, Lucian Popa, and P. Brighten Godfrey. 9th USENIX Symposium on Networked Systems Design and Implementation (NSDI), April 2012. (An earlier version appeared in HotCloud 2011.)
  * Introduced the idea of using a degree-bounded random graph as the data center network topology, leading to better throughput and greater flexibility in construction compared to Clos networks (fat trees). In particular, the paper showed 25% higher throughput than Clos networks for the workloads it considered, and 60% lower incremental expansion cost for a particular model of incremental expansion, and better resilience to failed components.
  * Compared throughput with degree-diameter optimal (Moore bound) graphs, as a benchmark of an optimal topology, finding Jellyfish comes within 10% of their throughput. (See discussion of Moore graphs elsewhere on this page.)
  * Proposed approaches to deployment challenges: routing with k-shortest paths, and simplifying cabling via physical switch placement, patch panels providing the random matchings, and clustering with fewer cross-cluster links and bundling cables

* [High Throughput Data Center Topology Design](https://www.usenix.org/conference/nsdi14/technical-sessions/presentation/singla). Ankit Singla, P. Brighten Godfrey, and Alexandra Kolla. 11th USENIX Symposium on Networked Systems Design and Implementation (NSDI), April 2014.
  * Shows that the Jellyfish topology is near optimal for throughput, by developing an analytical upper bound for throughput for any graph with a given number of nodes and node degree. In some configurations, with a dense (all-to-all) traffic matrix, Jellyfish matches this bound; in other cases it is 10-30% from the bound, depending on topology parameters and workload.
  * Studies heterogeneous topology design, with switches of different degree and different link capacity.

* [Slim Fly: A Cost Effective Low-Diameter Network Topology](https://spcl.inf.ethz.ch/Publications/.pdf/sf_sc_2014.pdf). Maciej Besta and Torsten Hoefler. International Conference on High Performance Computing, Networking, Storage and Analysis, November 2014 (SC 2014).

* [Measuring and Understanding Throughput of Network Topologies](https://pbg.cs.illinois.edu/papers/jyothi16throughput.pdf). Sangeetha Abdu Jyothi, Ankit Singla, P. Brighten Godfrey, and Alexandra Kolla. ACM/IEEE International Conference for High Performance Computing, Networking, Storage and Analysis (SC), November 2016.

* [Xpander: Towards Optimal-Performance Datacenters](https://dl.acm.org/doi/10.1145/2999572.2999580). Asaf Valadarsky, Gal Shahaf, Michael Dinitz, and Michael Schapira. ACM CoNEXT 2016. A prior version appeared in HotNets 2015.

* [Beyond fat-trees without antennae, mirrors, and disco-balls](https://dl.acm.org/doi/10.1145/3098822.3098836). Simon Kassing, Asaf Valadarsky, Gal Shahaf, Michael Schapira, and Ankit Singla. ACM SIGCOMM 2017.

* [Spineless Data Centers](https://dl.acm.org/doi/10.1145/3422604.3425945). Vipul Harsh, Sangeetha Abdu Jyothi, and P. Brighten Godfrey. Nineteenth ACM Workshop on Hot Topics in Networks (HotNets), November 2020.

* [Starfish: A Topology-Routing Co-Design for Small-Scale Data Centers](https://www.usenix.org/conference/nsdi26/presentation/zhou-starfish). Anchengcheng Zhou, Vipul Harsh, Sangeetha Abdu Jyothi, Maria Apostolaki, and P. Brighten Godfrey. 23rd USENIX Symposium on Networked Systems Design and Implementation (NSDI), May 2026.

* [RNG: Flat Datacenter Networks at Scale](https://arxiv.org/abs/2604.15261). Giacomo Bernardi, Ratul Mahajan, C. Seshadhri, Enrico Carlesso, Chinchu Merine Joseph, Saurabh Kumar, Pavan Manikonda, Luiza Popa, Randy Ram, Steven Robinson, Elizabeth Tennent. ArXiV, May 2026.

## Theoretical Background

* [Approximate Moore Graphs are good expanders](https://dl.acm.org/doi/10.1016/j.jctb.2019.08.003). Michael Dinitz, Michael Schapira, and Gal Shahaf. Journal of Combinatorial Theory Series B, Vol. 141, No. C, 2020. An earlier version appeared in ESA 2018.
  * Two major measures of topology optimality are (1) graph expansion and (2) approaching the Moore bound, which bounds the maximum number of nodes for a given degree and diameter. These have served as inspiration or explanation for data center and HPC network topology design.
  * This paper showed that the two major measures of optimality are actually fundamentally connected: it is easily seen that good expanders have low diameter; here it is shown that graphs with low diameter (for a given number of nodes and degree) are also forced to be good expanders.

# Talks and Lecture Slides

# Simulators and Data Sets
