### **Django Assignment: Secure Magic Link Login System**

#### **Objective**

In this assignment, you will build a **secure authentication system** that allows users to log in using a **magic link** sent to their email. Instead of using a traditional password, users will receive a **one-time login link** that grants them access to a protected page.

#### **Problem Statement**

Imagine a system where users don’t have to remember passwords. Instead, they enter their email, and the system sends them a **magic login link**. When they click the link, they are logged in automatically and redirected to a **secure page**. The link should:

 **Expire after a short time (e.g., 10 minutes)**  
 **Be valid for one-time use only** 
 **IP Restriction (create a checkbox, if checked login will work from user's IP only)**
 **Be secure to prevent unauthorized access**

Your task is to build this authentication flow in Django while ensuring security best practices.

* * *

### **Requirements**

1 **User Requests Login**

*   Create a page with a form where users enter their email.
*   When submitted, the system generates a **secure login token** and emails the user a **magic link**.

2 **Email the Magic Link**

*   Use Django’s email system to send the login link.
*   The email should contain a **clear call-to-action** for the user.


3 **Secure Page**

*   Only logged-in users who entered through a **valid magic link** can access a users only page.
*   If an unauthenticated user tries to access it, they should be redirected to the login page.

* * *
