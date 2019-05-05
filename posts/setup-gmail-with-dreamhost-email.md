# Setting up Dreamhost email to work in Gmail
#### 2017-09-09

![Featured:Illustration of letter with Dreamhost logo](/posts/media/dreamhost-gmail.jpg)

You've registered a domain with Dreamhost and you might even be hosting a site there.  In an ideal world you'd use Gmail with the domain for your email but you don't really want to shell out the money and have yet another new login.

Having your email forward to your Gmail address is easy, however its also worthwhile to be able to send from that address too. 

To have multiple emails work with your existing account, here is what you can do.

## Create your new email address in Dreamhost 

Lets pretend you have the domain "**example.com**" and you want to setup the email address "**jane@example.com**". 

1. Open link:
   * [Manage Email](https://panel.dreamhost.com/index.cgi?tree=mail.addresses&current_step=Index&next_step=New)
   * Login if necessary
2. Fill in the necessary details within the "*Fully Hosted Email*" part of the page
   * Choose "*example.com*" in the dropdown
   * Enter "*jane*" as the email address
   * Enter a password (Use this whenever I mention *password*)
   * Do not provide a "catch-all" email address etc.
3. Click the "*Create Address*" button
4. Find your "*Mail Cluster*" name and make a note for later.
  * It will be **one** of these:
    * *sub3.mail.dreamhost.com*
    * *sub4.mail.dreamhost.com*
    * *sub5.mail.dreamhost.com*
    * *master.mail.dreamhost.com*
  * This [support page on DreamHost](https://help.dreamhost.com/hc/en-us/articles/214918038#Server_names) has more information.
5. Think of a label name that you will want your email to show-up under in Gmail. 
  * In this guide is use "*Example Email*"

## Setting up Gmail for a second email address

1. Open link: 
   * https://atmail.dreamhost.com
2. Enter the following:
   * Username: **jane@example.com**
   * Password: **password**
3. Keep it open while you continue with next steps

## Setting up Gmail for a second email address

1. Open a new browser tab or window
2. Go to: https://mail.google.com/mail/
   * Sign-in to your account
3. Go to: https://mail.google.com/mail/u/0/#settings/accounts
4. Click on link “*Add a mail account*”
5. A new window will pop: “*Add a mail account*”
6. Enter the email address and click “*Next*”:
   * **jane@example.com**
   * Click “*Next*”
7. Choose “*Import emails from other account (POP3)*” 
   * It should be selected by default
   * Click “*Next*”
8. Enter the mail settings
   * Username: **jane@example.com**
   * Password: **password**
   * Pop Server: **sub3.mail.dreamhost.com** (use your one)
   * Port: **995**
   * Uncheck: “*Leave a copy of retrieved message on the server*”
   * Check: “*Always use a secure connection (SSL)…*”
   * Check: “*Label incoming messages*" 
     * Choose from list “*New label…*”
     * When asked to enter new label, type ”**Example Email**” and click “*OK*”
   * Uncheck: *Archive incoming messages (Skip the Inbox)*
   * Click “*Add Account*” button
9. You will be asked if you want to send email under this account
   * Select “*Yes, I want to…*” (default)
   * Click “*Next*” button
10. You will be asked to enter information
   * Your name will be populated by default (no need to change)
   * “*Treat as an alias*” is enabled (default)
11. Click “*Next Step*”
12. Enter SMTP Settings:
   * Username: **jane@example.com**
   * Password: **password**
   * Pop Server:  **sub3.mail.dreamhost.com** (use your one)
   * Port: **465**
   * Check: "*Secured connection using TLS*" (default)
   * Click "*Add Account*" button
13. Confirm the account
   * You will be asked for verification code
   * Switch over to the Webmail (mentioned at beginning and get it)
     * https://atmail.dreamhost.com
   * Enter code and hit “*Verify*” button
14. Go back to Gmail and open Settings (or go to this link)
   * https://mail.google.com/mail/u/0/#settings/accounts
   * Where it says "*When replying to a message*"
     * Choose "*Reply from the same address the message was sent to*"
15. Have a delicious drink of your choosing.

## The future…

All email sent to your new address will appear in Gmail under the "Example Email" category. You will see it in your regular Inbox too.

When you reply to an email sent to that the ‘example.com’ email address will be used as the *Reply-To*.

When composing a new email you will have options to choose from in the "*From*" part of the email.
