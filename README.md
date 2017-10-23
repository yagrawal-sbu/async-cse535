# async-cse535

## PROJECT INFO
Byzantine Chain Replication implementation on DistAlgo(Python).
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

Example - 
    1.dar -H 1.0.0.1 -n OlympusNode --message-buffer-size 8000 -f -F output --logfilename olympus.log bcr.da config.txt
2. dar -H 2.0.0.2 -R 1.0.0.1 -n ClientNode --message-buffer-size 8000 --idle -f -F output --logfilename client.log bcr.da
3. dar -H 2.0.0.2 -R 1.0.0.1 -n ReplicaNode --message-buffer-size 8000 --idle -f -F output --logfilename replica.log bcr.da

## WORKLOAD GENERATION
The pseudorandom workload generation consists of two parts, namely, a HashMap and a function producing the keys. 
- Key generation  
  key = 10 * seed * sin(i + 1)  
  where i loops through the number of desired operations starting from 0 and sin stands for the sine function.  
  A multiplication of 10 * seed helps spread the values out and creates more diversity.  
- HashMap  
  The associated hash function simply performs a modulus operation on the key based on the targeted array:  
  index = key % size_of_array  
  Several dictionaries are pre-defined to accomodate the needs including operations, values, keys, and etc.  
  As an example, the size of the operation dictionary is 4 (get, put, append, slice).  
  The HashMap ensures that the combo of seed and desired number of operations always generate valid workload.  
  Note that the seed has to be an integer equal or greater than 1 and number of operations has to be a positive number.  
  
## BUGS AND LIMITATIONS
a list of all known bugs in and limitations of your code.

## CONTRIBUTIONS
Yogesh Agrawal does ...  
Fan Wang does ...  
a list of contributions of each team member to the current submission.  this should reflect how the work was divided between the team members.  generally, a dozen lines or so is sufficient.

## MAIN FILES
The root folder of the submission is termed as ROOT.
ROOT/bcr.da     -> implements main function of the program
ROOT/client.da  -> codes for clients  
ROOT/replica.da -> codes for replica  
ROOT/olympus.da -> codes for Olympus  

## CODE SIZE
(1)  
(1a) The following categories of the system are reported in the number of non-blank non-comment lines of codes (LOC).  
- Algorithm: XX  
- Other: XX  
- Total: XX  

(1b) CLOC (https://github.com/AlDanial/cloc) is used to derive the numbers above. A Windows executable cloc-1.74.exe  
is downloaded and applied to count the loc.  

(2)  
92% of the algorithm codes are for the algorithm itself.  
The remaining 8% are for the functionalities interleaved with the algorithm.  

==========================================================================  
LANGUAGE FEATURE USAGE.  
- number of list comprehensions: XX  
- number of dictionary comprehensions: XX  
- number of set comprehensions: XX  
- number of aggregations: XX  
- number of quantifications: XX  


==========================================================================  
OTHER COMMENTS.  
anything else you want us to know.
