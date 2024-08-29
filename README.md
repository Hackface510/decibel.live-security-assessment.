# Decibel.live Security Assessment

## Overview
This repository contains the full documentation of the security assessment and penetration testing performed on Decibel.live. The goal of this project was to identify potential security vulnerabilities and provide actionable recommendations to strengthen the security of the website.

## Methodology
The assessment was divided into several phases, each focusing on different aspects of the security landscape.

### 1. Information Gathering
- **Tools Used:**
  - **BuiltWith:** Used to identify the technology stack and services used by the website.
  - **Wappalyzer:** Utilized for further analysis of frameworks, CMS, and JavaScript libraries in use.
- **Objectives:**
  - To collect detailed information about the website’s infrastructure, software, and potential attack surfaces.
- **Results:**
  - Decibel.live utilizes Cloudflare for CDN and security, jQuery for frontend scripting, and PHP as the server-side language.
  - Identified potential points of interest for further testing, such as login pages, form inputs, and third-party integrations.

### 2. Automated Vulnerability Scanning
- **Tools Used:**
  - **Pentest-Tools.com:** Conducted a light scan covering 39 different security checks.
- **Objectives:**
  - To quickly identify common vulnerabilities such as outdated software, missing security headers, and insecure cookie settings.
- **Results:**
  - Several medium to low-risk vulnerabilities were identified, including missing Secure and HttpOnly flags on cookies, outdated JavaScript libraries, and missing HTTP security headers (e.g., Content-Security-Policy, X-Content-Type-Options).
  - No high-risk vulnerabilities were detected.

### 3. Manual Testing
- **Cross-Site Scripting (XSS):**
  - **Objective:** To identify XSS vulnerabilities by injecting malicious scripts into input fields and URL parameters.
  - **Steps Taken:**
    - Tested various input fields and URL parameters using payloads such as `<script>alert('XSS')</script>`.
    - Reviewed the page source and browser behavior to check if the script was executed.
  - **Result:** The site successfully sanitized the input, and no XSS vulnerabilities were detected.
  - **Recommendation:** Maintain regular updates and testing of input sanitization processes to ensure they continue to be effective.

- **SQL Injection:**
  - **Objective:** To discover any SQL Injection vulnerabilities that could allow unauthorized access or data manipulation.
  - **Steps Taken:**
    - Manually tested input fields and URL parameters with common SQL injection payloads like `' OR '1'='1`.
    - Monitored the site for SQL errors, unexpected behavior, or data leakage.
  - **Result:** The website did not display any SQL errors or allow data leakage, indicating good protection against SQL Injection.
  - **Recommendation:** Continue using parameterized queries and perform regular database security audits.

- **Authentication Testing:**
  - **Objective:** To assess the robustness of authentication mechanisms against brute-force attacks and session management flaws.
  - **Steps Taken:**
    - Conducted password penetration tests using common weak credentials to see if the site enforced strong password policies.
    - Analyzed session cookies for security flags (Secure, HttpOnly) to protect against session hijacking.
  - **Result:** The site effectively blocked weak credentials and brute-force attempts. However, session cookies were found to be missing the Secure and HttpOnly flags.
  - **Recommendation:** Implement Secure and HttpOnly flags on all session cookies to enhance session security.

- **Business Logic Testing:**
  - **Objective:** To find flaws in the business logic that could be exploited by attackers.
  - **Steps Taken:**
    - Tested scenarios like multiple applications of the same discount code, accessing unauthorized pages, and bypassing intended application logic.
  - **Result:** No business logic vulnerabilities were detected.
  - **Recommendation:** Continue to evaluate and test business processes as the site evolves.

### 4. Post-Testing Recommendations
- Based on the manual and automated tests, the following recommendations were made:
  - **Secure Cookie Settings:** Ensure that all cookies, especially session cookies, have the Secure and HttpOnly flags enabled to prevent unauthorized access.
  - **Update Outdated Software:** Upgrade outdated JavaScript libraries such as jQuery to mitigate known vulnerabilities.
  - **Implement Missing Security Headers:** Add essential security headers like Content-Security-Policy, X-Content-Type-Options, and Referrer-Policy to protect against common web vulnerabilities.

### 5. Follow-Up Actions
- **Continuous Monitoring:** Regularly monitor and test the site for vulnerabilities, especially after updates or changes.
- **Security Training:** Provide ongoing security training for the development team to ensure best practices are followed.
- **Further Testing:** Schedule deeper, more extensive penetration testing periodically to uncover any emerging threats.

## Conclusion
The Decibel.live website demonstrated strong security measures in several key areas, including protection against XSS and SQL Injection. The recommendations provided will further enhance the site’s security and ensure it remains resilient against potential threats.

## Contact Information
For any questions or further details about this assessment, please contact:
- **Your Name:** Aundre Walker
- **Position:** Penetration Tester / Security Consultant
- **Email:** aundre40@gmail.com
- **GitHub:** (https://github.com/Hackface510)
