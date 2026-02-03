# **LinkedIn AI Agent: Complete Setup Guide & User Manual**

Welcome to your automated job application powerhouse\! This document will guide you through the technical setup and operation of your new AI Agent.

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

If you don't have an n8n account yet, sign up for a free trial or a cloud plan.

1. **n8n Cloud (Easiest):**  
   * Go to [n8n.io](https://n8n.io/) and click **get started**. Sign up for a free trial or a cloud plan. This is the fastest way to get started without technical setup. 

## **Setting Up Apify Scraper**

Apify is the "browser" that collects job data for the AI. Follow these steps to set it up from scratch:

### **Account Creation**

1. Go to [Apify.com](https://console.apify.com/sign-up) and click **Sign Up**.  
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

## **Setting up directories and Job Tracker in Google Drive**

1\. Create a copy of the [Jobs Tracker Template](https://docs.google.com/spreadsheets/d/1gYEA53D11wDjDJz9NwlQLVoIE5kjtU8zpg1IEI3OjT0/edit?gid=0#gid=0) Google Sheet and save in your Google Drive. 

2\. Create separate empty folders “Resume” and “Cover Letter” under your Google Drive, where the customized documents will be stored. Note down [Folder ID](#chapter-3:-setting-up-your-files) for Chapter 3\.


## **Chapter 1: Installing Apify and Importing the Workflow**

1. Log in to your n8n dashboard.  
2. Install Apify: Open nodes panel (+) on the right top corner and type in “Apify”, click on it and install node.
3. Click on **Workflows** in the left sidebar.  
4. Click the **Add Workflow** button (top right) and select **Import from File**.  
5. Select the `Linkedin_AI_Agent.json` file provided in your purchase.  
6. Once imported, you will see several nodes with orange/red warning icons. **This is normal\! It means we need to connect your personal accounts.**

## **Chapter 2: Connecting Your Accounts**

To get this AI Agent running, you need to connect four main services. Because this is a secure template, all connection IDs have been cleared. Follow these steps to "plug in" your own accounts.

### **1\. Google Gemini (The Brain)**

This workflow uses Gemini 2.5 Flash and 3 Flash (via the `googlePalmApi` connector).

* **Get your key:** Visit [Google AI Studio](https://aistudio.google.com/) and create a free API Key.  
* **In n8n:** Click on the **Check Relevance** node. Under "Credential for Google Gemini," select **Create New Credential**.  
* **Paste:** Enter your API Key and save it. After that, the remaining Gemini related nodes “Customise Resume”, “Customise Cover Letter” ‘s orange/red warning icons will be cleared.  

### **2\. Google Sheets, Docs & Drive (The Storage)**

You need to authorize n8n to read your tracker and save docs.

* **Setup:** Go to the [Google Cloud Console](https://console.cloud.google.com/), create a project, and click **APIs & Services \> Library** and search for the **Google Sheets API, Google Docs API** and **Google Drive API**, enable them. To validate completion, you can see them under “Enabled APIs & Services”.  

* **Credentials on Google Sheets:** We recommend using **OAuth2**. In n8n, click the **Append Relevant rows** node, select "**Create New Credential**" and follow the OAuth2 prompt to sign in with your Google Account.  

* **Credentials on Google Docs:** Again, we recommend using **OAuth2**. In n8n, click the **Create resume document** node, select "**Create New Credential**" and follow the OAuth2 prompt to sign in with your Google Account.  
 
* Ensure **Credentials on Google Docs** is selected under **“Http Request Add Resume”** and **“Http Request Add Cover Letter”** nodes**.

### **3\. Apify (The Scraper)**

* **In n8n:** Open the **Apify Scraper** node, **install** it if needed. Click "**Create New Credential**," and connect using **OAuth2** to sign in.

## **Chapter 3: Setting Up Your Files** {#chapter-3:-setting-up-your-files}

1. **LinkedIn Search URL**: Go to [https://www.linkedin.com/jobs/](https://www.linkedin.com/jobs/) and search for related jobs. Apply filters e.g. location, experience level, date posted for the scraper to obtain targeted results. Copy the URL.     
   Open **“Job Search URL”** node on n8n, replace the current URL with your filtered LinkedIn job search URL.  
2. **Folder ID**: Paste the ID of your Resume and Cover Letter folder. (Found in the URL between `/d/` and `/edit`).  
 - Open **“Create resume document”** node, paste the ID of your Resume folder.  
 - Open **“Create cover letter document”** node, paste the ID of your Cover Letter folder.  
3. Validate **Jobs Tracker Database Google Sheets** are being selected in the **“Get row(s) in sheet”, “Append irrelevant rows” and “Append Relevant rows”** nodes. 
4. Make sure your resume is ready in Google Doc. Open **“Get resume”** node, paste your resume URL under **Doc ID or URL** field.

## **Chapter 4: Operation**

### **Running the Agent**

1. Open the workflow and click **Execute Workflow**.  
2. The Agent will scrape jobs, check relevance, tailor your resume/cover letter, and save them to your Drive.

### **Pro-Tips for Success**

* **Review AI Outputs:** Always check the "Resume Link" in your spreadsheet before submitting.  
* **Update your Search URL:** Refresh your LinkedIn search filters regularly for fresh postings.

