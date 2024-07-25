# Mass Spec Query Language for Mass2Motifs
**This is a fork of [Mingxun Wang's Mass Spec Query Language repository](https://github.com/mwang87/MassQueryLanguage)!** <br>
This fork is needed to query the MotifDB of [MS2LDA](https://github.com/vdhooftcompmet/MS2LDA). Since a motif is a spectral pattern and not a spectrum that is used in the original massql, there are a few adjustments made to the source code to be compatible with motif querying. <br>
**Massql4Mass2Motifs cannot be used for spectra!** <br>
**Massql cannot be used for motifs!** <br>
The major changes that have been made to the source code:
- losses are not calculated in-time anymore (you cannot calculate a loss of a motif since it does not have a precusor)
- losses are also stored in the massql dataframe format. Losses show NaN values for fragment mz and intensities and the other way around
- additional field for annotation and further information was included in the ms2 dataframe and they will also show up in the results table
- overlap of scans (is used as an identifier) is avoided using a hash function for the combination of folder name + motif id (you can stack many motif sets together, without the need of correcting scan numbers)
<br>
Mass2Motifs are purely ms2 based spectral patterns and therefore ms1 level queries will result in error messages. The source code will still return ms1 dataframe and they are needed to query motifDB, even though their content is not important. It would be too much of an effort to change the entire source code for this.

## Installation

This package is not available in pypi, but can be installed using pip. The original massql should not be installed in your environement.

```git clone https://github.com/j-a-dietrich/MassQueryLanguage4Mass2Motifs.git```
```cd MassQueryLanguage4Mass2Motifs```
```pip install .```

## Usage
This package should only be used with MotifDB. MotifDB can either be downloaded (not yet) from Zenodo or created with MS2LDA.


# Original Mass Spec Query Readme
## Mass Spec Query Language

The Mass Spec Query Language (MassQL) is a domain specific language meant to be a succinct way to
express a query in a mass spectrometry centric fashion. It is inspired by SQL,
but it attempts to bake in assumptions of mass spectrometry to make querying much more
natural for mass spectrometry users. Broadly we attempt to design it according to several principles:

1. Expressiveness - Capture complex mass spectrometry patterns that the community would like to look for
1. Precision - Exactly prescribe how to find data without ambiguity
2. Scalable - Easily facilitating the querying of one spectrum all the way up to entire repositories of data
3. Relatively Natural - MassQL should be relatively easy to read and write and even use to communicate ideas about mass
   spectrometry, you know like a language.
### Repository Structure

This is the repository to define the language and reference implementation. This contains several parts

1. Language Grammar
1. Reference Implementation Python API
1. Command line Utility to execute
1. NextFlow Workflow For Large Scale Analysis
1. ProteoSAFe workflow
1. Dash interactive exploration

### Developers/Contact

Mingxun Wang is the main creator and developer of MassQL. Contact me for contributing or using it!

### Language Specification/Documentation

Checkout specifics for the language, examples, and design patterns at the documentation.

[Documentation Link](https://mwang87.github.io/MassQueryLanguage_Documentation/)


