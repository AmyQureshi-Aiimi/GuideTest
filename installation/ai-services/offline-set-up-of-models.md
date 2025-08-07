# Offline Set-up of Models

To use Huggingface models offline you will need to download the models on a machine connected to the internet and then copy them across. The easiest way to do this is to get the AI service(s) running on a machine connected to the internet and let it download all of the models for you.&#x20;

More Information about how the Huggingface cache works can be found here:

* [https://huggingface.co/docs/transformers/installation](https://huggingface.co/docs/transformers/installation)

## AI Service Set Up

1. Get the respective AI Service set up on an internet connected machine.
2. Enable the transformers based steps in your configuration.
3. Run the service with run.bat
   * These are large files and may take a few minutes.
   * You should see log messages that indicate its downloading models from the internet –&#x20;

<figure><img src="../../.gitbook/assets/image (438).png" alt=""><figcaption><p>Model Download</p></figcaption></figure>

***

## Find the models

1. Find your models.
   * On a windows, by default, they can be found in:\
     Local Disk > Users > username > .cache > huggingface > transformers

<figure><img src="../../.gitbook/assets/image (686).png" alt=""><figcaption></figcaption></figure>

2. Zip them up and move them to the same place on the target server.&#x20;
   * Make sure you place them into the right users .cache folder. You are probably running the service as a different user on the target system.
3. On the target system set an environment variable: `TRANSFORMERS_OFFLINE=1`
4. Run the service.
