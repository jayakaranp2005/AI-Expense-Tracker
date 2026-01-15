# AI-Expense-Tracker


# MIKE - AI Expense Tracker 🤖

MIKE is an intelligent expense tracking assistant that helps you manage your finances effortlessly through a Telegram bot interface. Simply send invoices, bank statements, or manually text your transactions, and MIKE will automatically organize and store your financial data. 

## 🌟 Features

- **Invoice Processing**: Upload invoice PDFs and automatically extract key information (date, invoice number, total amount, billed to)
- **Bank Statement Analysis**: Parse bank statements and automatically add transactions to your database
- **Manual Transaction Entry**: Quick text-based transaction entry for on-the-go expense tracking
- **Financial Summaries**: Generate comprehensive monthly financial summaries
- **Smart Conversation Handling**: Friendly AI assistant that handles general messages and queries
- **Automated Storage**: All data automatically synced to Google Sheets and Drive

## 🏗️ Architecture

This project is built using **n8n** (workflow automation tool) and consists of multiple interconnected workflows:

### Workflow Structure

1. **Main Workflow** (Parent) - Central orchestration hub
2. **Invoice Tracker** - Saves invoice PDFs and extracts data
3. **Bank Statements Tracker** - Processes bank statements and updates database
4. **Add Transactions** - Handles manual transaction entries via text
5. **Summarize Finances** - Generates monthly financial summaries
6. **Unknown Message Handler** - Manages general conversation and help requests

### Technology Stack

- **Workflow Automation**: n8n
- **LLM**:  Google Gemini (2.5 Flash used here)
- **Bot Interface**: Telegram Bot API
- **Storage**: Google Drive, Google Sheets
- **Processing**: JavaScript code nodes

## 📋 Prerequisites

Before setting up MIKE, ensure you have the following: 

### Required Accounts & Credentials

1. **Google Account** with access to: 
   - Google Drive
   - Google Sheets
   
2. **Google Gemini API Key**
   - Get your API key from [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Recommended model:  Gemini 2.5 Flash (or any Gemini model of your choice)

3. **Telegram Bot Token**
   - Create a bot via [@BotFather](https://t.me/botfather) on Telegram
   - Save your bot token

4. **n8n Instance**
   - Self-hosted or cloud-hosted n8n installation
   - Version 0.x.x or higher recommended

## 🚀 Setup Instructions

### Step 1: Google Drive Structure

Create the following folder structure in your Google Drive: 

```
📁 Expense Tracker (Main Folder)
├── 📁 Invoices
└── 📁 Bank Statements
```

**Important**: Note down the folder IDs for each folder (found in the URL when you open each folder).

### Step 2: Google Sheets Setup

Create a new Google Sheet with **two pages**:

#### Page 1: Invoices
Columns: 
- `Invoice Date`
- `Invoice Number`
- `Total Amount`
- `Billed To`

#### Page 2: Transactions
Columns:
- `Date`
- `Month`
- `Transaction Description`
- `Credit`
- `Debit`
- `Balance`

**Important**: Note down the Sheet ID (found in the Google Sheets URL).

### Step 3: Clone and Import Workflows

1. Clone this repository: 
   ```bash
   git clone https://github.com/jayakaranp2005/AI-Expense-Tracker.git
   cd AI-Expense-Tracker
   ```

2. Import the workflow files into your n8n instance:
   - `AI EXPENSE TRACKER main.json` (Import this first)
   - `INVOICE TRACKER.json`
   - `Bank Statements Tracker.json`
   - `add transactions.json`
   - `summarize_finances.json`
   - `unknown_msg.json`

### Step 4: Configure Credentials in n8n

For each workflow, update the following credentials:

#### Google Gemini API
- Add your Gemini API key in the LLM nodes
- Configure the model (recommended: gemini-2.5-flash)

#### Google Drive & Sheets
- Connect your Google account
- Update folder IDs for invoices and bank statements
- Update the Google Sheet ID

#### Telegram Bot
- Add your Telegram bot token
- Configure webhook or polling settings

### Step 5: Activate Workflows

1. Open the main workflow in n8n
2. Activate all sub-workflows first
3. Activate the main workflow last
4. Test the connection by sending a message to your Telegram bot

## 💬 Usage

### Sending Invoices
Simply send or forward an invoice PDF to the bot.  MIKE will:
1. Save the PDF to your Invoices folder
2. Extract invoice details using AI
3. Add the data to your Google Sheet

### Sending Bank Statements
Upload your bank statement PDF.  MIKE will:
1. Save the statement to your Bank Statements folder
2. Parse all transactions
3. Update your transaction log

### Manual Transaction Entry
Text your transaction in natural language: 
```
Spent $50 on groceries today
```
MIKE will parse and add it to your database.

### Getting Summaries
Ask MIKE for a summary: 
```
Summarize my finances for December
```
THANKS GOISSSSSS!!! :)
