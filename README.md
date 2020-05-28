# rhv-reporting
Trilio reporting tools for RHV backups

This procedure will create report files for each TrilioVault Workload and a single Overall report for each 24 hour period. This needs to be run on the TrilioVault Virtual Appliance.

### NOTE: Before you begin - if you're using TrilioVault 3.7, you'll need to use the ```overall_report_3.7.py``` file INSTEAD OF ```overall_report.py```

### DIRECTIONS TO ENABLE REPORTS
1. STEP 1- Create the directory structure that will house the backup reports
    ```mkdir -p /root/rhv-reporting/{overall_report,workload_report}```
1. STEP 2- Copy reporting Python scripts to the /root/report directory
  ```cd /root```
  ```git clone https://github.com/jon-tobin/rhv-reporting.git```
1. STEP 3- Add execute permissions to Python files
  ```chmod +x overall_report.py workload_report.py```
1. STEP 4- Activate Python and enable reporting scripts
 ```/home/rhv/myansible/bin/activate```
1. STEP 5- Install configparser
  ```pip install configparser```
1. STEP 6- Create a Cron job to run both scripts at the same time each day. This script will run both reports at 12:01 AM every day of the year
   1. STEP 6a- Copy crontab file from rhv-reporting folder
  ```cd /root/rhv-reporting```
  ```cp reporting_cron /var/spool/cron/root```
1. STEP 7- Register crontab file for root
  ```crontab -e```
 
