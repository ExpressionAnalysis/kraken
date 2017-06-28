Kraken taxonomic sequence classification system
===============================================
This is a modified version of the original Kraken program. Modified from the original on October 4, 2016.
MODIFICATIONS:
classify.cpp
seqreader.cpp
seqreader.hpp

ADDITIONS:
fqmapper.cpp
fqmapper.h
gzstream.cpp
gzstream.h

These modifications allow for the classify module to read directly from gzipped paired- or single- end fastq files. Additionally, if supplied with a divisions files, classify will split the fastqs into separate fastq files based on the taxnomic classification of the read(s).

Example usage:
classify -M -p <DIVISIONS_FILE> -t <THREADS> -f -d <LOCATION OF DATABASE .kdb FILE> -i  <LOCATION OF DATABASE .idx FILE> -x <OUTPUT_PREFIX> -n <LOCATION OF nodes.dmp FILE> -2 <READ1 FASTQ> <READ2 FASTQ>


EXAMPLE DIVISIONS FILE (tab-delimited)
hsap       9606
mmus       10090,39107,337687


For documentation on the full functionality of the original software, please see the original documentation below.
Please see the [Kraken webpage] or the [Kraken manual]
for information on installing and operating Kraken.
A local copy of the [Kraken manual] is also present here
in the `docs/` directory (`MANUAL.html` and `MANUAL.markdown`).

[Kraken webpage]:   http://ccb.jhu.edu/software/kraken/
[Kraken manual]:    http://ccb.jhu.edu/software/kraken/MANUAL.html
