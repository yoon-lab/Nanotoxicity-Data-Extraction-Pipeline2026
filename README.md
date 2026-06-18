# Nanotoxicity-Data-Extraction-Pipeline2026
LLM-assisted pipeline for extracting nanomaterial composition, physicochemical properties, and toxicity assay data from Zotero-hosted scientific PDFs.

## Overview
This repository provides a Jupyter Notebook-based workflow for automated nanotoxicity data extraction from scientific articles stored in a Zotero collection.

The pipeline is designed to support research on nanomaterial toxicity by extracting structured information from PDF articles, including nanomaterial composition, physicochemical properties, experimental conditions, assay information, and toxicity-related outcomes. It uses Zotero for literature management and large language models (LLMs) for structured information extraction from research papers.

## Key Features

- **Zotero-Based PDF Collection Handling**
  - Connects to a Zotero user or group library using the Zotero API.
  - Retrieves PDF attachments from a selected Zotero collection.
  - Organizes article metadata and PDF files for downstream processing.

- **Automated Nanotoxicity Data Extraction**
  - Uses LLM-based extraction to identify nanotoxicity-related information from scientific PDFs.
  - Extracts structured information such as nanomaterial composition, physicochemical properties, biological model, exposure conditions, assay type, and toxicity outcomes.

- **Stepwise Notebook Workflow**
  - Provides a sequential workflow from API configuration to PDF retrieval, text/image processing, LLM-based extraction, and result export.
  - Includes clearly labeled steps for easier execution, review, and modification.

- **Structured Output Generation**
  - Converts extracted information into structured tabular outputs.
  - Supports downstream review, cleaning, and analysis of extracted nanotoxicity data.
  - Saves extracted records, source-provenance information, event logs, runtime logs, and merged output files for traceability and reruns.

## File Structure

This repository contains the main Jupyter Notebook for the nanotoxicity data extraction pipeline.

- **script_extraction.ipynb**  
  Implements the complete workflow for extracting nanotoxicity-related data from Zotero-hosted scientific PDFs using an LLM-assisted pipeline.

The notebook covers the following steps:

1. **Environment and API Configuration**  
   Set up required libraries, Zotero credentials, OpenAI API key, and project-specific configuration.

2. **Zotero Collection Access**  
   Connect to the Zotero library and select the target collection containing PDF articles.

3. **PDF Retrieval and Organization**  
   Download or organize PDF attachments from the selected Zotero collection.

4. **PDF Processing**  
   Prepare PDF contents for extraction, including text and/or image-based processing when needed.

5. **Prompt and Extraction Schema Setup**  
   Define extraction prompts and structured output fields for nanotoxicity-related information.

6. **LLM-Based Data Extraction**  
   Apply the LLM-assisted extraction workflow to retrieve structured information from each article.

7. **Result Parsing and Formatting**  
   Parse model responses and convert extracted information into structured records.

8. **Data Export**  
   Save the extracted nanotoxicity data into output files for review and downstream analysis.

9. **Post-Processing**  
   Provide additional formatting.

## How to Run

1. **Environment Setup**
   - Install Python 3.10 or higher.
   - Install Jupyter Notebook or JupyterLab.
   - Install the required Python packages used in the notebook.
   - Recommended installation command: pip install jupyter pandas numpy openpyxl pyzotero openai PyMuPDF pytz pdf2image Pillow opencv-python layoutparser torch torchvision
   - The figure/table detection step uses LayoutParser with a PubLayNet Mask R-CNN model.

2. **Prepare the Zotero Library**
   - Create or select a Zotero collection containing the target scientific articles.
   - Make sure the articles have PDF attachments available in the Zotero library.
   - Prepare the Zotero library ID, Zotero API key, and target collection name or collection key.

3. **Configure API Keys**
   - Open `script_extraction.ipynb`.
   - Fill in the required configuration fields, including:
     - Zotero user ID or group library ID
     - Zotero API key
     - OpenAI API key
     - Target Zotero collection
     - Project name or output folder name
   - Required user configuration fields include:
     - selected_collection: exact Zotero collection name to process
     - project_name: short project label used in output folders
     - ZOTERO_USER_ID: Zotero user ID or group library ID
     - ZOTERO_API: Zotero API key with access to the target library and PDF attachments
     - OPENAI_API_KEY: OpenAI API key for LLM calls
     - CHAT_MODEL_NAME: LLM model ID
     - CHAT_TEMPERATURE: LLM temperature setting 

4. **Run the Notebook**
   - Open the notebook in Jupyter Notebook or JupyterLab.
   - Execute the cells sequentially from top to bottom.
   - Check intermediate outputs to confirm that Zotero access, PDF retrieval, and LLM extraction are working correctly.

## Outputs

The notebook saves batch-level and merged outputs under an automatically generated output folder:

../output/<selected_collection>_<project_name>_<timestamp>/

**Main outputs include:**
- extracted material records
- extracted physicochemical records
- extracted toxicological records
- PChem and Tox claim tables with source provenance
- event logs for API calls, errors, source pages, captions, and image inputs
- runtime and timing logs
- manifest files for reruns
- merged Excel output files for downstream review and analysis

## Citation

The code in this repository is based on the following paper:
> **Preparing...**
