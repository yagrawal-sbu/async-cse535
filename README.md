# async-cse535
Byzantine Chain Replication implementation on DistAlgo(Python).

==========================================================================
PLATFORM.
describe the software platform(s) used in your testing
including DistAlgo version
Python implementation (normally CPython) and version
operating system
and types of hosts (e.g., laptop (without any VMs), VMs running on VMWare Workstation Player on a laptop, VMs on Google Cloud Compute Engine, VMs on Amazon Web Services EC2).
for testcases involving multiple hosts, specify the platform for each host.  [2017-10-05 added this]

==========================================================================
INSTRUCTIONS.  
instructions to build and run your system.
--> download DistAlgo and add <DAROOT>/bin to your PATH.
--> install 'pynacl' module via pip3.
    pip install pynacl.
the instructions should not rely on an IDE.

provide a detailed sequence of commands, a shell script, or something similar.
1. dar -H 0.0.0.0 -n OlympusNode --message-buffer-size 8000 -f -F output --logfilename olympus.log bcr.da config.txt
2. dar -H 0.0.0.0  -n ClientNode --message-buffer-size 8000 --idle -f -F output --logfilename client.log bcr.da
3. dar -H 0.0.0.0 -n ReplicaNode --message-buffer-size 8000 --idle -f -F output --logfilename replica.log bcr.da

config.txt contains the test case and needs to be passed only to the olympus node ( or more generically, the node which runs 'main')

include a specific example of the command(s) to run a selected test case.


==========================================================================
WORKLOAD GENERATION.
briefly describe your algorithm for pseudorandom client workload generation.

==========================================================================
BUGS AND LIMITATIONS.
a list of all known bugs in and limitations of your code.

==========================================================================
CONTRIBUTIONS.
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
