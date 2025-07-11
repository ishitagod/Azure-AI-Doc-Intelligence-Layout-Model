# Document Intelligence Pipeline with Azure AI and LLMs

A powerful pipeline for extracting, processing, and querying structured data from PDF documents using Azure Document Intelligence and local LLMs.

## Features

- **Document Analysis**: Extract text, tables, and layout information from PDFs using Azure Document Intelligence
- **Structured Output**: Save extracted data in both Excel and JSON formats
- **Natural Language Querying**: Ask questions about your documents using local LLMs via Ollama
- **RAG Integration**: Implements Retrieval-Augmented Generation for accurate question answering

## Prerequisites

- Python 3.8+
- Azure subscription with Document Intelligence service
- Ollama installed and running locally
- Hugging Face account and API key

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/document-intelligence-pipeline.git
   cd document-intelligence-pipeline
   ```

2. Create and activate a virtual environment (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: .\venv\Scripts\activate
   ```

3. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

4. Install Ollama and download the model:
   ```bash
   # Install Ollama from https://ollama.ai/
   ollama pull gemma3:1b  # or your preferred model
   ```

## Configuration

1. Create a `.env` file in the project root with your credentials:
   ```
   AZURE_ENDPOINT=your_azure_endpoint
   AZURE_KEY=your_azure_key
   PDF_FILE_PATH=path/to/your/document.pdf
   HUGGINGFACEHUB_API=your_huggingface_api_key
   ```

## Usage

### 1. Document Analysis
```bash
python analyze_layout.py
```
This will process your PDF and generate:
- `document_analysis.xlsx`: Excel file with tables and page information
- `tables_data.json`: Structured JSON of extracted tables

### 2. Query Your Document
```bash
python llm_prompt.py
```
The script will process questions from `std_queries.py` and save answers to `output_file.json`

## File Structure

- `analyze_layout.py` - Extracts text and tables from PDFs
- `llm_prompt.py` - Implements RAG-based question answering
- `std_queries.py` - Contains predefined questions for document querying
- `requirements.txt` - Python dependencies
- `.env.example` - Example environment configuration

## Dependencies

- azure-ai-documentintelligence
- PyPDF2
- openpyxl
- python-dotenv
- sentence-transformers
- torch
- transformers
- huggingface-hub

## Output Examples

### Excel Output
- Multiple sheets for each table found
- Document metadata and layout information

### JSON Output
- Structured data in machine-readable format
- Organized by tables and document sections

### QA Output
- Answers to standard questions in JSON format
- Easy to integrate with other applications