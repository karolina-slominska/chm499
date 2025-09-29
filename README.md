# chm499
chm499 project at uoft

1. looked at lit

2. assemble a database based on ApisTox 
   - PPDB + BPDB + EcoTOX(?)
         - PPDB has 2120 compounds, BPDB 838,overlap 36 (exact Name + CAS match)
   - choose categories (Name, Description, Example pests, Example applications, Canonical SMILES, Isomeric SMILES, Type, Groups, Origin, Mode of action, CAS RN, Mol mass, Formulation/application, Solubility water, Solubility organic, Melting point, Boiling point, Degradation point, Flashpoint, Log Kow, Log P, Density, pKa, Vapour pressure, Henry constant, Surface tension, Soil degradation, DT50, Kd, Koc, Acute oral LD50, Fish LC50, Algae EC50, TTC (Cramer Class))
   -  do SMILES standardization (found issues - only correct 1471 SMILES :( )-> fixing it wiht standarization: Correct valence
Proper aromaticity (kekulization)
Chirality cleanup
Consistent RDKit canonical SMILES
--- Step 1: All SMILES (from Canonical or Isomeric) go through RDKit standardization.
Step 2: If missing/invalid → fetch from PubChem by CAS RN.
Step 3: If CAS fails/missing → fetch from PubChem by Name.
Step 4: Final Checked SMILES is always RDKit-canonical if available.
now 2324 correct, 598 not (usually no smiles present as it's an oil/mixture) 
---

   -  output columns:
         Direct copy: name, smiles, group, origin, mol_mass
         Cleaned numbers: solubility_water, solubility_organic, melting_point, boiling_point, log_kow, logp, density, vapour_pressure, henry_constant, acute_ld50
         Extracted categories: type (only pesticide/fungicide/insecticide/herbicide), ttc (low/moderate/high)
      current issues: - is the MW the same as for smiles?
                      - duplicates of some values for classes of compounds?
                      - toxicity scans don't work for intermediate toxicity - need to fix it
   -  can I get TPSA and rotatable bonds from smiles via rdkit? think about it

4. do the chemical space modelling/graphs
