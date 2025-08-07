# Troubleshooting

* I can’t see my enrichment step in Control Hub:
  * Does the DLL start with ‘InsightMaker’?
* I can’t see my configuration template in Control Hub:
  * Is it named correctly? \<step\_name>\_template.html
* I can’t see my log output when I test my step:
  * Have you configured Visual Studio to copy the log4net.config file to the output directory.
* I am not seeing my entities in the Insight App:
  * Have you created them properly in Control Hub and made sure the mappings have been applied to the indexes.
* I can’t copy my enrichment step DLL to the plugins folder:
  * Have you stopped all of the Aiimi Insight Engine services and the Web Server.
