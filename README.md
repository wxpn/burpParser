# Burp Suite XML Scan Parser

## Overview
The Burp Suite XML Scan Parser is a command-line tool designed to parse, analyze, and display vulnerability scan results from Burp Suite Professional's XML export format. It provides an interactive interface for security professionals to review and analyze security findings in a structured and readable format.

## Features
- Interactive CLI interface for viewing and managing findings
- Detailed vulnerability information display
- HTTP request/response message viewing
- Finding modification and deletion capabilities
- Export findings to formatted Word documents
- Color-coded severity indicators
- Grouped vulnerability display
- Base64 decoding of HTTP messages

## Installation

### Prerequisites
- Python 3.7 or higher
- pip package manager

### Setup
1. Create a virtual environment:
```bash
# Windows
python -m venv venv
.\venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

## Usage

### Basic Usage
```bash
python parser.py path/to/burp_export.xml
```

### Main Menu Options
- `1-N`: View detailed information for a specific finding number
- `d`: Delete one or multiple findings
- `m`: Modify a finding
- `s`: Save findings to a Word document report
- `q`: Quit the application

### Key Functions

#### Viewing Findings
- The main screen displays a table with finding numbers, names, and severity levels
- Select a finding number to view detailed information including:
  - Description
  - Remediation details
  - Affected locations
  - Vulnerability classifications
  - HTTP messages

#### HTTP Message Viewing
When viewing a finding's details:
- Choose a specific location number to view associated HTTP messages
- Messages are formatted for readability
- Cookie values are automatically truncated for security
- Base64-encoded content is automatically decoded

#### Modifying Findings
Using the 'm' option allows you to edit:
- Finding name
- Severity level
- Confidence level
- Description
- Remediation details
- Issue details
- Vulnerability classifications

#### Deleting Findings
Two ways to delete findings:
1. From the main menu using 'd'
2. While viewing finding details
- Supports deletion of multiple findings using comma-separated values

#### Report Generation
The 's' option generates a Word document containing:
- Complete finding details
- Formatted HTTP messages
- Vulnerability classifications
- Affected locations
- Color-coded severity indicators

### Class Reference

#### BurpScanParser
Main parser class for handling Burp Suite XML exports.

Key Methods:
- `extract_raw_vulnerabilities()`: Extracts and processes raw vulnerability data
- `group_vulnerabilities()`: Groups similar findings and sorts by severity
- `display_table()`: Shows the main findings table
- `show_detailed_finding()`: Displays comprehensive finding information
- `delete_finding()`: Removes specified findings
- `modify_finding()`: Enables finding modification
- `save_to_json()`: Exports findings data

#### SecurityReportGenerator
Handles Word document report generation.

Key Methods:
- `make_report()`: Creates the final Word document
- `format_issue_detail()`: Formats finding details
- `setup_styles()`: Configures document styling

### File Structure
```
.
├── parser.py           # Main script
├── requirements.txt    # Package requirements
├── README.md          # This documentation
└── template/          # Word document templates
    └── finding.docx   # Template for findings
```

## Error Handling
The tool includes comprehensive error handling for:
- Invalid XML files
- Missing files
- Incorrect file formats
- Invalid user inputs
- Base64 decoding errors
- JSON parsing errors

## Limitations
- Only processes Burp Suite Professional XML exports
- Requires valid finding.docx template
- Large HTTP messages may affect display formatting

## Contributing
Contributions are welcome! Please feel free to submit pull requests or create issues for bugs and feature requests.

## License
MIT License

## Author
Created by Aswin Gopalakrishnan
- LinkedIn: https://www.linkedin.com/in/aswingopalakrishnan/

## Support
For support, please create an issue in the project repository or contact the author via LinkedIn.
