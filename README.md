PDF Chat with Retrieval-Augmented Generation (RAG) Pipeline

Overview
This project implements a Retrieval-Augmented Generation (RAG) pipeline that allows users to interact with semi-structured PDF documents. By combining text extraction, semantic search, and language generation, the system enables efficient querying and accurate responses from PDF data.


Features:
1.PDF Data Ingestion: 
      Extracts and preprocesses text from PDFs using Optical Character Recognition (OCR).
2.Semantic Chunking and Embedding: 
            Divides extracted text into chunks and generates embeddings using a pre-trained SentenceTransformer model.
3.Vector Database (FAISS): 
             Stores embeddings for efficient similarity-based retrieval.
4.User Query Handling:
        Processes natural language queries, retrieves relevant content, and generates answers using an open-source Large Language Model (LLM).
5.Comparison Queries: 
           Supports comparison across multiple pages/documents for structured responses.
6.Response Generation:
             Combines retrieved data and LLM output to ensure accurate and contextual answers.

Requirements:
Install the required libraries before running the code:

bash:
pip install pdf2image paddleocr sentence-transformers faiss-cpu transformers pandas opencv-python-headless paddlepaddle
sudo apt-get update
sudo apt-get install -y poppler-utils

Workflow
1.Text Extraction:
Convert PDF pages into images using pdf2image.
Use PaddleOCR to extract text from images.

2.Embeddings Generation:
Generate sentence embeddings using SentenceTransformer.

3.Build FAISS Index:
Create a FAISS index to store embeddings for similarity search.

4.User Query Retrieval:
Encode user queries and perform a similarity search in FAISS to retrieve relevant text chunks.

5.Response Generation:
Pass retrieved content and query to an LLM (e.g., Google FLAN-T5) to generate a contextual response.

6.Result Saving:
Save responses as JSON files and allow downloads.

Usage

1.Upload PDF File:
Run the script in an interactive Python environment (e.g., Google Colab).
Upload the PDF file when prompted.

2.Process the Document:
The script will extract, chunk, and embed the text.

3.Ask Queries:
Input natural language queries when prompted.
Specify a specific page number or use "all" to search the entire document.

4.Generate Answers:
The system retrieves relevant content and generates answers using the LLM.

5.Save and Download:
The answer is saved as a JSON file for future reference.

Example

1.Input Query:
"What is the unemployment rate for bachelor’s degree holders?"

2.Process:
Extract text and identify relevant content (e.g., from Page 2).
Retrieve sentences from FAISS.
Generate an accurate answer using LLM.

3.Output:
"The unemployment rate for individuals with a bachelor’s degree is 4.2%."

Dependencies:
pdf2image: Convert PDFs into images.
PaddleOCR: Perform OCR on images.
SentenceTransformer: Generate text embeddings.
FAISS: Efficient similarity search for embeddings.
Transformers: Use LLM (e.g., Google FLAN-T5) for response generation.
pandas and json: Data handling.

File Structure:
main.py: The main pipeline script.
requirements.txt: List of dependencies.

Future Enhancements:
Support for multi-file comparisons.
Integration with a cloud-based vector database.
Improved pre-processing for structured tables.
