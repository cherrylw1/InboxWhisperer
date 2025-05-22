InboxWhisperer - Smart Email Summarizer & Prioritizer

Project Description

InboxWhisperer is a Python tool that connects to your Gmail account, summarizes unread emails, tags them by priority and sentiment, and exports a report. It uses the Gmail API to fetch emails, NLTK for summarization and sentiment analysis, and Pandas for report generation.

Key Features





Connects to Gmail using the Gmail API.



Summarizes email bodies using extractive summarization with NLTK.



Analyzes sentiment of emails using NLTK's SentimentIntensityAnalyzer.



Tags emails as high priority based on configurable keywords or senders.



Exports a CSV report with summaries, sentiments, and priorities.

Real-world Use Cases





Quickly review important emails without reading them fully.



Prioritize emails based on content or sender.



Keep a record of email summaries for reference.

Installation Steps





Clone this repository:

git clone https://github.com/yourusername/InboxWhisperer.git



Set up a Google Cloud project and enable the Gmail API:





Go to Google Cloud Console.



Create a new project.



Navigate to API Library and search for "Gmail API."



Enable the Gmail API.



Configure OAuth consent screen (select Internal for simplicity).



Create OAuth 2.0 credentials (Desktop app).



Download the credentials.json file and place it in the project directory.



Create a virtual environment (optional):

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate



Install dependencies:

pip install -r requirements.txt



Download NLTK data: In the project directory, run:

import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('vader_lexicon')

How to Run





Run the main script:

python main.py



When prompted, authorize the app via the browser and follow the OAuth flow instructions.



The script will fetch up to 10 unread emails, process them, and generate a CSV report named email_report.csv in the project directory.

Sample Output

The email_report.csv file will contain columns:





Email ID: Unique identifier for the email.



Subject: Email subject line.



Summary: Extracted summary of the email body.



Sentiment: Compound sentiment score (-1 to 1, where positive is >0).



Priority: High or normal, based on keywords or sender.

Example email_report.csv:

Email ID,Subject,Summary,Sentiment,Priority
12345,Urgent: Project Deadline,Project due tomorrow,0.3,high
67890,Meeting Notes,Team discussed goals,0.7,normal

Configuration

Edit config.py to customize:





HIGH_PRIORITY_KEYWORDS: Add keywords like 'urgent' or 'important'.



HIGH_PRIORITY_SENDERS: Add email addresses for priority senders. Example:

HIGH_PRIORITY_KEYWORDS = ['urgent', 'important', 'action required']
HIGH_PRIORITY_SENDERS = ['[email protected]', '[email protected]']

Note





Ensure the credentials.json file is in the project directory.



The project processes up to 10 unread emails to avoid excessive API calls; modify maxResults in main.py if needed.



For advanced summarization, consider integrating models like BERT, though this increases complexity.
