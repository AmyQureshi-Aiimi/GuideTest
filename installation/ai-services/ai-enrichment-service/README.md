# AI Enrichment Service

This details the AI Enrichment Service and the enrichment steps that are included with Workplace AI.

* **Bert Chinese NER** - Provides named entity recognition for Chinese text. It supports person, location and organisation classes.&#x20;
* **Classification** – This uses Aiimi’s clustering and classification framework to classify documents using a pre-trained model. Additional documentation for model training can be found in the InsightMaker.Python\DocumentClassification\docs folder.
* **DSAPI Model** - This allows you to invoke the data science API to run models and add enrichment labels to your objects in AIE.
* **Ext AI Prompt** - Allows you to run extractive AI over the text content of an object and store the results in entities.
* **Face Recognition** - Allows you to recognise faces. based on pretrained models.
* **Generative AI Prompt** - Allows you to run large language models at enrichment. You can define prompts which are then run over the text content of a file in Workplace AI.&#x20;
  * This works with the Model Server thst hosts both private (Llama2) and cloud based LLMs (Azure Open AI).
* **HFImageToText** - Generates text that describes an image.
* **HF Sentence Transformers** - Uses the Sentence Transformers framework to generate word embeddings which can be stored as dense vectors within Workplace AI. These provide users with a semantic search experience.
* **HF Sparse Vector** - Uses models running with the transformers framework to generate sparse vectors for files within Workplace AI. These are stored as Rank Features within Workplace AI and enable a search experience that can handle vocabulary mismatch. &#x20;
* **HF Vision Transformer** - This allows you to create dense vectors for images, which in turn support image similarities and search use-cases.
* **Huggingface Named Entity Recognition** – Extracts named entities from text or documents using statistical methods. This step is more accurate, but slower, than Spacy.
* **Language Detection** – Can detect 54 different languages from text.
* **Phase and Topic Detection** – Extracts repeating phrases from a document or text that are said to be ‘left right complete’. When writing about a topic, people generally repeat the core concepts and topics several times. This extracts these from the text and creates a list of the core concepts, themes, and topics.
* **Sentiment** - Assigns a sentiment label and score to an object stored within Workplace AI.
* **Document Summaries** – Creates a short multi-sentence summary of  a document so users can quickly understand what the document is about. There are several algorithms provided, each with different merits.

_Other services within the endpoints folder are alpha enrichment steps and are unsupported._
