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
full pathnames of the files containing the main code for clients, replicas, and Olympus.  this will help graders look at the most important code first.

==========================================================================
CODE SIZE.
(1a) report the numbers of non-blank non-comment lines of code (LOC) in your system in the following categories: algorithm, other, and total.
     "algorithm" is for the algorithm itself and other functionality interleaved with it (fault injection, logging, debugging, etc.).
     "other" is for everything that can easily be separated from the algorithm, e.g., configuration and testing.
(1b) report how you obtained the counts (I use CLOC https://github.com/AlDanial/cloc).
(2) give a rough estimate of how much of the "algorithm" code is for the algorithm itself, and how much is for other functionality interleaved with it.

LANGUAGE FEATURE USAGE. report the numbers of list comprehensions, dictionary comprehensions, set comprehensions, aggregations, and quantifications in your code.  the first two are Python features; the others are DistAlgo features.

OTHER COMMENTS.  anything else you want us to know.
