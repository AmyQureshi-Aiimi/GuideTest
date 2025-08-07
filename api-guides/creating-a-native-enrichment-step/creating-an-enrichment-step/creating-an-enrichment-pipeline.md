# Creating an Enrichment Pipeline

Now we have loaded our new enrichment step into Aiimi Insight Engine we can test it. To do this, create a test text file and ingest this into a source.

<figure><img src="../../../.gitbook/assets/image (576).png" alt=""><figcaption></figcaption></figure>

Next, we create an enrichment pipeline that uses our new enrichment step. We also include the content retrieval step and Tika text extraction.

<figure><img src="../../../.gitbook/assets/image (453).png" alt=""><figcaption></figcaption></figure>

Run the pipeline and then look the document up in Aiimi Insight Engine. If we search for ‘Some new text’ we should find it (assuming you don’t have lots of other items with the same text in).

<figure><img src="../../../.gitbook/assets/image (684).png" alt=""><figcaption></figcaption></figure>
