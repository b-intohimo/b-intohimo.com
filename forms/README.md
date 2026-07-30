# WPForms — Contact form

Contact form for the b-intohimo Contact page.

## Fields

| Field | Type | Required |
|-------|------|----------|
| Email | email | yes |
| Subject | single line text | yes |
| Message | paragraph text | yes |

## Import into WordPress

1. In WordPress admin go to **WPForms → Tools → Import**
2. Choose **`contact-form.json`** from this folder
3. Click **Import**
4. Go to **WPForms → All Forms** and note the form **ID** (usually `1` on a fresh site)
5. If the ID is not `1`, update:
   - `forms/config.json` → `form_id_after_import`
   - `content/pages/contact.html` → replace `id="1"` in the wpforms shortcode/block with your ID
6. Commit and push to GitHub, then **Tools → GitHub Sync → Fetch from GitHub**  
   — or edit the Contact page in WordPress and embed `[wpforms id="YOUR_ID"]`

## Embed on Contact page

The Contact page (`content/pages/contact.html`) already includes:

```
[wpforms id="1" title="false" description="false"]
```

Notifications are sent to `{admin_email}` with reply-to set to the submitter's email.

## Styling

Form submit button uses brand color `#5060a0` (set in the JSON export).  
Additional layout styles are in `assets/style.css` (`.bint-contact-form`).
