# ID Card Scanner Application

## Overview

The **ID Card Scanner Application** is a secure desktop tool that uses Optical Character Recognition (OCR) to extract and manage key information from physical ID cards. Users can scan cards from image files or a webcam feed. Extracted data—including school and student names—is stored in a local SQLite database, with an authentication system to ensure data security.

---

## Features

- 🔐 **User Authentication**  
  Secure login and registration with password hashing using `bcrypt`.

- 🖼️ **Scan from Image**  
  Upload existing card images (PNG, JPG, BMP, etc.) for OCR extraction.

- 📷 **Scan from Camera**  
  Use a webcam to capture ID cards. Guided cropping ensures accurate results.

- 🧠 **Smart OCR**  
  Tesseract OCR with preprocessing:
  - Grayscale, deskew, upscale
  - Binarization, noise reduction
  - Defined Regions of Interest (ROI) for accurate field extraction:
    - School Name (top)
    - Student Name (bottom-left)

- 💾 **Local Database**  
  Stores extracted data and images in an SQLite database.

- 🗂️ **Card Viewer**  
  Browse saved entries with extracted info and card thumbnails.

- 🧪 **Debug Tools**  
  Saves image processing stages for OCR accuracy tuning.

---

## Installation

### 1. Install Python 3.x  
Download from [python.org](https://www.python.org/). Add Python to PATH during setup.

### 2. Install Tesseract OCR

#### Windows
- Download from: [https://github.com/tesseract-ocr/tesseract](https://github.com/tesseract-ocr/tesseract)
- Enable “Add to PATH” during installation.
- Update your Python script:
  ```python
  pytesseract.pytesseract.tesseract_cmd = r"C:\Path\To\Tesseract-OCR\tesseract.exe"
macOS
bash
Copy
Edit
brew install tesseract
Linux
bash
Copy
Edit
sudo apt update && sudo apt install tesseract-ocr
3. Install Required Python Packages
bash
Copy
Edit
pip install opencv-python pillow pytesseract bcrypt numpy
Usage
1. Run the App
bash
Copy
Edit
python your_main_script.py
2. Login or Register
Register: New users can create an account.

Login: Enter credentials to access the main app.

3. Application Functions
Scan from Image: Choose an image file of an ID card to extract data.

Scan from Camera: Select and use a webcam to capture and scan an ID card.

View Saved Cards: Displays stored card data and thumbnails.

Delete Records: Remove any saved card and its associated image.

Project Structure
graphql
Copy
Edit
.
├── data/
│   ├── users.db             # SQLite DB for users and cards
│   ├── card_images/         # Saved ID card images
│   └── debug_images/        # Intermediate OCR debug images
└── your_main_script.py      # Main application script
Technologies Used
Python 3.x

Tkinter – GUI

OpenCV – Camera + Image Processing

Pillow (PIL) – Image Handling

PyTesseract – OCR

bcrypt – Password Hashing

SQLite3 – Local DB

NumPy – Image Array Operations

UUID, OS, Shutil – Utilities

Troubleshooting
Issue	Solution
Tesseract not found	Ensure it’s installed and added to PATH. Update tesseract_cmd.
table cards has no column named ...	Delete users.db and restart to rebuild DB with the correct schema.
Cannot open camera	Check device connection, OS permissions, and app conflicts.
Poor OCR results	Review saved images in data/debug_images/ and adjust ROI parameters in code.

Future Improvements
Enhanced OCR robustness

Additional fields (ID number, expiry, etc.)

Search, sort, and filter saved records

Export to CSV/PDF

Config file for custom settings

Full cross-platform support

License
This project is licensed under the MIT License. See the LICENSE file for details.
