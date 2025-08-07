# Running the Example

To run the example (or indeed your own step) from Workplace AI follow the following steps.

<figure><img src="../../../.gitbook/assets/image (482).png" alt=""><figcaption></figcaption></figure>

To do this, open the ./config/endpoints file and add the step name to the list. Here you can see example has been added.

Next start the Python REST Service. You can do this from your virtual environment on the command line by running run.bat from the root folder, or just double click on run.bat from Windows explorer.

<figure><img src="../../../.gitbook/assets/image (439).png" alt=""><figcaption></figcaption></figure>

You should see your endpoint load, before it reaches ‘ready for requests’.

Once the service is running you can ingest an example document and run it through enrichment.

<figure><img src="../../../.gitbook/assets/image (621).png" alt=""><figcaption></figcaption></figure>

You will need to create a file system source and get the file ingested (see the control help guide for further assistance with this).

Once ingested you can create an enrichment pipeline that includes the example step.

<figure><img src="../../../.gitbook/assets/image (711).png" alt=""><figcaption></figcaption></figure>

Now run the pipeline and you should see some debug output from the console window (assuming you are not running the REST Service as a service – in which case inspect the log file).

<figure><img src="../../../.gitbook/assets/image (408).png" alt=""><figcaption></figcaption></figure>

Here you can see in the console output the ‘Hello World!’ that we have added.

Lastly, let’s see what the item looks like in Workplace AI by searching for ‘test.txt example hello World’.

<figure><img src="../../../.gitbook/assets/image (495).png" alt=""><figcaption></figcaption></figure>
