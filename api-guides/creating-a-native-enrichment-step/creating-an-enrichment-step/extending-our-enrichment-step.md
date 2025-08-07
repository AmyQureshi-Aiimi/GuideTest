# Extending our Enrichment Step

We will now add some simple logic to append our configured ‘Text’ to the text content of the ‘work item’.

First, change the enrichment step so that Run reflects this.

```
public void Run(EnrichmentWorkItem work)
{
    work.File.TextContent += " " + configuration.HelloWorldES.Text;
}
```

Next, change the Program.cs to reflect this:

<pre><code>try
{
    Console.WriteLine("Before: " + workItem.File.TextContent);
    helloWorldESStep.Run(workItem);
<strong>    Console.WriteLine("After: " + workItem.File.TextContent);
</strong>}
</code></pre>

If we now run the console app again, we should see the following.

<figure><img src="../../../.gitbook/assets/image (553).png" alt=""><figcaption></figcaption></figure>
