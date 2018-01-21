# Visenze-Client-Solutions-Datafeed-Integration
This script creates a scheduled job on Visenze datafeed integration through FTP method. It supports two modes: 
1. FULL (Default):the contents of this file will be used to fully replace your current image database.
2. INCREMENT:	the contents of the datafeed file will be used to append new entries or update existing entries. If a delete file is provided, batch remove based on the data in the delete file will be performed after the successful index of the datafeed.

Steps to follow before executing the script
1. Create three folders: your_upload_folder_name, your_backup_folder_name, your_ftp_folder_name;
2. Put the csv files to be uploaded into your_upload_folder_name;
3. Review Visenze ftp indexing procedure: http://developers.visenze.com/setup/#FTP-upload
4. Pay special attention to the naming of the csv file
- Your admin access key should be the filename. For Example: 83b3a2dc6cf4b0966575250b26449770.csv.gz
- We accept only UTF-8 formatting for the data file.
5. Execute the command below. 

Install 
```bash

$ sudo apt-get install ncftp

```

Command
```bash

$ bash ~/dir/ftp_sample.sh --upload ~/dir/your_upload_folder_name --backup ~/dir/your_backup_folder_name --ftp ~/dir/your_ftp_folder_name --username XXX --password XXX --ftp_address XXX 

```

Schedule FTP task at 10am everyday 
```bash
crontab -e
```
```bash
0 10 * * * bash ~/dir/ftp_sample.sh --upload ~/dir/your_upload_folder_name --backup ~/dir/your_backup_folder_name --ftp ~/dir/your_ftp_folder_name --username XXX --password XXX --ftp_address XXX 
```
