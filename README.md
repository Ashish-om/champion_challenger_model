
# Champion-Challenger AI Document Processing Pipeline

## Overview
This project implements a document processing pipeline that extracts relevant information from PDF files using a Champion Model and evaluates the extracted information using a Challenger Model. The goal is to iteratively refine the extracted information until it meets a high accuracy and relevance standard.

## Features
- **Champion Model**: Uses `facebook/bart-large-cnn`, a summarization model, to extract key information from text.
- **Challenger Model**: Uses `MoritzLaurer/deberta-v3-base-zeroshot-v1` to evaluate the extracted information and provide feedback.
- **Iterative Refinement**: The system iterates up to three times to improve extracted information based on the Challenger Model's feedback.
- **Handles Large PDFs**: Splits large text into overlapping chunks for better processing.
- **Runs on CPU or GPU**: Automatically detects available hardware for optimal performance.

## Installation
To install the required dependencies, run the following command:
```sh
pip install pdfplumber transformers torch
```

## Usage
### Step 1: Set the PDF File Path
Modify the `pdf_path` variable to point to the PDF you want to process.
```python
pdf_path = "/path/to/your/pdf.pdf"
```

### Step 2: Run the Pipeline
Execute the script to process the PDF:
```sh
python script.py
```

### Step 3: Review the Output
The final extracted and refined information will be printed in the console.

## Workflow
1. Extract text from the PDF using `pdfplumber`.
2. Split text into chunks for better processing.
3. **Champion Model** extracts key information.
4. **Challenger Model** evaluates the output and provides feedback.
5. If necessary, refine the extracted information based on feedback.
6. Stop iterations when a high accuracy rating is achieved or max iterations are reached.

## Customization
- Modify `max_iterations` in `champion_challenger_pipeline` to adjust refinement attempts.
- Change the `max_length` and `min_length` parameters in the Champion Model for summary length tuning.
- Update the `labels` in the Challenger Model for different evaluation criteria.

## License
This project is open-source and free to use for research and development purposes.
