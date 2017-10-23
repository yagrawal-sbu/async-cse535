# async-cse535
Byzantine Chain Replication implementation on DistAlgo(Python).

==========================================================================
PLATFORM.  
DistAlgo version: 1.0.9  
Python implementation: CPython  
Python version: 3.5.2  
Operating system: macOS  
Type of hosts: VMs on Google Cloud Compute Engine  
Platform for each host:  

==========================================================================  
INSTRUCTIONS.  
instructions to build and run your system.  
--> download DistAlgo and add <DAROOT>/bin to your PATH.  
--> install 'pynacl' module via pip3.  
    pip install pynacl.  

provide a detailed sequence of commands, a shell script, or something similar.
1. dar -H 0.0.0.0 -n OlympusNode --message-buffer-size 8000 -f -F output --logfilename olympus.log bcr.da config.txt
2. dar -H 0.0.0.0 -n ClientNode --message-buffer-size 8000 --idle -f -F output --logfilename client.log bcr.da
3. dar -H 0.0.0.0 -n ReplicaNode --message-buffer-size 8000 --idle -f -F output --logfilename replica.log bcr.da

config.txt contains the test case and needs to be passed only to the olympus node ( or more generically, the node which runs 'main')  

include a specific example of the command(s) to run a selected test case.  

==========================================================================
WORKLOAD GENERATION.  
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
  
==========================================================================  
BUGS AND LIMITATIONS.  
a list of all known bugs in and limitations of your code.

==========================================================================
CONTRIBUTIONS.  
Yogesh Agrawal does ...  
Fan Wang does ...  
a list of contributions of each team member to the current submission.  this should reflect how the work was divided between the team members.  generally, a dozen lines or so is sufficient.
  
==========================================================================  
MAIN FILES.  
The root folder of the submission is termed as ROOT  
ROOT/client.da  -> codes for clients  
ROOT/replica.da -> codes for replica  
ROOT/olympus.da -> codes for Olympus  
ROOT/bcr.da     -> implements main function of the program  

==========================================================================
CODE SIZE.  
(1)  
(1a) The following categories of the system are reported in the number of non-blank non-comment lines of codes (LOC).  
- Algorithm: XX  
- Other: XX  
- Total: XX  
(1b) CLOC (https://github.com/AlDanial/cloc) is used to derive the numbers above.  
(2)  
92% of the algorithm codes are for the algorithm itself.  
The remaining 8% are for the functionalities interleaved with the algorithm.  

==========================================================================  
LANGUAGE FEATURE USAGE. report the numbers of list comprehensions, dictionary comprehensions, set comprehensions, aggregations, and quantifications in your code.  the first two are Python features; the others are DistAlgo features.

OTHER COMMENTS.  anything else you want us to know.
