- 👋 Hi, I’m @kajal607
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...import csv
import re
import smtplib

# ईमेल वैलिडेशन के लिए रेगुलर एक्सप्रेशन पैटर्न
email_pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'

def validate_email(email):
    if re.match(email_pattern, email):
        return True
    return False

def check_email_smtp(email):
    domain = email.split('@')[1]
    try:
        mx_record = smtplib.SMTP('mx.' + domain)
        mx_record.quit()
        return True
    except:
        return False

def bulk_email_checker(file_path):
    valid_emails = []
    invalid_emails = []
    
    with open(file_path, 'r') as file:
        reader = csv.reader(file)
        for row in reader:
            email = row[0]
            if validate_email(email) and check_email_smtp(email):
                valid_emails.append(email)
            else:
                invalid_emails.append(email)
    
    return valid_emails, invalid_emails

# CSV फाइल का पथ
file_path = 'emails.csv'
valid_emails, invalid_emails = bulk_email_checker(file_path)

print("Valid Emails:")
for email in valid_emails:
    print(email)

print("\nInvalid Emails:")
for email in invalid_emails:
    print(email)
    
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
kajal607/kajal607 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
