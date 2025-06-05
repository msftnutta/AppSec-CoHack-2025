# Cross-Site Scripting (XSS) Attack Challenge

## 🎯 Objective

Now that you've mastered SQL injection attacks and defenses, it's time to explore another critical vulnerability: Cross-Site Scripting (XSS). This challenge will test your ability to identify and exploit XSS vulnerabilities in the same OWASP Juice Shop application.

## 📋 Prerequisites

- OWASP Juice Shop deployed and accessible
- Completed SQL injection exercises
- Basic understanding of HTML, JavaScript, and web browsers
- Web browser with developer tools enabled

## 🔍 What is Cross-Site Scripting?

Cross-Site Scripting (XSS) is a vulnerability that allows attackers to inject malicious scripts into web pages viewed by other users. When successful, XSS can:

- **Steal user sessions and cookies**
- **Redirect users to malicious websites**
- **Modify page content dynamically**
- **Capture user keystrokes and form data**
- **Perform actions on behalf of the victim**

### Types of XSS Attacks

**Stored XSS (Persistent)**: Malicious script is permanently stored on the target server and executed when users access the affected page.

**Reflected XSS (Non-Persistent)**: Malicious script is reflected off a web server and executed immediately in the user's browser.

**DOM-based XSS**: The attack payload is executed as a result of modifying the DOM environment in the victim's browser.

## 🎮 Your Mission

Your task is to discover and exploit XSS vulnerabilities in the OWASP Juice Shop application. You need to:

1. **Reconnaissance**: Identify input fields and user interaction points
2. **Discovery**: Find at least 3 different XSS vulnerabilities
3. **Exploitation**: Successfully execute JavaScript code in the browser
4. **Impact Assessment**: Demonstrate the potential damage of each vulnerability

## 🔍 Areas to Investigate

Focus your testing on these application features:

### User Input Areas
- Search functionality
- Product reviews and comments
- User registration forms
- Contact/feedback forms
- Profile information fields

### Content Display Areas
- Product listings and descriptions
- User-generated content sections
- Error messages and notifications
- URL parameters and query strings

### Interactive Features
- File upload functionality
- Message boards or forums
- Social sharing features
- Any area where user input is displayed

## 📝 Challenge Tasks

### Task 1: Reflected XSS
Find a reflected XSS vulnerability where:
- Your payload is immediately reflected in the response
- The script executes in your browser
- The vulnerability could be exploited via a malicious link

**Hint**: Look for areas where user input is directly displayed back to the user without proper encoding.

### Task 2: Stored XSS
Discover a stored XSS vulnerability that:
- Persists your payload in the application's data store
- Executes the script for other users who view the content
- Could affect multiple victims over time

**Hint**: Focus on areas where users can submit content that will be viewed by others.

### Task 3: DOM-based XSS
Identify a DOM-based XSS where:
- The vulnerability exists in client-side JavaScript code
- The payload modifies the DOM without server interaction
- The attack works entirely within the browser environment

**Hint**: Examine URL fragments, client-side routing, or JavaScript that processes user input.

## 🧪 Testing Techniques

### Basic Payloads to Try
Start with simple test cases:
- `<script>alert('XSS')</script>`
- `<img src=x onerror=alert('XSS')>`
- `javascript:alert('XSS')`

### Advanced Techniques
- Try different encoding methods (URL, HTML, JavaScript)
- Test various HTML tags and event handlers
- Experiment with filter bypass techniques
- Use different contexts (HTML, attribute, JavaScript)

## 🏆 Success Criteria

You have successfully completed this challenge when you can:

1. **Execute JavaScript**: Demonstrate script execution in the browser
2. **Steal Information**: Show how you could access cookies or session data
3. **Modify Content**: Prove you can alter the page's appearance or behavior
4. **Create Exploits**: Develop working proof-of-concept attacks

## 📊 Documentation Requirements

For each XSS vulnerability you discover, document:

- **Location**: Specific page and input field
- **Type**: Reflected, Stored, or DOM-based
- **Payload**: The exact input that triggers the vulnerability
- **Context**: Where in the HTML/JavaScript the payload appears
- **Impact**: What an attacker could achieve
- **Evidence**: Screenshots of successful exploitation

## ⚠️ Important Reminders

- Only test on your own OWASP Juice Shop instance
- This is a controlled learning environment
- Focus on understanding the attack mechanisms
- Consider the real-world implications of each vulnerability
- Never attempt these techniques on systems you don't own

## 🎯 Ready for the XSS Hunt?

XSS vulnerabilities can be subtle and require creative thinking. Take your time to explore the application thoroughly and think about how user input flows through the system.

Remember: every piece of user input that gets displayed somewhere is a potential XSS vector!

Good luck, and may your scripts execute successfully! 🕷️

---

**Final Step**: Once you've completed your XSS attacks, proceed to demonstrate to the coach on how protect applications from these vulnerabilities.