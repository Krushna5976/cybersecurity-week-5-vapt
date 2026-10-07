# Week 5 – VAPT Findings

## Target

- Target: testasp.vulnweb.com
- IP observed: 44.238.29.244
- Protocol: HTTP
- Port: 80/tcp
- Platform: Linux Mint
- Tools: Nmap, Nikto, Burp Suite

## Findings

### F-01 – ASP Session Cookie Without HttpOnly

**Evidence:** Nmap `-A`, Nikto, and Burp Suite response.

The ASP session cookie was observed without the `HttpOnly` attribute.

**Risk:** Medium

**Recommendation:** Configure session cookies with the HttpOnly attribute and review Secure and SameSite settings.

---

### F-02 – Missing X-Frame-Options Header

**Evidence:** Nikto scan.

Nikto reported that the anti-clickjacking `X-Frame-Options` header was not present.

**Risk:** Low–Medium

**Recommendation:** Configure an appropriate anti-framing policy such as Content-Security-Policy `frame-ancestors` and/or X-Frame-Options where appropriate.

---

### F-03 – HTTP TRACE Method Enabled

**Evidence:** Nmap `-A` and Nikto.

TRACE was identified as an allowed/potentially risky HTTP method.

**Risk:** Low–Medium

**Recommendation:** Disable TRACE if it is not required.

---

### F-04 – Server/Technology Information Disclosure

**Evidence:** Nmap `-sV`, Nmap `-A`, Nikto, and Burp Suite.

The server disclosed Microsoft IIS 8.5 and ASP.NET information through service detection and HTTP response headers.

**Risk:** Low

**Recommendation:** Minimize unnecessary server and framework version disclosure where practical.

---

### F-05 – ETag Information Disclosure

**Evidence:** Nikto.

Nikto reported that the server leaks inode-related information through ETags.

**Risk:** Low

**Recommendation:** Review ETag configuration and disable or modify it if the exposed information is unnecessary.

---

### F-06 – Login Page Exposed

**Evidence:** Nikto.

Nikto identified `/login.asp` as an accessible login page.

**Risk:** Informational / Review

**Recommendation:** Review authentication, authorization, rate limiting, monitoring, and access-control requirements for the login functionality.

## Important Note

These findings are security observations from automated and manual inspection. They should not automatically be interpreted as proof of successful exploitation or compromise.

Further validation would be required before assigning a confirmed vulnerability classification.
