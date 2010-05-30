csBackupPlugin
==============

csBackupPlugin is an attempt to provide a simple and easy backup solution for your database and files.

Currently Supported Databases:

  * Mysql (using [AutoMysqlBackup](http://www.debianhelp.co.uk/mysqlscript.htm))
  
Currently Supported File Sync Applications:

  * rsync
  * ftp
  * scp

Database Backup
---------------
  
``php symfony backup:db`` will pull credentials directly from your databases.yml for the specified environment. 
If you desire special credentials for your backup script, you can pass them directly into the script
``php symfony backup:db --username=root --password=password --dbname='db1 db2'``.  If you want to set your script
to import multiple databases, you can configure this in your app.yml

    [yaml]
    all:
      csBackup:
        mysql:
          dbname:  [db_prod, db_dev, db_staging]
          
Some other command options include:

  * __email__: to receive notification
  * __command__: to be called by the backup script (default is mysqldump, but could be mysql5dump)
  * __backup_dir__: absolute path or path relative to your project root for the backup files to be stored.

File Backup
-----------

``php symfony backup:file`` is still in development, but works much the same way as the database backup task.  
All options are configurable in app.yml and over-ridden by options passed to the task.  
Some common options here are 

  * __source__: an array of files/directories to be backed up
  * __target__: the location for the backup (false for local machine)
  * __target_dir__: path on the target machine for the backup files
  
To Do
-----

  * add support for other database backup scripts
  * add support for file backup compression
  * clean up configuration structure