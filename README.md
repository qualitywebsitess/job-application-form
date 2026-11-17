# Job Application Form

A self-contained, browser-based job application form covering personal details, education, employment history, skills, projects, referees, and document attachments.

[**View the live project**](https://qualitywebsitess.github.io/job-application-form/) · [**View the source**](https://github.com/qualitywebsitess/job-application-form)

## What it does

- Collects all 25 application questions in nine grouped sections with clear required-field validation.
- Supports repeatable entries for education, employment history, and referees, so applicants are not limited to one of each.
- Accepts multiple document attachments (CV, academic certificates, training certificates, and other files), which are read in the browser and embedded in the exported response as data URLs.
- Yes/no questions reveal a details field only when answered "Yes".
- Exports the completed application as a timestamped JSON file, or POSTs it to a configurable endpoint. The layout is responsive and uses semantic labels for accessibility.

## How it is made

This is a single static `index.html` file with no build step, framework, or third-party dependency. All styling is scoped CSS in the document head, and all behavior is vanilla JavaScript at the end of the body. Repeatable sections use `<template>` elements that are cloned into the page on demand.

The form is entirely client-side. By default nothing is transmitted: responses are assembled into a JSON object and downloaded to the applicant's device. A form owner who needs server collection can set `SUBMIT_ENDPOINT` near the top of the `<script>` block to a URL that accepts a JSON `POST`. If that request fails, the form falls back to downloading the response so no applicant data is lost.

Because the page itself handles personal data and file attachments, it should be served over HTTPS (GitHub Pages does this automatically). The default download-only behavior means the hosted page stores no applicant information.

## Run locally

Open `index.html` directly in a browser, or serve it over HTTP:

```bash
python3 -m http.server 4173
```

Then visit `http://localhost:4173/`. No installation, environment variables, or network access is required at runtime.

## Project structure

```text
job-application-form/
├── index.html    # entire form: markup, styles, and behavior
├── README.md     # this file
└── .gitignore
```

## Design and attribution

Original implementation. No external fonts, images, scripts, or assets are loaded, and there are no third-party runtime dependencies.
