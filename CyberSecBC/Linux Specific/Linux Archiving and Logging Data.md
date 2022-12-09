# Archiving and Logging Data
##### INTRO TO TAR COMMAND
Backups
	- full  backups are more reliable and offer complete restoration, but require large storage space.
	- Incremental and differential backups include only data that changed since the last full or incremental backup. Faster and Less space!

Tar (tape archive)
  ![[Pasted image 20220912221549.png]]
sudo = root command
tar = command
c = create
W = verify integrity
v = verbose (progress status and useful info (extra v shows more)
f = indicates the title of the archive
	Hurricane...... name of folder
/var/log = what we are backing up

gzip is used to compress files with gzip (compress) and gunzip (decompress)

tar tvvf "file name"
	test very verbose file // see whats in the archive
tar xvvf "file name" -C "directory" --wildcards "*.csv"
	xvvf extract // unarchive with outpu
    -C "directory" // where we are restoring
	 --wildcards // targets what to extract or just name the files/directories

Incremental Backup
	- Stores a list of which files have changed in a snapshot file, with the extension .snar
    - created when the admin creates the initial level 0 backup
    - every time this backup completes a new snapshot is created and contains only the files that have changed
![[Pasted image 20220912221820.png]]
![](en-cache://tokenKey%3D%22AuthToken%3AUser%3A232435070%22+b8f13ea1-1f76-7ddc-7b47-b1fd21cf2320+1b559e9d82306064195ce5adcaabcb6a+https://www.evernote.com/shard/s699/res/6c09ecf3-dfc0-cf01-3814-19b56de75845)
emerg_back_sun.tar // the archive we are creating
--listed-incremental=emerg_backup.snar // the backup file that will be incremented)
--level=0 // its the first backup or zero level backup
emergency // folder we are backing up

  DAY 2

Cron Jobs
	: a script or command designated to run at periodic, predetermined intervals
	    - user-level cron jobs can automate the process of deleting cache emptying trash, and backing up documents.
	    -  system-level cron jobs can automate dauly software updates
cron tab  
	also known as a cron table is a file that stores all the tasks and schedules.
![](en-cache://tokenKey%3D%22AuthToken%3AUser%3A232435070%22+b8f13ea1-1f76-7ddc-7b47-b1fd21cf2320+d164249b8914a6374fa11bf7582007a5+https://www.evernote.com/shard/s699/res/8163298f-ed1e-ea5b-8f79-8e922e23249e)
![[Pasted image 20220912221950.png]]
==minute | hour | day of month | month | day of the week==
Commands
	- crontab -e // edits crontabs
    - crontab -l // lists all cronjobs in the crontable
[Generate easy cron tabs here!](http://crontab-generator.org)

Scripts for Cronjobs
```bash
apt update
apt upgrade 
apt dist upgrade  
apt autoremove --purge  
-y # for all commands tells any prompts yes
```
System Cronjobs

System-wide directories are located at
    /etc/crontab
    /etc/cron.d
    /etc/cron.daily
    /etc/cron.hourly
    /etc/cron.monthly
    /etc/cron.weekly

Lynis Scanner
	: a security scanner used to check a machine for vulnerabilities
	    - generates and saves reports of its findings for administrators to review.
	    - offers numerous scan types
```bash
-   sudo lynis show help # shows the help page 
-   sudo lynis show # shows which types of audits you can run
-   sudo lynis show groups # shows groups you can test from
-   sudo lynis audit system --test-from-group accounting # run the audit and run  it from a group specified with the --argument
```

DAY 3

Log Management  
	- Ensuring logs are protected through detailed recordings of changes.
    - Storing logs for a sufficient amount of time
    - Omitting unnecessary data to avoid excessive and gratuitous logs
	    - Stored in /var/log/auth.log or /var/log/syslog
![[Pasted image 20220912222552.png]]
![](en-cache://tokenKey%3D%22AuthToken%3AUser%3A232435070%22+b8f13ea1-1f76-7ddc-7b47-b1fd21cf2320+3097caeb59353df1d2a0e137a6c14e9f+https://www.evernote.com/shard/s699/res/5f1b3880-2fb8-0175-f76f-b4676861a30d)

Journal control command
	- Failed Logins
    - Improper Shutdown
    - Successful Login
    - Printing Documents
    - System Startups
    - Cron Job Activity
    - 
_systemd and jounald are the two processes that are responsible for tracking information used with journalctl_

Syntax for jounalctl
```bash
journalctl # returns massive content of the system logs.  
--list-boots # diplays lines for each individual boots  
-ef # e diplays the end of the journal and f tells it to follow that end to monitor ongoing processes.  
_UID # view systemd-journald logs for a user
```
edit the journald configuration in /etc/systemd/journald.conf and then restart the process
`sudo systemctl restart systemd-journald`

Log Rotation /etc/logrotate.conf
	: the process of archiving a log once it reaches a specific size or a point in a set schedule and rotating it our with a new, empty log.
	- Schedule the creation of new logs
    - Compress log files to save hard drive space
    - execute commands prior to and after a log is rotated
    - Time stamp old logs and rename them during rotation
    - log file archive pruning to maintain only a certain number of backlogs.
    - Smaller archives mean faster transfer time

Linux auditing system (auditd)
	: an excellent way for sysadmins to create log rules for nearly every action on a data center server or user host. This system allows you to track and record events, and even detect abuse or unauthorized activity, via log files.
![[Pasted image 20220912222933.png]]
	create rules in /etc/audit/rules.d/audit.rules
```bash
-w # watched 
-p # permissions 
w # write
a # change attribute 
-k # rule keyname
```
test