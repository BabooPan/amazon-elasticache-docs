# Supported node types<a name="CacheNodes.SupportedTypes"></a>

For information on which node size to use, see [Choosing your node size](nodes-select-size.md#CacheNodes.SelectSize)\. 

ElastiCache supports the following node types\. Generally speaking, the current generation types provide more memory and computational power at lower cost when compared to their equivalent previous generation counterparts\.

For more information on performance details for each node type, see [Amazon EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/)\.
+ General purpose:
  + Current generation: 

    **M6g node types** \(available only for Redis engine version 5\.0\.6 onward\)\.

     `cache.m6g.large`, `cache.m6g.xlarge`, `cache.m6g.2xlarge`, `cache.m6g.4xlarge`, `cache.m6g.8xlarge`, `cache.m6g.12xlarge`, `cache.m6g.16xlarge` 
**Note**  
For region availability, see [Supported node types by AWS Region](#CacheNodes.SupportedTypesByRegion)\.

    **M5 node types:** `cache.m5.large`, `cache.m5.xlarge`, `cache.m5.2xlarge`, `cache.m5.4xlarge`, `cache.m5.12xlarge`, `cache.m5.24xlarge` 

    **M4 node types:** `cache.m4.large`, `cache.m4.xlarge`, `cache.m4.2xlarge`, `cache.m4.4xlarge`, `cache.m4.10xlarge`

    **T4g node types** \(available only for Redis engine version 5\.0\.6 onward\)\.

     `cache.t4g.micro`, `cache.t4g.small`, `cache.t4g.medium` 

    **T3 node types:** `cache.t3.micro`, `cache.t3.small`, `cache.t3.medium`

    **T2 node types:** `cache.t2.micro`, `cache.t2.small`, `cache.t2.medium`
  + Previous generation: \(not recommended\. Existing clusters are still supported but creation of new clusters is not supported for these types\.\)

    **T1 node types:** `cache.t1.micro`

    **M1 node types:** `cache.m1.small`, `cache.m1.medium`, `cache.m1.large`, `cache.m1.xlarge`

    **M3 node types:** `cache.m3.medium`, `cache.m3.large`, `cache.m3.xlarge`, `cache.m3.2xlarge`
+ Compute optimized:
  + Previous generation: \(not recommended\)

    **C1 node types:** `cache.c1.xlarge`
+ Memory optimized with data tiering:
  + Current generation: 

    **R6gd node types** \(available only for Redis engine version 6\.2 onward\)\. For more information, see [Data tiering](data-tiering.md)\.

     `cache.r6gd.xlarge`, `cache.r6gd.2xlarge`, `cache.r6gd.4xlarge`, `cache.r6gd.8xlarge`, `cache.r6gd.12xlarge`, `cache.r6gd.16xlarge` 
+ Memory optimized:
  + Current generation: 

    \(*R6g node types* are available only for Redis engine version 5\.0\.6 onward\.\)

    **R6g node types:** `cache.r6g.large`, `cache.r6g.xlarge`, `cache.r6g.2xlarge`, `cache.r6g.4xlarge`, `cache.r6g.8xlarge`, `cache.r6g.12xlarge`, `cache.r6g.16xlarge` `cache.r6g.24xlarge` 
**Note**  
For region availability, see [Supported node types by AWS Region](#CacheNodes.SupportedTypesByRegion)\.

    **R5 node types:** `cache.r5.large`, `cache.r5.xlarge`, `cache.r5.2xlarge`, `cache.r5.4xlarge`, `cache.r5.12xlarge`, `cache.r5.24xlarge`

    **R4 node types:** `cache.r4.large`, `cache.r4.xlarge`, `cache.r4.2xlarge`, `cache.r4.4xlarge`, `cache.r4.8xlarge`, `cache.r4.16xlarge`
  + Previous generation: \(not recommended\)

    **M2 node types:** `cache.m2.xlarge`, `cache.m2.2xlarge`, `cache.m2.4xlarge`

    **R3 node types:** `cache.r3.large`, `cache.r3.xlarge`, `cache.r3.2xlarge`, `cache.r3.4xlarge`, `cache.r3.8xlarge`

You can launch general\-purpose burstable T4g, T3\-Standard and T2\-Standard cache nodes in Amazon ElastiCache\. These nodes provide a baseline level of CPU performance with the ability to burst CPU usage at any time until the accrued credits are exhausted\. A *CPU credit* provides the performance of a full CPU core for one minute\.

Amazon ElastiCache's T4g, T3 and T2 nodes are configured as standard and suited for workloads with an average CPU utilization that is consistently below the baseline performance of the instance\. To burst above the baseline, the node spends credits that it has accrued in its CPU credit balance\. If the node is running low on accrued credits, performance is gradually lowered to the baseline performance level\. This gradual lowering ensures the node doesn't experience a sharp performance drop\-off when its accrued CPU credit balance is depleted\. For more information, see [CPU Credits and Baseline Performance for Burstable Performance Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/burstable-credits-baseline-concepts.html) in the *Amazon EC2 User Guide*\.**

The following table lists the burstable performance node types, the rate at which CPU credits are earned per hour\. It also shows the maximum number of earned CPU credits that a node can accrue and the number of vCPUs per node\. In addition, it gives the baseline performance level as a percentage of a full core performance \(using a single vCPU\)\.


| Node type | CPU credits earned per hour |  Maximum earned credits that can be accrued\* |  vCPUs  |  Baseline performance per vCPU  |  Memory \(GiB\)  |  Network performance  | 
| --- | --- | --- | --- | --- | --- | --- | 
| t4g\.micro | 12 | 288 | 2 | 10% | 0\.5 | Up to 5 Gigabit | 
| t4g\.small | 24 | 576 | 2 | 20% | 1\.37 | Up to 5 Gigabit | 
| t4g\.medium | 24 | 576 | 2 | 20% | 3\.09 | Up to 5 Gigabit | 
| t3\.micro | 12 | 288 | 2 | 10% | 0\.5 | Up to 5 Gigabit | 
| t3\.small | 24 | 576 | 2 | 20% | 1\.37 | Up to 5 Gigabit | 
| t3\.medium | 24 | 576 | 2 | 20% | 3\.09 | Up to 5 Gigabit | 
| t2\.micro | 6 | 144 | 1 | 10% | 0\.5 | Low to moderate | 
| t2\.small | 12 | 288 | 1 | 20% | 1\.55 | Low to moderate | 
| t2\.medium | 24 | 576 | 2 | 20% | 3\.22 | Low to moderate | 

\* The number of credits that can be accrued is equivalent to the number of credits that can be earned in a 24\-hour period\.

\*\* The baseline performance in the table is per vCPU\. Some node sizes that have more than one vCPU\. For these, calculate the baseline CPU utilization for the node by multiplying the vCPU percentage by the number of vCPUs\.

The following CPU credit metrics are available for T3 burstable performance instances:

**Note**  
These metrics are not available for T2 burstable performance instances\.
+ `CPUCreditUsage`
+ `CPUCreditBalance`

For more information on these metrics, see [CPU Credit Metrics](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/viewing_metrics_with_cloudwatch.html#cpu-credit-metrics)\.

In addition, be aware of these details:
+ All current generation node types are created in a virtual private cloud \(VPC\) based on Amazon VPC by default\.
+ Redis append\-only files \(AOF\) aren't supported for T1 or T2 instances\.
+ Redis Multi\-AZ isn't supported on T1 instances\.
+ Redis configuration variables `appendonly` and `appendfsync` aren't supported on Redis version 2\.8\.22 and later\.

**Note**  
Supported engine versions vary by AWS Region\. The latest engine versions are supported in all AWS Regions\. To find the available engine versions in your AWS Region, see [Supported ElastiCache for Redis versions](supported-engine-versions.md)\.

## Supported node types by AWS Region<a name="CacheNodes.SupportedTypesByRegion"></a>

See [Amazon ElastiCache pricing](https://aws.amazon.com/elasticache/pricing/)\.

For a complete list of node types and specifications, see the following:
+ [Amazon ElastiCache Product Features and Details](https://aws.amazon.com/elasticache/details)
+ [Redis\-specific parameters](ParameterGroups.Redis.md)