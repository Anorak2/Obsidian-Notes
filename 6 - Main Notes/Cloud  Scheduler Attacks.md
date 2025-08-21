
2025-02-11

Tags: [[Security]] 
# Cloud  Scheduler Attacks
The idea is that the cloud is just someone else's computer, and that to improve efficiency cloud providers will run multiple people's code on the same computer. We can exploit this scheduling algorithm if we try to guess the requirements of our opponents program, by doing this we can get a high collocation rate.

One approach to measuring this would be to use Hetero-Score which takes all of the server attributes into a n dimensional space. Using this approach we can calculate the similarity between two different servers by simply comparing the distance between vectors.


### how to defend?
We can defend by changing the heterogeneity of the servers, but that is difficult and can cost a lot of money. A simpler way to defend would be to control the flow of information to the scheduler so that we can reduce the determinism of our scheduling by a little bit.

# References
[[Why cloud computing]]
