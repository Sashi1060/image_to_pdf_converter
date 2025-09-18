# 📄 Images to PDF Converter

## A simple and modern web tool to convert multiple images into a single, downloadable PDF document. Built with a beautiful Vanilla JS & Tailwind CSS front-end and a powerful FastAPI back-end.

**(Suggestion: Replace this placeholder with a real screenshot of your application!)**

##

# ✨ Features

## Multiple File Uploads: Select as many images as you need.

Drag & Drop Support: Intuitive drag-and-drop interface for uploading files.

Image Previews: See thumbnails of your selected images before conversion.

Easy Management: Remove individual images with a single click.

Custom PDF Settings:

Choose Page Size (A4, Letter, Legal).

Set Page Orientation (Portrait, Landscape).

Real-time Progress: A visual progress bar shows the status of the conversion.

Secure & Private: Images are processed in-memory on the server and are not stored.

Responsive Design: A clean and functional UI that works on all screen sizes.

##

# 🛠️ Tech Stack

This project is built with two main components:

Front-End:

HTML5

Tailwind CSS

Vanilla JavaScript (no frameworks)

Back-End:

Python 3

FastAPI: For the high-performance API.

Uvicorn: As the ASGI server.

Pillow: For robust in-memory image processing.

fpdf2: For generating the final PDF document.

## ⚙️ How It Works

The application follows a simple client-server architecture to process your files securely and efficiently.

Image Selection: The user selects image files via the "Browse" button or by dragging them onto the upload area.

Front-End Pre-processing: JavaScript's FileReader API is used to generate local, temporary URLs for each image, allowing for instant previews without uploading anything yet.

API Request: When the "Convert to PDF" button is clicked, the front-end constructs a FormData object. This object bundles all the image files and the selected PDF settings (page size, orientation).

Back-End Processing: A POST request is sent to the /convert/ endpoint on the FastAPI server.

The server receives the images as UploadFile objects.

It iterates through each file in-memory.

The Pillow library reads the image's properties (like dimensions) without ever saving it to the disk.

The fpdf2 library creates a PDF document, adds a new page for each image, and draws the image onto the page, automatically scaling it to fit perfectly.

PDF Download: Once all images are processed, the server sends the complete PDF back as a StreamingResponse with a media type of application/pdf. The front-end receives this response as a blob and triggers a download prompt in the user's browser.

## 🚀 Getting Started

Follow these instructions to get the project running on your local machine.

Prerequisites
Python 3.8+

An active internet connection (for the front-end CDN)

Installation & Setup
Clone the repository:

## git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)

cd your-repo-name

Set up the Back-End:

It's highly recommended to use a virtual environment.

python -m venv venv
source venv/bin/activate # On Windows, use `venv\Scripts\activate`

Install the required Python packages.

pip install "fastapi[all]" pillow fpdf2

Run the Application:

Start the back-end server:

uvicorn main:app --reload

The API will now be running at http://127.0.0.1:8000.

Start the front-end:
Simply open the index.html file in your web browser. Using a tool like the VS Code "Live Server" extension is recommended for the best experience.

Usage
Open index.html in your browser.

Drag and drop your images or use the "Browse Files" button.

Adjust the PDF settings (Page Size, Orientation) as needed.

Click "Convert to PDF".

Your browser will prompt you to save the generated PDF file.

## 🔮 Future Improvements

Allow reordering of images in the preview grid via drag-and-drop.

Add client-side image compression options (e.g., Low, Medium, High quality).

Implement a "preview PDF" option before downloading.

Add support for more file types (e.g., TIFF, HEIC).
