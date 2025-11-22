Aadhaar OCR & AI-Powered Identity Verification API
Deep Learning (ResNet-18) + EasyOCR + Flask API
This project provides a complete Aadhaar Verification System using:

Deep Learning (ResNet-18) to classify Aadhaar as
➤ Real Aadhaar
➤ Fake Aadhaar
EasyOCR to extract text from Aadhaar images
Flask REST API for backend integration
Optional lookup of Aadhaar numbers using a local CSV database
Optional image serving via /get_image
This is the same system you built in Google Colab and exported into Python.

🚀 Features
✅ 1. Fake/Real Aadhaar Classification
A pre-trained ResNet-18 binary classifier (aadhar_resnet_model.pth) identifies whether an Aadhaar card is genuine.

✅ 2. OCR Extraction using EasyOCR
Extracts:
Name
Aadhaar number
Address
DOB
Other details present on card

✅ 3. Flask REST API
With the following endpoints:
🔹 GET /
{"message": "Aadhaar Verification API is running!"}
🔹 POST /predict
Uploads an Aadhaar image → Returns:
Real / Fake prediction
Extracted text via OCR
Request
Content-Type: multipart/form-data
file = <aadhaar-image>

{
  "filename": "1.jpg",
  "Aadhaar_Status": "Real Aadhaar",
  "Extracted_Text": "GOVERNMENT OF INDIA 1234 5678 9012 ..."
}

ET /get_image?image_id=ID
Returns Aadhaar image from a folder (local dataset).
If CSV contains Aadhaar number for that image_id, it is sent in response headers.
Response Headers Example
aadhaar_number: 123456789012

🧠 Model Details
Architecture:
ResNet-18
Modified final layer with:
model.fc = nn.Linear(model.fc.in_features, 2)
→ Class 0 = Real
→ Class 1 = Fake
Preprocessing for inference:
Resize 224×224
ToTensor
Normalize with ImageNet stats

Health ceck
Response:
🔍 OCR Extraction Pipeline
Uses EasyOCR (English reader)

📌 Future Improvements
Face/Photo matching
Aadhaar number masking
Address field extraction parser
Frontend for uploading & viewing results
Deploy via Docker

💡 Credits
PyTorch for deep learning
EasyOCR for text recognition
Flask for API


Run reader.readtext()

All detected text lines are concatenated
