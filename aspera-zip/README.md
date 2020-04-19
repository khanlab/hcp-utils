# hcp-utils aspera-zip
Tools for working with downloaded aspera packages

## Why aren't all the HCP zip files extracted already?

We have strict limits on the number of files in the `/project` filesystem of compute canada. Thus, we can only keep the downloaded zip files in project space. To use this data, you must extract them to scratch. 

## unzip_hcp.py

The `unzip_hcp.py` script provides an easy way to extract just the files you want to use

It uses a config.yml file to pick what files to include from each zip file, and which to exclude. The `zipfiles` section of the config file is used for this, and each sub-section (e.g. `3T_Structural_1.6mm_preproc`) refers to a different aspera HCP package (e.g. a zip file). There is a list of include entries, and exclude entries. If there is nothing in either list, then this zipfile will not be extaracted. If there is `'*'` in the include list, then all files will be extracted. For further control, you can use filenames as include or exclude criteria. The `sample_subject_listing.txt` file provides a list of all files in the zip files to help you decide. You can use globbing and wildcards in these strings as well. See `man unzip` for more details on this.

## Instructions

1. Clone this repository
    git clone http://khanlab/hcp-utils/aspera-zip

2. Edit the config.yml file, setting `out_scratch_dir` to a scratch folder you control

3. Choose what zip files you want to extract by placing `'*'` in the download list.

3. Use the `sample_file_listing.txt` to update the config.yml to include or exclude any files you wish. This text file contains a listing of all the files in each zip file, replacing the subject id with `{subject}`. 

4. Do a dry-run with:
    python 
