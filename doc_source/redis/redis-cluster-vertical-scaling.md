# Online vertical scaling by modifying node type<a name="redis-cluster-vertical-scaling"></a>

By using online vertical scaling with Amazon ElastiCache for Redis version 3\.2\.10 or newer, you can scale your Redis clusters dynamically with minimal downtime\. This allows your Redis cluster to serve requests even while scaling\.

**Note**  
Scaling is not supported between a data tiering cluster \(for example, a cluster using an r6gd node type\) and a cluster that does not use data tiering \(for example, a cluster using an r6g node type\)\. For more information, see [Data tiering](data-tiering.md)\.

You can do the following:
+ **Scale up** – Increase read and write capacity by adjusting the node type of your Redis cluster to use a larger node type\.

  ElastiCache dynamically resizes your cluster while remaining online and serving requests\.
+ **Scale down** – Reduce read and write capacity by adjusting the node type down to use a smaller node\. Again, ElastiCache dynamically resizes your cluster while remaining online and serving requests\. In this case, you reduce costs by downsizing the node\.

**Note**  
The scale up and scale down processes rely on creating clusters with newly selected node types and synchronizing the new nodes with the previous ones\. To ensure a smooth scale up/down flow, do the following:  
Ensure you have sufficient ENI \(Elastic Network Interface\) capacity\. If scaling down, ensure the smaller node has sufficient memory to absorb expected traffic\.   
For best practices on memory management, see [Managing Reserved Memory](redis-memory-management.md)\. 
While the vertical scaling process is designed to remain fully online, it does rely on synchronizing data between the old node and the new node\. We recommend that you initiate scale up/down during hours when you expect data traffic to be at its minimum\. 
Test your application behavior during scaling in a staging environment, if possible\. 

**Contents**
+ [Online scaling up](redis-cluster-vertical-scaling-scaling-up.md)
  + [Scaling up Redis cache clusters \(Console\)](redis-cluster-vertical-scaling-scaling-up.md#redis-cluster-vertical-scaling-console)
  + [Scaling up Redis cache clusters \(AWS CLI\)](redis-cluster-vertical-scaling-scaling-up.md#Scaling.RedisStandalone.ScaleUp.CLI)
  + [Scaling up Redis cache clusters \(ElastiCache API\)](redis-cluster-vertical-scaling-scaling-up.md#VeticalScaling.RedisReplGrps.ScaleUp.API)
+ [Online scaling down](redis-cluster-vertical-scaling-scaling-down.md)
  + [Scaling down Redis cache clusters \(Console\)](redis-cluster-vertical-scaling-scaling-down.md#redis-cluster-vertical-scaling-down-console)
  + [Scaling down Redis cache clusters \(AWS CLI\)](redis-cluster-vertical-scaling-scaling-down.md#Scaling.RedisStandalone.ScaleDown.CLI)
  + [Scaling down Redis cache clusters \(ElastiCache API\)](redis-cluster-vertical-scaling-scaling-down.md#Scaling.Vertical.ScaleDown.API)