# Week 5 Mini-Project – Basic VAPT Assessment

## Project Title

Basic Vulnerability Assessment & Penetration Testing of an Authorized Web Application

## Objective

The objective was to perform a basic VAPT assessment using Nmap, Nikto, and Burp Suite and understand how each tool contributes to security testing.

## Target

- Target: testasp.vulnweb.com
- IP observed: 44.238.29.244
- Protocol: HTTP
- Port: 80/tcp
- Environment: Authorized VulnWeb training application

## Tools Used

### Nmap

Used for:

- Port discovery
- Service detection
- Version detection
- Comprehensive enumeration

Important observations:

- 80/tcp was open
- Microsoft IIS httpd 8.5 was detected
- The application title was identified as acuforum forums
- TRACE was reported as a potentially risky HTTP method
- The ASP session cookie was reported without the HttpOnly flag

### Nikto

Used for web-server security checks.

Important observations:

- Missing HttpOnly cookie flag
- Missing X-Frame-Options header
- TRACE method enabled
- ETag/inode information disclosure
- Microsoft IIS/8.5 and ASP.NET information disclosure
- Accessible `/login.asp` page

### Burp Suite

Used to inspect HTTP traffic.

Captured:

- GET `/`
- GET `/showforum.asp?id=1`
- HTTP 200 responses
- Host and User-Agent headers
- ASP session cookie
- Server and application information

## Main Findings

1. ASP session cookie without HttpOnly
2. Missing X-Frame-Options
3. HTTP TRACE enabled
4. Server/technology information disclosure
5. ETag information disclosure
6. Login page exposed for review

## Recommendations

- Configure secure session-cookie attributes.
- Add an appropriate anti-clickjacking policy.
- Disable TRACE if it is not required.
- Minimize unnecessary server/version disclosure.
- Review ETag configuration.
- Review authentication and access controls around the login functionality.

## Learning Outcome

This practical demonstrated the basic VAPT workflow:

**Discover → Enumerate → Inspect → Correlate → Document**

The exercise also showed that automated security-tool output should be treated as evidence and leads for investigation rather than automatically assuming that every reported item is an exploitable vulnerability.

## Evidence

Supporting screenshots and scan outputs are stored in:

- `01-Nmap/`
- `02-Nikto/`
- `03-Burp-Suite/`

The final report and presentation are stored in the root of the Week 5 submission folder.
