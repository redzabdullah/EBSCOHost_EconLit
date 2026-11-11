# EBSCOHost_EconLit
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

Steps
1. Data extraction: Retrieved 50 EconLit records using the search term greenwashing and exported the records in XML format through EBSCOhost.

2. Metadata inspection: Identified 283 subject descriptor assignments, comprising 73 unique descriptors, across the 50 records.

3. AEA classification lookup: Used Python to retrieve 859 classification entries from the AEA's official EconLit classification listing.

4. Programmatic mapping: Matched the exported EconLit subject descriptors against the AEA descriptions to reconstruct their corresponding JEL codes.

5. Verification: Compared the reconstructed JEL codes against the original codes for five selected EconLit records.
