---
title: "Mendix AI Assistance (Maia)"
url: /refguide/mendix-ai-assistance/
weight: 45
description: "Describes Mendix AI Assistance (Maia) in Studio Pro."
aliases:
    - /refguide/mx-assist-studio-pro/
---

## Introduction 

Mendix AI Assistance (Maia) refers to Mendix Platform capabilities that leverage [artificial intelligence (AI)](https://www.mendix.com/glossary/artificial-intelligence-ai/) and [machine learning (ML)](https://www.mendix.com/glossary/machine-learning/) to assist developers in application development. Maia is designed to help development teams in modeling and delivering Mendix applications faster, more consistently, and with higher quality. 

Mendix developers can use Maia to get guidance by asking questions, get recommendation and assistance for certain development tasks, and even generate part of their app. 

For information on Mendix data storage policies and practices for Maia, see [Maia Privacy Policy](https://www.mendix.com/legal/privacy/maia/).

For information on what third-party services Maia uses and what data are sent to the third-party services, see the [Maia Third-Party Services](#maia-third-party-services) section below.

## Maia Capabilities in Mendix Studio Pro 

In addition to Maia Chat, Maia in Mendix Studio Pro has the following capabilities: 

Guidance:

* **Maia Chat** (generally available in Studio Pro 10.12.0) – a built-in chat interface powered by Generative AI in Studio Pro. It answers questions about app development in Mendix, including how to apply concepts, best practices, and development patterns. For more information, see [Maia Chat](/refguide/maia-chat/). 
* **Maia Learn** (available in Studio Pro 10.18 and above) - helps you to quickly learn Mendix core concepts and get started with Studio Pro. For more information, see [Maia Learn](/refguide/maia-learn/).

Recommenders:

* **Best Practice Recommender** – helps you inspect your app against Mendix development best practice detecting and pinpointing development anti-patterns and, in some cases, automatically fixing them. For more information, see [Best Practice Recommender](/refguide/best-practice-recommender/).
* **Logic Recommender** – helps you model and configure microflows, nanoflows, and rules in Mendix Studio Pro. It gives you contextualized recommendations on the next best activity based on the activities and parameters that are already configured in your application. For more information, see [Logic Recommender](/refguide/logic-recommender/).
* **UI Recommender** (available in Studio Pro 10.18 and above) – helps you easily add new widgets to a page in Mendix Studio Pro without losing the context of what you are currently working on. For more information, see [UI Recommender](/refguide/ui-recommender/).
* **Workflow Recommender** (available in Studio Pro 10.12 and above) – helps you model and configure workflows in Mendix Studio Pro. It gives you contextualized recommendations on the next best activity in your workflow based on context-related information. For more information, see [Workflow Recommender](/refguide/workflow-recommender/).

Generators:

* **Domain Model Generator** (currently an [experimental feature](/releasenotes/beta-features/) introduced in Studio Pro 10.13.0) - an AI-powered tool that you can use for generating a [domain model](/refguide/domain-model/). It helps you to generate entities and associations based on text input. It currently only works for empty domain models. For more information, see [Domain Model Generator](/refguide/domain-model-generator/).
* **Translation Generator** (currently an [experimental feature](/releasenotes/beta-features/) introduced in Studio Pro 10.12.0) - an AI-powered translation tool available in Mendix Studio Pro. Currently, it can be used for [batch translate](/refguide/translation-generator/#batch-translate) and [translating system texts](/refguide/translation-generator/#translate-system-text) in the new web-based system texts editor (in Studio Pro 10.14.0 and above). For more information, see [Translation Generator](/refguide/translation-generator/).

## Maia in Mendix Portal

Various Maia features are available in Mendix Portal. For more information, see the [Maia in Mendix Portal](/developerportal/global-navigation/#maia-mx-portal) section in *Global Navigation*.

## Maia Third-Party Services {#maia-third-party-services}

The table below presents all the third-party services each Maia capability uses and what data are sent to the third-party services.

| Maia | Third-Party Service | Data Sent to Third-Party Service |
| --- | --- | --- |
| Maia Chat | [Mistral 7B](https://mistral.ai/news/announcing-mistral-7b/) hosted in Mendix AWS environment | User prompts and the generated answers |
| Best Practice Recommender | No third-party services used | N/A |
| Logic Recommender | No third-party services used | N/A |
| UI Recommender | No third-party services used | N/A |
| Workflow Recommender | No third-party services used | N/A |
| Domain Model Generator | [Claude in Amazon Bedrock](https://aws.amazon.com/bedrock/claude/) | User prompts and the generated content |
| Translation Generator | [Amazon Translate](https://aws.amazon.com/translate/) | All translatable texts in the application, for example, labels, button names, and menu items |
| Maia Rewrite | [Mistral 7B](https://mistral.ai/news/announcing-mistral-7b/) hosted in Mendix AWS environment | The draft question description from users |
| Maia Summarize | [Mistral 7B](https://mistral.ai/news/announcing-mistral-7b/) hosted in Mendix AWS environment | [Community](https://community.mendix.com/p/community) threads |
