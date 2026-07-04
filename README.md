# YouTube NLP Sentiment Analysis — ChatGPT Comments

**LSE Data Analytics and Machine Learning

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
- Removed English stopwords (e.g. 'the', 'and', 'is')
- Removed punctuation and numbers using `.isalpha()`
- Filtered to valid English dictionary words only using `nltk.corpus.words`

### 3. Sentiment Analysis (VADER)
- Applied VADER `SentimentIntensityAnalyzer` to each cleaned comment
- Extracted four scores per comment: positive %, neutral %, negative %, compound
- Compound score ranges from -1 (most negative) to +1 (most positive)

### 4. Evaluation and Visualisation
- Identified top 5 most positive and top 5 most negative comments
- Generated descriptive statistics on compound score distribution
- Visualised distribution using boxplot and histogram

## Results

| Statistic | Compound Score |
|---|---|
| Mean | 0.236 |
| Median | 0.318 |
| Min | -0.891 |
| Max | 0.923 |
| Std Dev | 0.450 |

**Overall sentiment: Positive** — mean and median compound scores both 
above 0, with 75th percentile at 0.572.

**Top positive themes:** Enthusiasm for ChatGPT's capabilities, recognition 
of rapid advancement, practical applications in productivity and investment.

**Top negative themes:** Concerns about safety and bias, fears about 
AI making people less capable, warnings about information as a weapon.

## Business Recommendation
Public sentiment towards ChatGPT is broadly positive (mean compound: 0.236).
The technology is well received by the general public. However, negative 
sentiment around bias and safety should be considered — particularly for 
regulated industries or customer-facing applications where accuracy and 
fairness are critical.

## Limitations
- 100 comments may not represent full audience sentiment
- Pre-processing removes unrecognised words (including 'ChatGPT' itself)
- VADER may miss sarcasm and complex context
- YouTube commenters skew tech-enthusiast — may not represent broader business audience
- HTML formatting in some comments may affect scoring accuracy

## Libraries Used
```python
googleapiclient, pandas, nltk, dotenv, matplotlib
```

## How to Run
1. Clone the repo
2. Obtain a YouTube Data API v3 key from Google Cloud Console
3. Create a `.env` file in the same directory as the notebook containing:
   `YouTube_API_key=YOUR_KEY_HERE`
4. Install dependencies:
   `pip install google-api-python-client python-dotenv`
5. Open `YouTube_NLP_Sentiment.ipynb` and run all cells in order

## Skills Demonstrated
- YouTube Data API v3 integration and live data extraction
- Secure API key management using `.env` files
- NLP text pre-processing — tokenisation, stopword removal, lemmatisation
- VADER sentiment analysis — polarity scoring and compound score interpretation
- Sentiment distribution analysis and business recommendation
- Python: googleapiclient, pandas, nltk, matplotlib
