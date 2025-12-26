---
title: Sample CTF Writeup - Web Exploitation Challenge
date: 2025-12-26 15:00:00 +0300
categories: [CTF Writeup]
tags: [ctf, web, writeup, exploitation]
image: https://i.postimg.cc/ZqKmx66V/Chat-GPT-Image-Dec-26-2025-11-20-41-PM.png
---

# Sample CTF Writeup - Web Exploitation Challenge

This is a detailed writeup of a web exploitation challenge from a recent CTF competition.

## Challenge Information
- **Platform**: TryHackMe
- **Category**: Web Exploitation
- **Difficulty**: Easy
- **Points**: 100

## Challenge Description
The challenge presented a simple web application with a login form. The goal was to bypass authentication and retrieve the flag.

## Reconnaissance
First, I visited the website and examined the login form. It had username and password fields.

I tried basic SQL injection payloads like `' OR 1=1 --` but it didn't work.

## Enumeration
I used Burp Suite to intercept the requests. The login request was a POST to `/login` with parameters `username` and `password`.

I checked for common vulnerabilities like XSS, but the input was sanitized.

## Exploitation
After some testing, I noticed that the application was vulnerable to command injection in the username field.

By entering `; cat /flag.txt` as username, I was able to execute the command and retrieve the flag.

## Flag
`THM{command_injection_master}`

## Lessons Learned
- Always test for command injection in input fields
- Use proper input validation and sanitization
- Never trust user input

## Tools Used
- Burp Suite for request interception
- Browser developer tools
- Linux terminal for testing

{: .prompt-tip }