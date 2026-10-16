# Fuzzy Checkpointing (Cont.)

When recovering using a fuzzy checkpoint, start scan from the checkpoint record pointed to by last_checkpoint

+   Log records before last_checkpoint have their updates reflected in database on disk, and need not be redone.

+   Incomplete checkpoints, where system had crashed while performing checkpoint, are handled safely

![](bbox=[0.05, 0.42, 0.95, 0.88])