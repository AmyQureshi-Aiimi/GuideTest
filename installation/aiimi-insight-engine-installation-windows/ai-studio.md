# AI Studio

<details>

<summary><strong>Fresh Install Prerequisites</strong></summary>

For a fresh Workplace AI Install you will need to complete the build for Workplace AI first.

For guidance on this process see our Workplace AI Installation guides.

</details>

{% hint style="info" %}
The following guide assumes your install is stored in the C: drive.
{% endhint %}

1. Open the InsightMaker\Apps folder.
2. Create an empty folder within here called AIStudio.
   * The path for this folder should be C:\InsightMaker\Apps\AIStudio
3. Run the upgrade script like any other upgrade.
4. Once the upgrade has finished open the AI Studio folder.
5. Rename the file 'web.default.config' to 'web.config'.
6. Open IIS and navigate to the Default web site.
7. Right click the default site and select Add Application.
   * Alias - Enter 'studio'
   * Physical path - Enter C:\InsightMaker\Apps\AIStudio\app
     * This will vary depending on your folder structure.
8. Select OK.
9. To test this was successful navigate to https:\\\localhost\studio.
   * You should see the login prompt for AIStudio.
