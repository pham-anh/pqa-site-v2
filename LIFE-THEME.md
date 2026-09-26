# life.pqa.icu — Blogger Photo Journal

Custom Blogger theme ([`contents/life.xml`](file:///Users/quynhanhpham/my-project/pqa-site-v2/contents/life.xml)) written from scratch to match the clean, responsive photo journal design.

---

## Why the Previous Versions Rendered an Empty Page

In the previous versions, Blogger's server returned:
```html
<main id='journal' tabindex='-1'>
  <div class='main no-items section' id='main'></div>
</main>
```
The reason Blogger rendered `no-items section` (dropping `Blog1` completely) was:
- The template had `b:layoutsVersion='3'` and `b:defaultwidgetversion='2'` declared on `<html>`.
- In Blogger's Version 3 layout framework, widgets use a componentized model that **strictly requires `<b:defaultmarkups>`**.
- Without `<b:defaultmarkups>`, Blogger's v3 compiler cannot assemble the widget components, causing it to silently fail and drop the widgets from the section.

### The Solution: Clean Native Theme from Scratch
The updated [`contents/life.xml`](file:///Users/quynhanhpham/my-project/pqa-site-v2/contents/life.xml) has been written from scratch without the fragile v3 layout dependencies. It uses clean, direct Blogger XML templates that:
1. Guarantee that `<b:widget id='Blog1' type='Blog'>` compiles and renders directly into the section without relying on missing Google defaultmarkups.
2. Directly implement the exact layout from the design mockup.

---

## How to Apply in Blogger (Takes 1 minute)

> [!IMPORTANT]
> Apply via **Theme > Edit HTML** (not "Restore", which merges with cached layout states):

1. Go to your **[Blogger Dashboard](https://www.blogger.com/)** $\rightarrow$ `life.pqa.icu`.
2. In the left menu, click **Theme**.
3. (Optional) Click the dropdown arrow next to **Customize** and select **Backup** to save a copy.
4. Click the dropdown arrow next to **Customize** and select **Edit HTML**.
5. Select everything in the code editor (`Ctrl + A` or `Cmd + A`) and delete it.
6. Open [`contents/life.xml`](file:///Users/quynhanhpham/my-project/pqa-site-v2/contents/life.xml), copy the entire file content, and paste it into the Blogger HTML editor.
7. Click the **Save** icon (diskette icon in the top right).
8. Refresh `https://life.pqa.icu/` in your browser.

---

## Design Features & Matching the Mockup

1. **Desktop Header**:
   - Left: `life.pqa.icu` (brand) and `small moments outside work` (subtitle).
   - Right: Category links `All`, `Balcony`, `Camping` (active link has an underline indicator) and Search icon.
   - Hamburger menu is hidden on desktop (matches the mockup).

2. **Mobile Header & Drawer Navigation**:
   - Header top row: `life.pqa.icu`, Search icon, and Hamburger menu icon (three lines).
   - Header second row: Category tabs (`All`, `Balcony`, `Camping`).
   - When the Hamburger icon is clicked: Opens a menu panel with a close button (`✕`), links (`All`, `Balcony`, `Camping`, `Archive`), and the Dark mode switch.

3. **Homepage Post Cards**:
   - **Cover Photo**: The 1st photo in the post automatically becomes the large landscape cover photo.
   - **Meta & Category**: Shows relative date (e.g. `Sep 2025`) and category emoji badge (`🌿 Balcony` or `⛺ Camping`).
   - **Title**: Clean serif styling.
   - **Thumbnails**: The next 3 photos in the post (photos 2, 3, and 4) automatically form the 3 square thumbnails row below the title.

4. **Single Post Page**:
   - Top meta: Date + Category (`Apr 26, 2025 · 🌿 Balcony`).
   - Title: Large serif heading (`Spring herbs`).
   - Intro text: The first paragraph of the post is styled as a subtle intro/subtitle.
   - Photo Grid: Photos in the post body automatically format into the **1 - 2 - 1 - 2 alternating layout** (full-width hero, two side-by-side, full-width, two side-by-side).
   - Post pagination: `← Newer post`, `⌂`, `Older post →`.

5. **Dark Mode**:
   - Includes seamless light and dark mode toggling (`#faf9f7` light / `#191a18` dark) with visitor preference saved in `localStorage`.
