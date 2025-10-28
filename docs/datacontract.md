### 1. Raw Headlines (data\raw\raw_headlines.csv)
- Purpose: Store NewsAPI results as is pre cleaning
- Columns: 
    - headline_id = Unique identifier
    - publish_utc = Timestamp of publication date
    - source = API source used(expanded later)
    - publisher = News publisher
    - headline = Full headline text
    - url = Link for article
    - assoc_ticker = Ticker(s) associated with article

### 2. Staged Documents (data\processed\staged_documents.csv)
- Purpose: Cleaned and deduped headlines taken from raw_headlines, and assigned to a ticker
- Columns:
    - doc_id = Unique identifier
    - date = Timestamp of document
    - ticker = Matched company ticker
    - cleaned_headline = Cleaned headline (if needed)
    - source = API source
    - dedupe_key = Hash to catch duplicate
    - q_flag = Notes on any filtering or mapping issues

### 3. Sentiment Scores (data\processed\sentiment_score.csv)
- Purpose: Store FinBERT sentiment predictions for each cleaned document
- Columns:
    - doc_id = Unique identifier
    - label = Sentiment label assigned
    - pos_prob = Positive probability
    - neg_prob = Negative probability
    - neu_prob = Neutral probability

### 4. Daily Features (data\processed\daily_features.csv)
- Purpose: Aggregate sentiment results for the day at the company level
- Columns:
    - ticker = Ticker for company
    - date = Timestamp
    - num_docs = Number of documents associated for the day
    - pos_share = Fraction of positive
    - neg_share = Fraction of negative
    - sent_mean = Mean score
    - sentiment_z7 = 7-day rolling z-score of sentiment_mean
    

