# Template-based Crystal Structure Exploration (Li–Si System)

This directory contains the data used for the template-based exploration of the Li–Si phase space and the reconstruction of the convex hull using DFT-relaxed structures.

---

## Directory structure

A1B/ A2B/ A3B/ A4B/ A6B/
OneEl.json
INPUT.txt
pseudo/
qEspresso_options_1
qEspresso_options_2
qEspresso_options_3
qEspresso_options_4


---

## Meaning of main folders

Each folder `A1B`, `A2B`, ..., `A6B` corresponds to a different composition explored.

Inside each folder are DFT relaxation outputs which correspond to the final relaxed structures obtained from the substitution of the Li–Si system into the templates at the corresponding composition.

---

## File naming convention

Files inside each folder follow the pattern:

Y_LiSi_AB_XXX.out

where:

- `Y` → composition index (here corresponding to the AYB composition)
- `LiSi` → chemical system (Li–Si)
- `AB` → elemental pair used to generate the original template
- `XXX` → space group index of the template
- `.out` → Quantum ESPRESSO relaxation output


---

## Thermodynamic reconstruction

The combination of:

- Relaxed structures in `A*/` folders
- Reference monoatomic enthalpies in `OneEl.json`

allows reconstruction of the **convex hull of the Li–Si system**, as presented in the associated paper.

`OneEl.json` contains the reference energies of the elemental phases (Li and Si), required for computing formation enthalpies.

---

## USPEX setup

The directory contains input files for Quantum ESPRESSO used during the relaxation workflow:

- `qEspresso_options_1`
- `qEspresso_options_2`
- `qEspresso_options_3`
- `qEspresso_options_4`

These correspond to the **four-step relaxation protocol used by USPEX**, applied to each generated structure.

Each step gradually increases accuracy and convergence to ensure stable relaxed geometries.

`INPUT.txt` contains an example input file used for USPEX structure generation.

---

## Pseudopotentials

The folder:

pseudo/

contains all pseudopotentials used in the DFT calculations.

These are required for reproducing the Quantum ESPRESSO runs.
