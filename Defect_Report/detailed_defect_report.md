# Defect Report: BUG-SAUCE-001

| Field | Details |
|---|---|
| **Defect ID** | BUG-SAUCE-001 |
| **Title** | UI Glitch: Incorrect/broken product images loaded across catalog for `problem_user` |
| **Module** | Product Catalog / UI Rendering |
| **Environment** | Chrome 124.0, Windows 11 Desktop, Target URL: https://www.saucedemo.com |
| **Severity** | High |
| **Priority** | Medium |
| **Reported Date** | October 29, 2026 |
| **Status** | Open |

---

## 1. Description
When authenticating with the test persona `problem_user`, the application successfully navigates to `/inventory.html`. However, all product item cards display the same static fallback image (`sl-404.jpg`) instead of rendering their respective specific product assets.

---

## 2. Preconditions
* User is on the login page (`https://www.saucedemo.com/`).
* Internet connection is active.

---

## 3. Steps to Reproduce
1. Navigate to `https://www.saucedemo.com/`.
2. Enter `problem_user` in the **Username** field.
3. Enter `secret_sauce` in the **Password** field.
4. Click the **Login** button.
5. Inspect the rendered image assets for all 6 inventory items on `/inventory.html`.

---

## 4. Expected Result
Each product card should display its unique item image matching the title (e.g., Backpack image for *Sauce Labs Backpack*, Bike Light image for *Sauce Labs Bike Light*).

---

## 5. Actual Result
All product cards render the exact same image (`/static/media/sl-404.168b1cce.jpg`), failing to show the relevant product thumbnails.

---

## 6. Screenshots / Attachments
* Path: `defect_reports/screenshots/problem_user_broken_images.png`

---

## 7. Additional Context / Impact
* **Impact:** High UI distortion. Users cannot visual inspect products before adding them to cart, leading to poor user experience.