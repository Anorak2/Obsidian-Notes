Status:

Tags: [[Databases]]
# System Log

The system log keeps track of [[Transactions|transaction]] operations by maintaining a sequential, append only file. Because of this its not affected by failure, except disk or catastrophic. To avoid it from being too slow we also keep a **log buffer**, which is the main memory buffer, and when its full it gets appended to the log file on disk. This allows for undo and redo operations to be done based on what the log says.

**How far back should a log should we go?**
We can use a sync point to fix this, a sync point represents boundaries between two consecutive transactions.

In the event of a system failure, such as a crash, the contents of the log buffer are lost and the precise state of any transaction in progress is not known. Those transactions that were in process have to be undone (rolled back), and sometimes as a result we will redo transactions. These are transactions that completed before the crash but did not manage to get their updates transferred to the DB.

# References
[[Transactions]]

[[The System Log]]