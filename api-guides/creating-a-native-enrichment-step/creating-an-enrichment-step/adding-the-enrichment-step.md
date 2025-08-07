# Adding the Enrichment Step

We will now add the new enrichment step to your Workplace AI installation. To do this we need to first stop all the Workplace AI services and the Web Server. You can always create a script (PowerShell) to automate this if you wish.

<figure><img src="../../../.gitbook/assets/image (584).png" alt=""><figcaption></figcaption></figure>

Now copy the following files from your class library project to your Workplace AI plugins folder:

* helloworldes\_template.html
* bin\Debug\net6.0\InsightMaker.Enrichment.HelloWorldES.dll

<figure><img src="../../../.gitbook/assets/image (712).png" alt=""><figcaption></figcaption></figure>

Finally, restart the Workplace AI services and the Web Server.

Note, you can add some post build steps to your Visual Studio configuration to copy the template file and DLL to the plugins location.
