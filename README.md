ID Card Scanner Application


Overview

The ID Card Scanner Application is a secure desktop tool that uses 
Optical Character Recognition (OCR) to extract and manage information 
from physical ID cards. Users can scan from image files or webcams. 
Extracted data - such as school and student names - is stored locally 
in an SQLite database. A secure login system is included.


Features


• User Authentication:
  - Secure login and registration with bcrypt password hashing.

• Scan from Image File:
  - Upload an image (PNG, JPG, JPEG, BMP, GIF) of an ID card for OCR.

• Scan from Camera:
  - Use a webcam to capture ID cards in real-time.
  - Includes a guided crop box and support for multiple webcams.

• Smart OCR Extraction:
  - Tesseract OCR with preprocessing (grayscale, deskewing, upscaling,
    binarization, and noise reduction).
  - Extracts:
      • School Name (top section of the ID)
      • Student Name (bottom-left section of the ID)

• Local Data Storage:
  - Stores extracted info and image paths in an SQLite database.

• Card Management:
  - View saved records with thumbnails.
  - Delete individual cards from both the database and file storage.

• Debug Image Generation:
  - Saves intermediate images for OCR tuning and troubleshooting.


Installation Instructions


1. Install Python 3.x
   - Download from: https://www.python.org/
   - During setup, check “Add Python to PATH”.

2. Install Tesseract OCR

   • Windows:
     - Download from: https://github.com/tesseract-ocr/tesseract
     - Enable “Add to PATH” during installation.
     - In your script, set:
       pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe"

   • macOS:
     brew install tesseract

   • Linux (Debian/Ubuntu):
     sudo apt update && sudo apt install tesseract-ocr

3. Install Python Packages
   pip install opencv-python pillow pytesseract bcrypt numpy


Usage


1. Run the App:
   python your_main_script.py

2. Login or Register:
   - New users: enter a username and password to register.
   - Returning users: log in using existing credentials.

3. Main Menu Options:

   • Scan from Image File:
     - Upload an image of an ID card.
     - Extracted data is stored automatically.

   • Scan from Camera:
     - Select an available webcam.
     - Align the ID card in the red dashed crop box.
     - Press 'S' or click Capture to extract and save the data.

   • View Saved Cards:
     - Displays all records with thumbnails.
     - Each record has a delete button.


Technologies Used


• Python 3.x                  → Programming language
• Tkinter                     → GUI framework
• Pillow (PIL)                → Image processing
• OpenCV                      → Webcam & image operations
• PyTesseract                 → OCR processing
• Bcrypt                      → Password hashing
• SQLite3                     → Local database
• NumPy                       → Numerical operations
• uuid, os, shutil, re        → Utility modules


Troubleshooting


• "Tesseract not found":
  - Ensure it's installed and in system PATH.
  - Update `tesseract_cmd` in your script if needed.

• "table cards has no column named ...":
  - Delete `users.db` and restart the app. It will auto-create a new schema.

• "Cannot open camera":
  - Ensure webcam is connected and not used by another app.
  - Check privacy settings on Windows/macOS.

• Poor OCR Results:
  - Check debug images in `data/debug_images/`
  - Adjust ROI values or preprocessing steps as needed.


Future Improvements


• Improve OCR under various lighting/fonts.
• Extract additional fields (ID number, expiry date, etc.).
• Add search, filter, and sort features in the card viewer.
• Export data to CSV or PDF formats.
• External config file for app settings.
• Better cross-platform support for macOS and Linux.


License


This project is licensed under the MIT License.
See the LICENSE file for more information.


