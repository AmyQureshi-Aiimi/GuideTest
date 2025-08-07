# Creating an Enrichment Step

This section will guide you through creating a simple enrichment step which will manipulate the text content of an indexed document, and also manipulate an entity.

### Creating the Project in Visual Studio

The first step is to create a class library project in Visual Studio. You can locate this project anywhere, but you will need to link to some of the DLLs that ship with you Workplace AI installation.

For this guide we will call our new enrichment step ‘InsightMaker.Enrichment.HelloWorldES’. Note that enrichment step projects must start with InsightMaker (the output DLL must start with InsightMaker).

<figure><img src="../../../.gitbook/assets/image (466).png" alt=""><figcaption></figcaption></figure>

At the time of writing .NET 6.0 was the required framework requirement.

Now create a new console app in the same solution which will be the test harness that you use to test the enrichment step before deploying to Workplace AI.

<figure><img src="../../../.gitbook/assets/image (471).png" alt=""><figcaption></figcaption></figure>

Once created add a project reference from the test harness to the class library project that you created.

### Adding Required Dependencies

There are several dependencies that are required to build a Native enrichment step. Note that both the class library project and the console app project will need the dependencies.

&#x20;Add InsightMaker.Core.dll – this can be found in your Workplace AI installations plugins sub-folder.

<figure><img src="../../../.gitbook/assets/image (616).png" alt=""><figcaption></figcaption></figure>

You will also want to add log4net using NuGet (we use version 2.0.15 at the time of writing), and System.ComponentModel.Composition (we use version 6.0.0 at the time of writing).

<figure><img src="../../../.gitbook/assets/image (327).png" alt=""><figcaption></figcaption></figure>
