# What is RAID?

RAID (Redundant Array of Independent Disks) is a way to prevent data loss.  
4 common types of RAID:

## RAID 0 
Not fault tolerant, and shouldn't even be called RAID. 
Data is striped across multiple disks. 
If just one disk fails, then all the data in that data is lost. 
The only reason to use RAID 0 is speed, because if you have multiple disk controllers working, then accessing data is much faster. 

## RAID 1
Data is copied on more than one disk.
In the event of one disk failure, the duplicate data is safe on the other running disk.
RAID 1 allows you to use a minimum of 2 disks.
This configuration is space inefficient compared to parity based configurations, but has less CPU overhead and therefore gives good performance for read intensive operations. 


## RAID 5
Requires 3 or more disks. 
Data is not duplicated, but striped across multiple disks along with parity. 
Parity is used to rebuild the data in the event of disk failure. 
The downside is the equivalent of an entire disk is used to store parity. 
E.g. An array of 4 disks total 4 terabytes, but only 3 terabytes will be used for actual storage.

## RAID 10
Combines RAID 1 and RAID 0 and therefore needs a minimum of 4 disks. 
A set of 2 disks are mirrored using a RAID 1 setup. Both sets of the 2 disks are striped using RAID 0. 
Therefore RAID 10 benefits from the speed of RAID 0 and the fault tolerance of RAID 1. 
Downside is that you can only use 50% of the capacity for data storage. I.e. when using 4 disks in a RAID 10 setup, you can only use 2 for actual storage.
