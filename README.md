# SauceDemo E-Commerce Manual & REST API Testing Suite

## 📌 Project Overview
This repository contains a comprehensive, end-to-end QA Testing Suite for the **SauceDemo (Swag Labs)** e-commerce web application along with functional automation tests for **JSONPlaceholder REST APIs**.

The project covers complete Software Testing Life Cycle (STLC) deliverables including Test Planning, Test Case Creation, Test Execution, Defect Logging, and Postman API Testing.

---

## 📁 Repository Structure
```text
├── test_cases/
│   ├── manual_test_cases.csv                # Executed Test Matrix (33 Test Cases)
│   └── SauceDemo_Manual_Test_Cases_Suite.xlsx # Formatted Excel Execution Suite
├── defect_reports/
│   └── BUG_SAUCE_001.md                     # Detailed Defect Report for problem_user UI glitch
├── postman/
│   └── JSONPlaceholder_API_Tests.postman_collection.json # API Tests with Assertions
└── README.md                                # 
```
## Project Documentation

## 🛠️ Tools & Technologies
Manual Testing: STLC, Functional, Smoke, Sanity, Regression, Boundary Value Analysis (BVA), Negative Testing

API Testing: Postman, REST APIs, JSON Validation, HTTP Assertions

Documentation & Version Control: MS Excel, Markdown, Git, GitHub

## 📊 Test Execution Summary

Total Web Test Cases Executed: 33

Execution Status: 33 Passed / 0 Failed

Defects Logged: 1 Major Defect (UI Asset Rendering Glitch)

REST API Endpoints Tested: 9 Endpoints (GET, POST, PUT, DELETE)

## 🔍 Key Testing Highlights
1. Web Functionality Coverage
   
* Login Module: Positive login, invalid credentials, locked-out user validation, empty field errors, password masking, direct URL restriction (/inventory.html), and session logout.

* Products Module: Product catalog load, detail page navigation, and 4-way sorting (Name A-Z, Z-A, Price Low-High, High-Low).

* Cart Module: Item addition, dynamic badge counter update, item removal, cart persistence across pages.

* Checkout Module: Input validation (First Name, Last Name, Zip Code), order summary math calculation (Subtotal + Tax = Total), order placement, and cart auto-reset.

2. Defect Identified

* Defect ID: BUG-SAUCE-001

* Summary: Inconsistent asset rendering under problem_user profile where all products load a broken placeholder image (sl-404.jpg).

* Severity/Priority: High Severity / Medium Priority.

3. REST API Testing via Postman
Status Code Verification (200 OK, 201 Created, 404 Not Found).

* Response Time assertions (< 2000 ms).

* JSON schema and payload key-value structure validation.

## 🤝 How to Run
Clone the repository: git clone https://github.com/jigyasa1829/saucedemo-manual-api-testing.git

Open test_cases/SauceDemo_Manual_Test_Cases_Suite.xlsx in Excel or Google Sheets to inspect execution details.

Import postman/JSONPlaceholder_API_Tests.postman_collection.json into Postman to execute API tests.