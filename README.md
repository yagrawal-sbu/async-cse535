# async-cse535

## PROJECT INFO
Byzantine Chain Replication implementation on DistAlgo(Python3). 

Team Members -  
Yogesh Agrawal (111493656)  
Fan Wang       (111104886)  

## PLATFORM  
DistAlgo Version:       1.0.9  
Python Implementation:  CPython  
Python Version:         3.6.2  
OS:                     macOS Sierra
Type of hosts:          Two different laptops
Platform for each host: Windows and macOS Sierra

## INSTRUCTIONS  
Instructions to build and run your system.
### PreRequisites
    1. python
    2. pip

### Download
    1. DistAlgo
    2. pip install pynacl  ( to download Libsodium crypto library )

### Setup
    1. Add DistAlgo <DAROOT>/bin to your PATH environmental variable.  

### Executing the scripts

    1. dar -H <local_ip> -n OlympusNode --message-buffer-size 8000 -f -F output --logfilename <olympus_log_file_name> bcr.da <config_file>
    2. dar -H <local_ip> -R <olympus_ip> -n ClientNode --message-buffer-size 8000 --idle -f -F output --logfilename <client_log_file_name> bcr.da
    3. dar -H <local_ip> -R <olympus_ip> -n ReplicaNode --message-buffer-size 8000 --idle -f -F output --logfilename <replica_log_file_name> bcr.da
We need to create 3 nodes, one each for olympus, replica and client.

<config_file> contains the test case and needs to be passed only to the olympus node ( or more generically, the node which runs 'main').

## Example - 
    1.dar -H 1.0.0.1 -n OlympusNode --message-buffer-size 8000 -f -F output --logfilename olympus.log bcr.da config.txt
    2. dar -H 2.0.0.2 -R 1.0.0.1 -n ClientNode --message-buffer-size 8000 --idle -f -F output --logfilename client.log bcr.da
    3. dar -H 2.0.0.2 -R 1.0.0.1 -n ReplicaNode --message-buffer-size 8000 --idle -f -F output --logfilename replica.log bcr.da

## WORKLOAD GENERATION
We generate the pseudorandom workload by using random number generator in pyhton with a seed.
1. Initialise operations array, key array and value arrays.
2. Generates random numbers(with seed) within limits of array size of above mentioned arrays.
3. Pick element from each array corresponding to the array.
4. Create 1 operation from above selected values.
5. Repeat 2-4 for generating n operations.

Arrays are pre-defined to accomodate the needs including operations, values, keys, and etc.  
Note that the seed has to be an integer and number of operations has to be a positive number.
  
## BUGS AND LIMITATIONS
.

## CONTRIBUTIONS
Yogesh Agrawal completed the parts of code in replica, olympus and main code; logging, testing and documentation.
Fan Wang completed the parts of code in client, multi-host setup and testing.


## MAIN FILES
The root folder of the submission is termed as ROOT.
ROOT/bcr.da     -> implements main function of the program
ROOT/client.da  -> codes for clients  
ROOT/replica.da -> codes for replica  
ROOT/olympus.da -> codes for Olympus  

## CODE SIZE
(1) number of non-blank non-comment lines of codes (LOC)
- Algorithm: 498
- Other: 300
- Total: 798
CLOC (https://github.com/AlDanial/cloc) is used to derive the numbers above.
Installed via 'brew install cloc'.

(2)  
Approximately 270 Lines are the main algorithm.
Remaining 228 functionalities interleaved with the algorithm.

# LANGUAGE FEATURE USAGE.  
- number of list comprehensions: 0
- number of dictionary comprehensions: 0
- number of set comprehensions: 0
- number of aggregations: 0
- number of quantifications: 0

