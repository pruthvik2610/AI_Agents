Gmail Classification AI Agent (n8n Workflow)

Description:
-------------
This n8n workflow automatically classifies incoming job application-related emails from Gmail, summarizes them, and applies appropriate Gmail labels. It can also send an SMS notification with the summary using Twilio.

Workflow Overview:
-------------------
1. **Gmail Trigger**: Polls Gmail every minute for new emails.
2. **AI Agent (LangChain)**: Uses a prompt to:
   - Analyze the subject and body of the email.
   - Classify it into one of five categories:
     • applied
     • rejected
     • assessment
     • technical interview
     • screening round
   - Summarize the email in 3 professional lines.
3. **Text Classifier (LangChain)**: Validates classification using predefined labels.
4. **Labeling**: Applies the relevant Gmail label based on the result:
   - Gmail node (5 instances for each label)
5. **Twilio Node**: Sends an SMS with the summarized message to a designated number.

Required Credentials:
---------------------
- Gmail OAuth2 (`gmailOAuth2`)
- Google Gemini API (`googlePalmApi`)
- Twilio API (`twilioApi`)

Use Case:
----------
Perfect for job seekers who want to automatically track their application process and receive categorized summaries in real-time.

Status:
--------
Inactive by default. Enable to start automatic email classification.

License:
---------
Free to use and modify.
