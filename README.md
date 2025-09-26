# chm499
chm499 project at uoft

1. looked at lit

2. assemble a database based on ApisTox 
   - PPDB + BPDB + EcoTOX(?)
         - PPDB has 2149 compounds while BPDB has 834, overlap 40
   - choose categories (Name, Description, Example pests, Example applications, Canonical SMILES, Isomeric SMILES, Type, Groups, Origin, Mode of action, CAS RN, Mol mass, Formulation/application, Solubility water, Solubility organic, Melting point, Boiling point, Degradation point, Flashpoint, Log Kow, Log P, Density, pKa, Vapour pressure, Henry constant, Surface tension, Soil degradation, DT50, Kd, Koc, Acute oral LD50, Fish LC50, Algae EC50, TTC (Cramer Class))
   -  do SMILES standardization (found issues - only correct 1471 SMILES :( )
   -  output columns:
         Direct copy: name, smiles, group, origin, mol_mass
         Cleaned numbers: solubility_water, solubility_organic, melting_point, boiling_point, log_kow, logp, density, vapour_pressure, henry_constant, acute_ld50
         Extracted categories: type (only pesticide/fungicide/insecticide/herbicide), ttc (low/moderate/high)
   -  can I get TPSA and rotatable bonds from smiles via rdkit? think about it

4. do the chemical space modelling/graphs
