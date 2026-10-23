# EasyOCR — Image to Text Recognition

## 📌 Project Overview

This project is a simple Optical Character Recognition (OCR) application built using **EasyOCR and Python**. It extracts text from images and displays the recognized text along with confidence scores.

The project is implemented in Google Colab, making it easy to run without setting up a local Python environment.

## 🎯 Objectives

- Extract text from images automatically.
- Understand the basic working of OCR technology.
- Detect text regions and recognize characters using deep learning.
- Display extracted text with confidence scores.
- Save the recognized text into a `.txt` file.

## 🚀 Features

- **Image Upload:** Upload images directly from your computer.
- **Text Recognition:** Extract printed text from images.
- **Confidence Scores:** View the model's confidence for recognized text.
- **Text Export:** Save extracted text as a downloadable text file.
- **Text Detection Visualization:** Optionally visualize detected text regions using bounding boxes.

## 🛠️ Technologies Used

- Python
- EasyOCR
- PyTorch (used by EasyOCR)
- OpenCV (optional, for visualization)
- Matplotlib (optional, for visualization)
- Google Colab

## ⚙️ How It Works

The application follows these steps:

1. **Image Input:** The user uploads an image containing text.
2. **Text Detection:** The model identifies text regions in the image.
3. **Text Recognition:** The model recognizes characters and words within those regions.
4. **Output Generation:** The recognized text and confidence scores are displayed.
5. **Text Export:** The extracted text can be saved to a text file.

## 📂 Project Structure

```text
EasyOCR-Project/
│
├── EasyOCR_Project.ipynb   # Main Google Colab notebook
├── README.md               # Project documentation
└── extracted_text.txt      # Example OCR output (optional)
```

## 💻 Getting Started

### Option 1: Run in Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Upload or open the project notebook.
3. Install EasyOCR:

   ```python
   !pip install easyocr
   ```

4. Import the required libraries:

   ```python
   import easyocr
   from google.colab import files
   ```

5. Initialize the English OCR reader:

   ```python
   reader = easyocr.Reader(['en'], gpu=False)
   ```

6. Upload an image:

   ```python
   uploaded = files.upload()
   image_path = next(iter(uploaded))
   ```

7. Extract the text:

   ```python
   results = reader.readtext(image_path)

   for bbox, text, confidence in results:
       print("Text:", text)
       print("Confidence:", f"{confidence:.2%}")
   ```

### Option 2: Run Locally

Install EasyOCR:

```bash
pip install easyocr
```

Then use the following Python code:

```python
import easyocr

reader = easyocr.Reader(['en'], gpu=False)

image_path = "sample.png"
results = reader.readtext(image_path)

for bbox, text, confidence in results:
    print(f"Text: {text}")
    print(f"Confidence: {confidence:.2%}")
```

Replace `sample.png` with the path to your image.

## 📊 Sample Output

```text
OCR Results:

Text: Machine Learning
Confidence: 98.50%
----------------------------------------
Text: Deep Learning
Confidence: 96.20%
----------------------------------------
```

*Note: This is an illustrative example. Actual results depend on the input image and model predictions.*

## 📤 Export Extracted Text

The recognized text can be saved to a text file:

```python
texts = reader.readtext(image_path, detail=0)
extracted_text = "\n".join(texts)

with open("extracted_text.txt", "w", encoding="utf-8") as file:
    file.write(extracted_text)
```

## ⚠️ Limitations

- Accuracy may decrease with blurry or low-resolution images.
- Handwritten text may not be recognized reliably.
- Complex backgrounds and unusual fonts can affect recognition.
- The default configuration is intended for English text.
- The pretrained EasyOCR models are used; this project does not train a custom OCR model.

## 🔮 Future Improvements

- Train a custom OCR model from scratch.
- Improve image preprocessing for noisy and blurry images.
- Add support for multiple languages.
- Develop a web interface for image uploads and text extraction.
- Add PDF input and batch image processing.
- Evaluate OCR performance using character error rate (CER) and word error rate (WER).

## 📚 Learning Outcomes

Through this project, I explored:

- The fundamentals of Optical Character Recognition.
- Text detection versus text recognition.
- Using pretrained deep-learning models with Python.
- Image processing and OCR confidence scores.
- Exporting model predictions into text files.

