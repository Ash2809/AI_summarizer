# Medical Report Analyzer
## Overview

The **Medical Report Analyzer** is a Python-based workflow that processes images of medical reports to extract, summarize, and analyze the contents. The application leverages Optical Character Recognition (OCR) and Large Language Models (LLMs) to provide key insights, including anomaly detection and root cause analysis, and can also translate the summaries into different languages.

This project includes three key components:
1. **bot.py**: Contains the core logic for processing medical reports using OCR, generating summaries, detecting anomalies, and identifying root causes.
2. **workflow.py**: Defines the workflow that connects the various processing stages into a coherent pipeline.
3. **app.py**: Provides a Streamlit web interface where users can upload medical reports and see the results after analysis.
4. **requirements.txt**: Specifies the required libraries and dependencies for the project.

## Features

- **OCR Processing**: Extracts text from medical report images using EasyOCR.
- **Text Summarization**: Summarizes the extracted medical report using the Google Generative AI (Gemini model).
- **Anomaly Detection**: Identifies whether the medical report contains abnormal values.
- **Root Cause Analysis**: Determines the root cause based on detected anomalies.
- **Translation**: Provides translation of the medical report summary into other languages (e.g., Telugu).
- **Web Interface**: Uses Streamlit to provide a user-friendly interface for uploading and analyzing medical reports.

## Files

### `bot.py`
This file contains the following functions:
1. **ocr**: Extracts text from a medical report image.
2. **report**: Corrects grammatical errors in the extracted text without adding extra content.
3. **generate_summary**: Generates a concise summary of the medical report.
4. **Translate_Summary**: Translates the English summary into another language (default: Telugu).
5. **anamoly_detection**: Detects whether the report contains abnormal values.
6. **value_extractor**: Extracts specific abnormal values from the report.
7. **root_cause**: Identifies the root cause of the abnormal values.

### `workflow.py`
This file defines the state graph workflow using **LangGraph**. It connects the various stages of the report processing pipeline:
- The workflow starts with OCR, followed by report correction, summary generation, translation, anomaly detection, and root cause analysis.
- Conditional edges are used to decide whether to continue with anomaly detection or to skip straight to root cause analysis.

### `app.py`
The Streamlit application provides a user interface where users can upload medical reports (in image format). The uploaded image is processed through the workflow, and the outputs (summary, anomalies, root cause) are displayed.

### `requirements.txt`
Lists the dependencies required for the project, including:
- **langchain**: For working with LLMs and building workflows.
- **langchain_google_genai**: Google Generative AI integration.
- **easyocr**: For OCR text extraction.
- **streamlit**: For building the web interface.
- **torch**: Required for EasyOCR.

## Installation

1. **Clone the repository**:
   ```bash
   git clone <https://github.com/Ash2809/AI_summarizer>
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**:
   Create a `.env` file and set your Google API key:
   ```
   GOOGLE_API_KEY=your-google-api-key
   ```

## Running the Application

To run the Streamlit web app:
```bash
streamlit run src/app.py
```

## Usage

1. Upload a medical report image in formats such as `jpg`, `jpeg`, `png`, or `pdf`.
2. The app will process the image through the OCR and LLM workflow to provide the following outputs:
   - A grammatically corrected version of the report.
   - A summary of the report.
   - Detection of any anomalies in the report.
   - A translation of the summary into a different language (default: Telugu).
   - The root cause analysis based on abnormal values.

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request for any improvements.

Enjoy analyzing medical reports with ease using this streamlined and AI-powered tool!
