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
- 41 rows, each a human gut microbiome sample, labelled S001-S041 in the
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
- 304 of the 553 columns are 0 in every sample; they are included unchanged.

The values are reproduced exactly as supplied: they have not been
normalized, transformed, filtered, or otherwise altered.

sample_metadata.tsv
-------------------
- sequencing_technology: sequencing method used (the same for every sample).
- project: arbitrary code (P1-P6) for the research project that contributed
  the sample.
- nationality, gender, age, clinical_status: as recorded with the data. Ages
  are as supplied and appear to be in years (some values are below 1). The
  clinical_status abbreviations are not defined in the accompanying
  documentation.
- NA means the value was not recorded. Some samples are missing some fields,
  and 2 samples have only sequencing_technology recorded.
