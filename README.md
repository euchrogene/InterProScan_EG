# This is for EuchroGene Members.

InterProScan is a software to perform protein functional analysis by classifying sequences into 
families and predicting domains and important sites.

To use this software, you must download the database for InterProScan first.
You can follow the instructions to download the database.
Input files can be protein sequences or CDS.

## To install, copy and paste the following commands in a Jupyter Terminal, and execute:

0. Install EG_tools (*** If this is already installed, skip this step ***)
```
wget https://github.com/euchrogene/EG_tools/raw/refs/heads/main/EG_tools
sudo chmod 777 EG_tools
sudo mv EG_tools /usr/bin
```

1. install the software:
```
sudo EG_tools install -r https://github.com/euchrogene/InterProScan_EG.git -d InterProScan_EG -e InterProScan_v.1.0 -m "InterProScan_v.1.0 =>  A software to perform protein functional analysis by classifying sequences into families and predicting domains and important sites."
```

2. display installed software
```
EG_tools
```

3. download database for InterProScan (download it once and reuse it)
```
InterProScan_v.1.0 -download_database InterProScan_DB 
```
You can change the DB name ('InterProScan_DB') to the one you want.
The path of the DB will be the input of -db to run InterProScan.

4. download example protein sequence
```
wget https://github.com/euchrogene/InterProScan_EG/raw/refs/heads/main/test_prot.fa
```

5. example command line
```
InterProScan_v.1.0 -db_path InterProScan_DB -i test_prot.fa -dp -f TSV
```

6. show help contents
```
InterProScan_v.1.0
```

## Help contents:
```
============================================================================
EuchroGene InterProScan v.1.0 - Protein Functional Annotation Pipeline
============================================================================

InterProScan is a comprehensive functional annotation tool for characterizing
protein sequences by identifying domains, families, sites, and Gene Ontology terms.

FIRST-TIME SETUP:
-----------------
Before running analyses, you must download the InterProScan database:

  InterProScan -download_database <DB_FOLDER_NAME>

This will download ~30GB of data. Only needs to be done once.
The database will be organized as: <DB_FOLDER_NAME>/data/

BASIC USAGE:
------------
  InterProScan -db_path <DB_PATH> -i <PROTEIN.fasta> -dp -goterms

EXAMPLE COMMANDS:
-----------------
  # Basic protein annotation
  InterProScan -db_path ./IPS_DB -i proteins.fasta -dp -f TSV,XML

  # With GO terms and pathway mapping
  InterProScan -db_path ./IPS_DB -i proteins.fasta -dp -goterms -pa

  # Specific analyses with custom output folder
  InterProScan -db_path ./IPS_DB -i proteins.fasta -dp -appl Pfam,SMART -out MyResults

REQUIRED OPTIONS:
-----------------
  -db_path <PATH>              Path to InterProScan database folder
                               (folder containing 'data' subdirectory)
  -i <FILE>                    Input protein sequences (FASTA format)

COMMON OPTIONS:
---------------
  -cpu <N>                     Number of CPU cores (default: 32)
  -f <FORMATS>                 Output formats: TSV, XML, JSON, GFF3
                               (default: TSV,XML,GFF3)
  -out <FOLDER>                Output folder name (default: InterProScan_Results)
  -dp                          Disable precalculated matches (recommended)
  -goterms                     Include Gene Ontology annotation
  -pa                          Include pathway annotation
  -iprlookup                   Include InterPro annotation lookup

ANALYSIS SELECTION:
-------------------
  -appl <ANALYSES>             Comma-separated list of specific analyses
                               (e.g., Pfam,SMART,Gene3D)
  -exclappl <ANALYSES>         Exclude specific analyses

ADVANCED OPTIONS:
-----------------
  -b <BASENAME>                Output file basename
  -d <DIR>                     Output directory (overrides -out)
  -o <FILE>                    Explicit output filename
  -T <DIR>                     Temporary file directory
  -t <TYPE>                    Sequence type: p (protein) or n (nucleotide)
  -verbose                     Verbose logging

AVAILABLE ANALYSES:
-------------------
  AntiFam, CDD, Coils, FunFam, Gene3D, Hamap, MobiDBLite, NCBIfam,
  PANTHER, Pfam, PIRSF, PIRSR, PRINTS, ProSitePatterns, ProSiteProfiles,
  SFLD, SMART, SUPERFAMILY

OUTPUT:
-------
  All results will be saved in the output folder:
  - Functional domain annotations
  - GO term mappings
  - Pathway associations
  - HTML report with interpretation
  - Methods section for publication

SUPPORT:
--------
  For bugs or questions: bioinformatics@euchrogene.com
  For licensing: support@euchrogene.com

============================================================================
```
7. Uninstall 
```
sudo EG_tools uninstall -t InterProScan_v.1.0 -i managene7/interproscan:v.1.1
```

# Citation

## InterProScan
Mulder, N., Apweiler, R. (2007). InterPro and InterProScan. In: Bergman, N.H. (eds) Comparative Genomics. Methods In Molecular Biology™, vol 396. Humana Press. https://doi.org/10.1007/978-1-59745-515-2_5
