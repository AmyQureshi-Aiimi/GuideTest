# Creating the Core Classes

Several classes need to be generated for configuration, the enrichment step itself, and the factory that creates it on demand.

### Configuration

Create a class called HelloWorldESConfiguration for the configuration. This class will extend the Enrichment Step Configuration class, and also contain a class object that contains enrichment step specific configuration. Here we have a single ‘Text’ property that will contain text to append to the text content on a Workplace AI item.

```
using InsightMaker.Core.Types.Config;

namespace InsightMaker.Enrichment.HelloWorldES
{
    public class HelloWorldESConfiguration : EnrichmentStepConfiguration
    {
        public HelloWorldESConfiguration()
        {
            base.Type = "HelloWorldES";
        }

        public HelloWorldESSpecificConfiguration HelloWorldES { get; set; } 
            = new HelloWorldESSpecificConfiguration();
    }

    public class HelloWorldESSpecificConfiguration
    {
        public string Text { get; set; } = "";
    }
}
```

### Enrichment Step

Create a class called HelloWorldESStep for the actual enrichment step. This class will implement the Enrichment Step interface. For the minute the class will simply print ‘Hello World’ to the console window.

```
using InsightMaker.Core.Types;

namespace InsightMaker.Enrichment.HelloWorldES
{
    public class HelloWorldESStep : IEnrichmentStep
    {
        protected static readonly log4net.ILog log = 
            log4net.LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        private HelloWorldESConfiguration configuration;
        private CancellationToken cancellationToken;

        public HelloWorldESStep(HelloWorldESConfiguration configuration, 
                                CancellationToken token)
        {
            this.configuration = configuration;
            this.cancellationToken = token;
        }

        public void Run(EnrichmentWorkItem work)
        {
            log.Debug("Hello World");
        }
    }
}
```

### Enrichment Step Factory

Create a class called HelloWorldESFactory that will be responsible for creating the enrichment step.

```
using InsightMaker.Core.Types.Plugin;
using InsightMaker.Core.Types;
using InsightMaker.Core.Types.Config;
using System.ComponentModel.Composition;

namespace InsightMaker.Enrichment.HelloWorldES
{
    [Export(typeof(IEnrichmentStepFactory))]
    [ExportMetadata("Type", "HelloWorldES")]
    [ExportMetadata("Description", "Hello World Enrichment Step")]
    [ExportMetadata("DisplayName", "HelloWorldES")]
    [ExportMetadata("Chargeable", false)]
    [ExportMetadata("ConfigurationType", typeof(HelloWorldESConfiguration))]
    [ExportMetadata("StepGroup", StepGroup.Entities)]
    [ExportMetadata("DisplayOrder", 40)]
    [ExportMetadata("Inputs", EnrichmentStepDataType.Text)]
    [ExportMetadata("Outputs", EnrichmentStepDataType.Text)]
    [ExportMetadata("ThirdParty", Dependency.None)]
    public class HelloWorldESFactory : IEnrichmentStepFactory
    {
        public IEnrichmentStep BuildEnrichmentStep(EnrichmentStepConfiguration       configuration, CancellationToken cancellationToken)
        {
            return new HelloWorldESStep((HelloWorldESConfiguration)configuration, 
                                        cancellationToken);
        }

        public object GetDefaultConfiguration()
        {
            return new HelloWorldESConfiguration();
        }
    }
}
```

### Creating the Test Console App

We will now create the console app that we use to iterate development and test the enrichment step.

Edit the Program.cs file (or create a Program.cs file) in the console app project.

```
using InsightMaker.Core.Types;

[assembly: log4net.Config.XmlConfigurator(ConfigFile = "log4net.config")]

namespace InsightMaker.Enrichment.HelloWorldES.Test
{
    class Program
    {
        protected static readonly log4net.ILog log = 
            log4net.LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        static void Main(string[] args)
        {
            log.Info("InsightMaker.Enrichment.HelloWorldES.Test");
 
            var workItem = new EnrichmentWorkItem(new IndexedFile
            {
                Uri = "does not matter for testing",
                TextContent = "This is our documents text content."
            });

            var helloWorldESConfiguration = new HelloWorldESConfiguration();
            helloWorldESConfiguration.HelloWorldES.Text = "Hello World";

            var helloWorldESFactory = new HelloWorldESFactory();
            var helloWorldESStep = (HelloWorldESStep)helloWorldESFactory.BuildEnrichmentStep(helloWorldESConfiguration, 
                                                                                             new System.Threading.CancellationToken());

            try
            {
                helloWorldESStep.Run(workItem);
            }
            catch (Exception e)
            {
                Console.WriteLine(e.Message);
                Console.WriteLine(e.StackTrace);
            }
        }
    }
} 
```

Before attempting to run this, you will also need to add a log4net.config file. Add the following to the project, being sure to select ‘Copy to Output Directory’ on the files properties.

```
<?xml version="1.0" encoding="utf-8" ?>
<log4net>
  <appender name="RollingFile" type="log4net.Appender.RollingFileAppender">
    <file value="c:/temp/logs/InsightMaker.Enrichment.HelloWorldESStep.Test.log" />
    <appendToFile value="true" />
    <rollingStyle value="Size" />
    <maxSizeRollBackups value="10" />
    <maximumFileSize value="10240KB" />
    <staticLogFileName value="true" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%date [%-2t] %-5level %logger - %message%newline" />
    </layout>
  </appender>
  <appender name="ConsoleAppender" type="log4net.Appender.ConsoleAppender">
    <param name="Threshold" value="DEBUG" />
    <layout type="log4net.Layout.PatternLayout">
      <param name="ConversionPattern" value="[%-2t] %message%newline" />
    </layout>
  </appender>
  <root>
    <level value="DEBUG" />
    <appender-ref ref="RollingFile" />
    <appender-ref ref="ConsoleAppender" />
  </root>
</log4net>
```

Now run the console app and you should see the following.

<figure><img src="../../../.gitbook/assets/image (340).png" alt=""><figcaption></figcaption></figure>
