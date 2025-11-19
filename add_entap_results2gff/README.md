# add_entap_results2gff python script
Adding funtional annotation from EnTAP results to a .gff file

## Introduction
[EnTAP](https://entap.readthedocs.io/en/latest/index.html) is a useful functional annotation pipeline that we use at FRR. The final results of EnTAP are found in the file `entap_results.tsv` usually in the directory `entap_outfiles/final_results/`. This is a very useful table, but it has a lot of information about each transcript, including those with no annotations. The purpose of the `add_entap_results2gff` utility is to add user-specified columns from the `entap_results.tsv` file as tag-value pairs in the 9th (attribute) column of a gff3 file so that they can be integrated with the structral annotation of the gff file and viewed in a web browser.

## Requirements
This script requires python3 to run.  
It also requires the `entap_results.tsv` file from EnTAP output.  

## Usage

