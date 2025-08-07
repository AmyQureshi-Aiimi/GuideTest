# Python Library

The Aiimi Insight Engine python library provides various wrappers and utilities for use with Aiimi Insight Engine. Its primary purpose is to provide shared code used by the python AI Enrichment, AI Model and AI Classification services. However, the various available wrappers are also useful for building bespoke scripts or applications powered by Aiimi Insight Engine. This documentation covers all currently available wrappers.

<details>

<summary>Prerequisites</summary>

When installing the python library to use with an AI Enrichment, AI Model or AI Classification service, the listed requirements for that service should be installed before the Aiimi Insight Engine library.&#x20;

</details>

## Installation

The Aiimi Insight Engine python library is published with InsightMaker.Python releases. Please ensure you install the python library version associated with your Aiimi Insight Engine version. The python library is distributed as a python wheel file.&#x20;

Python wheel file example: AiimiInsightEngine-0.5.0-py3-none-any.whl \
&#xNAN;_(The version number will vary depending on release)_.&#x20;

### Install the Library&#x20;

1. Activate the desired virtual environment&#x20;
2. Run pip install AiimiInsightEngine-0.5.0-py3-none-any.whl \
   (you may need to prefix the wheel file name with a directory if it is not in your working one)&#x20;

### Installing Offline

The Aiimi Insight Engine library has its own requirements, separate from those required by the services which pip will install with Aiimi Insight Engine. When working in an offline environment or one behind a proxy which prevents access to The Python Package Index, these installs will fail. In this scenario, you need to provide the required wheels in a local directory and run:&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
pip install AiimiInsightEngine-0.5.0-py3-none-any.whl --no-index --find-links C:\my-local-wheels-directory 
```
{% endcode %}

You can find the required wheels you need in the requirements.txt file in the source code.

***

## Upgrading

When upgrading the majority of changes should be backwards compatible. Any breaking changes between releases will be detailed in the release notes.&#x20;

If you are using the library with any python service, the required changes will be included with the release. You will only need to change any use case specific bespoke code affected by breaking changes.&#x20;
