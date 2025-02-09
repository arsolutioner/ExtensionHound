<p align="center">
  <img src="https://github.com/user-attachments/assets/cb493d1f-b689-466b-839d-52ef506b211e" alt="Centered Image" width="500">
</p>
<hr />

![2025012701061-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/7b6b0073-8856-4e44-bd3a-dab4ecebda3b)

## The Challenge: Chrome Extension DNS Forensics

As a security investigator, you've encountered a common frustration: Chrome extensions making suspicious DNS requests, but they're nearly impossible to trace back to their source. Why? Because all DNS requests appear to come from the chrome process, making it extremely difficult to determine which extension is responsible for what network activity.

Traditional network monitoring tools show:
```
Process: chrome.exe
DNS Query: suspicious-domain.com
```
But which extension made that request? The trail goes cold... until now.

ExtensionHound is purpose-built to solve this forensic challenge by:
1. Analyzing Chrome's internal network state
2. Correlating DNS requests with specific extensions
3. Revealing the hidden connections between extensions and their network activities


## What ExtensionHound Does

ExtensionHound is a powerful forensic tool that breaks through the chrome process attribution barrier, allowing you to:
- 🔍 Scans Chrome profiles for extension DNS request history
- 📊 Provides detailed analysis of network connections
- 🌐 Optional VirusTotal integration for domain reputation checking
- 🔐 Optional Secure Annex integration for extension details (users, rating,Yara pattern matching)
- 📁 Multiple output formats (Console, CSV, JSON)
- 🖥️ Cross-platform support (Windows, macOS, Linux)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/arsolutioner/ExtensionHound.git
cd ExtensionHound
```

2. Create and activate a virtual environment (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use: venv\Scripts\activate
```

3. Install required packages:
```bash
pip install -r requirements.txt
```

4. Set up API integrations (optional):
   - Create a `.env` file in the project root
   - Add your API keys:
     ```
     # VirusTotal API Key for domain reputation checks
     VT_API_KEY=your_virustotal_api_key_here
     
     # Secure Annex API Key for extension details
     SECUREANNEX_API_KEY=your_secureannex_api_key_here
     
     # Rate limit for API calls (per minute)
     RATE_LIMIT_PER_MINUTE=4
     ```

## Usage

Common flags:
- `--chrome-dir PATH`: Specify custom Chrome directory
- `--vt`: Enable VirusTotal domain checking
- `--secure-annex`: Enable Secure Annex extension details
- `--output FORMAT`: Choose output format (csv/json)
- `--output-file PATH`: Specify output file path

## Usage Examples

Here are some practical examples of how to use ExtensionHound:

### Run a basic scan and save results to csv
```bash
python ExtensionHound.py --output csv --output-file audit_results.csv
```

### Run a full analysis with both VirusTotal and Secure Annex
```bash
python ExtensionHound.py --vt --secure-annex --output json --output-file "audits/$(date +%Y-%m-%d)_security_report.json"
```

### Run Offline For Profile-Specific Analysis
```bash
# Analyze a specific Chrome profile
python ExtensionHound.py --chrome-dir "/path/to/Chrome User Data/Profile 1"

# Deep dive into the Default profile with all features enabled
python ExtensionHound.py --chrome-dir "/path/to/Chrome User Data/Default" --vt --secure-annex
```

## Features

### YARA Rules Integration
- Uses YARA rules for advanced extension signature detection
- Identifies potentially malicious extensions based on code patterns
- Helps detect known malicious behaviors and techniques
- Supports custom YARA rule sets for specialized detection needs

### VirusTotal Integration
- Checks domain reputation against VirusTotal's database
- Shows detection ratios with severity indicators:
  - ✅ Clean (0 detections)
  - ⚠️ Low Risk (1-2 detections)
  - 🚨 Medium Risk (3-9 detections)
  - ⛔ High Risk (10+ detections)

### Secure Annex Integration
- Retrieves detailed information about Chrome extensions:
  - Extension name and developer
  - Number of active users
  - Extension rating
  - Helps identify potentially malicious or suspicious extensions
- YARA Rules Integration
  - Uses YARA rules for advanced extension signature detection
  - Identifies potentially malicious extensions based on code patterns
  - Helps detect known malicious behaviors and techniques
  
## Contact & Support

- 💼 LinkedIn: [Amram Englander](https://www.linkedin.com/in/amram-englander-a23a6a89/)
- 📧 Secure Email: amrameng@proton.me
- 🛡️ For urgent security assistance or consultation, feel free to reach out via ProtonMail or LinkedIn

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
