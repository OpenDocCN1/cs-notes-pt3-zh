# Distributed Lock Manager

In this approach, functionality of locking is implemented by lock managers at each site

+   - Lock managers control access to local data items

+   - But special protocols may be used for replicas

Advantage: work is distributed and can be made robust to failures

Disadvantage: deadlock detection is more complicated

+   - Lock managers cooperate for deadlock detection

+   - More on this later

Several variants of this approach

+   - Primary copy

+   - Majority protocol

+   - Biased protocol

+   - Quorum consensus