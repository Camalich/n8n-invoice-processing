\# n8n Invoice Processing Automation



Production-ready n8n workflow for automated invoice ingestion, classification, extraction, normalization, and logging using Google Drive, LLMs, and Google Sheets.



\## Overview

\## Workflow Overview

![Workflow overview](screenshots/workflow-overview.png)



This workflow automatically processes invoices uploaded to a Google Drive folder.  

It supports \*\*native PDFs\*\* and \*\*scanned PDFs/images\*\*, applies the correct extraction strategy, normalizes the data, validates results, and logs outcomes.



Designed with:

\- Clear branching logic

\- Deterministic parsing

\- Defensive normalization

\- Audit-friendly outputs



\## Workflow Architecture



1\. \*\*Google Drive Trigger\*\*

&nbsp;  - Watches a specific folder for new files



2\. \*\*File Download\*\*

&nbsp;  - Retrieves the uploaded document



3\. \*\*PDF vs Image Detection\*\*

&nbsp;  - Identifies whether the file is a PDF or image



4\. \*\*Native vs Scanned PDF Detection\*\*

&nbsp;  - Uses text density heuristics to classify PDFs



5\. \*\*Data Extraction\*\*

&nbsp;  - Native PDFs → Text extraction + OpenAI

&nbsp;  - Scanned PDFs / Images → Vision model (Gemini)



6\. \*\*LLM Output Parsing\*\*

&nbsp;  - Strict JSON extraction

&nbsp;  - Model-agnostic defensive parsing



7\. \*\*Normalization \& Validation\*\*

&nbsp;  - Date normalization (multiple formats)

&nbsp;  - Currency normalization

&nbsp;  - Numeric coercion

&nbsp;  - Validation contract (`is\_valid`)



8\. \*\*Google Sheets Logging\*\*

&nbsp;  - Clean invoices → main sheet

&nbsp;  - Invalid invoices → error sheet (optional extension)



\## Extracted Fields



\- Date

\- Invoice Number

\- Vendor

\- Tax ID

\- Subtotal

\- Tax

\- Total

\- Currency

\- Description



All fields are \*\*null-safe\*\*. No inference or guessing.



\## Key Design Decisions



\- No brittle regex-based extraction

\- LLMs constrained to strict JSON output

\- Explicit normalization layer

\- Separation between extraction, parsing, and validation

\- Credential-free export for safe sharing



\## Requirements



\- n8n v2+

\- Google Drive credentials

\- Google Sheets credentials

\- OpenAI API key

\- (Optional) Google Gemini API key for image invoices



\## Setup Instructions



1\. Import the JSON workflow into n8n

2\. Create credentials for:

&nbsp;  - Google Drive

&nbsp;  - Google Sheets

&nbsp;  - OpenAI

&nbsp;  - Gemini (optional)

3\. Replace placeholder IDs:

&nbsp;  - Google Drive folder ID

&nbsp;  - Google Sheets document ID

4\. Activate the workflow

5\. Upload an invoice to the watched folder



\## Use Cases



\- Accounting automation

\- Expense tracking

\- Invoice digitization

\- Finance ops workflows

\- AI-assisted document processing



\## Notes



This repository intentionally excludes credentials and cached metadata.  

All sensitive values must be configured manually after import.



---



\*\*Author:\*\*  

Automation \& AI Workflow Engineer  

Specialized in n8n, LLM pipelines, and document automation



