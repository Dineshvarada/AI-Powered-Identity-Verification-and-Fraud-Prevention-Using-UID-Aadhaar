# AI-Powered-Identity-Verification-and-Fraud-Prevention-Using-UID-Aadhaar

# Aadhaar OCR & Identity Verification

**Project:** Aadhaar OCR + Identity Verification & Fraud Detection 
## Overview
This repository provides:
- OCR extraction of Aadhaar card fields using Tesseract (pluggable OCR backends).
- Fraud / tamper detection model (CNN) to flag tampered Aadhaar cards.
- A lightweight API (Flask) for server-side integration and an optional Streamlit demo UI.
- Secure defaults: Aadhaar numbers are masked and raw PII storage is disabled by default.

> ⚠️ This project processes highly sensitive personal data (Aadhaar). Read `SECURITY.md` before running or publishing.

## Features
- Upload Aadhaar image → OCR extraction (name, Aadhaar number, DOB, address block)
- Tamper detection (CNN model) with a confidence score
- Masking of Aadhaar numbers in responses
- Configurable OCR engine (`TESSERACT`, `GOOGLE_VISION`, `AWS_TEXTRACT`)
- Docker support for easy deployment

Files of interest
app.py — Flask API entry (uploads, OCR call, parsing, masking)
src/ocr_engine.py — wrapper for OCR backends
src/document_verification.py — CNN tamper detection
openapi.yaml — API schema
requirements.txt — dependencies
Dockerfile / docker-compose.yml

Model & dataset
Large model files and any datasets should not be committed. Use cloud storage (Google Drive link, S3). Example pattern:
Add models/README.md describing where to download pre-trained .h5 files.
Add script scripts/download_model.sh to fetch model into the right folder (gitignored).

Security & privacy
By default STORE_RAW=false (raw OCR text and images not persisted).
Aadhaar numbers masked in logs & responses (only last 4 digits shown).
Use TLS in production and store secrets in a secret manager.
See SECURITY.md.

google drive: "https://colab.research.google.com/drive/1k57c3DqBU1C9zEBegJXBLWLeoBIe4bPa?usp=drive_link"
