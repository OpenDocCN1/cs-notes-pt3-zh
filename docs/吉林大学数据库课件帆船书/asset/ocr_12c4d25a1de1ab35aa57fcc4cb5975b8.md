# Thomas' Write Rule

![](bbox=[0.02, 0.12, 0.22, 0.45])

+   Modified version of the timestamp-ordering protocol in which obsolete write operations may be ignored under certain circumstances.

+   When Ti attempts to write data item Q, if TS(Ti) < W-timestamp(Q), then Ti is attempting to write an obsolete value of {Q}.

+   Rather than rolling back Ti as the timestamp ordering protocol would have done, this {write} operation can be ignored.

+   Otherwise this protocol is the same as the timestamp ordering protocol.

+   Thomas' Write Rule allows greater potential concurrency.

+   Allows some view-serializable schedules that are not conflict-serializable.