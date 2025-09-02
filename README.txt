# Comic Archive Processing Toolkit (C.A.P.T) - Archive Converter v1.0.0

## Overview

The Comic Archive Processing Toolkit (C.A.P.T) is a comprehensive Python-based application designed for converting and managing comic book archives. This specific module, the Archive Converter, provides a standalone GUI window for seamless conversion between different comic archive formats including CBR (RAR), CBZ (ZIP), and PDF.

The application features a modern PyQt6-based interface with real-time progress tracking, drag-and-drop support, and comprehensive error handling. It's designed as a completely independent window that can run standalone or be integrated into larger comic management workflows.

## Features

### Core Conversion Capabilities
- **CBR ↔ CBZ Conversion**: Convert between RAR-based (CBR) and ZIP-based (CBZ) comic archives
- **PDF ↔ CBZ Conversion**: Extract images from PDF files and create CBZ archives, or convert CBZ archives to PDF format
- **Batch Processing**: Convert multiple files simultaneously with individual progress tracking
- **Format Detection**: Automatic detection of archive formats (CBZ, CBR, PDF)

### User Interface
- **Standalone Window**: Completely independent GUI that doesn't require parent dependencies
- **File Management**: Intuitive file/folder selection with drag-and-drop support
- **Real-time Progress**: Live progress bars and status messages during conversion
- **Context Menus**: Right-click options for refreshing lists and removing files
- **Keyboard Shortcuts**: F5 for refresh, Delete key for removing selected files

### Advanced Features
- **Progress Tracking**: Per-file and overall progress with throttling to reduce UI updates
- **Error Handling**: Comprehensive error reporting and recovery mechanisms
- **Logging**: Detailed operation logs for troubleshooting and user feedback
- **Threading**: Background processing to keep the UI responsive during conversions
- **Archive Validation**: Built-in validation for comic archive integrity

## Requirements

### System Requirements
- Python 3.8 or higher
- Windows/Linux/macOS (cross-platform support)

### Python Dependencies
- PyQt6: For the graphical user interface
- PyMuPDF (fitz): For PDF processing
- rarfile: For RAR archive handling
- Pillow (PIL): For image processing
- pathlib: For path handling (built-in)
- logging: For logging functionality (built-in)
- subprocess: For external tool execution (built-in)
- zipfile: For ZIP archive handling (built-in)

### External Tools
- Rarfile or rar command-line tool (for CBR creation on Windows)
- The application will attempt to use system-installed RAR tools for CBR creation

## Installation

1. **Clone or Download** the project files to your local machine

2. **Install Python Dependencies**:
   ```bash
   pip install PyQt6 PyMuPDF rarfile Pillow
   ```

3. **Ensure External Tools**:
   - For CBR creation, install Rarfile (Windows) or rar package
   - The application will check for these tools automatically

4. **Run the Application**:
   ```bash
   python main.py
   ```

## Usage

### Basic Operation

1. **Launch the Application**:
   - Run `python main.py` to open the Archive Converter window

2. **Add Files**:
   - Click "Add Folder" to select an entire directory of comic archives
   - Click "Add File(s)" to select individual files
   - Drag and drop files/folders directly onto the file list
   - Supported formats: .cbz, .cbr, .pdf

3. **Select Conversion Format**:
   - Choose from the radio buttons:
     - CBR → CBZ
     - CBZ → CBR
     - PDF → CBZ
     - CBZ → PDF

4. **Configure Options**:
   - Check "Delete Original Files" to remove source files after successful conversion

5. **Start Conversion**:
   - Click the "Convert" button to begin processing
   - Monitor progress in real-time through the progress bar and status messages

### Advanced Usage

#### Keyboard Shortcuts
- **F5**: Refresh the file list
- **Delete**: Remove selected files from the list

#### Context Menu
- Right-click on files in the list for additional options:
  - Refresh List
  - Remove Selected

#### Progress Monitoring
- Individual file progress (0-100% per file)
- Overall batch progress
- Detailed status messages for each operation step

## Project Structure

```
C.A.P.T._v2.3_files/
├── main.py                    # Main application entry point and GUI window
├── requirements.txt           # Python dependencies
├── requirements.md            # Detailed requirements documentation
├── logs/                      # Log files directory
│   └── convert_window_operations.log
├── widgets/                   # GUI widget components
│   ├── file_mgnt.py          # File management widget
│   └── prgrs_wdgt.py         # Progress tracking widget
├── utils/                     # Utility modules
│   ├── logger.py             # Centralized logging system
│   ├── arc_convert_util.py   # Archive format detection and validation
│   └── arc_conv_helpers.py   # Archive extraction and creation helpers
└── processors/                # Conversion processing modules
    ├── arc_convert_worker.py  # Background worker for conversions
    ├── arc_conv_pdf_proc.py   # PDF ↔ CBZ conversion processor
    └── arc_conv_cb_proc.py    # CBR ↔ CBZ conversion processor
```

## Architecture

### Core Components

#### Main Window (main.py)
- `ConvertWindow` class: Main GUI window managing the conversion interface
- Handles user interactions, signal connections, and conversion initiation
- Manages the worker thread for background processing

#### Widget System
- `FileManagementWidget`: Handles file selection, display, and management
- `ProgressWidget`: Displays progress bars and status messages
- Both widgets are reusable across different GUI windows

#### Processing Pipeline
- `ConversionWorker`: Qt thread worker for background processing
- `PdfArchiveConverter`: Handles PDF-related conversions
- `ArchiveArchiveConverter`: Handles CBR/CBZ conversions
- Uses helper functions for archive operations

#### Utility Layer
- `ArchiveConverter`: Core conversion and validation logic
- Logging system with operation-specific log files
- Helper functions for archive manipulation

### Threading Model
- Main thread handles GUI updates
- Worker thread performs file processing
- Signals/slots mechanism for thread-safe communication
- Progress throttling to prevent UI freezing

## Error Handling

The application includes comprehensive error handling:

- **File Validation**: Checks file existence and format compatibility
- **Archive Integrity**: Validates archive contents before processing
- **Conversion Errors**: Graceful handling of conversion failures
- **Logging**: Detailed error logs for troubleshooting
- **User Feedback**: Clear error messages in the GUI

## Logging

The application maintains detailed logs in the `logs/` directory:

- `convert_window_operations.log`: Main conversion operations
- `comic_toolkit_main.log`: General application logging
- Logs include timestamps, operation details, and error information

## Development Notes

### Code Style
- Comprehensive docstrings following Google style
- Type hints for better code maintainability
- Modular design with clear separation of concerns
- Error handling with custom exceptions

### Extensibility
- Widget-based architecture allows easy addition of new features
- Processor classes can be extended for new conversion types
- Logging system supports additional operation types

## Troubleshooting

### Common Issues

1. **RAR Tool Not Found**:
   - Install Rarfile or rar command-line tool
   - Ensure it's in your system PATH

2. **PDF Processing Errors**:
   - Ensure PyMuPDF is properly installed
   - Check PDF file integrity

3. **Permission Errors**:
   - Ensure write permissions in target directories
   - Close files if they're open in other applications

4. **Memory Issues**:
   - Large PDFs may require significant memory
   - Process files in smaller batches if needed

### Log Analysis
- Check `logs/convert_window_operations.log` for detailed error information
- Look for specific error messages and stack traces

## Version History

- **v1.0.0**: Current version with enhanced PDF support and improved UI
- **v1.0.0**: Previous version with logging improvements

## License

This project is licensed under the GNU General Public License v3.0 (GPLv3). 

You are free to use, modify, and distribute this software under the terms of the GPL v3.0 license. However, any derivative works must also be licensed under GPL v3.0, and you must include the original copyright notice and license text.

For the full license text, see the [LICENSE](LICENSE) file in this repository or visit: https://www.gnu.org/licenses/gpl-3.0.html

If you have questions about the license or need clarification, refer to the GNU GPL FAQ at: https://www.gnu.org/licenses/gpl-3.0.en.html

## Contact

For support, bug reports, or feature requests, please refer to the main project repository or contact the development team.

---

*This README was generated based on the application's docstrings and code documentation. For the most up-to-date information, refer to the inline documentation within the source code.*
