#autorepo

##How to Use:
###1.  Add below to your .bashrc:  
> export PATH=$HOMD/autorepo/:$PATH  

###2. Put autorepo in your linux  
> $ cd ~  
> $ git clone https://github.com/codediablos/autorepo.git  
> $ source .bashrc  
> $ cp ~/autorepo/.autorepo_conf_template ~/.autorepo_conf  

###3. Set auto repo & build  
> $ autorepo --config    #Setting repo dir & build dir(you can change EDITOR env value for different editor) 

Config file:  

[A9]                    <----your project name  
project_dir = /home/holiday/project/ics-robin          <------ project location  
repo = yes                            <------ Run auto repo  
build = yes                            <------ Run auto build  
sku = s500_ww_gen1  
variant = userdebug              <------ Build VARIANT mode images, Supported: user, userdebug, eng  
cleanbuild = no                     <------ Using clean build or not  

 #Set output directory for check function  
[output_dir]  
a100 = vangogh                  <---- a100 out dir is out/target/product/vangogh  
a200 = picasso_e  
a210 = picasso_e2  
a500 = picasso  
a510 = picasso_m  
a700 = picasso_mf  

###4. Add "autorepo" on your crontab  
> $ crontab -e                         #Setting daily run  
  
'm h  dom mon dow   command'  
ex. 10 2  *   *   *     /home/username/cron/autorepo --start  #every 2:10 am running autorepo  
     10 2  *   *   *     /home/username/cron/autorepo --start --clean #every 2:10 am running autorepo using cleanbuild  

###5. Other function  
> $ autorepo -c  #check repo is success or fail.  
> $ autorepo --help  
> $ autorepo --log savelog  

-----------------------------------------------------

###Change Logs  
Version: 2.8.15  
1. Add --log to save build log  

Version: 2.8.8  
1. Can check repo is fail or success.  
2. Change  config file  

Version: 2.7.19  
1. Using OptionParser  

Version: 2.7.13  
1. Refactoring  

Version: 2.7.9.2  
1. Change building fail judgment condition  

Version: 2.7.9  
1. Add make clean: Using command "python autorepo.py clean" (setting in crontab)  
2. Fix environment variable EDITOR not set bug (default using vi)  
3. Add check command: Using command "autorepo --check"  check building is fail or success.  

Version: 2.7.6.2  
1. Can build user or userdebug version (ex. /home/holiday/project/ics-robin:s500:user)  
2. Add repo log ($HOME/cron/repo_log.txt) & build log ($HOME/cron/repo_log.txt)  
