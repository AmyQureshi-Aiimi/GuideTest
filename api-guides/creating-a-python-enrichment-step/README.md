# Creating a Python Enrichment Step

This document presents a guide for developers wishing to create a custom Workplace AI enrichment step with Python.

### Background

Enrichment is the process of adding additional context to items that Workplace AI discovers through a series of steps that run in an enrichment pipeline. Most of this additional context manifests itself as labels that are applied to the items that help Workplace AI present more meaningful information to users.

Enrichment may add classifications, geotags, named entities and other such things to items. Again, like source connectors, enrichment is extensible and underpinned by a framework that makes it easy for both Aiimi and our customers and partners to create enrichment steps. Enrichment steps are generally written in .NET or Python, but they can in fact be written in any language and interfaced with using the generic REST enrichment step.

AIE ships with the Python REST Service which Aiimi use to host Python enrichment steps. These enrichment steps typically use machine learning or other frameworks that are specific to Python and help accelerate delivering value.

Python enrichment steps are a great and quick way to extend the enrichment capabilities of Workplace AI, and customers and partners can add new enrichment steps to the Python REST Service. You can of course write your own enrichment endpoint independently from the Python REST Service, and if you wish to do this, following this guide will give you valuable insight on how to achieve that (it’s just a REST / JSON end point that updates a data structure).

### Python REST Service

This guide assumes that you have read the installation and configuration guide for the Python REST Service and have set it up.
