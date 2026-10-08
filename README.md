## 🧾 Invoice Parser Automation (n8n + Groq + Google Workspace)

An n8n workflow that reads invoice PDFs from Google Drive, extracts the key details with a free AI model (Groq), saves them to Google Sheets, and emails the billing team.
<img width="1152" height="491" alt="Invoice Parser" src="https://github.com/user-attachments/assets/8cdd7e1e-8af0-43ba-a3c4-6bf620595b1e" />

## How it works

1. Upload an invoice PDF to a Google Drive folder.
2. The workflow downloads it and extracts the text.
3. Groq model pulls out the invoice number, sender, dates, currency and total.
4. The data is checked. If it looks wrong, a "needs manual review" email is sent instead.
5. Valid data is saved to Google Sheets (no duplicate rows for the same invoice number).
6. The billing team gets an email with the details and a link to the PDF.

## Tools used

- n8n
- Groq (free tier)
- Google Drive, Google Sheets, Gmail

## Setup

1. Import `invoice-parser-groq-clean.json` into n8n (**Workflows → Import from File**).
2. Add your credentials: Google Drive, Google Sheets, Gmail and Groq.
3. Set your Drive folder ID in the trigger and your sheet ID in the Google Sheets and Gmail nodes.
4. Put these headers in row 1 of your sheet:
   `Invoice Number | Sender Name | Sender Email | Invoice Date | Due Date | Currency | Total Amount | File Name | File Link | Processed At`
5. Upload `demo-invoice-INV-2026-0142.pdf` to the folder and turn the workflow on.

## Limitations

- Works with text PDFs only (no scanned images).
- Assumes one invoice per PDF.


## Author
Ansar Hayat, [@ansarhayat9](https://github.com/ansarhayat9)
