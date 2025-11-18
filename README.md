NCRP: a graph-based framework for improving long-read metagenomic classification via neighborhood-consistency refinement and label propagation on the overlap graph.

- [Installation](#installation)
  - [With Conda](#with-conda)
    - [From yaml file](#from-yaml-file)
- [Input files](#input-files)
- [Testing your NCRP installation](#testing-your-ncrp-installation)
- [Basic Usage](#basic-usage)
- [Main output files](#main-output-files)
- [Advanced usage](#advanced-usage)
  - [Using an edge list instead of PAF](#using-an-edge-list-instead-of-paf)
  - [Tuning overlap and plotting diagnostics](#tuning-overlap-and-plotting-diagnostics)
- [Simulation script](#simulation-script)
  - [Reference preparation](#reference-preparation)
  - [Basic usage](#simulation-basic-usage)
- [Citation](#citation)

---

## Installation

### With Conda

We recommend installing NCRP in a dedicated conda environment.

#### From yaml file

Create a file called `environment.yml` in the repository root:

yaml
name: ncrp
channels:
  - conda-forge
  - bioconda
  - defaults
dependencies:
  - python>=3.8
  - matplotlib
Then create and activate the environment:
conda env create -f environment.yml
conda activate ncrp
### Input file
NCRP expects two main inputs:

1.classification file
```
The standard per-read output:
C   read_0001   1345   ...
U   read_0002   0       ...
```
2.overlap graph

You can provide the graph in two formats:
- minimap2 PAF(--paf) : NCRP parses the file and builds an overlap graph,keeping the best overlap for each read pair.
- Sample edge list(--edges) : a 3-column,tab-delimitered file:
```
readA   readB   350
readB   readC   420
...
```
where the third column is the overlap length.Exactly one of --paf or --edges must be provided.

