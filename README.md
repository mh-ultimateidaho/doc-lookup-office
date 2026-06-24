# Office Doc Lookup

Browser-based search tool for office staff at Ultimate Logistics LLC.

**URL:** https://mh-ultimateidaho.github.io/doc-lookup-office/

---

## What It Does

Combines driver and equipment lookup with a deep search of the Office Documents folder in SharePoint.

### Sections
- **Drivers** — searches Driver Documents folder by last name.
- **Equipment** — searches Tractors, Trailers, and CA TRU Certificates by unit number.
- **Office Documents** — deep search across Office Documents subfolders with category filtering, smart aliases, and a "Where does this live?" hint.

---

## Technical Details

| Item | Value |
|------|-------|
| Hosting | GitHub Pages |
| Azure App | Office Lookup Tool |
| Client ID | fd8d0730-6d5c-4ac6-aa95-bfdb5dfb7385 |
| Tenant ID | 2c6b3d13-b98c-4605-8fcc-d8eed3579136 |
| Redirect URI | https://mh-ultimateidaho.github.io/doc-lookup-office/ |
| Permissions | Files.Read, Sites.Read.All (delegated, admin consented) |
| SharePoint Site | https://ultimatecorp.sharepoint.com/sites/UltimateLogisticsLLC |

### SharePoint Paths
| Category | Path |
|----------|------|
| Drivers | Shared Documents / Driver Documents |
| Tractors | Shared Documents / Equipment / Tractors |
| Trailers | Shared Documents / Equipment / Trailers |
| CA TRU Certs | Shared Documents / Equipment / Trailers / 1 CA TRU certificates |
| Agreements | Shared Documents / Office Documents / Agreements |
| Broker Packets | Shared Documents / Office Documents / Broker Packets |
| DACH | Shared Documents / Office Documents / DACH |
| EFS Money Codes | Shared Documents / Office Documents / EFS Money Codes |
| Factoring | Shared Documents / Office Documents / Factoring |
| Insurance | Shared Documents / Insurance |
| Onboarding | Shared Documents / Office Documents / Onboarding |
| Payroll | Shared Documents / Office Documents / Payroll |
| Templates & Forms | Shared Documents / Office Documents / Templates & Forms |

---

## Office Documents Search Features

- **Category filter** — narrow search to a specific subfolder. When a category is selected, uses folder traversal which accurately matches folder names (e.g. `5.31.26`). "All Office Documents" uses the SharePoint Search API.
- **Results limit** — choose 10, 25, 50, or 100 results. Defaults to 25.
- **Date normalization** — searching `05.31.26` automatically also searches `5.31.26`, `05/31/26`, and `5/31/26`.
- **Where does this live?** — collapsible hint card appears when the search term matches a known document type, showing its SharePoint path.

---

## Making Changes

### Search aliases
Find `SEARCH_ALIASES` near the top of the script in `index.html`:
```js
const SEARCH_ALIASES = {
  'certificate': 'COI',
  'cert': 'COI',
  'insurance': 'COI',
  // add more below this line — format: 'search term': 'file name',
};
```

### Adding a new category
Find the `officeCategory` `<select>` element in the HTML and add a new `<option>` line. Make sure the folder path matches exactly.

### Adding to the "Where does this live?" hint
Find the `LOOKUP_GUIDE` array in the script. Each entry has `terms`, `where`, and `path`. Add new entries following the same format.

### Redirect URI
If the tool moves to a new URL, add the new URL in Azure Portal → App registrations → Office Lookup Tool → Authentication → Single-page application.

---

## Troubleshooting

- **Sign-in not working** — check redirect URI in Azure matches the URL exactly. Try Ctrl+Shift+R.
- **Too many results** — select a specific category and/or lower the results limit.
- **Category search missing folder names** — make sure a category is selected; "All Office Documents" uses the Search API which may miss folder names.
- **Tool looks outdated** — hard refresh with Ctrl+Shift+R.

---

## Planned Updates
Updates/ideas to implement.
### Pending
- 

---
