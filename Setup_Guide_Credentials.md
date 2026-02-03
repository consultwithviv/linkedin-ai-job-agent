# **LinkedIn AI Agent: Complete Setup Guide & User Manual**

Welcome to your automated job application powerhouse\! This document will guide you through the technical setup and daily operation of your new AI Agent.

## **Table of Contents**

1. [Prerequisites](https://www.google.com/search?q=%23prerequisites)  
2. [Setting Up Credentials](https://www.google.com/search?q=%23step-0-setting-up-n8n)  
3. [Chapter 1: Importing the Workflow](https://www.google.com/search?q=%23chapter-1-importing-the-workflow)  
4. [Chapter 2: Connecting Your Accounts](https://www.google.com/search?q=%23chapter-2-connecting-your-accounts)  
5. [Chapter 3: Setting Up Your Files](https://www.google.com/search?q=%23chapter-3-setting-up-your-files)  
6. [Chapter 4: Daily Operation](https://www.google.com/search?q=%23chapter-4-daily-operation)

## **Prerequisites**

Before starting, ensure you have the following:

* A **n8n** Account (for workflow execution).  
* A **Google Account** (for Sheets and Drive).  
* An **Apify** account (for LinkedIn data scraping).  
* A **Google AI Studio** account (for Gemini 2.5 or 3).

## **Setting Up n8n**

If you don't have an n8n account yet, you have three options to get started:

1. **n8n Cloud (Easiest):**  
   * Go to [n8n.io](https://www.google.com/search?q=https://n8n.io/) and sign up for a free trial or a cloud plan. This is the fastest way to get started without technical setup.   
2. **n8n Desktop (Free):**  
   * [Download](https://docs.n8n.io/hosting/installation/npm/) the app to run it locally on your computer using these direct links:  
3. **Self-Hosted (Advanced):**  
   * If you have a server, you can host n8n yourself using Docker.

## **Setting Up Apify Scraper**

Apify is the "browser" that collects job data for the AI. Follow these steps to set it up from scratch:

### **Account Creation**

1. Go to [Apify.com](https://www.google.com/search?q=https://apify.com/) and click **Sign Up**.  
2. You can use your Google account for a fast setup.  
3. **The Free Tier:** Apify gives you $5 of platform credits every month for free. This is usually enough for hundreds of job scrapes.

## **Setting up Google AI Studio & Gemini** 

Google AI Studio is where you get the "brain" for your agent. It is currently the most generous free AI platform for developers.

###    **Get Your API Key**

1. Go to [aistudio.google.com](https://aistudio.google.com/).  
2. Sign in with your standard Google/Gmail account.  
3. In the top left sidebar, click the **"Get API key"** button.  
4. Click **"Create API key in new project"**.  
5. Copy the generated key (it starts with `AIza...`). **Warning:** Treat this like a password; do not share it.

## **Chapter 1: Importing the Workflow**

1. Log in to your n8n dashboard.  
2. Click on **Workflows** in the left sidebar.  
3. Click the **Add Workflow** button (top right) and select **Import from File**.  
4. Select the `Linkedin_AI_Agent.json` file provided in your purchase.  
5. Once imported, you will see several nodes with orange/red warning icons. T**his is normal\! It means we need to connect your personal accounts.**

## **Chapter 2: Connecting Your Accounts**

To get this AI Agent running, you need to connect four main services. Because this is a secure template, all connection IDs have been cleared. Follow these steps to "plug in" your own accounts.

### **1\. Google Gemini (The Brain)**

This workflow uses Gemini 2.5 Flash and 3 Flash (via the `googlePalmApi` connector).

* **Get your key:** Visit [Google AI Studio](https://www.google.com/search?q=https://aistudio.google.com/) and create a free API Key.  
* **In n8n:** Click on the **Check Relevance** node. Under "Credential for Google Gemini," select **Create New Credential**.  
* **Paste:** Enter your API Key and save it as `Google Gemini (AI Studio)`.

### **2\. Google Sheets & Drive (The Storage)**

You need to authorize n8n to read your tracker and save PDFs.

* **Setup:** Go to the [Google Cloud Console](https://www.google.com/search?q=https://console.cloud.google.com/), create a project, and enable the **Google Sheets API** and **Google Drive API**.  
* **Credentials:** We recommend using **OAuth2**. In n8n, click the **Append Relevant rows** node, select "Create New Credential," and follow the OAuth2 prompt to sign in with your Google Account.

### **3\. Apify (The Scraper)**

* **Get your key:** Log in to [Apify](https://www.google.com/search?q=https://apify.com/) and navigate to **Settings \> Integrations** to find your Personal API Token.  
* **In n8n:** Open the **Apify Scraper** node, click "Create New Credential," and paste your token.

## **Chapter 3: Setting Up Your Files**

### **1\. The Tracking Spreadsheet**

Create a copy of the [Jobs Tracker Template](https://docs.google.com/spreadsheets/d/1gYEA53D11wDjDJz9NwlQLVoIE5kjtU8zpg1IEI3OjT0/edit?gid=0#gid=0) Google Sheet. 

**2\. Setting Your Variables**

Open the **"Set Project Variables"** node (the first node after the trigger) and update:

1. **LinkedIn Search URL**: Paste your filtered LinkedIn job search URL.  
2. **Spreadsheet ID**: Paste the ID of your Google Sheet. (Found in the URL between `/d/` and `/edit`).  
3. **Resume Text**: Paste your current, full resume text into the `user_resume_text` field.

## **Chapter 4: Daily Operation**

### **Running the Agent**

1. Open the workflow and click **Execute Workflow**.  
2. The Agent will scrape jobs, check relevance, tailor your resume/cover letter, and save them to your Drive.

### **Pro-Tips for Success**

* **Review AI Outputs:** Always check the "Resume Link" in your spreadsheet before submitting.  
* **Update your Search URL:** Refresh your LinkedIn search filters every few days for fresh postings.

*Note: A red triangle on a node means a credential hasn't been selected yet. Click the node and choose your account from the dropdown.*

