# harmfull_plasmids_compensatory_mutation_in_plasmid
This is a repository for the python scripts underlying the paper "Plasmid costs explain plasmid maintenance, irrespective of the nature of compensatory mutations".
Note that the parameter/variable notations in the scripts and in the files differ from those in manuscript.
 

Motivation

The numerous combinations of bacterial species and strains, plasmids, and environments claim a robust elucidatory mechanism of plasmid maintenance. 
Our previous work has shown that donor cells already adapted to the plasmid may use the plasmid as a 'weapon' to compete with non-adapted plasmid-free cells. Computer 
simulations corroborated this hypothesis with a wide range of parameters. In the previous work we considered that compensatory mutations exist in transconjugant 
bacteria (recipient bacteria that received the plasmid). Thus, a transconjugant bacterium that divided a certain number of times (70 or 400) had a decrease in the 
fitness cost associated with being on the plasmid These mutations occurred on the chromosome, i.e. when the transconjugant bacteria passed on the plasmid, the 
recipient bacteria continued with the cost and also needed to divide (70 or 400 times) to have the cost of the plasmid decreased.
However, in nature, these mutations sometimes happen in plasmids as well. When plasmids contain mutations that compensate entirely for their cost, they become neutral
in the second-order transconjugants (cells that received the plasmid from transconjugants), third-order transconjugants, and so on. As a result, the plasmid would 
cause less harm to the local community of bacterial cells, thereby potentially undermining the success of the donors. To test the effect of mutations in the plasmid we 
considered that adaptation is dependent on the number of bacterial divisions of transconjugant bacteria in which the plasmid is present. For example, if 70 divisions 
are required to consider the appearance of a compensatory mutation and the plasmid is in a dividing transconjugant bacterium, this number decreases to 69 generations. 
If this transconjugant bacterium transferes the plasmid to a new recipient bacterium and this divides, then only 68 divisions are missing for mutation to occur. When 
compensatory mutation occurs, the new bacteria receiving that plasmid and their offspring no longer have any associated costs. To test the effect of mutations in the 
plasmid we consider that adaptation is dependent on the number of bacterial divisions of transconjugant bacteria in which the plasmid is present. For example, if 70 
divisions are required to consider the appearance of a compensatory mutation and the plasmid is in a dividing transconjugant bacterium, this number decreases to 69 
generations. If this transconjugant bacterium passes the plasmid to a new recipient bacterium and this divides, then only 68 divisions are missing for mutation to 
occur. When compensatory mutation occurs, the new bacteria receiving that plasmid and their offspring no longer have any associated costs.

Model

The flow of the model is as follows:
- Random distribution of bacteria in the user-defined recipient/donor ratio on a 1000X1000 space grid (script "bacteria_distribution").
- Random choice of a bacterium (which may be donor, transconjugant, recipient or segregated)
- Check for bacterial growth (function "bacterial_growth" of the script "functions.py").
- If the selected bacterium is donor or transconjugant, check for bacterial conjugation (function "conjugation" of the script "functions.py")
- If the bacteria selected is a donor or transconjugant, check for bacterial segregation
- Check the number of bacteria present in the grid (maximum of one bacterium per space). If this value is less than 95% of grid capacity, repeat the steps 
described above (excluding distribution). If the value is higher, eliminate bacteria randomly until only 50% of the spaces are filled (lines 51 to 101 of the 
script "cycles.py").
- Repeat these steps until the grid is filled 1073 times (simulation of 1000 bacterial generations)


Repository

The repository is composed by three folders. 
The folder "Code - compensatory mutation in plasmid", has the code of the model considering that compensatory mutation occurs in the plasmid. 
To run the program, we use the script "program.py", where we can define the variables we want to test. This script uses the other scripts placed in the folder.
At the end of each simulation, we have a file with the densities of the different types of bacteria throughout all the cycles.
The folders "Data considering compensatory mutation in chromosome" and "Data considering compensatory mutation in plasmid" have the bacterial density files 
throughout the cycles for all the repetitions of all the cases tested, both considering the mutation in the plasmid and in the chromosome.
