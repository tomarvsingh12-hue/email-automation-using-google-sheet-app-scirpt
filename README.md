📌 Google Sheets Payment Reminder Automation
📖 Overview

This project automates sending payment reminder emails to customers directly from Google Sheets using Google Apps Script.

With a single click, the script reads customer data from the sheet and sends personalized email reminders including:

Customer Name

Due Amount

Due Date

This helps businesses save time and avoid manual follow-ups.

🚀 Features

✅ One-click email sending

✅ Personalized email for each customer

✅ Reads data directly from Google Sheet

✅ Simple and lightweight automation

✅ No external tools required

🗂️ Google Sheet Structure

Your Google Sheet must have the following columns:

SR.NO.	Name	Email	Due Amount	Due Date

Make sure:

Row 1 contains headers

Emails are valid

Due Date is properly formatted

🛠️ Tech Stack

Google Sheets

Google Apps Script (JavaScript)

Gmail (MailApp Service)

📜 Script Code
function sendPaymentReminders() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = sheet.getDataRange().getValues();
  
  var subject = "Payment Reminder";
  
  for (var i = 1; i < data.length; i++) {
    
    var name = data[i][1];
    var email = data[i][2];
    var dueAmount = data[i][3];
    var dueDate = data[i][4];
    
    if (email != "" && dueAmount != "") {
      
      var body = "Dear " + name + ",\n\n" +
                 "Your installment of Rs " + dueAmount +
                 " is pending till date " + dueDate + ".\n\n" +
                 "Please pay your installment ASAP to avoid unwanted charges or penalty.\n\n" +
                 "Regards,\n" +
                 "Vivek Singh";
      
      MailApp.sendEmail(email, subject, body);
    }
  }
  
  SpreadsheetApp.getUi().alert("All payment reminder emails sent successfully!");
}

⚙️ How to Use

Open your Google Sheet

Click Extensions → Apps Script

Paste the above code

Save the project

Click Run

Authorize permissions

Emails will be sent automatically

📧 Sample Email Format

Subject: Payment Reminder

Body:

Dear John,

Your installment of Rs 5000 is pending till date 10 Feb 2026.

Please pay your installment ASAP to avoid unwanted charges or penalty.

Regards,
Vivek Singh

⚠️ Important Notes

Gmail free account limit: 100 emails/day

Google Workspace: up to 1500 emails/day

First-time authorization required

Ensure sheet columns match script index positions

🎯 Use Cases

Finance teams

Small businesses

Loan recovery teams

Subscription services

Educational institutes collecting fees

📌 Future Improvements

Add “Email Sent” status column

Add auto-send based on Due Date

Add HTML professional email template

Add custom button inside sheet

Add logging system

👨‍💻 Author

Vivek Singh
Automation & Excel Enthusiast
