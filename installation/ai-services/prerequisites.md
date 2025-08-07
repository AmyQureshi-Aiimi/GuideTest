# Prerequisites

There are a number of prerequisites that are required for all AI Services.

## **Unzip the AI Service Distro**

1. Create a folder called InsightMaker.Python.&#x20;
   * This drive needs enough space for the Python virtual environment. These are around 6GB per service.
2. Extract the distro to a sub-folder with the same name as the original zip file.
   * AIEnrichmentService
   * AIModelService

***

## Python

1. Check if you have a version of Python running on the server.&#x20;
   * You can check the PATH and location of installed applications.
   * Or, open a prompt and run the following:

```
python --version
```

### **Python Doesn't Exist**

#### **Install Python**

1. Install Python 3.12.8
   * To run Python REST services as a Window Service you need to install Python for ‘all users’.

#### Create a Python Virtual Environment

1. Create a venv folder in the root of the respective AI Service you are setting up.
   * .\InsightMaker.Python\AIEnrichmentService
   * .\InsightMaker.Python\AIModelService
2. Open command prompt.
3. Navigate to the venv folder.
4. Create the venv with the following python command: `python -m venv ./`

### **Python Exists**

#### Install Python

1. Install Python 3.12.8
   * To run Python REST services as a Window Service you need to install Python for ‘all users’.
   * Do not add to the system variables or path as this may impact existing Python applications on the server.
2. Open an administrator command prompt.
3. Install virtualenv using the following command: `pip install virtualenv`

#### Create a Python Virtual Environment

1. Create a venv folder in the root of the respective AI Service you are setting up.
   * .\InsightMaker.Python\AIEnrichmentService
   * .\InsightMaker.Python\AIModelService
2. Open command prompt.
3. Navigate to the venv folder.
4. Create the venv with the following python command: `python -m virtualenv ./ -p="C:\Program Files\Python312\python.exe"`

{% hint style="warning" %}
Replace the -p parameter with the path to the Python 3.12.8 executable.
{% endhint %}

***

## **Configure and Install Prerequisites**

### Windows ONLY - Ensure long path support

1. Using Regedit:
   * `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem`
   * `LongPathsEnabled`
   * `DWORD = 1`

### Setup NLTK

Many of the AI Model Services and AI Enrichment Service require NLTK.

* Install the nltk Python libraries using: `pip install nltk`
* Install the NLTK data (models) to a location on the server using:`python -m nltk.downloader all -d <LOCATION>`
* Set an environment variable to point at the NLTK data using: `NLTK_DATA=LOCATION`

For more information see the NLTK documentation: [https://www.nltk.org/data.html](https://www.nltk.org/data.html)

***

## Workplace AI Wheel

AI Classification, Enrichment and Model services require the AiimiInsightEngine Wheel to be installed. This installs the AiimiInsightEngine library.&#x20;

1. After installing packages from requirements.txt.
2. Within the correct virtual envrionment run `pip install AiimiInsightEngine-0.4.2-py3-none-any.whl`&#x20;
