# Our Family — GitHub Pages website

A mobile-friendly family clothing-size directory with 18 starter profiles, nickname (“Known as”) support, upcoming birthday/anniversary reminders, and email-based change requests.

## Put the website on GitHub

1. Extract all files into your repository folder: `C:\Users\danep\Documents\codex\github\family` (please check the exact spelling of your local folder).
2. Edit `config.js` and replace the empty `updateEmail` with **your own** email address. This address will be visible in the website's source, which is normal for a `mailto:` contact form. Consider a dedicated address if you prefer.
3. Commit and push all files to GitHub (`index.html`, `styles.css`, `app.js`, `config.js`, `data/family.json`).
4. In the repository's GitHub **Settings → Pages**, select **Deploy from a branch**, `main`, folder `/(root)` and save.
5. Visit `https://YOUR-USERNAME.github.io/family/` (assuming the repository is named `family`).

**Use a local web server for testing.** Opening `index.html` directly with `file://` won't load JSON in some browsers. Run `python -m http.server 8000` from this folder and visit `http://localhost:8000` if Python is available.

## Access and privacy

The website opens without a password. GitHub Pages is public, and anyone can access the site files and `data/family.json`. Do not add private addresses or birth years to the repository. Use authenticated hosting and storage if the directory needs to be private.

## How updates work

- A family member selects their profile, reviews the pre-filled details, makes changes, and clicks **Send updates via email**.
- Their device's default email application opens a **draft**. They must press **Send**. The website itself cannot reliably deliver email or track submission status.
- You review the message, then update `data/family.json` manually in a text editor and push the change to GitHub.
- Never copy `privateAddress` or any `year` fields from email into `data/family.json`. The public schema only needs birthday `{ "day": 12, "month": 6 }` and events `{ "day": 5, "month": 8, "type": "anniversary", "with": ["mark"] }`.
- Updating just shoes or a shirt size should **not** erase other values. Only change the fields the email explicitly supplies.
- An update request does not automatically modify the website; you approve and publish it.
- Web-based email can be used if you manually copy the generated draft; `mailto:` is not a fully reliable submission method on devices without an email app configured.
- Email is not a secure vault. Get consent before collecting personal addresses or years, and use an access-restricted private system if you need to store them centrally. We recommend not including full birth years/addresses in ordinary email if stronger privacy is needed.

## Example published JSON profile

```
{
  "id": "rebekah",
  "name": "Rebekah",
  "knownAs": "Bex",
  "type": "female",
  "birthday": { "day": 18, "month": 4 },
  "sizes": { "tops": "UK 12", "waist": "UK 12", "length": "Regular", "footwear": "UK 5 / EU 38" },
  "notes": "Likes blue",
  "events": [{ "day": 11, "month": 7, "type": "anniversary", "with": ["mark"] }]
}
```

This illustrative entry would display **Bex's Birthday** and **Bex & Mark's Anniversary**. The original name `Rebekah` remains as a stable identifier behind the scenes. No year is shown or stored in the public entry.

## Dates

- The homepage lists upcoming events within the next **60 days** and names the person(s) involved.
- Birthday is driven by the optional profile `birthday` field.
- Other events are stored in optional `events` arrays; select `anniversary`, `birthday`, or `other`, and use `label` for other events.
- The `with` field names another person's `id`, e.g. `["mark"]`, so the homepage shows both names.
- For Feb 29 birthdays in non-leap years, reminders appear on Feb 28.
- The site intentionally does **not** publish full dates of birth or addresses.

## Shoe sizes

Listed UK/EU conversions are approximate, not exact equivalences. Retailers differ; always check the brand's size chart. Children's UK sizes are labelled infant/junior where applicable.

## Notes

- 18 people are included: 12 adults and 6 children, with designated guardians.
- There is no online shared database, authentication service, or automated merge system.
- Google Fonts is an optional external styling dependency; the website uses fallbacks if offline.
