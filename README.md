# PDF File Manipulations

A Python project for manipulating and working with PDF files using PyPDF2 library.

## Project Overview
This project demonstrates various PDF manipulation capabilities including:
- Extracting text and information from PDFs
- Copying pages to create new PDFs
- Rotating PDF pages
- Reading multiple pages
- Adding watermarks to PDFs

## Technologies Used
- Python 3.x
- PyPDF2: Library for reading and manipulating PDF files

## Prerequisites
```bash
pip install PyPDF2
```

## Features

### 1. Extract Information from PDFs
- Read PDF metadata and document information
- Extract text content from specific pages
- Get total page count

### 2. PDF Page Operations
- Copy individual pages to new PDFs
- Rotate pages clockwise/counterclockwise
- Merge pages from different PDFs
- Read multiple pages sequentially

### 3. PDF Watermarking
- Add watermarks to PDF pages
- Support for batch watermarking multiple pages

## Usage Examples

### Reading PDF Information
```python
from PyPDF2 import PdfFileReader

# Open PDF file in binary mode
with open('input.pdf', 'rb') as f:
    # Create PDF reader object
    read_pdf = PdfFileReader(f)
    
    # Get document info
    doc_info = read_pdf.getDocumentInfo()
    
    # Get number of pages
    num_pages = read_pdf.numPages
```

### Extracting Text from a Page
```python
# Get text from specific page
page = read_pdf.getPage(0)
text = page.extractText()
```

### Rotating and Saving Pages
```python
from PyPDF2 import PdfFileWriter

write_pdf = PdfFileWriter()
rotated_page = read_pdf.getPage(0).rotateClockwise(90)
write_pdf.addPage(rotated_page)

with open('output.pdf', 'wb') as output:
    write_pdf.write(output)
```

### Adding Watermarks
```python
# Open watermark PDF
watermark = PdfFileReader(open('watermark.pdf', 'rb'))
watermark_page = watermark.getPage(0)

# Add watermark to all pages
for page in range(read_pdf.numPages):
    content_page = read_pdf.getPage(page)
    content_page.mergePage(watermark_page)
    write_pdf.addPage(content_page)
```

## Future Improvements
- Add support for PDF encryption/decryption
- Implement PDF form field manipulation
- Add PDF compression capabilities
- Create GUI interface for PDF operations
- Support for PDF annotations and comments

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request.