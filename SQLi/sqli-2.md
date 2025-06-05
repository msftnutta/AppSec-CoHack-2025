# SQL Injection Attack Exercise

## 🎯 Objective

Now that you have successfully deployed OWASP Juice Shop, it's time to put your SQL injection knowledge to the test. In this exercise, you will identify and exploit SQL injection vulnerabilities within the application.

## 📋 Prerequisites

- OWASP Juice Shop deployed and accessible (from [previous exercise](sqli-1.md))
- Basic understanding of SQL syntax
- Web browser with developer tools
- Optional: Burp Suite, OWASP ZAP, or similar web application testing tools

## 🎮 Your Mission

Your task is to discover and exploit SQL injection vulnerabilities in the OWASP Juice Shop application. You will need to:

1. **Reconnaissance**: Explore the application and identify potential injection points
2. **Discovery**: Find at least 3 different SQL injection vulnerabilities
3. **Exploitation**: Successfully exploit each vulnerability you discover
4. **Documentation**: Record your findings and the impact of each vulnerability

## 🔍 Areas to Investigate

Focus your testing efforts on these application areas (but don't limit yourself to only these):

### User Authentication
- Login functionality
- User registration
- Password reset features

### Search and Filtering
- Product search functionality
- Category filters
- Sorting mechanisms

### User Profile Management
- Profile viewing
- Account settings
- Order history

### Administrative Functions
- User management (if accessible)
- Product management
- Review and feedback systems

## 📝 What You Need to Accomplish

### Task 1: Basic SQL Injection
Find and exploit a basic SQL injection vulnerability that allows you to:
- Bypass authentication
- Access unauthorized data
- Retrieve information from the database

### Task 2: Union-Based SQL Injection
Discover a union-based SQL injection that enables you to:
- Extract data from multiple tables
- Enumerate database structure
- Retrieve sensitive information

### Task 3: Blind SQL Injection
Identify and exploit a blind SQL injection where:
- No direct error messages are displayed
- Data extraction requires inference techniques
- Boolean-based or time-based methods are needed

## 🏆 Success Criteria

You have successfully completed this exercise when you can demonstrate:

1. **Vulnerability Discovery**: Identify at least 3 distinct SQL injection points
2. **Successful Exploitation**: Prove that each vulnerability can be exploited
3. **Data Extraction**: Show that you can retrieve unauthorized data
4. **Impact Assessment**: Understand and document the potential impact of each vulnerability

## 📊 Documentation Requirements

For each vulnerability you discover, document:

- **Location**: Where in the application the vulnerability exists
- **Type**: Classification of the SQL injection type
- **Payload**: The specific input that triggers the vulnerability
- **Impact**: What data or functionality can be compromised
- **Evidence**: Screenshots or output proving successful exploitation

## ⚠️ Important Reminders

- Only test on your own deployed instance
- This is a controlled learning environment
- Do not attempt these techniques on any other systems
- Focus on learning the attack vectors and their implications

## 🎯 Ready for the Challenge?

Take your time to methodically explore the application. Remember, real-world penetration testing requires patience, creativity, and systematic approach. 

Good luck, and may your queries be injected successfully! 🕵️‍♂️

---

**Next Step**: Once you've completed your attacks, proceed to [SQLi Defense Strategies](sqli-3.md) to learn how to protect applications from these vulnerabilities.