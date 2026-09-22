# Change-Related Testing: The Basics

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/2f124f0b-ca23-481d-920d-70950b69ba1e" />


When software is changed (to fix a bug or add a feature), we must test it to make sure nothing went wrong. This is done using two simple steps:

---

## 1. Confirmation Testing (Re-Testing)
* **What it means:** Checking if the bug is actually fixed.
* **The Goal:** To confirm the specific problem is gone.
* **Simple Example:** A button was broken. The developer fixes it. You click the button again to see if it works now.

---

## 2. Regression Testing
* **What it means:** Checking the rest of the application that *wasn't* changed.
* **The Goal:** To make sure the new fix didn't accidentally break old features.
* **Simple Example:** Since you fixed that button, you now quickly check the Login page and the Profile page to make sure they are still working perfectly.

---

## 📊 Quick Summary

| Testing Type | What does it check? | Key Question |
| :--- | :--- | :--- |
| **Confirmation** | The specific fix/change. | *"Did we fix the bug?"* |
| **Regression** | The rest of the app. | *"Did we break anything else?"* |
