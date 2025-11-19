# add_entap_results2gff python script
Adding funtional annotation from EnTAP results to a .gff file

## Introduction
[EnTAP](https://entap.readthedocs.io/en/latest/index.html) is a useful functional annotation pipeline that we use at FRR. The final results of EnTAP are found in the file `entap_results.tsv` usually in the directory `entap_outfiles/final_results/`. This is a very useful table, but it has a lot of information about each transcript, including those with no annotations. The purpose of the `add_entap_results2gff` utility is to add user-specified columns from the `entap_results.tsv` file as tag-value pairs in the 9th (attribute) column of a gff3 file so that they can be integrated with the structral annotation of the gff file and viewed in a web browser.

## Requirements
This script requires python3 to run.  
It also requires the `entap_results.tsv` file from EnTAP output.  

## Usage
Script usage and options can be obtained using the commmand  
``` 
python add_entap_results2gff.py
```
Which prints
```
Usage: python3 gff_parse.py [OPTION] tsv_file gff_file columns_txt_file output_file_name

columns_txt_file should be a text file with column names seperated by semicolons (;)

Options
    -h      Show this help
    -q      Suppress non-error messages
    -f      Force overwrite of files (doesn't prompt)
```

The positional arguments are:

1. `tsv_file` - The `entap_results.tsv` output file from EnTAP
2. `gff_file` - The input gff file to which the EnTAP functional annotation will be added
3. `columns_txt_file` - a file with a single line that contains the headings of the columns from the `entap_results.tsv` file that should be added to the input gff file. Each heading should be separated by a semicolon.
   - Example: `Description;EggNOG Seed Ortholog;EggNOG Description;IPScan InterPro ID;IPScan Protein Description`
   - The heading and value from the `entap_results.tsv` file of each transcript will be added as tag-value pairs to the input gff file at the end of column 9, separated by a semicolon
     - Example with functional annotation: `description=XP_051205201.1 protein MEI2-like 3 [Lolium perenne];eggnog_seed_ortholog=4513.MLOC_34765.1;eggnog_description=RNA recognition motif 2;ipscan_interpro_id=-(-);ipscan_protein_description=PTHR23189(RNA RECOGNITION MOTIF-CONTAINING)`
     - Example with no functional annotation: `description=NA;eggnog_seed_ortholog=NA;eggnog_description=NA;ipscan_interpro_id=NA;ipscan_protein_description=NA`
4. `output_file_name` - the name of the new output gff file with the functional annotation added

## Script source
This script was developed by Kaden Patten at the USDA ARS Forage and Range Research Unit in Logan, UT
