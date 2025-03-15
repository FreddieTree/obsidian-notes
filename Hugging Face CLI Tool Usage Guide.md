---
tags:
  - HuggingFace
  - CLI
---

## **1. Getting Started with the CLI**

- **Installation:**  
  - Install the CLI via pip:
    ```bash
    pip install huggingface_hub
    ```
- **Login:**  
  - Login to your Hugging Face account:
    ```bash
    huggingface-cli login
    ```

---

## **2. Common CLI Commands**

- **Clone a Repository:**
 ```bash
  huggingface-cli repo clone <repo-name>
 ```
* ***Enable Large Files:**
For handling files larger than 5GB:
```bash
huggingface-cli lfs-enable-largefiles .
```
* **Upload Files:**
After committing, simply push your changes using Git:
```bash
git push
```
