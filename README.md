[![DOI](https://zenodo.org/badge/doi/10.5281/zenodo.46599.svg)](http://dx.doi.org/10.5281/zenodo.46599)

These scripts demonstrate the use of [IMP](http://integrativemodeling.org/),
[MODELLER](http://salilab.org/modeller/) and
[Chimera](http://www.cgl.ucsf.edu/chimera/) in the modeling of the
phosphodiesterase (PDE6).

## Homology modeling

MODELLER is used to generate initial models for the structure using multiple templates
(PDB codes 1tbf, 3bjc, 3dba, 3ibj). Cross links, symmetry and secondary structure restraints are used in modeling:
 `cd comparative_modelling; ./model_mult.py`


## Integrative modeling with IMP

The initial models do not fit well into the 3D EM density map (20Å resolution).
Therefore, IMP is used to fit the complex into the electron microscopy density map.

Usage and content of the directory `integrative_modeling`

0) access the directory:
`cd integrative_modeling`

1)  test the python script:
`./run_modeling.py test`
no error = all tests passed

2) run sampling:
`./run_modeling.py`
all output data will be stored in output/

3) analyse the results:

3.1) compile the clustering algorithm in `bin/`
`gfortran cluster.f u3best.f -o cluster.x`

3.2) run the analysis script:
`bin/get_frames.sh`

100 best scoring frames will be stored in `best_pdb/`
and clustering data will be stored in `clustering/`

## Refinement

Finally the final models are rebuilt and refined with Modeller:

`cd model_refinement/cluster1; ./model-single.py`


_Author(s)_: Riccardo Pellarin, Dina Schneidman

_Version_: 1.0


_License_: [LGPL](http://www.gnu.org/licenses/old-licenses/lgpl-2.1.html).
This library is free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2 of the License, or (at your option) any later version.

_Last known good IMP version_: [![build info](https://integrativemodeling.org/systems/2/badge.svg?branch=master)](https://integrativemodeling.org/systems/) [![build info](https://integrativemodeling.org/systems/2/badge.svg?branch=develop)](https://integrativemodeling.org/systems/)

_Testable_: Yes.

_Parallelizeable_: No

_Publications_:
 - X. Zeng-Elmore, X. Gao, R. Pellarin, D. Schneidman-Duhovny, X. Zhang, K. Kozacka, Y. Tang, A. Sali, R. Chalkley, R. Cote, F. Chu. [Molecular architecture of photoreceptor phosphodiesterase elucidated by chemical cross-linking and integrative modeling](http://www.ncbi.nlm.nih.gov/pubmed/25149264), J Mol Biol 426, 3713-3728, 2014.
