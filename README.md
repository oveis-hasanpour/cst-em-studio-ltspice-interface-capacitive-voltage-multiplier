# cst-em-studio-ltspice-interface-capacitive-voltage-multiplier

This script is a toolkit developed to ease data transfer from CST EM STUDIO to LTSPICE. It is aimed to simulate circuit equivalent (LTSPCIE) of a capacitive structure (CST STUDIO SUITE). Since it is developed for a specific project, it cannot be used as a general tool to generate equivalent circuit for any capacitive structure in CST STUDIO SUITE. It is designed for simulation of parallel-fed capacitive coupled cascade generator (see parallel-fed-capacitive-coupled-cascade-generator-circuit.png / a capacitive structure and its complicated equivalent circuit is presented in parallel-fed-capacitive-coupled-cascade-generator-structure-circuit.png).
For each specifically-designed CST EM STUDIO project, the script will do the following steps:
1.	Runs CST EM STUDIO with the project file(s) given and waits for simulation of each file to finish.
2.	Reads parameters file (<project data folder>\Model\Parameters.json) to find out number of circuit repetition ("number_of_stages").
3.	Reads capacitive matrix of the structure (<project data folder>\Result\Capacitance Matrix (lumped).stx) and extracts the ones needed for equivalent circuit construction. (Naming of electric potentials are important because capacitance values in CST EM STUDIO are calculated and reported between electric potential pairs. / v_ring_[up/down]_##, v_hf_[up/down], v_container are predefined names which the code will be looking for and they should be attributed to the right electrode in CST EM STUDIO model. (parallel-fed-capacitive-coupled-cascade-generator-structure-circuit.png might help.)
4.	Generates a text-based circuit schematic input file (.asc) for LTSPICE with given variables and capacitive values extracted from previous steps.
5.	Runs LTSPICE with the schematic input file (.asc) and interacts with LTSPICE GUI to find out when the simulation is finished and to extract current-voltage output of the circuit.
6.	Calculates and reports mean and ripple of the output current and output voltage.

![parallel-fed-capacitive-coupled-cascade-generator-circuit](https://github.com/oveis-hasanpour/cst-em-studio-ltspice-interface-capacitive-voltage-multiplier/blob/main/parallel-fed-capacitive-coupled-cascade-generator-circuit.png)
![parallel-fed-capacitive-coupled-cascade-generator-structure-circuit](https://github.com/oveis-hasanpour/cst-em-studio-ltspice-interface-capacitive-voltage-multiplier/blob/main/parallel-fed-capacitive-coupled-cascade-generator-structure-circuit2.png)
