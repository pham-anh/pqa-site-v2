# PQA Homepage - ChatGPT Project Context

Use this file as the canonical context when updating the PQA personal homepage.

## Project

- ChatGPT project: `pqa`
- Repository: <https://github.com/pham-anh/pqa-site-v2>
- Production domain: <https://www.pqa.icu>
- Root domain: <https://pqa.icu> (redirects to `www` after Blogger setup is complete)
- Hosting: Blogger
- Blogger address: <https://pqa-homepage.blogspot.com>

## Purpose

Maintain a simple, low-visual-noise personal homepage for Pham Quynh Anh. The site presents selected engineering work, skills, experience, certificates, education, languages, personal projects, hobbies, and contact information.

## Design direction

- Near-black background with soft off-white text
- One system sans-serif font stack
- Restrained contrast for supporting text
- Generous spacing and thin separators
- No cards, gradients, decorative illustrations, animated effects, or unnecessary controls
- Keep the interface calm and easy on the eyes
- Preserve responsive behavior for desktop and mobile
- Use the 2025 avatar at `assets/avatar2025.png`

## Source of truth

- `contents/hp.xml` - complete Blogger XML theme and homepage content
- `assets/avatar2025.png` - homepage avatar
- `README.md` - installation, DNS, publishing, and rollback guide
- `CHATGPT_PROJECT.md` - reusable project context

The homepage is embedded directly in the Blogger theme. It does not require a published Blogger post.

## Content facts to preserve

- Name: Pham Quynh Anh / Anh Pham
- Role: Backend and cloud engineer based in Osaka
- Main technologies: Go, PHP, Google Cloud, Kubernetes, Docker, Linux, SQL, Playwright
- Career transition: Japanese-Vietnamese interpreter to engineer in 2016
- Performance result: aggregation runtime reduced from 60 minutes to 10 minutes while expanding from about 200 million to 480 million records
- Search modernization: in development as of March 2026; results described as test-environment results until production evidence is available
- SimpleMath: personal Go application deployed on Cloud Run
- Worth Money: previously published iOS app; no longer available on the App Store
- OSS-DB Silver acquisition date: 8 October 2022
- Hobbies: camping and growing plants on a balcony
- Contact email: `pqa.dev@gmail.com`
- GitHub profile: <https://github.com/pham-anh>

Do not invent business results, production outcomes, dates, credentials, or current employment details. Ask for updated facts when a requested change depends on information not recorded here.

## Update workflow

1. Pull the latest `main` branch.
2. Read `CHATGPT_PROJECT.md`, `README.md`, and `contents/hp.xml`.
3. Make focused edits in `contents/hp.xml`.
4. Keep Blogger XML escaping valid (`&amp;`, `&lt;`, and `&gt;`).
5. Validate the theme:

   ```bash
   xmllint --noout contents/hp.xml
   ```

6. Review the diff and verify that unrelated content was not removed.
7. Update `README.md` when installation, domain, asset, or publishing behavior changes.
8. Commit and push the repository only when requested.
9. Blogger deployment is manual: back up the current theme, then paste the complete `contents/hp.xml` into **Blogger → Theme → Edit HTML**.
10. Check desktop and mobile layouts after saving.

## Domain rules

- Blogger serves the site at `www.pqa.icu`.
- DNS uses `www` as a CNAME to `ghs.google.com`.
- The root `pqa.icu` uses Blogger's four A records and redirects to `www.pqa.icu`.
- Do not change or remove DNS records for unrelated subdomains such as `123`, `blog`, `money`, or `worthmoney`.
- Do not change DNS, Blogger publishing settings, or the live theme unless the user explicitly requests that external action.
- Consult the exact DNS table in `README.md` before advising on domain changes.

## Avatar

The Blogger theme uses this stable raw asset URL:

```text
https://raw.githubusercontent.com/pham-anh/pqa-site-v2/main/assets/avatar2025.png
```

If the avatar filename or location changes, update both `contents/hp.xml` and `README.md`.

## Reusable prompt

Use this prompt to begin a future ChatGPT conversation inside the `pqa` project:

```text
Update my PQA homepage using the pqa-site-v2 repository. Read CHATGPT_PROJECT.md, README.md, and contents/hp.xml first. Preserve the minimal dark design and validate the Blogger XML with xmllint. Make the requested change, show me what changed, and commit and push only if I ask you to.
```

Then add the specific request, for example:

```text
Add my new project to Selected work. Here are the verified project details: ...
```

