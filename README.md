# SecureScope

Real-time browser security audit tool for cookies, sessions, and JWT authentication.

SecureScope is a Chrome Extension built using Manifest V3 that analyzes client-side session data to identify potential security vulnerabilities. It provides actionable insights into cookie configurations, authentication tokens, and browser storage to help developers and security enthusiasts understand and improve web application security.

---

## Features

### Audit Engine (Security Grading)
- Analyzes cookies in real time
- Assigns a Security Grade (A–F) based on:
  - HttpOnly flag validation
  - Secure flag enforcement
  - SameSite attribute checks (CSRF protection)
  - Session token length (basic entropy check)

### Live JWT Inspection
- Detects JWT tokens from:
  - Cookies
  - LocalStorage
- Decodes and displays:
  - Header
  - Payload (claims such as exp, iat, sub)
  - Signature
- Security warnings:
  - Expired tokens
  - alg set to none

### Panic Button (Session Purge)
- Clears session data for the active domain:
  - Cookies
  - LocalStorage
  - SessionStorage
- Useful for debugging and session testing

### Optional Breach Detection
- Integration with Have I Been Pwned API (k-anonymity model)
- Checks if user credentials appear in known data breaches

---

## Tech Stack

- Frontend: Quasar (Vue.js)
- Extension Framework: Chrome Extension Manifest V3
- APIs:
  - chrome.cookies
  - chrome.storage
  - chrome.tabs
- Languages: JavaScript, HTML, CSS

---

## Project Structure

```
SecureScope/
│── src/
│   ├── popup/          # Quasar UI (main interface)
│   ├── background/     # Service worker (logic)
│   ├── content/        # Content scripts (DOM and storage access)
│
│── manifest.json
│── README.md
```

---

## Installation

1. Clone the repository:
```
git clone https://github.com/your-username/securescope.git
cd securescope
```

2. Build the Quasar application:
```
quasar build
```

3. Open Chrome and navigate to:
```
chrome://extensions/
```

4. Enable Developer Mode

5. Click "Load Unpacked"

6. Select the project folder

---

## Permissions Used

```
{
  "permissions": [
    "cookies",
    "storage",
    "activeTab",
    "tabs"
  ],
  "host_permissions": [
    "<all_urls>"
  ]
}
```

---

## Use Cases

- Security auditing of web applications
- Debugging authentication and session issues
- Learning browser security concepts
- Testing OWASP Top 10 vulnerabilities

---

## Security Focus

- Broken Access Control
- Sensitive Data Exposure
- Weak Session Management
- CSRF and XSS risks via cookies and tokens

---

## Future Enhancements

- Advanced entropy analysis
- UI dashboard with historical scans
- Improved vulnerability scoring system
- Integration with additional security APIs
- DevTools panel support

---

## Contributing

Contributions are welcome. Fork the repository and submit a pull request with improvements or new features.

---

## License

This project is licensed under the MIT License.

---

## Final Note

SecureScope is designed as a client-side security audit toolkit to help identify real-world vulnerabilities directly within the browser.