# Portal Sync Job

1. Check or Uncheck any of the purge and sync options available for use with the Privacy Portal.

#### File Scanner Configurator

1. You can drag the file scanners you want to perform to the right box.
   1. ScaniiFileScanner requires no more details added.
   2. TestFileScanner requires you to add a Test Signature.
   3. LocalFileScanner requires a working directory and a wait time in seconds.
      1. The working directory will default to Path.GetTempPath() if left blank.
      2. The Wait Time will default to 1 second and is for non Windows operating systems.
