# Comic Archive Converter Requirements

This document lists the main Python package dependencies required to run the Comic Archive Converter application. These packages are detected from imports across all source files in the project.

## Required Packages

| Package      | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| PyQt6        | Python bindings for the Qt application framework (GUI components).          |
| rarfile      | Python library for handling RAR archive files.                              |
| PyMuPDF      | Converts PDF files to images using Python.                                  |
| Pillow (PIL) | Python Imaging Library for image processing.                                |

## Installation

You can install all required packages using pip:

```bash
pip install PyQt6 rarfile PyMuPDF Pillow
```

## Notes
- Some files also use standard library modules (e.g., sys, os, pathlib, zipfile, tempfile, logging, shutil, re, math, threading, datetime, typing), which do not require installation.
- If you use features from these packages that require additional system dependencies, refer to their documentation for setup instructions.

---
This requirements list is generated from all Python files in the project as of August 31, 2025.
