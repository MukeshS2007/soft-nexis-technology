# Selenium Framework Types (POM, Data-Driven, Keyword-Driven & Hybrid)

## Introduction

When learning Selenium, you'll often hear about these framework types:

- **Page Object Model (POM)**
- **Data-Driven Framework**
- **Keyword-Driven Framework**
- **Hybrid Framework**

These are **not different Selenium tools**. They are simply different ways of organizing your automation project so it is easier to maintain.

---

# 1. Page Object Model (POM)

## Purpose

POM keeps all **web element locators and page actions** in one class.

Instead of writing Selenium code in every test, we create a page class.

---


✅ POM stores:

- Web element locators
- Page actions

---

# 2. Data-Driven Framework

## Purpose

Data-Driven Framework keeps **test data outside Java code**.

Examples:

- Excel
- CSV
- JSON
- Properties file


Every time new test data is needed, Java code must change.

---

### Summary

✅ Data-Driven stores:

- Username
- Password
- URL
- Search text
- Expected values

outside the Java code.

---

# 3. Keyword-Driven Framework

## Purpose

Instead of writing Java code, we write simple **keywords**.

Examples:

- OPEN_BROWSER
- OPEN_URL
- CLICK
- TYPE
- VERIFY

---
