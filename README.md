# contact_mothership
### A simple Bash-Script to manage Backups

Contact_mothership is a bash-script to make backups hassle-free.
## The problem it solves:
Many ppl have some sort of external-drive, net-storage or similar to keep all their data (documents, programs, code, music ...) in a central place in clear structure.
Then they have as example a laptop where they copy a subset of this data into when they need to work on it.
Then it comes to backing this data up, they need to:
 * remember what directory matches what directory on the backup
 * keep track if the changes on the backup are newer than the local changes or vice versa
 * make sure they do not forget anything (take a config-file of a program as example)
 * in case of heaving the same data multiple times coped on their local machine decide what version should be backed up

contact_mothership works on directory level only and solves these issues by making sure that every directory on local.
* knows where its sibling on the backup-drive is located
* knows in what state local was after the last synchronization
* knows in what state backup was after the last synchronization
* providing a mechanism to periodically scan the entire file system for directories that are relevant to be backed up.

## example:
```bash
contact_mothership -setmothership /media/BackupDrive # setting the location of the backup-drive
contact_mothership -grab /media/BackupDrive/awesomeFiles /home/$USER/ #copying files from backup to local
echo "bla" > /home/$USER/awesomeFiles/bla #manipulation data
contact_mothership -diff /home/$USER/awesomeFiles #display difference between local and backupcontact_mothership -diff /home/$USER/awesomeFiles #display difference between local and backup
contact_mothership -check /home/$USER/awesomeFiles #display if backup is newer, local is newer or there is a conflict
contact_mothership -sync /home/$USER/awesomeFiles #synchronize       (in this case push)
mv ~/awesomeFiles /mnt #move files around
contact_mothership -index #scan whole file system for directories marked as backups (/mnt/awesomeFiles as example)
contact_mothership -pushtotal # push all changes from local to backup (for all directories appearing in the index)
```













