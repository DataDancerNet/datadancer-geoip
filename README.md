# DataDancer GeoIP Database

Public distribution of the **DataDancer GeoIP** database in SQLite format, including an update manifest for automated client updates.

This repository contains:
- **`manifest.json`** – machine-readable update information (version, checksum, download URL, recommended TTL, rollout percentage).
- **Release assets** – compressed SQLite database (`.sqlite.zst`) and its SHA256 checksum.

The database is intended for use in the [DataDancer analytics/statistics system](https://datadancer.net), but it can be integrated into other projects.

---

## 📦 Latest Release

- **Manifest (CDN)**:  
  [https://cdn.jsdelivr.net/gh/DataDancerNet/datadancer-geoip@main/manifest.json](https://cdn.jsdelivr.net/gh/DataDancerNet/datadancer-geoip@main/manifest.json)
- **Releases**:  
  [https://github.com/DataDancerNet/datadancer-geoip/releases](https://github.com/DataDancerNet/datadancer-geoip/releases)

---

## 🔄 Update Workflow

Clients should:
1. Fetch `manifest.json` using HTTP `If-None-Match` (ETag) to check for updates.
2. Compare `version` and `sha256` from the manifest with their local copy.
3. If an update is needed, download the `.sqlite.zst` asset from the release specified in `asset`.
4. Verify the SHA256 checksum before replacing the local database.

**Example `manifest.json` structure:**
```json
{
  "version": "2025-08-15",
  "sha256": "abc123...",
  "asset": "geoip-20250815/geoip.sqlite.zst",
  "suggested_ttl_days": 45,
  "urgency": "normal",
  "rollout": 100,
  "created_at": "2025-08-15T00:00:00Z"
}
