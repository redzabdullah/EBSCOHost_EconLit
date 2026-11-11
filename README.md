# EBSCOHOst_EconLit
EBSCOhost EconLit → JEL Code Reconstruction

EBSCOhost EconLit exports carry subject descriptors but often lack the JEL classification codes behind them. This Google Colab notebook rebuilds those codes in a transparent, reproducible way.

What it does

Parses an EBSCOhost EconLit XML export, pulling out each record’s accession number, title and subject descriptors.
Downloads the official AEA EconLit classification vocabulary from aeaweb.org and builds a descriptor-to-JEL lookup table.
Matches descriptors exactly but case-insensitively. Punctuation is kept as is, and compound descriptors that contain internal semicolons stay intact.
Flags unmatched and ambiguous descriptors for review. It never uses fuzzy matching, AI or inference to assign a code.

Outputs

Enriched article-level CSV: each record with its reconstructed JEL codes and match status.
Descriptor-level mapping audit: every unique descriptor, the code(s) it matched and any flags.
Summary report: matching coverage statistics and validation results.

Reproducibility
Each run records source provenance: the vocabulary URL, the retrieval timestamp and the input file details. It also runs validation checks on record counts, duplicate accession numbers and lookup-table integrity, so results can be audited and repeated.

Intended use: library and research workflows that need JEL-level analysis of EconLit search results, such as bibliometric studies, collection analysis and literature mapping.
