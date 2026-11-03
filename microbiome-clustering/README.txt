Microbiome abundance data
=========================

Files
-----
abundances.tsv       Tab-separated table. One row per sample, one column per
                     feature.
sample_metadata.tsv  Tab-separated table. One row per sample, describing the
                     sample and the person it came from.
Both files use the same sample_id values.

abundances.tsv
--------------
- 280 rows, each a human gut microbiome sample, labelled S001-S280 in the
  first column (sample_id). Row order is random and carries no meaning.
- 553 further columns, F001-F553, each a microbial taxonomic category.
  Sample and category labels are arbitrary codes.
- Each value is the relative abundance of that category in that sample
  (a proportion, not a count). Within a sample the values sum to
  approximately 1; small deviations from exactly 1 are present in the
  supplied values and have been left as they are.

Zeros and missing values
------------------------
- A value of 0 means no abundance was recorded for that category in that
  sample. The data do not distinguish true absence from absence of
  detection.
- abundances.tsv has no missing values.
- Every column has a nonzero value in at least one sample.

The values are reproduced exactly as supplied: they have not been
normalized, transformed, filtered, or otherwise altered.

sample_metadata.tsv
-------------------
- sequencing_technology: sequencing method used (Sanger, Illumina, or
  Pyro454). Recorded for every sample.
- project: code (P1-P6) for the research project that contributed the
  sample; see "Sources" below for what each code refers to.
- nationality, gender, age, clinical_status: as recorded with the data. Ages
  are as supplied and appear to be in years (some values are below 1). The
  clinical_status abbreviations are not defined in the accompanying
  documentation.
- NA means the value was not recorded. Some samples are missing some fields,
  and 241 samples have only sequencing_technology recorded. This includes
  every Illumina and Pyro454 sample: project, nationality, gender, age and
  clinical_status are recorded only for some Sanger samples.

Sources
-------
The samples come from the following studies and projects.

Sanger samples (41), identified by the project column:
  P1  Kurokawa et al. (2007); 13 Japanese samples.
  P2  Gill et al. (2006); 2 American samples.
  P3  MicroObes project; 8 French samples.
  P4  MetaHIT project; 8 Danish and Spanish samples.
  P5  MicroAge project; 6 Italian samples.
  P6  Turnbaugh et al. (2009); 2 American samples.
  NA  2 samples with no project recorded.

Illumina samples (85): MetaHIT project, Qin et al. (2010).
Pyro454 samples (154): Turnbaugh et al. (2009).

  Gill, S. R., Pop, M., DeBoy, R. T., Eckburg, P. B., Turnbaugh, P. J.,
  et al. (2006). Metagenomic analysis of the human distal gut microbiome.
  Science, 312, 1355-1359. https://doi.org/10.1126/science.1124234

  Kurokawa, K., Itoh, T., Kuwahara, T., Oshima, K., Toh, H., et al.
  (2007). Comparative metagenomics revealed commonly enriched gene sets in
  human gut microbiomes. DNA Research, 14, 169-181.
  https://doi.org/10.1093/dnares/dsm018

  Turnbaugh, P. J., Hamady, M., Yatsunenko, T., Cantarel, B. L.,
  Duncan, A., et al. (2009). A core gut microbiome in obese and lean
  twins. Nature, 457, 480-484. https://doi.org/10.1038/nature07540

  Qin, J., Li, R., Raes, J., Arumugam, M., Burgdorf, K. S., et al.
  (2010). A human gut microbial gene catalogue established by metagenomic
  sequencing. Nature, 464, 59-65. https://doi.org/10.1038/nature08821
