# Project 8 - Pentesting Live Targets

Time spent: **X** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each color is vulnerable to only 2 of the 6 possible exploits. First discover which color has the specific vulnerability, then write a short description of how to exploit it, and finally demonstrate it using screenshots compiled into a GIF.

## Blue

Vulnerability #1: SQL injection (SQLi)

Description: I inject this SQL command "%27%20OR%20SLEEP(10)=0--%27" as the idof the url. The website had to wait for some seconds while quering the data.

<img src="BlueSQLi.gif">


Vulnerability #2: Session Hijacking/Fixation

Description: I logged into the target first, then I give the logged-in session ID to the attacker. I used two different browsers, I logged in one first first as a staff, then I took that session ID, then I changed the session ID in the other browser actinng as the user, and then this browser had access to the staff menu too.

<img src="BlueSession.gif">

## Green

Vulnerability #1: Cross site scripting

Description: I injected <script>alert('An outsider found the XSS!');</script> to the input of feedback form of Contact tab which triggered an alert showing the message saying "An outsider found the XSS!".

<img src="greenXSS.gif">

Vulnerability #2: User enumeration

Description: In inspect, the login message differs for the username that exist and doesn't exist. There's 2 different classes, 'failed' and 'failure'. The 'failure' means that username exist and 'failed' means that username don't exist. The developer forgot to keep spaning the tag class each time there's a login.

<img src="GreenUser.gif">


## Red

Vulnerability #1: IDOR

Description: When you change the id parameters of the user profile that isn't suppose to be made public until a given date in "Find a Salesperson", you are able to see its profiles in Red. But when you go in the others such as Blue and Green and input the id parameter of 10, it redirect you to the profile they have available. Red doesn't have the code that prevent important information from being made public.


<img src="RedIDOR.gif">

Vulnerability #2:CSRF

Description: When you send the post request of the edited user profile, you can see in Burpsuite it ignore the CSRF token. Red doesn't check the token when it is sumbitted so you can change the CSRF token and the name of the user which should only be managed by the staff. As you can see after it is edited, the changes appear on the user profile.

<img src="RedCSRF.gif">


## Notes

Describe any challenges encountered while doing the work

I first didn't know where to type the malicious input, but once I figured out how this works it I was able to find the vulnelabilities. The past assignment were obvious which attack we should use in which part of the webpage, but in this assignment we had to figure out all on our own so that was a little tricky.
