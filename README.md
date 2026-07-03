# YouTube-NLP-Sentiment-Analysis
NLP sentiment analysis on live YouTube comments using VADER and the YouTube Data API. LSE DA301 — includes API integration, NLTK pre-processing, polarity scoring, and visualisation.
# YouTube NLP Sentiment Analysis — ChatGPT Comments

**LSE Data Analytics Career Accelerator | DA301 — Advanced Analytics for Organisational Impact**

## Overview
This project performs sentiment analysis on live YouTube comments extracted 
via the YouTube Data API v3. The analysis focuses on public sentiment towards 
ChatGPT, using NLP pre-processing and VADER sentiment scoring to help a 
business decide whether to adopt the technology.

## Business Question
Should a business adopt ChatGPT based on public sentiment? What are the 
key positive and negative themes in public opinion about the technology?

## Video Analysed
**'What is ChatGPT and How You Can Use It'**
https://youtu.be/40Kp_fa8vIw

## Dataset
- **Source:** YouTube Data API v3 (live extraction)
- **Comments extracted:** 100
- **No static dataset file** — comments are pulled in real time via API

## Methodology

### 1. Data Collection
- Connected to YouTube Data API v3 via Google Cloud credentials
- Extracted 100 top-level comments from the target video
- Stored API key securely in a `.env` file using python-dotenv

### 2. Data Pre-Processing (NLTK)
- Tokenised each comment into individual words using `word_tokenize()`
- Converted all words to lowercase
-
