# Form and PDF Automation Project :computer:

This repository contains code and resources for a project aimed at automating the completion of forms, PDFs and others documents. The goal of this project is to streamline the process of filling out forms and PDFs, reducing manual effort and increasing efficiency.

## Features :clipboard:
- **Automated Form Filling**: This feature allows for automatic filling of web and digital forms based on predefined user information.
- **PDF Completion**: This feature enables automatic filling of PDF forms, with support for various types of form fields including text, checkboxes, and dropdowns.
- **Data Extraction**: Extract data from filled forms and PDFs for further processing or analysis.
- **Support for Various Form Formats**: The project aims to support various form formats including but not limited to HTML, XML, and PDF.

## Technologies Used :floppy_disk:
- Python for scripting and automation
- Libraries such as PyPDF2 and pdfrw for PDF processing
- Selenium WebDriver for automating web-based form filling

## Contribution :pencil2:

To contribute to this repository follow our [Contributing
Guide](https://github.com/ai-cfia/.github/blob/main/profile/CONTRIBUTING.md)
rules and norms.

## Template propose by Louis

To eventually kick start the project, we ask Louis to give us a template.

```python
from PyPDF2 import PdfFileReader, PdfFileWriter

def print_field_names(pdf_path):
    pdf = PdfFileReader(pdf_path)
    fields = pdf.getFields()
    print("PDF Field Names:")
    for field in fields:
        print(f"{field}: {fields[field]['/T']}")

def fill_pdf(input_pdf_path, output_pdf_path, data_dict):
    pdf_reader = PdfFileReader(input_pdf_path)
    pdf_writer = PdfFileWriter()

    # Clone the original PDF
    pdf_writer.cloneDocumentFromReader(pdf_reader)

    # Get the fields from the PDF
    fields = pdf_writer.getFields()

    # Fill the fields with the data from data_dict
    for field_name, value in data_dict.items():
        if field_name in fields:
            fields[field_name].update({
                '/V': value
            })
    
    # Write the data to the output PDF
    with open(output_pdf_path, "wb") as output_pdf:
        pdf_writer.write(output_pdf)

# The path to your PDF file
input_pdf_path = '/mnt/data/your_input.pdf'

# The path where you want to save the new PDF
output_pdf_path = '/mnt/data/your_output.pdf'

# This is a dictionary where the key is the field name, and the value is what you want to populate
data_dict = {
    'FieldName1': 'Value1',
    'FieldName2': 'Value2',
    # Add more fields as necessary
}

# First, let's print out all the field names
print_field_names(input_pdf_path)

# Now let's fill the PDF
fill_pdf(input_pdf_path, output_pdf_path, data_dict)
```
