AI-Assisted STRIDE Threat Model Generator
> Automated threat modelling powered by Claude AI.

What It Does
This tool takes a plain-English description of any system and uses the Anthropic Claude API to generate a structured STRIDE threat model — identifying realistic threats, severity ratings, and concrete mitigations across all six STRIDE categories.
Built to demonstrate the practical application of AI in security engineering workflows.

Skills Demonstrated
Area	Detail
AI / LLM Integration	Anthropic Claude API, prompt engineering, structured JSON output
Security Methodology	STRIDE threat modelling, risk rating, mitigation design
Python	API integration, JSON parsing, CLI tooling, file I/O
Cloud Security	Threat analysis covers cloud-native architectures (AWS, GCP, Azure)


STRIDE Categories Covered
Category	Description
Spoofing	Identity impersonation attacks
Tampering	Unauthorised data or code modification
Repudiation	Denial of actions without audit trail
Information Disclosure	Unintended data exposure
Denial of Service	Availability disruption
Elevation of Privilege	Gaining unauthorised access levels

Quick Start
1. Clone the repo
```bash
git clone https://github.com/YOUR-USERNAME/ai-threat-model-generator
cd ai-threat-model-generator
```
2. Install dependencies
```bash
pip install -r requirements.txt
```
3. Set your Anthropic API key
```bash
export ANTHROPIC_API_KEY="your-api-key-here"
```
4. Run the tool
Interactive mode:
```bash
python main.py
```
Inline mode:
```bash
python main.py "A web app with React frontend, Node.js API, PostgreSQL database and AWS S3 storage. Auth via JWT tokens."

Example Output

  STRIDE THREAT MODEL — SUMMARY

System  : Patient-facing healthcare web app with JWT auth and AWS S3 storage
Risk    : High
Threats : 7

[Critical] Elevation of Privilege — JWT token with weak signing allows token forgery
[High]     Spoofing — Stolen JWT replay attack via unencrypted connection
[High]     Information Disclosure — S3 bucket misconfiguration exposes patient docs
[High]     Tampering — SQL injection via unvalidated REST API inputs
[Medium]   Denial of Service — Unauthenticated endpoints vulnerable to flooding
[Medium]   Repudiation — No audit logging for staff or admin actions
[Low]      Information Disclosure — Verbose error messages expose stack traces
========================================
```
A full markdown report is saved automatically to `sample_output/`.
 See a full sample report here
---
How It Works
```
User Input (system description)
        ↓
Prompt Engineering (STRIDE-structured prompt)
        ↓
Anthropic Claude API (claude-sonnet-4)
        ↓
JSON Response Parsing
        ↓
Severity-sorted Markdown Report
```
The prompt instructs Claude to return structured JSON only — no hallucinated prose — which is then parsed, sorted by severity, and rendered into a clean report.
---
AI + Security Engineering Notes
This tool demonstrates how LLMs can augment not replace security engineering judgement:
AI is good at: Rapidly generating threat hypotheses across STRIDE categories, ensuring no category is overlooked, and producing consistent structured output
Human judgement still needed for: Validating threats against actual system architecture, prioritising by business context, and signing off on mitigations
ISO 42001 relevance: This tool itself would require AI risk assessment under ISO 42001 before use in a regulated environment  the outputs should be reviewed by a qualified security professional

Project Structure
```
ai-threat-model-generator/
├── main.py                  # Core tool
├── requirements.txt         # Dependencies
├── .gitignore               # Excludes API keys and secrets
├── sample_output/
│   └── report.md            # Example generated report
└── README.md
```
---
Author
Ashish Mukherjee

Disclaimer
This tool is for educational and professional development purposes. Threat model outputs should always be reviewed by a qualified security professional before use in production or regulated environments.
