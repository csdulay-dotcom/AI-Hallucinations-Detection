# AI-Hallucinations-Detection

## Motivation/Goals: 

This project’s motivation revolves around hallucinations. For this project, the definition of hallucinations is when a large language model (LLM) perceives patterns or objects that don’t exist or are nonsensical based on the reference text provided, leading to it producing incorrect outputs. Hallucinations are incredibly common when asking questions in AI, leading to misleading, misinformed, or dangerous information being spread. We hope to provide a method that can quickly and accurately identify hallucinations in AI-generated text output.


## Detailed Problem Statement:

Current solutions to the problem of identifying hallucinations in AI-generated texts are dominated by the use of LLMs. Although LLM-based methodologies for identifying hallucinations are able to achieve impressive accuracies, extensive prompt engineering, fine tuning, and computation are required. Moreover, discrepancies in accuracy between different LLMs for the task of hallucination detection may introduce uncertainty. For instance, in the LLM-as-Judge method, a group of multiple LLMs are each asked to classify text as hallucinated or not hallucinated, and justify why. In the case of disagreement between models, uncertainties over which LLM to believe due to their explanation may arise. We propose an alternative method that does not rely on multiple LLMs to identify hallucinations, potentially helping to reduce the amount of uncertainty. This would also reduce subjectivity because in LLM-based outputs we may believe one LLM over the other due to the preference of the explanation. Figuring out this problem would help reduce the spread of misinformation and ensure that information given out by AI is more trustworthy.


## Dataset(s) and data acquisition methods: 
Obtained through the use of Arize LibreEval 1.0, an open source tool that allows users to generate their own datasets to evaluate hallucinations in LLMs. This is achieved by scraping web text from provided urls, then pulling the most important passage(s) of the reference text using an LLM. Based on these parts of the text, an LLM is prompted to generate questions, some of which are worded in such a way that encourage a responding LLM to hallucinate. Finally, a council of three LLMs were given the passage(s) and each asked the same question. A label of “hallucinated” or “not hallucinated” is decided based on a majority vote by the LLM council. 

Both types of data, synthetic and nonsynthetic, will be used. The data acquired will feature "Default question type" only. This data will also target the English dataset from Arize LibreEva and their reference texts.

### Methods:

- Sentence similarity model (similarity between reference text and LLM response)
- Topic Modeling (pulling out subject area of LLM response)
- Clustering: Gaussian Mixture Model

