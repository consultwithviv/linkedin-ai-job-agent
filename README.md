# LinkedIn AI Agent - Automated Your Job Application
An enterprise-grade n8n workflow designed to automate the most time-consuming parts of the job hunt. This agent scrapes LinkedIn, analyzes job relevance using Gemini 3 Flash, and automatically generates tailored resumes and cover letters.

🌟 **Key Features**

**Automated Scraping**: Fetches up to 100 job postings at once via Apify.

**AI Relevance Scoring**: Uses Google Gemini to compare your resume against job descriptions, filtering out "junk" and focusing only on high-match roles.

**Smart Deduplication**: Integrated with Google Sheets to ensure you never process or apply to the same job twice.

**Dynamic Asset Creation**: Automatically generates customized Resumes and Cover Letters as Google Docs and saves them directly to your Google Drive.

**Master Tracker**: Every action is logged in a centralized Google Sheet for easy follow-ups.

**🏗️ The Architecture**

<img width="939" height="214" alt="Architecture_Diagram" src="https://github.com/user-attachments/assets/1c78f4e0-29ed-4816-9b72-c304511e6356" />

The system follows a modular logic flow:

Trigger: Manual or scheduled search.

Fetch: Scrape job data using LinkedIn search URLs.

Filter: Check against local database (Google Sheets) for duplicates.

Analyze: Gemini AI evaluates fit based on your specific career goals.

Generate: Tailored PDF/Doc assets created only for "High Relevance" jobs.

Store: Automated filing in Google Drive.

**📁 Repository Contents**

Architecture Diagram.png: Full architecture diagram and logic flow.

Setup_Guide_Credentials.md: Step-by-step technical documentation (n8n, Apify, Google Cloud).

Terms_of_Use.md: Licensing and usage policies.

**🛒 How to Get the Workflow**

The executable .json workflow file and the pre-configured n8n template are available exclusively on Etsy.

👉 Buy the LinkedIn AI Agent on Etsy

**Why buy the template?**
**Plug & Play**: Import the JSON and start applying in minutes.

**Prompt Engineered**: Includes the exact, battle-tested AI prompts used to generate high-conversion resumes.

**Full Support**: Detailed documentation included to guide you through API setup.

**🛠️ Technical Requirements**

-n8n (workflow execution)

-Apify Account (LinkedIn Scraper Actor)

-Google Cloud Console (Sheets & Drive API)

-Google AI Studio (Gemini API Key)

**⚖️ License**

This documentation and architectural overview are licensed under the MIT License. The .json workflow file available on Etsy is subject to a Single-User Personal License. See Terms_of_Use.md for details.
