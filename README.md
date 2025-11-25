Random Web Search Extension
A lightweight browser extension that opens a random web search from a list of configured search engines and queries. Useful for exploration, discovery, testing, or playful browsing.

Features
Open a random search in a new tab with one click.
Uses a configurable list of search engines and queries.
Simple, minimal UI (HTML + JavaScript).
Works as an unpacked extension in Chromium-based browsers and Firefox (developer mode).
Table of contents
Features
Installation
Usage
Configuration
Development
Contributing
License
Contact
Installation
To test or use locally:

Chrome / Edge / Chromium-based browsers

Open chrome://extensions.
Enable "Developer mode" (top-right).
Click "Load unpacked" and select the repository folder (the folder containing manifest.json).
Firefox

Open about:debugging#/runtime/this-firefox.
Click "Load Temporary Add-on..." and select the manifest.json file from the repository.
Note: If you publish to the Web Store or Firefox Add-ons, follow the respective store packaging and submission guidelines.

Usage
Click the extension icon (or use a configured keyboard shortcut) to open a new tab with a randomly chosen search engine and query.
Each click picks one engine and one query (from the configured lists) and opens the resulting search URL.
Configuration
The extension's behavior is controlled by its JavaScript configuration (an array of search engines and a list of sample queries). Typical locations and filenames in this repo are:

popup.html — UI
popup.js or background.js — main logic and engine/query lists
manifest.json — extension metadata and permissions
To customize:

Open the JavaScript file that contains the list of search engines and queries (look for an array named engines, searchEngines, or similar).
Edit or add search engine entries. A search engine entry commonly includes:
name: friendly name (e.g., "Google")
url: search URL template (e.g., https://www.google.com/search?q=%s) where %s or {query} is replaced by the query
Edit the list of queries (sample terms/phrases) to control what random searches are performed.
Save and reload the extension in the browser (chrome://extensions -> Reload).
Example engine entry (pseudo): { name: "Google", url: "https://www.google.com/search?q=%s" }

Replace %s with whatever placeholder the extension uses (check the JS to confirm — many use %s or {query}).

Permissions
For full functionality the extension may request:

"tabs" or "activeTab" — to open new tabs and navigate to the generated search URL.
Any other permission listed in manifest.json. Keep permissions minimal for privacy and security.
Development
Reload the extension after making code changes.
Keep UI and logic separated: popup HTML/CSS for UI, JS for behavior.
If adding features (options page, persistent storage), consider using storage permission and an options.html page to allow end users to edit the engine/query lists without editing source files.
Suggested development flow:

Make code changes locally.
Reload the unpacked extension in the browser.
Test by clicking the extension and verifying the random search opens as expected.
Contributing
Contributions are welcome. Suggested process:

Fork the repo.
Create a branch for your feature or bugfix.
Open a pull request with a clear description of the change and why it's useful.
Add tests or manual verification steps when applicable.
Please keep changes small and focused. If you want to add more search engines or localization, include examples in the repo and update this README.

Troubleshooting
Extension not appearing: ensure manifest.json is present and valid, and that the correct folder was loaded.
Random search not opening: check console logs in the extension popup (right-click popup -> Inspect) or background page for errors.
Placeholder mismatch: if searches open with %s or {query} in the URL, check that the JS replacement uses the same placeholder as the engine entries.
License
This repository does not include a declared license. If you want to allow others to reuse your code, add a license file (e.g., MIT License) to the repo. Example: create a LICENSE file with the MIT text.

Contact
If you want help improving this README or the extension code, open an issue or PR in this repository. You can also reach out via your GitHub account: https://github.com/shivranjan0
