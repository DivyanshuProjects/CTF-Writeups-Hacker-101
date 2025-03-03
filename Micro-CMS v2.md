 Micro-CMS v2 - Web CTF Walkthrough

🏆 Challenge Overview

- Challenge Name: Micro-CMS v2  
- Category: Web  
- Difficulty: Moderate  
- Flags: 3  

Hey everyone! I'm Divyanshu Kumar, a cybersecurity enthusiast. In this post, I’ll walk you through my experience solving the Micro-CMS v2 CTF challenge. This is part of my series where I explore cybersecurity concepts through CTF (Capture The Flag) walkthroughs.

⚠️ Disclaimer: I’m still learning, and these posts are meant to document and share my knowledge as I grow in the cybersecurity field. Now, let’s dive into the challenge! 🕵️‍♂️

---

 Flag 0: SQL Injection Authentication Bypass

 Exploitation
The login page of the application is vulnerable to SQL injection. Entering a single quote (`'`) in the username field results in a 500 Internal Server Error, indicating that the application is improperly handling SQL queries.

To exploit this, we use a simple SQL injection payload to bypass authentication:

```sql
username=usr' UNION SELECT 'pass';--`
password=pass
```

 Outcome
This payload allows us to log in successfully. However, we are prompted with a message:

> "You got logged in, congrats! Do you have the real username and password? If not, might want to do that!"

This suggests that further enumeration might be required to retrieve actual credentials.

---

 Flag 1: Exploiting Improper HTTP Method Handling

 Issue Identified
In Micro-CMS v1, we had the ability to edit and create pages, which is no longer possible in v2 through GET requests. However, by analyzing the application, we can attempt to send a POST request to modify pages.

 Exploitation
Using Burp Suite or a simple cURL request, we send a POST request to `/page/edit/1` instead of a GET request:

```http
POST /page/edit/1 HTTP/1.1
Host: target-site.com
Content-Type: application/x-www-form-urlencoded

page_content=NewContent
```

 Outcome
Upon executing this, we successfully retrieve Flag 1.

---

 Flag 2: Extracting Credentials Using SQLMap

 Preparation
We create a text file (`h.txt`) containing an intercepted login request using Burp Suite or browser’s Developer Tools → Network Tab.

```http
POST /login HTTP/1.1
Host: target-site.com
Content-Type: application/x-www-form-urlencoded

username=admin&password=admin
```

 SQLMap Execution
Using the saved request, we run SQLMap to extract credentials:

```bash
sqlmap -r h.txt --batch --proxy="http://127.0.0.1:8080" --random-agent -p username --level=2 --risk=2 --dump --force-ssl
```

 Outcome
- The command dumps the database, revealing the username and password.
- Using these credentials, we log in and retrieve Flag 2.

---

 Conclusion
The Micro-CMS v2 CTF challenge demonstrates several common web vulnerabilities:
1. SQL Injection to bypass authentication.
2. Improper HTTP Method Handling allowing unauthorized modifications.
3. Database Extraction using automated tools like SQLMap.

These vulnerabilities highlight the importance of secure coding practices such as prepared statements, proper HTTP method validation, and limiting SQL query exposure.

