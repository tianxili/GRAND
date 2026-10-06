# GRAND
This repository contains the code for examples in the paper

GRAND: Graph Release with Assured Node Differential Privacy, by Suqing Liu, Xuan Bi and Tianxi Li. (https://arxiv.org/abs/2507.00402). 

Abstract: Differential privacy is a well-established framework for safeguarding sensitive information in data. While extensively applied across various domains, its application to network data — particularly at the node level — remains underexplored. Existing methods for node-level privacy either focus exclusively on query-based approaches, which restrict output to pre-specified network statistics, or fail to preserve key structural properties of the network. In this work, we propose GRAND (Graph Release with Assured Node Differential privacy), which is, to the best of our knowledge, the first network release mechanism that releases networks while ensuring node-level differential privacy and preserving structural properties. Under a broad class of latent space models, we show that the released network asymptotically follows the same distribution as the original network. The effectiveness of the approach is evaluated through extensive experiments on both synthetic and real-world datasets.


We ask you to kindly include the reference to the above paper if you use any part of the code for publications.

The core functions for GRAND and the network models are provided by the `GRANDpriv` and `randnet` packages. The scripts in `CommunityFitNet` instead source `GraphDIP-Source.R`, included at the top level of `GRAND-PublicCode`, which provides the same core functions in script form. The code is organized as follows:

1) MainSimulation
   - Public-SimulationExamples_LSM.R: Code for simulation examples in the paper under the inner product latent space model.
   - Public-SimulationExamples_RDPG.R: Code for simulation examples in the paper under the RDPG model.
   - DataExamples.R: Code for the two data examples (Caltech network and statisticians' network).
   - Caltech36.mtx: Data for the Caltech Facebook network collected by Traud et al. [2012].
   - DataForGNC-Plot-Combined.Rda: Statisticians' collaboration network originally collected by Ji and Jin [2016]. The version used here is the processed version in Li et al. [2020].

2) Ratio
   - Fix_N_LSM.R and Fix_N_RDPG.R: Split-ratio experiments with fixed total network size N.
   - Fixn_LSM.R and Fixn_RDPG.R: Split-ratio experiments with fixed released-network size n.
   - Fixm_LSM.R and Fixm_RDPG.R: Split-ratio experiments with fixed hold-out-network size m.
   - The corresponding files ending in `_Plot.R` summarize the saved results and generate the figures.

3) Sparsity
   - Sparsity_LSM.R and Sparsity_RDPG.R: Network-sparsity experiments under LSM and RDPG.
   - Sparsity_LSM_Plot.R and Sparsity_RDPG_Plot.R: Code for summarizing the saved results and generating the figures.

4) Misspecification
   - Misspecification_LSM.R, Misspecification_RDPG.R, Misspecification_ER.R, Misspecification_SBM.R, Misspecification_Graphon1.R, and Misspecification_Graphon2.R: Model-misspecification experiments under the corresponding data-generating mechanisms.
   - The corresponding files ending in `_Plot.R` summarize the saved results and generate the figures.
   - Graphon1_Heatmap.R and Graphon2_Heatmap.R: Code for generating the two graphon heatmaps.

5) MembershipInference
   - Membership_Attack.R: Membership-inference attack against the hold-out set, over the four split ratios reported in the paper.
   - Membership_Attack_Table.R: Code for summarizing the saved results and generating the table of attack advantages and permutation p-values.

6) AttributedNetwork
   - Attributed_GRAND.R: GRAND for networks with node attributes, applied to the school friendship network, producing the joint distributions of community and attribute in the true and the privatized released network.
   - Attributed_Plot.R: Code for summarizing the saved results and generating the paired heatmaps for the four attributes.
   - The scripts read the processed objects `averge_network.Rda`, `X_true.Rda` and `Y.Rda`, the friendship network and node attributes used in Wang et al. [2026], available from the materials of that paper. The underlying survey is ICPSR study 37070 [Paluck et al., 2019], whose terms of use do not permit redistribution, so these files are not included here.

7) CommunityFitNet
   - CommunityFitNet_Evaluation.R: Evaluation of GRAND and the Laplace mechanism on the social networks of the CommunityFitNet collection with more than 200 nodes.
   - CommunityFitNet_Plot.R: Code for summarizing the saved results and generating the scatterplots of the Wasserstein distances.
   - SocialGList.Rda: The social networks used here, taken from the CommunityFitNet collection of Ghasemian et al. [2019].

8) CommunityRecovery
   - SBM_Community_Recovery.R: Recovery accuracy of the true community labels from the GRAND-privatized network, under a stochastic block model with three communities, size 4000 and average degree 200.





## References

S. Liu, X. Bi, and T. Li. GRAND: Graph Release with Assured Node Differential Privacy. *arXiv preprint arXiv:2507.00402*, 2025.

A. Ghasemian, H. Hosseinmardi, and A. Clauset. Evaluating overfit and underfit in models of network community structure. *IEEE Transactions on Knowledge and Data Engineering*, 32(9):1722–1735, 2019.

E. L. Paluck, H. R. Shepherd, and P. Aronow. Changing Climates of Conflict: A Social Network Experiment in 56 Schools, New Jersey, 2012-2013. *Inter-university Consortium for Political and Social Research* [distributor], ICPSR 37070.

J. Wang, C. M. Le, and T. Li. Perturbation-robust predictive modeling of social effects by network subspace generalized linear models. *The Annals of Applied Statistics*, 20(2):1691–1718, 2026.

A. L. Traud, P. J. Mucha, and M. A. Porter. Social structure of Facebook networks. *Physica A: Statistical Mechanics and its Applications*, 391(16):4165–4180, Aug. 2012.

P. Ji and J. Jin. Coauthorship and citation networks for statisticians. *The Annals of Applied Statistics*, 10(4):1779–1812, 2016.

T. Li, C. Qian, E. Levina, and J. Zhu. High-dimensional Gaussian graphical models on network-linked data. *Journal of Machine Learning Research*, 21(74):1–45, 2020.

