# This is for EuchroGene customers.

InterProScan is a software to perform protein functional analysis by classifying sequences into 
families and predicting domains and important sites.

To use this software, you must download the database for InterProScan first.
You can follow the instruction to download the database.
Input files can be protein sequences or CDS.

## To install, copy and paste the following commands in a Jupyter Terminal, and execute:

1. install the software:
```
wget https://github.com/euchrogene/InterProScan/raw/refs/heads/main/Install_InterProScan.sh
sudo bash Install_InterProScan.sh
sudo rm Install_InterProScan.sh
```

2. display installed pipelines (or software)
```
pipelines
```

3. download database for InterProScan (download it once and reuse it)
```
InterProScan -download_database InterProScan_DB 
```
You can change the DB name ('InterProScan_DB') that you want.
The path of the DB will be the input of -db to run InterProScan.

4. download example protein sequence
```
wget https://github.com/euchrogene/InterProScan_EG/raw/refs/heads/main/test_prot.fa
```

5. example command line
```
InterProScan -db_path InterProScan_DB -i test_prot.fa -dp -f TSV
```

6. show help contents
```
InterProScan
```

## Help contents:
```
________________________________________________________________________________________________

Tool Type: InterProScan-5.76-107.0

InterProScan is a comprehensive functional annotation tool used to characterize protein and 
nucleotide sequences by identifying the functional domains, families, and sites they contain.
Functions:
- Predict Protein Function
- Identify Domains and Motifs
- Map Gene Ontology (GO)
- Reconstruct Pathways

If you find any bugs, please email: bioinformatics@euchrogene.com

________________________________________________________________________________________________


***   Important!   ***

InterProScan needs to download its own database.
If you this is the first time to use, you must install database.
Go to the path where you will download the database, and use the following command.

InterProScan -download_database InterProScan_DB 

You can change the DB name ('InterProScan_DB') that you want.
The path of the DB will be the input of -db to run InterProScan.

________________________________________________________________________________________________

You can run this software by modifying this example:

InterProScan -i sequence_file.fa -dp -f TSV
________________________________________________________________________________________________

Usage;

 -help                                                     show options
 -db_path                                  (required)      path for InterProScan database (It should be the path 
                                                           that contains 'data', not the path of 'data')
 
 -appl,--applications <ANALYSES>                           Optional, comma separated list of analyses.  If this option
                                                           is not set, ALL analyses will be run.
 -b,--output-file-base <OUTPUT-FILE-BASE>                  Optional, base output filename (relative or absolute path).
                                                           Note that this option, the --output-dir (-d) option and the
                                                           --outfile (-o) option are mutually exclusive.  The
                                                           appropriate file extension for the output format(s) will be
                                                           appended automatically. By default the input file path/name
                                                           will be used.
 -cpu,--cpu <CPU>                                          Optional, number of cores for inteproscan.
 -d,--output-dir <OUTPUT-DIR>                              Optional, output directory.  Note that this option, the
                                                           --outfile (-o) option and the --output-file-base (-b) option
                                                           are mutually exclusive. The output filename(s) are the same
                                                           as the input filename, with the appropriate file extension(s)
                                                           for the output format(s) appended automatically .
 -dp,--disable-precalc                                     Optional.  Disables use of the precalculated match lookup
                                                           service.  All match calculations will be run locally.
 -dra,--disable-residue-annot                              Optional, excludes sites from the XML, JSON output
 -etra,--enable-tsv-residue-annot                          Optional, includes sites in TSV output
 -exclappl,--excl-applications <EXC-ANALYSES>              Optional, comma separated list of analyses you want to
                                                           exclude.
 -f,--formats <OUTPUT-FORMATS>                             Optional, case-insensitive, comma separated list of output
                                                           formats. Supported formats are TSV, XML, JSON, and GFF3.
                                                           Default for protein sequences are TSV, XML and GFF3, or for
                                                           nucleotide sequences GFF3 and XML.
 -goterms,--goterms                                        Optional, switch on lookup of corresponding Gene Ontology
                                                           annotation (IMPLIES -iprlookup option)
 -help,--help                                              Optional, display help information
 -i,--input <INPUT-FILE-PATH>                              Optional, path to fasta file that should be loaded on Master
                                                           startup. Alternatively, in CONVERT mode, the InterProScan 5
                                                           XML file to convert.
 -incldepappl,--incl-dep-applications <INC-DEP-ANALYSES>   Optional, comma separated list of deprecated analyses that
                                                           you want included.  If this option is not set, deprecated
                                                           analyses will not run.
 -iprlookup,--iprlookup                                    Also include lookup of corresponding InterPro annotation in
                                                           the TSV and GFF3 output formats.
 -ms,--minsize <MINIMUM-SIZE>                              Optional, minimum nucleotide size of ORF to report. Will only
                                                           be considered if n is specified as a sequence type. Please be
                                                           aware of the fact that if you specify a too short value it
                                                           might be that the analysis takes a very long time!
 -o,--outfile <EXPLICIT_OUTPUT_FILENAME>                   Optional explicit output file name (relative or absolute
                                                           path).  Note that this option, the --output-dir (-d) option
                                                           and the --output-file-base (-b) option are mutually
                                                           exclusive. If this option is given, you MUST specify a single
                                                           output format using the -f option.  The output file name will
                                                           not be modified. Note that specifying an output file name
                                                           using this option OVERWRITES ANY EXISTING FILE.
 -pa,--pathways                                            Optional, switch on lookup of corresponding Pathway
                                                           annotation (IMPLIES -iprlookup option)
 -t,--seqtype <SEQUENCE-TYPE>                              Optional, the type of the input sequences (dna/rna (n) or
                                                           protein (p)).  The default sequence type is protein.
 -T,--tempdir <TEMP-DIR>                                   Optional, specify temporary file directory (relative or
                                                           absolute path). The default location is temp/.
 -verbose,--verbose                                        Optional, display more verbose log output
 -version,--version                                        Optional, display version number
 -vl,--verbose-level <VERBOSE-LEVEL>                       Optional, display verbose log output at level specified.
 -vtsv,--output-tsv-version                                Optional, includes a TSV version file along with any TSV
                                                           output (when TSV output requested)
Copyright ? EMBL European Bioinformatics Institute, Hinxton, Cambridge, UK. (http://www.ebi.ac.uk) The InterProScan
software itself is provided under the Apache License, Version 2.0 (http://www.apache.org/licenses/LICENSE-2.0.html).
Third party components (e.g. member database binaries and models) are subject to separate licensing - please see the
individual member database websites for details.

Available analyses:
                      AntiFam (8.0) : AntiFam is a resource of profile-HMMs designed to identify spurious protein predictions.
                          CDD (3.21) : CDD predicts protein domains and families based on a collection of well-annotated multiple sequence alignment models.
                        Coils (2.2.1) : Prediction of coiled coil regions in proteins.
                       FunFam (4.3.0) : Prediction of functional annotations for novel, uncharacterized sequences.
                       Gene3D (4.3.0) : Structural assignment for whole genes and genomes using the CATH domain structure database.
                        Hamap (2025_01) : High-quality Automated and Manual Annotation of Microbial Proteomes.
                   MobiDBLite (4.0) : Prediction of intrinsically disordered regions in proteins.
                      NCBIfam (17.0) : NCBIfam is a collection of protein families based on Hidden Markov Models (HMMs).
                      PANTHER (19.0) : The PANTHER (Protein ANalysis THrough Evolutionary Relationships) Classification System is a unique resource that classifies genes by their functions, using published scientific experimental evidence and evolutionary relationships to predict function even in the absence of direct experimental evidence.
                         Pfam (38.0) : A large collection of protein families, each represented by multiple sequence alignments and hidden Markov models (HMMs).
                        PIRSF (3.10) : The PIRSF concept is used as a guiding principle to provide comprehensive and non-overlapping clustering of UniProtKB sequences into a hierarchical order to reflect their evolutionary relationships.
                        PIRSR (2025_01) : PIRSR is a database of protein families based on hidden Markov models (HMMs) and Site Rules.
                       PRINTS (42.0) : A compendium of protein fingerprints - a fingerprint is a group of conserved motifs used to characterise a protein family.
              ProSitePatterns (2025_01) : PROSITE consists of documentation entries describing protein domains, families and functional sites as well as associated patterns and profiles to identify them.
              ProSiteProfiles (2025_01) : PROSITE consists of documentation entries describing protein domains, families and functional sites as well as associated patterns and profiles to identify them.
                         SFLD (4) : SFLD is a database of protein families based on hidden Markov models (HMMs).
                        SMART (9.0) : SMART allows the identification and analysis of domain architectures based on hidden Markov models (HMMs). 
                  SUPERFAMILY (1.75) : SUPERFAMILY is a database of structural and functional annotations for all proteins and genomes.

Deactivated analyses:
                      Phobius (1.01) : Analysis Phobius is deactivated, because the resources expected at the following paths do not exist: bin/phobius/1.01/phobius.pl
                  SignalP_EUK (4.1) : Analysis SignalP_EUK is deactivated, because the resources expected at the following paths do not exist: bin/signalp/4.1/signalp
        SignalP_GRAM_NEGATIVE (4.1) : Analysis SignalP_GRAM_NEGATIVE is deactivated, because the resources expected at the following paths do not exist: bin/signalp/4.1/signalp
        SignalP_GRAM_POSITIVE (4.1) : Analysis SignalP_GRAM_POSITIVE is deactivated, because the resources expected at the following paths do not exist: bin/signalp/4.1/signalp
                        TMHMM (2.0c) : Analysis TMHMM is deactivated, because the resources expected at the following paths do not exist: bin/tmhmm/2.0c/decodeanhmm.Linux_x86_64, bin/tmhmm/2.0c/TMHMM2.0.model

______________________________________________________________________________________________
```


# Citation

## InterProScan
Mulder, N., Apweiler, R. (2007). InterPro and InterProScan. In: Bergman, N.H. (eds) Comparative Genomics. Methods In Molecular Biology™, vol 396. Humana Press. https://doi.org/10.1007/978-1-59745-515-2_5
