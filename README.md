# Scam Radar

Scam Radar is an explainable scam-detection web application designed to analyse messages, emails, documents, screenshots, and voice transcripts for potential scam indicators.

The system combines a machine-learning text classifier with deterministic scam-detection rules to provide a **SCAM / LEGIT** prediction, confidence score, risk level, and plain-English explanations of the warning signs detected.

The project was developed using **Flask, React, scikit-learn, SQLite, and Vite**.


## Live Demo
- **GitHub Repository:** https://github.com/Anbarasu-Projects/scam-radar
## Features
Scam Radar supports several forms of scam analysis:

- Pasted text messages
- Raw emails and `.eml` files
- PDF, DOCX and TXT documents
- Screenshots with OCR
- Voice recordings or transcripts
- Scam-awareness quiz
- Scan history

The application provides:

- Scam or legitimate classification
- Confidence score
- Risk level
- Plain-English explanations
- Suspicious-link detection
- Urgency and threat detection
- Credential and OTP request detection
- Payment and gift-card warning signals
- Remote-access scam detection
- Email-header analysis
- Document security checks
- Voice scam pattern detection

## How the Detection System Works
The system uses two complementary layers.
### 1. Machine-Learning Classification
Messages are converted into numerical features using:

- Word-level TF-IDF features
- Character-level TF-IDF features

A Logistic Regression classifier then estimates the probability that the submitted content is scam-related.

### 2. Rule-Based Scam Detection

The classifier is supported by deterministic rules that detect common scam indicators such as:

- Urgent calls to action
- Threats or intimidation
- Requests for passwords or credentials
- OTP requests
- Suspicious payment requests
- Gift-card demands
- Remote-access instructions
- Suspicious URLs
- Government or bank impersonation
- Delivery and parcel scams

The results from both layers are combined to produce the final risk assessment.

## Supported Input Types

| Input Type | Processing |
|---|---|
| Message | Direct text analysis |
| Email | Header and body analysis |
| PDF | Text extraction and structural checks |
| DOCX | Text extraction and document inspection |
| TXT | Direct text extraction |
| Screenshot | OCR-based text extraction |
| Voice | Speech-to-text or supplied transcript |

## Email Analysis
The email-analysis component checks both message content and email metadata.
Examples include:
- Sender and Reply-To mismatch
- Return-Path mismatch
- SPF failures
- DKIM failures
- DMARC failures
- Brand impersonation
- Suspicious links
- Hidden link destinations
- Dangerous attachment patterns

This helps identify scams that may not be obvious from message wording alone.
## Document Analysis

Uploaded documents can be inspected for both textual and structural evidence.

Examples include:

- Suspicious wording
- Embedded links
- PDF JavaScript
- Automatic PDF actions
- Word macros
- Double file extensions
- Disguised attachments
## Voice Scam Detection

Voice recordings can be converted into text before analysis.

The system also checks for patterns commonly associated with voice scams, including:

- Requests to read out verification codes
- Instructions not to hang up
- Remote-access software requests
- Arrest or legal threats
- Gift-card demands
- Bank or government impersonation

Server-side transcription can optionally use `faster-whisper`.

## Scam Awareness Quiz
The project also includes an educational scam-awareness quiz.
Each round:
- randomly selects five questions
- draws them from a larger question bank
- keeps correct answers on the server
- provides feedback after each answer
- generates final feedback after completion
This reduces the likelihood that users can simply inspect the frontend code to obtain the answers.
