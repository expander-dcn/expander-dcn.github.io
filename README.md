# Expander Data Center Networks

This site is a compendium of resources on expander graphs, in particular including random graphs, for data center networks.

# Key Research Papers

* [Jellyfish: Networking Data Centers Randomly](https://www.usenix.org/conference/nsdi12/technical-sessions/presentation/singla). Ankit Singla, Chi-Yao Hong, Lucian Popa, and P. Brighten Godfrey. 9th USENIX Symposium on Networked Systems Design and Implementation (NSDI), April 2012. (An earlier version appeared in HotCloud 2011.)
  * Introduced the idea of using a degree-bounded random graph as the data center network topology, leading to better throughput and greater flexibility in construction compared to Clos networks (fat trees). In particular, the paper showed 25% higher throughput than Clos networks for the workloads it considered, and 60% lower incremental expansion cost for a particular model of incremental expansion, and better resilience to failed components.
  * Compared throughput with degree-diameter optimal (Moore bound) graphs, as a benchmark of an optimal topology, finding Jellyfish comes within 10% of their throughput. (See discussion of Moore graphs elsewhere on this page.)
  * Proposed approaches to deployment challenges: routing with k-shortest paths, and simplifying cabling via physical switch placement, patch panels providing the random matchings, and clustering with fewer cross-cluster links and bundling cables

* [High Throughput Data Center Topology Design](https://www.usenix.org/conference/nsdi14/technical-sessions/presentation/singla). Ankit Singla, P. Brighten Godfrey, and Alexandra Kolla. 11th USENIX Symposium on Networked Systems Design and Implementation (NSDI), April 2014.
  * Evaluates how close to optimal homogeneous random graphs are: Jellyfish closely approaches an analytical upper bound with a dense (all-to-all) traffic matrix; in other cases it ranges up to around 30% from the bound. Path length is within a few percent of the lower bound and approaches optimal with increased scale.
  * Studies how to configure connectivity in random graphs with heterogeneous degree and line speed.
  * Theoretically explains the effect (previously noted in the Jellyfish paper) that connectivity can be reduced between clusters of switches without impacting throughput.
  * Shows that randomizing the VL2 topology, which has heterogeneous line speeds and degrees, improves throughput by 43% (depending on exact topology and workload parameters, this could be more or less).

* [Slim Fly: A Cost Effective Low-Diameter Network Topology](https://spcl.inf.ethz.ch/Publications/.pdf/sf_sc_2014.pdf). Maciej Besta and Torsten Hoefler. International Conference on High Performance Computing, Networking, Storage and Analysis, November 2014 (SC 2014).

* [Measuring and Understanding Throughput of Network Topologies](https://pbg.cs.illinois.edu/papers/jyothi16throughput.pdf). Sangeetha Abdu Jyothi, Ankit Singla, P. Brighten Godfrey, and Alexandra Kolla. ACM/IEEE International Conference for High Performance Computing, Networking, Storage and Analysis (SC), November 2016.
  * Demonstrates that cut-metrics, like bisection bandwidth and sparsest cut, are the wrong metrics for throughput. In fact, they can be asymptotically wrong: there are networks A and B, where A has a higher cut and B has asymptotically higher throughput.
  * Instead, proposes to measure worst-case throughput with an efficient algorithm to generate a near-worst-case traffic matrix for any given topology.
  * Benchmarks a wide range of topologies using worst-case and common-case traffic, including: BCube, DCell, Dragonfly, Fat Tree, Flattened Butterfly, Hypercube, HyperX, Jellyfish, Long Hop, and Slim Fly. At small scale, DCell performs well. At moderate to large scale (>1000 servers) the expanders -- Jellyfish, Long Hop, and Slim Fly -- perform best, with Jellyfish and Long Hop handling worst-case traffic best. Fat trees perform particularly poorly with nonuniform traffic, around half the throughput of Jellyfish.

* [Xpander: Towards Optimal-Performance Datacenters](https://dl.acm.org/doi/10.1145/2999572.2999580). Asaf Valadarsky, Gal Shahaf, Michael Dinitz, and Michael Schapira. ACM CoNEXT 2016. ([Prior version](https://dl.acm.org/doi/10.1145/2834050.2834059) in HotNets 2015. [Project page](https://husant.github.io/Xpander/).)
  * Proposes Xpander, a deterministic expander graph construction for a data center network based on 2-lifts which can be incrementally expanded.
  * Shows that several recently proposed data center topologies perform well because they are expanders -- in particular showing Jellyfish, Xpander, and several other expander graph constructions have nearly identical throughput, path length, and failure resilience. Also shows Slim Fly has reasonbly high expansion, though not quite as high as Jellyfish and Xpander.
  * Experiments with a hardware test (the first ever?) of an expander graph on a small testbed, showing better performance than fat trees.

* [Beyond fat-trees without antennae, mirrors, and disco-balls](https://dl.acm.org/doi/10.1145/3098822.3098836). Simon Kassing, Asaf Valadarsky, Gal Shahaf, Michael Schapira, and Ankit Singla. ACM SIGCOMM 2017. ([Prior version](https://dl.acm.org/doi/10.1145/3005745.3005747) in HotNets 2016.)

* [Spineless Data Centers](https://dl.acm.org/doi/10.1145/3422604.3425945). Vipul Harsh, Sangeetha Abdu Jyothi, and P. Brighten Godfrey. Nineteenth ACM Workshop on Hot Topics in Networks (HotNets), November 2020.

* [Starfish: A Topology-Routing Co-Design for Small-Scale Data Centers](https://www.usenix.org/conference/nsdi26/presentation/zhou-starfish). Anchengcheng Zhou, Vipul Harsh, Sangeetha Abdu Jyothi, Maria Apostolaki, and P. Brighten Godfrey. 23rd USENIX Symposium on Networked Systems Design and Implementation (NSDI), May 2026.

* [RNG: Flat Datacenter Networks at Scale](https://arxiv.org/abs/2604.15261). Giacomo Bernardi, Ratul Mahajan, C. Seshadhri, Enrico Carlesso, Chinchu Merine Joseph, Saurabh Kumar, Pavan Manikonda, Luiza Popa, Randy Ram, Steven Robinson, Elizabeth Tennent. ArXiV, May 2026.
  * Describes the first production deployment of random graphs (also the first deployment of any expander based data center) at Amazon Web Services, where it is "now the default datacenter network for most workloads at Amazon"
  * Uses 45% fewer switches than fat trees (with a corresponding 45% cost reduction), while matching or exceeding fat tree performance
  * Addresses deployment challenges: (1) spraypoint routing to provide diverse paths with limited router memory, (2) passive optical devices called ShuffleBoxes, used as intermediate panels to ease wiring and incremental addition of racks, (3) analytical models to assist operator capacity planning

## Theoretical Background

* [Approximate Moore Graphs are good expanders](https://dl.acm.org/doi/10.1016/j.jctb.2019.08.003). Michael Dinitz, Michael Schapira, and Gal Shahaf. Journal of Combinatorial Theory Series B, Vol. 141, No. C, 2020. An earlier version appeared in ESA 2018.
  * Two major measures of topology optimality are (1) graph expansion and (2) approaching the Moore bound, which bounds the maximum number of nodes for a given degree and diameter. These have served as inspiration or explanation for data center and HPC network topology design.
  * Showed that the two major measures of optimality are actually fundamentally connected: it is easily seen that good expanders have low diameter; here it is shown that graphs with low diameter (for a given number of nodes and degree) are also forced to be good expanders.

# Talks and Lecture Slides

* [Networking Data Centers Randomly](https://www.youtube.com/watch?v=yEjcZC34qNo). Brighten Godfrey. Talk at Texas A&M University, November 14, 2013.

# Simulators and Data Sets

* [Topobench](https://github.com/ankitsingla/topobench-1): topology comparison tool used in Jellyfish (NSDI'12) and later extended in several papers (NSDI'14, SC'16, HotNets'16). Uses a multicommodity flow analysis -- that is, modeling network flow as a fluid rather than a packet-level simulation.
* [NetBench](https://github.com/ndal-eth/netbench): packet level simulator from Beyond Fat-Trees (SIGCOMM'17).
* [Starfish simulator](https://github.com/AnnZhouCcc/Starfish): packet level simulator from Starfish (NSDI'26), which also includes other topologies for comparison.
