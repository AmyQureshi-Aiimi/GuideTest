# Creating a Native Enrichment Step

This document presents a guide for developers wishing to create a custom Aiimi Insight Engine native enrichment step.

A native enrichment step is built in Microsoft.NET and the examples in here use the C# programming language. It is assumed that the reader is proficient in Microsoft.NET and C#.

### Background

Enrichment is the process of adding additional context to items that Aiimi Insight Engine discovers through a series of steps that run in an enrichment pipeline. Most of this additional context manifests itself as labels that are applied to the items that help Aiimi Insight Engine present more meaningful information to users.

Enrichment may add classifications, geotags, named entities and other such things to items. Again, like source connectors, enrichment is extensible and underpinned by a framework that makes it easy for both Aiimi and our customers and partners to create enrichment steps. Enrichment steps are generally written in .NET or Python, but they can in fact be written in any language and interfaced with using the generic REST enrichment step.

### Prerequisites

This guide assumes the following:

* You have an Aiimi Insight Engine development environment set up.
* You have Visual Studio (this guide was written using Visual Studio 2022).
* You have .NET Core SDK.
* You are proficient in Microsoft.NET.
* You are proficient in the C# programming language.
* You have internet access, or know how to install packages offline (this guide uses NuGet).
