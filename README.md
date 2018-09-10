SYNOPSIS
========

This script parses and analyzes quantum Monte Carlo data to determine the ground-state wave equation of harmonically trapped many-fermion systems in two spatial dimensions. These are systems that are realized with ultracold atom experiments because this is where the resistivity of a system goes to zero.

SETUP
=====

Requirements
------------
* `pip3 install -r requirments.txt`
    
    * run this command in terminal to install the required python modules*


# quantum_research

MANY BODY
====
The number of particles that were used to take measurements during this experiment ranged from N = 2 to N = 20, skipping by 2. Each pair possessed a bare value of 0.2, 1, 2, 3, 4, or 6.

The script does as follows:
* The CSV containing the mechanical data, which is not included due to this being innovative research measurements, was sorted such that data measurements for the same number of fermions was grouped together
* Each of these data groups was sorted by increasing bare value
* The following nested for loop:
    `for key in sort.keys():`
        `data = sort[key]`
        `for bare in bare_space:`
        `sliced = data[data.bare==bare]`
        `group = sliced.groupby('beta_omega').mean()`
    can be translated as: for each key (N value), slice the data into dataframes for each bare value. For that specific N and bare value's dataframe, take the mean of all data for each beta_omega value in that data frame. This step takes the 10,000 line data frame and splices it into a 10-line dataframe for each N value. 
* The energy values (`<E>/Omg`) were plotted against the beta_omega value

* The error is then given by the `stderr(E)/Omg` values. The error bars are plotted on the graphs. 

* The energy values for each fixed bare and N value were seen to converge at beta_omega = 2.5. This was the expected result. 

TWO BODY
====
* The steps explained above were repeated for just the two-body case.

* Again, the energy values for each fixed bare and N value were seen to converge at beta_omega = 2.5. This was the expected result. 

TWO BODY VS. MANY BODY
====
* The plots generated used a fixed beta_omega value of 2.5 because this is the beta_omega value where the particles can be approximated as non-interacting.
* To represent the many-body case as a two-body case, the energy for the many body case was divided by the number of fermions in the many body case and doubled thereafter. 
* Plots compared the energy for many body case represented as a two body case versus the energy two body case. All cases used a fixed beta omega value of 2.5 - again, because this is the beta_omega value where the particles can be approximated as non-interacting (a.k.a. the electron-electron repulsion is minimized).
* The green arrows on the plot represent the ideal case

The conclusions drawn from this study will be published in mid 2018. 

