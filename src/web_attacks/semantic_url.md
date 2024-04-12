Translating "ataki semantyczne" (semantic attacks) to specific URL addresses requires understanding the context and specific examples of such attacks. Semantic attacks can encompass a wide range of techniques that exploit vulnerabilities in the meaning or interpretation of data or systems.

Here's a breakdown of some common semantic attack categories and potential corresponding URL addresses that illustrate them:

**1. Injection Attacks:**

- **SQL Injection:** `https://en.wikipedia.org/wiki/SQL_injection`
   - Example URL: `https://example.com/login?username=admin' OR 1=1; --&password=password`

- **Cross-Site Scripting (XSS):** `https://en.wikipedia.org/wiki/Cross-site_scripting`
   - Example URL: `https://example.com/profile?bio=<script>alert('XSS attack successful!')</script>`

**2. Data Manipulation Attacks:**

- **Cross-Site Request Forgery (XSRF):** `https://en.wikipedia.org/wiki/Cross-site_request_forgery`
   - Example URL: `https://example.com/transfer?amount=1000&account=victim&token=forged_token`

- **JSON Web Token (JWT) Hijacking:** `https://en.wikipedia.org/wiki/JSON_Web_Token`
   - Example URL: `https://example.com/api/protected?token=eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyMSIsIm5hbWUiOiJVc2VyIDEiLCJpYXQiOjE2NTM2OTAwMDAsImV4cCI6MTY1MzY5MzYwMCwiYWxncmFpbSI6IkpXVCJ9.eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyMiIsIm5hbWUiOiJVc2VyIDIiLCJpYXQiOjE2NTM2OTAwMDAsImV4cCI6MTY1MzY5MzYwMCwiYWxncmFpbSI6IkpXVCJ9.forged_signature`

**3. Business Logic Attacks:**

- **Logic Bombs:** `https://en.wikipedia.org/wiki/Logic_bomb`
   - Example URL: `https://example.com/update?date=2023-04-12&action=delete_all_data`

- **Denial-of-Service (DoS) Attacks:** `https://en.wikipedia.org/wiki/Denial-of-service_attack`
   - Example URL: `https://example.com/api/endpoint?request=large_data_payload&repeat=1000`

**4. Evasion Attacks:**

- **Obfuscation:** `https://en.wikipedia.org/wiki/Obfuscation_%28software%29`
   - Example URL: `https://example.com/script.js?code=eval%28atob%28'bXkgY29uc29sZS5sb2cgKCdDb2RlIGhhdCB3b3VsZCByZWNlaXZlIGl0IScpOyAnKQ=='%29)`

- **Encoding Attacks:** `https://en.wikipedia.org/wiki/Encode`
   - Example URL: `https://example.com/login?username=%60admin%60&password=%60password%60`

These are just a few examples, and there are many other types of semantic attacks. The specific URLs used will vary depending on the attack and the target system.

**Remember:**

- Semantic attacks can be highly sophisticated and require in-depth knowledge of the target system and its vulnerabilities.
- It's crucial to implement proper security measures and keep systems up-to-date with security patches to mitigate these attacks.
