# life.pqa.icu — Blogger photo journal

Upload `contents/life.xml`. It is the complete theme; there are no companion files to install. CSS and JavaScript are embedded. Your photographs and writing come from Blogger posts, not the reference mockup.

## Install

1. In Blogger, select the correct blog. In Theme, use the menu next to Customize to back up your current theme.
2. In that menu, use Restore → Upload and select `contents/life.xml`. Alternatively, open Edit HTML, replace the entire template with the XML file's contents, and save.
3. If Blogger offers a mobile-theme setting, select the desktop/custom theme for mobile so Blogger uses this responsive layout rather than its separate legacy mobile theme.
4. Set the homepage post count to approximately 6 in Settings. This theme uses Blogger pagination, including on label and search results.
5. In Layout, the Blog Archive gadget can be configured to your preferred monthly archive style.

The theme does not configure the custom domain. Keep life.pqa.icu configured in Blogger's publishing settings.

## Write posts

- Use the exact label `Balcony` or `Camping`. Both may be used together; additional labels also appear in post metadata. All shows every post.
- Add a normal title and, optionally, a short opening paragraph.
- Insert photos with the Blogger editor. The first photo is the card cover; the next three distinct image URLs become its thumbnail strip. Posts without images show a text placeholder.
- Insert each gallery image as its own image block, as Blogger normally does. Consecutive image-only blocks become a full-width photo, a pair of photos, and then repeat. Text between images begins a new gallery group.
- Normal paragraphs, links, video embeds, and captions remain in the post. Figure captions remain attached. Legacy Blogger table-based captions are preserved in their original layout rather than moved into the gallery.
- Supply descriptive image alt text and use sufficiently large uploads. Cards crop to fill their frames; gallery photos also crop to the reference's proportions. Clicking linked images retains the image link created by Blogger.
- A label page uses the same responsive photo-card layout as the homepage.

## Navigation and appearance

All, Balcony, and Camping are always available on the homepage. The menu also includes Archive and a dark/light switch; on mobile post pages the menu contains the category navigation. Search submits to Blogger's native `/search` endpoint. Newer/older links use Blogger's own context-aware URLs. No feed API or external JavaScript library is required.

Light mode is the initial appearance. The optional dark-mode selection is remembered in the visitor's browser when storage is available. Thumbnails, gallery arrangement, search disclosure, and dark mode use JavaScript; post text, cover images, category links, pagination, and the native archive remain available without it.

## Validation and limits

Passed:
- XML parsing, namespace checks, section/widget structure, unique rendered IDs, and local includable references.
- JavaScript syntax check.
- Chromium fixture tests at 375, 650, and 1100 pixel widths: no horizontal overflow, three card thumbnails, gallery arrangement, preserved prose/captions, search open/close, dark-mode switch, and archive expansion.
- Visual inspection of desktop and mobile fixtures. Fixtures use placeholder images; your actual photography determines the final look.

The theme has not been uploaded to a live Blogger account. Local XML/browser tests cannot execute Blogger's server-side template compiler or confirm its generated archive widget. Blogger's Save/Restore step is the remaining platform validation. Test a real image post, text-only post, label, search, archive, and older/newer link after upload.

Blogger syntax references:
- https://support.google.com/blogger/answer/47270?hl=en
- https://support.google.com/blogger/answer/46995?hl=en
- https://support.google.com/blogger/answer/46888?hl=en

The theme is maintained in `contents/life.xml`. GitHub updates do not deploy it to Blogger; install the XML manually after each update.
