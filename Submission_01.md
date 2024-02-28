---


---

<h1 id="weak-authentication-on-the-login-page-resulted-to-a-brute-force-attack">Weak authentication on the login page resulted to a brute force attack</h1>
<h3 id="severity-critical">Severity: Critical</h3>
<h2 id="issue-description">Issue Description</h2>
<p>Found a vulnerability on the login page during a security review, which is illustrated by weak authentication methods. This vulnerability made it easier for a brute force assault to succeed, compromising the security integrity of the system.</p>
<h2 id="risk-rating">Risk Rating</h2>
<ul>
<li>
<p>Risk: Critical</p>
</li>
<li>
<p>Difficulty to Exploit: Medium</p>
</li>
<li>
<p>Authentication : No</p>
</li>
</ul>
<h2 id="affected-urls">Affected URLs</h2>
<ul>
<li><a href="http://13.234.225.30:31337/wp-login.php">http://13.234.225.30:31337/wp-login.php</a></li>
</ul>
<h2 id="steps-to-reproducepoc">Steps to Reproduce/PoC</h2>
<p>The steps below provide a proof of concept for a brute force attack to access the admin page and log in to the login page.</p>
<p><strong>Step 1:</strong><br>
A Wpscan was conducted  on the website to identify the vulnerabilities and it revealed that two users are there.</p>
<p><a href="https://ibb.co/sH54JzV"><img src="https://i.ibb.co/fv8WGLx/Screenshot-2024-02-28-123446.png" alt="Screenshot-2024-02-28-123446" border="0"></a></p>
<p><strong>Step 2:</strong></p>
<p>After identifiying the user as an admin. It appears that the username matches ‘admin’.  In the course of testing, it was observed that while the username input was Correct, there was an error encountered on the login page due to an incorrect password entry as shown  below.</p>
<p><a href="https://ibb.co/zZ8GMy6"><img src="https://i.ibb.co/w4JMk9c/Screenshot-2024-02-28-125008.png" alt="Screenshot-2024-02-28-125008" border="0"></a></p>
<p><strong>Step 3:</strong></p>
<p>A brute force technique was used to find the password of the user name admin. The burp suite tool was used for that.</p>
<p>Go to the Open browser option and navigate to the logging page with the URL :- <a href="http://13.234.225.30:31337/wp-login.php">http://13.234.225.30:31337/wp-login.php</a></p>
<p><a href="https://ibb.co/QrqkwjQ"><img src="https://i.ibb.co/18pMWJQ/Step-1.png" alt="Step-1" border="0"></a></p>
<p>Turn on the Intercept</p>
<p><a href="https://ibb.co/kxdvkZn"><img src="https://i.ibb.co/SPLGWST/Step-2.png" alt="Step-2" border="0"></a></p>
<p>Enter a password for the found user name admin and capture the request with burp.</p>
<p><a href="https://ibb.co/zXkhB4s"><img src="https://i.ibb.co/LxGzcZS/Step-3.png" alt="Step-3" border="0"></a></p>
<p><a href="https://ibb.co/QMTb14H"><img src="https://i.ibb.co/pdM09SK/Screenshot-9.png" alt="Screenshot-9" border="0"></a></p>
<p>Brute force the captured request sent to the intruder.</p>
<p><a href="https://ibb.co/nDqwSkg"><img src="https://i.ibb.co/fCVX701/Screenshot-11.png" alt="Screenshot-11" border="0"></a></p>
<p>Put the payload marker in the value field to do the brute force</p>
<p><a href="https://ibb.co/42T8hsd"><img src="https://i.ibb.co/1MqrFs6/Screenshot-12.png" alt="Screenshot-12" border="0"></a></p>
<p>Navigate to the Github Link <a href="https://github.com/danielmiessler/SecLists">https://github.com/danielmiessler/SecLists</a></p>
<p>And get a commonly used weak password list and copy it .</p>
<p>Go to the Payloads tab and paste the password list</p>
<p><a href="https://ibb.co/rwpLZKC"><img src="https://i.ibb.co/9r4fqmF/Step-7.png" alt="Step-7" border="0"></a></p>
<p>Then start the attack.</p>
<p><a href="https://ibb.co/DgMf58p"><img src="https://i.ibb.co/rfp24cs/Step-8.png" alt="Step-8" border="0"></a></p>
<p>Sort the length field. It will show the correct password with a different length.</p>
<p><a href="https://ibb.co/K5pK3VP"><img src="https://i.ibb.co/tHTLWYG/Step-9.png" alt="Step-9" border="0"></a></p>
<p><strong>Step 4:</strong><br>
Log in to the Admin page using the username and password found from the brute force attack.</p>
<p><a href="https://ibb.co/NyMHC92"><img src="https://i.ibb.co/1mkwQrG/last.png" alt="last" border="0"></a></p>
<p><a href="https://ibb.co/rFCPRRF"><img src="https://i.ibb.co/34DX994/Screenshot-16.png" alt="Screenshot-16" border="0"></a></p>
<h2 id="bussiness-impact">Bussiness Impact</h2>
<p>This security vulnerability affects our platform’s integrity and puts sensitive data’s accessibility and confidentiality in danger. Because of this, run the risk of suffering financial losses from compromised user accounts, damage to our reputation from security breaches, and legal liabilities from failing to protect client information.</p>
<h2 id="recommendation">Recommendation</h2>
<p>Implement Multi-Factor Authentication (MFA)<br>
Regular Security Audits<br>
Enforce Strong Password Policies<br>
Implement CAPTCHA<br>
Monitor Login Attempts</p>
<h2 id="references">References</h2>
<ol>
<li><a href="https://www.fortinet.com/resources/cyberglossary/brute-force-attack">https://www.fortinet.com/resources/cyberglossary/brute-force-attack</a></li>
<li><a href="https://portswigger.net/burp/documentation/desktop/testing-workflow/authentication-mechanisms/brute-forcing-passwords">https://portswigger.net/burp/documentation/desktop/testing-workflow/authentication-mechanisms/brute-forcing-passwords</a></li>
</ol>

