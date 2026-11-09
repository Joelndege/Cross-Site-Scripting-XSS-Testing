# Cross-Site Scripting (XSS) Testing

**Course:** 351 CP 81 — Comprehension 2  
**Review deadline:** 20 November 2026  
**Project:** Demonstrate reflected or stored XSS in a deliberately vulnerable local web application and implement input validation and output encoding.

## Project contents

- `index.html`, `methodology.html`, `findings.html`: three-page portfolio suitable for GitHub Pages.
- `demo.html`: local educational demonstration with vulnerable and safe rendering modes.
- `styles.css`: shared responsive visual styling.
- `REPORT.md`: practical demonstration and remediation report.
- `DEPLOYMENT.md`: repository and GitHub Pages setup checklist.

## Run locally

Use Python's static server from this directory:

```sh
python -m http.server 8000
```

Open `http://localhost:8000/` for the portfolio and `http://localhost:8000/demo.html` for the demonstration. Keep the intentionally vulnerable page local; do not deploy it publicly. Only deploy the portfolio pages (`index.html`, `methodology.html`, `findings.html`, and `styles.css`) to GitHub Pages.

## Before submitting

1. Add your name and allocated serial number to the portfolio and report.
2. Create a GitHub repository and replace the placeholder repository link in `index.html`.
3. Follow `DEPLOYMENT.md` to publish the portfolio pages through GitHub Pages.
4. Add `stanslausphillimon@gmail.com` as a repository collaborator.
5. Put the final repository URL and portfolio URL in the submission details in `DEPLOYMENT.md`.
6. Add screenshots and your actual test date to the report.

The portfolio currently contains placeholders because no GitHub account or repository URL was provided.
