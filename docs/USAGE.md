- For installation please refer to README.md

- Do a vacuum calculation for your system first and save the wavefunction file WAVECAR by 
  specifying LWAVE = .TRUE. in the INCAR file.

- Start the solvation calculation from the vacuum WAVECAR, specify ISTART = 1 in the INCAR file.

- The solvation parameters are read from the INCAR file.

- In the simplest case the only parameter that need to be set is the solvation flag LSOL = .TRUE.
```
    This corresponds to the default case where the solvent is water with a 
    relative permittivity of 80. Note, The cavitation energy in the solvation 
    model requires a higher resolution than neeed for vacuum calculations. 
    So pleae make sure that ENCUT is large enough and also set PREC=Accurate.
```

- The relative permittivity of the solvent can be changed from the default value of 78.4 for water 
  to any value using the INCAR parameter EB_k, e.g. EB_k = 20.

- You can also change the surface tension parameter tau in the INCAR file. For example, to neglect 
  the the cavitation energy contribution, set TAU = 0 in the INCAR file. Note that you may have to 
  increase the cutoff energy to converge the caviation energy because the grid must be fine enough 
  to resolve the cavity surface. 

- Set LRHOB = .TRUE. if you would like to write out the bound charge density in the CHGCAR format.
  The file is named RHOB.

- For examples, please see the Examples folder

- Set LAMBDA_D_K(the debye length in Angstroms) parameter in the INCAR file to use the linearized Poisson-Boltzmann model(electrolyte model)
```
	The constant, FERMI_SHIFT, printed out to the stdout needs to be added to 
	the fermi level to get the alignment right(the sign of the shift becomes 
	apparent once you plot the x-y averaged local potential  in the z direction. 
	Without the shift the the electrostatic potential would not go to zero in 
	the bulk of the electrolyte as expected from the poisson-boltzmann solution).
```
