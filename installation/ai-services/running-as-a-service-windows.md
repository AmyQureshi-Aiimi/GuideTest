# Running as a Service (Windows)

## Install AI Services as a Windows Service

1. Make sure Python is installed for all users.
   * If this isn't done, system users running this service will not be able to see it.
   * Python needs to be in the system PATH
2. Edit the run.bat so it contains an absolute path to the **waitress\_server.py file** and your **virtual environment**.
3. Run a command line window as an administrator.
4. Navigate to the Rest Enrichment Service subfolder in your InsightMaker distribution.
5. Execute: `nssm install “InsightMaker AI Enrichment Service”`.
   * <mark style="color:red;">For the AI Model Service, update the above command respectively.</mark>
6. Set the path to run.bat
7. Set the start up directory to the path of the Rest Enrichment Service.
8. **Optional** - Configure which user the service runs as. (See point 1.)
9. Run the service.
   * The first time the app service runs it will download a series of modules and models.&#x20;
   * If this instance does not have internet access,  please reach out to your contact at Aiimi.
10. Check the log file.

<figure><img src="../../.gitbook/assets/image (465).png" alt=""><figcaption></figcaption></figure>
