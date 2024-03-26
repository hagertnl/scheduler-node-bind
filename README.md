# scheduler-node-bind

This repo contains scripts that are used to reorder nodes and ranks in the LSF and Slurm schedulers on the OLCF supercomputers, Summit and Frontier.

The reordering is performed based on network topology.

On Frontier, the default behavior is to distribute nodes across as many dragonfly groups as possible, using a block distribution, where sequential nodes are packed in the same dragonfly group, except in the case of the first/last node in the group. When the ``--randomize`` flag is set, then that resulting block distribution is shuffled to remove inherent intra-group locality.

On Summit, the default behavior is to pack nodes into the fewest fat-tree groups as possible, using a block distribution, where sequential nodes are packed in the same fat-tree group, except in the case of the first/last node in the group. When the ``--randomize`` flag is set, then the entire node list for the allocation is shuffled, and the first `N` nodes are chosen.
