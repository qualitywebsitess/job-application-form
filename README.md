# Job Application Form

A self-contained, browser-based job application form covering personal details, education, employment history, skills, projects, awards, and referees.

[**View the live project**](https://qualitywebsitess.github.io/job-application-form/) · [**View the source**](https://github.com/qualitywebsitess/job-application-form)

## What it does

- Collects all 25 application questions in eight grouped sections with clear required-field validation.
- Supports repeatable entries for education, employment history, and referees, so applicants are not limited to one of each.
- Yes/no questions reveal a details field only when answered "Yes".
- Emails the completed application to the form owner through Web3Forms when an access key is configured, with a JSON download fallback. The layout is responsive and uses semantic labels for accessibility.

## How it is made

This is a single static `index.html` file with no build step, framework, or third-party dependency. All styling is scoped CSS in the document head, and all behavior is vanilla JavaScript at the end of the body. Repeatable sections use `<template>` elements that are cloned into the page on demand.

The form is entirely client-side: it builds a JSON object in the browser and, when `WEB3FORMS_ACCESS_KEY` is set near the top of the `<script>` block, POSTs a flattened copy to Web3Forms, which emails the answers to the configured address. Without a key, the response is downloaded to the applicant's device instead. A failed delivery also falls back to downloading, so no answer is lost.

The page handles personal data, so it is served over HTTPS (GitHub Pages does this automatically). No applicant information is stored by the site itself. Set the destination email address in your Web3Forms account, not in this repository.

## Run locally

Open `index.html` directly in a browser, or serve it over HTTP:

```bash
python3 -m http.server 4173
```

Then visit `http://localhost:4173/`. No installation or build step is needed. Network access is only required when a Web3Forms access key is configured.

## Project structure

```text
job-application-form/
├── index.html    # entire form: markup, styles, and behavior
├── README.md     # this file
└── .gitignore
```

## Design and attribution

Original implementation. No external fonts, images, scripts, or assets are loaded. Delivery, when enabled, uses the Web3Forms service; the project itself has no code dependencies.
