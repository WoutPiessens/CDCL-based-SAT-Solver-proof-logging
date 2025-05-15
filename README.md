This is an extension of the CDCL based SAT solver from thtran97 (https://github.com/thtran97/CDCL-based-SAT-Solver/tree/main).

It extends the solver with proof logging for the VeriPB proof system. 
To do this, the solver calls auxiliary functions in different stages of the solving algorithm, in order to write new information to the proof_log.opb and proof_log.pbp files.
Using the initial constraints (in proof_log.opb), and the constraints from derived clauses in the CDCL algorithm (in proof_log.pbp), a proof of unsatisfiability is constructed by making use of reverse unit propagation.

In order to run the solver and write proofs to the proof_log.opb and proof_log.pbp files, the following command can be run:

python3 main.py --input input.cnf

In order to verify the proof using VeriPB, the following command can be run within VeriPB:

veripb --trace --useColor proof_log.opb proof_log.pbp

The new proof logging functionality was tested on several SAT problems from the SATLIB benchmark problems (https://www.cs.ubc.ca/~hoos/SATLIB/benchm.html). Only unsatisfiable problems were considered, since checking that a solution for a satisfiable problem is correct is trivial.

Another addition is pure literals: if a variable only occurs in one polarity, the truth of the corresponding literal is derived.



 

