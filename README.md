# ShrinkWatch

**A Zero-Budget Shrinkflation Scanner Built with Flutter**

ShrinkWatch is a mobile app that detects shrinkflation — when product sizes decrease but prices remain the same or increase.

Using barcode scanning, on-device OCR, and crowdsourced validation, ShrinkWatch helps shoppers track silent size reductions in everyday grocery products.

---

## Problem

Grocery products quietly shrink:

* 64 oz → 59 oz
* 200 g → 170 g
* Taller box, less cereal

Prices rarely decrease. Consumers are rarely informed.

ShrinkWatch makes shrinkflation visible.

---

## Tech Stack

Built entirely with **free and open-source tools**:

* **Flutter** – Cross-platform mobile framework
* ZXing – Barcode scanning
* Google ML Kit – On-device barcode & text recognition
* Tesseract – OCR for reading package sizes
* OpenCV – Image preprocessing for OCR accuracy
* Open Food Facts – Open product database
* Firebase (Firestore – Free Tier) – Cloud database
* SQLite (optional offline mode)

---

## Core Features (MVP)

### 1. Barcode Scanning

* Scan product barcode using phone camera
* Auto-detect UPC/EAN codes
* Lookup product in local/cloud database

### 2. Size Extraction via OCR

* Capture product label image
* Extract text like “Net Wt 500 g”
* Parse numeric size & units
* Compare against historical size

### 3. Shrink Detection

If:

```
New Size < Previous Size
```

→ Log a Shrink Event

Example:

```
Old Size: 200g
New Size: 170g
Shrink: 15%
```

### 4. Crowdsourced Verification

* Mark shrink events as “Pending”
* Require multiple confirmations
* Community validation model

---

## Data Model

### Products

| Field        | Type                 |
| ------------ | -------------------- |
| barcode      | String (Primary Key) |
| name         | String               |
| brand        | String               |
| current_size | Double               |
| unit         | String               |

### Scans

| Field         | Type     |
| ------------- | -------- |
| scan_id       | String   |
| barcode       | String   |
| detected_size | Double   |
| unit          | String   |
| timestamp     | DateTime |
| image_url     | String   |

### ShrinkEvents

| Field             | Type    |
| ----------------- | ------- |
| event_id          | String  |
| barcode           | String  |
| old_size          | Double  |
| new_size          | Double  |
| shrink_percentage | Double  |
| confirmed         | Boolean |

---

## App Flow

1. Open app
2. Scan barcode
3. Product info loads
4. Capture label image
5. OCR extracts size
6. Compare with previous size
7. Log shrink event (if applicable)

---

## Deployment Strategy

* Flutter → Android (Primary Target)
* Firebase Firestore (Free tier)
* Firebase Hosting (Optional Web Dashboard)
* GitHub for version control

No paid APIs. No infrastructure cost.

---

## Why This Matters

Shrinkflation impacts:

* Consumer trust
* Price transparency
* Economic awareness

ShrinkWatch gives data back to shoppers.

---

## Future Improvements

* Price tracking integration
* Brand shrink trend analysis
* Notifications when favorite product shrinks
* Data visualization dashboard
* AI packaging change detection

---

## Project Type

College MVP
Zero budget
Open-source stack
Scalable architecture

---

## License

MIT License

---

## Author

Arvind Nandigam
B.Tech Student
Built as part of an academic innovation project
