# PaLM-Docsearch-and-Evaluation
This project was made using Google's generative AI methods and Langchain's methods, including PyPDF.
It includes three files: the main notebook to generate responses, a criteria evaluation, and an embedding distance calculator.

**PaLM is not used anymore so these programs are outdated and will not work. Langchain may have also updated their library since this was written Jul-Sep 2023.**

## Main Notebook
This program uses Google's API and large language model (at the time PaLM LLM) and parses through and interprets a PDF to answer user input questions based on the PDF itself.

## Criteria Evaluation
This algorithm uses the Langchain criteria evaluator and takes in the question (user input from main notebook), answer (AI response), and reference text (relevant passage from the PDF) to determine whether the answer is correct or not.
In this case, the reference text is always assumed to be correct. Unlike the main notebook and embedding distance calculator, this did not require the LLM.

_Note: This program had all three parameters in an Excel spreadsheet over multiple rows. Skip the fourth and fifth code blocks for only one set of inputs._

## Embedding Distance
Unlike the criteria evaluator, Langchain was not compatible with the PaLM LLM so I couldn't use Langchain's embedding distance formula. Langchain uses a Euclidian distance formula (with other options) while my algorithm is different.

- The PaLM LLM was used to convert both the relevant passage from the PDF and the AI response into vector embeddings via tokenization.
- These vector embeddings were multiplied via the vector dot product operation. Normally dot products are between -1 and 1 (if the vector magnitudes are both 1, which is true in this case), but in this case the dot products were all between 0 and 1. A dot product of 1 would be identical texts.
- Because we want distance, this result was subtracted from 1 to get a "distance" (lower value = closer texts).

Formula = 1 - (dot product of reference text embeddings and AI response embeddings)
