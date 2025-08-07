# OCR Agent

To get the most out of images and PDFs within Workplace AI an OCR agent converts them to text and image-over-text pdf files. This means you can:

* Search the contents of a PDF or image file.
* See hit highlighting on a PDF or image file.
* Easily find entities and metadata for PDF or image files within preview.

[View our guide to configuring an OCR.](../../../control-hub/agents/configurations/ocr-engine.md)

### OCR Engines

The OCR agent ships with a built in engine called IronOCR. It can also run a series of other OCR engines like ABBY Reader.&#x20;

The enrichment pipeline invokes the OCR agent through the OcrRest enrichment step.

### OCR Requirements

For light OCR loads the agent can share a server with other agents such as enrichment and source agents.&#x20;

If you are OCR’ing lots of content then you will want to run this agent on a dedicated server. The initial load to Workplace AI may require increases computing power but can be reduced once you are processing deltas.
