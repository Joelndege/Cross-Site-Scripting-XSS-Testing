# Practical XSS Demonstration and Remediation Report

**Course:** 351 CP 81 — Comprehension 2  
**Project:** Cross-Site Scripting (XSS) Testing  
**Student:** [Add name]  
**Allocated serial number:** [Add serial number]  
**Test date:** [Add date]  
**Review deadline:** 20 November 2026

## 1. Objective

Demonstrate reflected cross-site scripting behavior in a deliberately vulnerable local page, then compare it with safe output handling. The test is confined to the included page running on the student's own computer.

## 2. Scope and setup

The target is `demo.html`, served locally with `python -m http.server 8000`. No remote application is tested, and no information is collected or transmitted. This is a small client-side teaching simulation rather than a full server-backed application.

## 3. Procedure

1. Start the local server and open `http://localhost:8000/demo.html`.
2. In vulnerable mode, enter the harmless sample `<img src=x onerror=alert('XSS demo')>` and render it.
3. Observe the browser alert. The input was parsed as HTML, which created an image element; its error handler ran when the invalid image source failed.
4. Select safe mode and render the same value.
5. Observe that the complete payload is displayed literally and no alert appears.
6. Repeat with ordinary text, markup characters, empty input, and whitespace-only input.

## 4. Results

| Case | Vulnerable mode | Safe mode |
|---|---|---|
| Ordinary text | Displayed | Displayed as text |
| Markup and quotes | May be interpreted as markup | Displayed literally |
| Harmless event-handler sample | HTML element and handler execute | Payload remains visible text |
| Empty value | Fallback message shown | Fallback message shown |

The vulnerable branch uses `innerHTML`, an HTML parsing sink. The safe branch uses `textContent`, so the browser does not treat the value as markup. The value is read from the `q` URL parameter and reflected immediately; it is not stored.

## 5. Remediation

- Render untrusted text with `textContent` or a framework's escaped text interpolation.
- Validate input against the feature's expected length and format. Validation is complementary and does not make unsafe output insertion safe.
- When HTML is genuinely required, sanitize with a maintained, allowlist-based HTML sanitizer. For other output contexts, use the correct context-specific encoder or safe DOM API.
- Add a restrictive Content Security Policy as defense in depth; it does not replace safe output handling.

## 6. Limitations

This demonstration is client-side and only models reflected behavior. It does not implement persistence, server-side validation, or a complete vulnerability assessment. Browser and policy behavior may vary. The deliberately vulnerable mode is included only as an isolated teaching example and must not be deployed publicly.

## 7. Conclusion

The demonstration shows how treating a query value as HTML can turn input into browser-executable markup. Rendering that same value as text prevents the browser from interpreting it in this context. Input validation helps enforce the expected data rules, while safe output handling addresses the injection sink.

## 8. Evidence to attach

Add dated screenshots showing (a) the harmless payload and resulting alert in local vulnerable mode, and (b) the same payload displayed literally in safe mode. Do not include real credentials, personal data, or third-party targets.
