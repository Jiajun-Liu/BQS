# Bounded Quadrant System: Error-bounded trajectory compression on the go
Official reference implementation of the 2015/2016 papers:

1. *J. Liu, K. Zhao, P. Sommer, S. Shang, B. Kusy and R. Jurdak, "Bounded Quadrant System: Error-bounded trajectory compression on the go," 2015 IEEE 31st International Conference on Data Engineering, 2015, pp. 987-998, doi: 10.1109/ICDE.2015.7113350.*

1. *J. Liu et al., "A Novel Framework for Online Amnesic Trajectory Compression in Resource-Constrained Environments," in IEEE Transactions on Knowledge and Data Engineering, vol. 28, no. 11, pp. 2827-2841, 1 Nov. 2016, doi: 10.1109/TKDE.2016.2598171.*

LEGACY CODE PROVIDED AS IS, NOT THE BEST READABILITY. 

## Description
This repository implements an error-bounded, online trajectory simplification algorithm called Bounded Quadrant System (BQS). This method has two versions: the full version and the light version. The full version searches for a solution by looking into the error upperbound when adding a new point to a quadrant-wise bounding system. As an online algorithm, the full version of BQS outperforms buffer/batch-based methods. And the light version reaches O(1) in both space and time complexity for proces a new point, with very competitive compression rate and error.

Later this algorithm was extended to handle more data than a given memory budget by using an amnesic strategy, so that error grows gradually and slow. We formulate the BQS algorithm with an uncertainty vector to support the progressive compression of trajectories, and subsequently propose Progressive BQS (PBQS). Using PBQS as the corner stone, we propose a sophisticated online framework called Amnesic Bounded Quadrant System which not only simplifies streaming trajectory data efficiently, but also manages historical data in an amnesic way. ABQS introduces graceful degradation to the entire trajectory history without hard data loss (overwriting), and hence achieves excellent compression performances when the operation duration is unknown and the data volume far exceeds the storage limit.

## Usage
The main simplification interface is provided in class TrajProcessor in qs_p_to_seg.py (https://github.com/Jiajun-Liu/BQS/blob/235c2234ddf4ae9fb2b2316ef6e089c9f93b9ff9/qs_p_to_seg.py#L430)

See function runone for its sample usage. (https://github.com/Jiajun-Liu/BQS/blob/235c2234ddf4ae9fb2b2316ef6e089c9f93b9ff9/qs_p_to_seg.py#L819)

The amnesic storage strategy ABQS is implemented in class BQSStorage in amnesic_bubbling.py (https://github.com/Jiajun-Liu/BQS/blob/235c2234ddf4ae9fb2b2316ef6e089c9f93b9ff9/amnesic_bubbling.py#L19)
