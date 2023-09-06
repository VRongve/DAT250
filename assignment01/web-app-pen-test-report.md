# Social Insecurity - Penetration Testing Report

run shift+ctrl+v to visualize the markdown in separate window

## Introduction

## Vaurnabilitie notes:

### Weak password

This lets the user create whatever password they want. For example a password could be the letter "A", which can be very easy to break for the attacker by using the brut force technique.

- Cateogory: A7:Identification and Authentication Failures
  - Subcategory: Credential Security
    - Issue: Weak Passwords
    - Description: Weak passwords refer to passwords that lack the necessary complexity or strength to withstand unauthorized access attempts. These passwords are often easy to guess, predict, or crack using various techniques, such as brute force attacks, dictionary attacks, or common password lists. Weak passwords pose a significant security risk as they can lead to unauthorized access to user accounts, exposing sensitive data, and potentially allowing attackers to compromise the integrity and confidentiality of an application.

Solution: 
- Enforcing password complexity
- Educate users about the importance of strong passwords
- MFA (multi-factor authentication)

### User enumeration

Instead of telling the user that either the password or username entered is wrong, the app tells that the user does not exist or that the password is incorrect. This give the attacker usefull information, by telling him that the user exist, but the password is incorrect. Now the user can continoue continoue with for instance brut force technique on that username. 

- Cateogory: A7:Identification and Authentication Failures (NOT SURE IF THIS IS A1 or A7)
  - Issue: User Enumeration
  - Description: Attackers can determine valid usernames through differential error messages or other means, which can aid in launching various attacks, including brute force attacks and targeted attacks on known user accounts.

Solution:
- The application should ensure consistent error messages or responses regardless of whether the username or password is incorrect, making it more difficult for the attackers to gather information about valid usernames

### Bypassing access control by modifying URL

- Cateogory: A1:Broken Access Control
  - Issue: Session management

I'm able to login to the app by only modifying the URL. The only thing the user will need is to know a username.

For instance:\
If I enter the following intot the URL "http://127.0.0.1:5000/stream/th" I will be logged in as th, without entering any password. 

Due to the lack of session management in the app the log out button is also useless. The intention of the button is to log the user out of the app, but due to lack of session management this does not work. Essentially what this button does now is to just bring the user back to the login page. 

Another issue i experience while testing the app is that when clicking on the username of a friend or the username of someone that has commented you post, the app changes the user. I believe the user should not be changed unless the user logs out of the app and a new user logs in.

#### Risk - High

### Authentication

The app is lacking user authentication. Currently an attacker is able to modify anyones profile as long as he knows their username. This can be done by modifying the URL and then pressing the "Edit" button. This lets the attacker change all the "About info" for a user. 

### File upload

The web app does not give an guidelines for what kind of files that can be uploaded and not. It looks like the app excepts any kind of file extensions. This means that an attacker might potentially upload malicious and dangenrous files. 

- Category: Insecure File Uploads
  - Description: Insecure file uploads refer to vulnerabilities where a web application does not adequately validate, sanitize, or secure user-uploaded files. Attackers can exploit these weaknesses to upload malicious files, potentially compromising the integrity and security of the application and its server.



### Form validation

The app lacks form validation. For example the user might share something without actually writing or uploading anything. A solution would be to restrict the user for publishing their thoughts if for instance the text field is empty. 

The sign up form can be submitted without any data. This should not be allowed. Also a user can be registered without a first name and last name. This should also not be allowed. Form validation will solve this issue.

### Cross origin = "anonymous"

I can see through the developer tool in the browser that cross origin is set on the javascripts. Is this a vaulrnabiliti?



## Black box testing

The steps i am doing above is essentially black box testing as I'm testing the web app wihtout looking at any source code. I'm only testing the app by manually clicking around.

## White box testing

White box testing is testing the app while looking at all the source code. Essentially the pen tester have access to everything.

# Assignment Strcuture from Canvas

## Introduction 

Briefly introduce the “Social Insecurity” Flask application and the purpose of the assignment.

## Vulnerability Assessment

1. Conduct a thorough vulnerability assessment of the Flask-based web application. Use both automated scanning tools and manual techniques to identify potential security vulnerabilities.
2. Document the vulnerabilities you discover along with a brief description of each vulnerability, its potential impact, and the affected part of the application.
3. Categorize the vulnerabilities based on common vulnerability types (e.g., SQL injection, cross-site scripting, insecure authentication).

## Vulnerability Exploitation

1. Select at least five distinct vulnerabilities that you have identified.
2. Choose appropriate penetration testing tools (such as Metasploit, Burp Suite, OWASP Zap, sqlmap) and techniques to exploit these vulnerabilities.
3. Clearly document the steps you took to exploit each vulnerability, including any commands, payloads, or configurations used. These instructions should be detailed enough for the teaching assistants or the lecturers to reproduce your attack.
4. Explain the results of each successful exploitation, including the extent of the compromise, potential data accessed, and system control achieved.

## Impact Analysis

Discuss the potential consequences if these vulnerabilities were present in a real-world application.

## Lessons Learned

Reflect on the challenges you encountered, the tools and techniques you found most effective, and the importance of securing web applications.

# Grading Criteria

Your assignment will be evaluated based on the following criteria:

- Thoroughness of vulnerability assessment
- Accuracy and effectiveness of vulnerability exploitation
- Clarity and quality of the report
- Demonstrated understanding of web application security concepts
- Creativity in selecting and exploiting vulnerabilities




