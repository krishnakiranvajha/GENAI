# Master Test Plan: VWO Login Dashboard

**Document Version:** 1.0
**Date:** 2026-03-14
**PRD Reference:** VWO Login Dashboard PRD
**AUT:** https://app.vwo.com/#/login

---

## 1. Test Strategy Overview

Validate that the VWO Login Dashboard meets all functional, non-functional, security, performance, and accessibility requirements. Strategy emphasizes edge-case and negative testing, cross-browser compatibility, and enterprise-grade security validation.

## 2. In-Scope

- Email/Password Login
- Google Sign-In (OAuth)
- SSO Login (SAML/OAuth)
- Passkey Authentication (WebAuthn)
- Remember Me
- Forgot Password Flow
- Free Trial CTA
- Input Validation and Error Handling
- Password Visibility Toggle
- UI/UX and Responsive Design
- Security (HTTPS, XSS, CSRF, brute force, session mgmt)
- Performance (page load, concurrent users, API response)
- Accessibility (WCAG 2.1 AA)
- Cross-Browser Testing
- API/Backend Validation
- Legal Compliance

## 3. Out-of-Scope

- Post-login dashboard
- VWO core platform features
- Biometric auth (future)
- Adaptive auth (future)
- PWA capabilities (future)

## 4. Test Types Required

| Test Type | Priority |
|---|---|
| Smoke Testing | Critical |
| Functional Testing | Critical |
| Negative Testing | Critical |
| Edge Case Testing | Critical |
| Integration Testing | Critical |
| E2E Testing | High |
| Regression Testing | High |
| Security Testing | Critical |
| Performance/Load Testing | High |
| Accessibility Testing | High |
| Cross-Browser Testing | High |
| Responsive Testing | High |
| Compliance Testing | High |

## 5. Test Scenarios (166 Total)

### 5.1 Email/Password Login (30 cases)
- TC-LGN-001: Valid login | Positive | Critical
- TC-LGN-002: Wrong password | Negative | Critical
- TC-LGN-003: Unregistered email | Negative | Critical
- TC-LGN-004: Empty email | Negative | Critical
- TC-LGN-005: Empty password | Negative | Critical
- TC-LGN-006: Both empty | Negative | Critical
- TC-LGN-007: Email with spaces | Edge Case | High
- TC-LGN-008: Mixed case email | Edge Case | High
- TC-LGN-009: Email with + and . | Edge Case | High
- TC-LGN-010: Invalid email format | Negative | Critical
- TC-LGN-016: SQL injection in email | Security | Critical
- TC-LGN-017: XSS in email | Security | Critical
- TC-LGN-020: Rate limiting | Security | Critical
- TC-LGN-024: Enter key submit | Functional | High
- TC-LGN-027: Double-click prevention | Edge Case | High

### 5.2 Password Toggle (6 cases)
### 5.3 Remember Me (8 cases)
### 5.4 Forgot Password (17 cases)
### 5.5 Google Sign-In (10 cases)
### 5.6 SSO Login (8 cases)
### 5.7 Passkey Auth (7 cases)
### 5.8 Free Trial CTA (5 cases)
### 5.9 Input Validation (8 cases)
### 5.10 UI/UX (13 cases)
### 5.11 Legal/Compliance (6 cases)
### 5.12 Security (13 cases)
### 5.13 Performance (9 cases)
### 5.14 Accessibility (10 cases)
### 5.15 Cross-Browser (6 cases)
### 5.16 API/Backend (10 cases)

## 6. Priority Distribution

| Priority | Count | % |
|---|---|---|
| Critical | 48 | 29% |
| High | 82 | 49% |
| Medium | 36 | 22% |
| **Total** | **166** | **100%** |

## 7. Automation Strategy

### Automate
- Smoke tests (Cypress/Playwright)
- Login functional tests (data-driven)
- API tests (REST Assured/Postman)
- Cross-browser (Playwright)
- Accessibility scans (axe-core)
- Performance (Lighthouse CI/k6)
- Security headers (OWASP ZAP)

### Do NOT Automate
- Exploratory testing
- Visual/design review
- Google OAuth full flow (mock instead)
- SSO IdP interaction (mock instead)
- Passkey WebAuthn prompts (stub instead)
- Penetration testing

## 8. Test Environments

| Environment | Purpose |
|---|---|
| DEV | Unit and integration testing |
| QA/Staging | Full functional, regression, E2E |
| Performance | Load and stress testing |
| Production | Post-deploy smoke tests |

## 9. Risk Assessment

| Risk | Impact | Mitigation |
|---|---|---|
| Brute Force | Critical | Rate limiting at API and UI |
| Session Hijacking | Critical | HttpOnly, Secure, SameSite flags |
| Password Reset Abuse | Critical | Token single-use and expiry |
| XSS/Injection | Critical | Input sanitization |
| OAuth Misconfiguration | High | State parameter validation |
| Accessibility Violations | High | axe-core scans + manual testing |

## 10. Reporting Metrics

- Pass Rate target: >= 95%
- Automation Coverage: >= 80%
- Critical defects in production: 0
- Defect resolution: <= 24hrs Critical, <= 72hrs High

---

*Full detailed test plan with all 166 test cases available in the complete testplan.md document.*
