# PQA Site v2

Minimal dark personal homepage for [pqa.icu](https://pqa.icu), implemented as a custom [Blogger](https://www.blogger.com/) XML theme.

The portfolio content is embedded directly in the theme. A published Blogger post is not required for the homepage to appear.

## Repository structure

```text
.
├── README.md
└── contents/
    └── hp.xml       # Complete Blogger theme
```

## Requirements

- A Google account
- A Blogger blog
- A plain-text editor for changing the XML
- Optional: `xmllint` for local XML validation
- Optional: a custom domain such as `www.pqa.icu`

There are no package dependencies and no build command.

## Clone the repository

```bash
git clone https://github.com/pham-anh/pqa-site-v2.git
cd pqa-site-v2
```

## Install the theme in Blogger

Test the theme on a temporary Blogspot address before connecting a production domain.

1. Sign in to [Blogger](https://www.blogger.com/).
2. Create or select the blog that will host the homepage.
3. Open **Theme**.
4. Before changing an existing blog, open the menu beside **Customize**, select **Backup**, and download the current theme.
5. Open **Theme → Edit HTML**.
6. Open [`contents/hp.xml`](contents/hp.xml) in a text editor and copy the complete file.
7. Replace all code in Blogger's theme editor with the copied XML.
8. Save the theme and select **View blog**.

Do not paste `hp.xml` into a Blogger post or page editor. It is a complete theme.

Once Blogger has a custom domain configured, its `blogspot.com` address redirects to that domain. Temporarily remove the custom domain in **Settings → Publishing** if you need to test the Blogspot address independently.

## Validate changes locally

On macOS, `xmllint` is normally available with the operating system:

```bash
xmllint --noout contents/hp.xml
```

No output means the XML is well formed.

This check validates XML syntax only. Blogger performs the final validation of its own `b:`, `data:`, and `expr:` template tags when the theme is saved.

## Customize the homepage

Edit [`contents/hp.xml`](contents/hp.xml) and search for the following text:

| Content | Search for |
|---|---|
| Name | `Anh Pham` |
| Role and location | `Backend &amp; cloud engineer` |
| Main introduction | `I build reliable software` |
| Selected work | `<section id="work">` |
| Skills | `<section id="skills">` |
| Experience | `<section id="experience"` |
| Certificates | `<section id="certificates">` |
| Education and languages | `<section id="education">` |
| Biography and hobbies | `<section id="about">` |
| Contact email | `pqa.dev@gmail.com` |
| Avatar URL | `raw.githubusercontent.com` |

Because this is XML, escape special characters in visible text:

```text
&  →  &amp;
<  →  &lt;
>  →  &gt;
```

Run `xmllint` after editing and before copying the theme into Blogger.

## Avatar

The current theme loads the avatar from:

```text
https://raw.githubusercontent.com/pham-anh/pqa-site/draft/homepage-redesign/static/avatar2025.png
```

This works while that branch remains available. For a permanent Blogger-hosted image:

1. Create a draft post in Blogger.
2. Insert the avatar image.
3. Switch the post editor to HTML view.
4. Copy the HTTPS URL from the image's `src` attribute.
5. In `contents/hp.xml`, replace the existing `raw.githubusercontent.com` URL with the copied URL.
6. Validate and reinstall the theme.

The draft post does not need to be published.

## Custom domain

Blogger serves a custom domain from a subdomain such as `www.pqa.icu`. The root domain can redirect to it.

### 1. Configure `www`

1. In Blogger, open **Settings → Publishing → Custom domain**.
2. Enter `www.pqa.icu` without `https://` or a trailing slash.
3. At the DNS provider, configure:

   ```text
   Type: CNAME
   Name: www
   Target: ghs.google.com
   ```

4. If Blogger displays a second account-specific security CNAME, add it exactly as shown. Do not invent this value.
5. Wait for DNS propagation and verify that `https://www.pqa.icu` shows the Blogger homepage.

An A record and CNAME cannot coexist with the same `www` name. Remove a previous `www` A record before creating the CNAME.

### 2. Redirect the root domain

Only change the root domain after `www.pqa.icu` works correctly.

Configure these four A records for the root (`@`):

```text
@    A    216.239.32.21
@    A    216.239.34.21
@    A    216.239.36.21
@    A    216.239.38.21
```

Then enable **Redirect domain** in Blogger so that:

```text
pqa.icu → www.pqa.icu
```

When **HTTPS availability** becomes active, enable **HTTPS redirect**. All of these addresses should eventually finish at `https://www.pqa.icu`:

```text
http://pqa.icu
https://pqa.icu
http://www.pqa.icu
https://www.pqa.icu
```

If the domain has CAA records, permit `letsencrypt.org` so Blogger can issue and renew its certificate.

## Updating the live homepage

There is no automatic deployment from GitHub to Blogger.

1. Create a branch for the change.
2. Edit `contents/hp.xml`.
3. Run `xmllint --noout contents/hp.xml`.
4. Review and merge the change into `main`.
5. Back up the current Blogger theme.
6. Copy the updated XML into **Blogger → Theme → Edit HTML**.
7. Save and check the desktop and mobile layouts.

## Rollback

If a change breaks the layout:

1. Open **Blogger → Theme**.
2. Open the menu beside **Customize**.
3. Select **Restore**.
4. Upload the last working theme backup.

You can also copy a previous version of `contents/hp.xml` from the Git history and reinstall it.

## References

- [Create a Blogger blog](https://support.google.com/blogger/answer/1623800?hl=en)
- [Use and customize Blogger themes](https://support.google.com/blogger/answer/1227173?hl=en)
- [Blogger layout tags](https://support.google.com/blogger/answer/46888?hl=en)
- [Back up a Blogger theme](https://support.google.com/blogger/answer/41387?hl=en)
- [Set up a Blogger custom domain](https://support.google.com/blogger/answer/1233387?hl=en-uk)
- [Enable HTTPS in Blogger](https://support.google.com/blogger/answer/6284029?hl=en)
