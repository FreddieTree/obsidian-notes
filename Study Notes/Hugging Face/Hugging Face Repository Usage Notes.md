---
title: Hugging Face Repository Usage Notes
tags:
  - HuggingFace
  - Repository
  - Git
  - Workflow
---
# **Hugging Face Repository Usage Notes**

## 1. Creating a New Repository & File Management

- **Create a New Repo:**
  - Visit [huggingface.co/new](https://huggingface.co/new) to create a new repository.
  - *Set the repository type* (Model, Dataset, or Space) and configure its visibility.

- **Creating a New File:**
  - Click the **New File** button on the repository page.
  - **Name your file** and add the desired content.
  - Provide a **commit message** that summarizes your changes.
  - **Pull Request Option:** Select *Open as a pull request* so that your changes go through a review process instead of being pushed directly to the main branch.

> **Tip:** Consider creating a separate note for a detailed **Pull Request Workflow**. See [[Pull Request Workflow]].

---

## 2. Terminal Operations: Cloning and Adding Files

For detailed terminal commands and best practices, see the note [[Terminal Operations and Repository Management]].

**Basic Commands:**

| **Repository Type** | **Command**                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------- |
| **Model Repo**      | `git clone https://huggingface.co/FreddieTree/<model-name>`<br>`cd <model-name>`              |
| **Dataset Repo**    | `git clone https://huggingface.co/datasets/FreddieTree/<dataset-name>`<br>`cd <dataset-name>` |
| **SSH Clone**       | `git clone git@hf.co:FreddieTree/<model-name>`<br>`cd <model-name>`                           |

---

## 3. Git LFS and Large File Support

- **Git LFS Overview:**
  - **Git LFS** is used to manage files larger than *10 MB*.
  - **Installation:** Run `git lfs install` in your repository.

- **Tracking Additional File Types:**
  - If your file type is not automatically handled, run:
    ```bash
    git lfs track "*.your_extension"
    ```

- **For Files > 5GB:**
  - Enable large file support with:
    ```bash
    huggingface-cli lfs-enable-largefiles .
    ```


---

## 4. Pushing Files to Repository

**Step-by-Step Commands:**

```bash
# Create or modify your files
git add .
git commit -m "First model version"  # Use a descriptive commit message
git push

```

## **5. Additional Best Practices and Automation**

• **Branching & Version Control:**

	Create branches for significant updates or experimental features.
Use **tags** for release versions to facilitate rollbacks.
**See also:** [[Git Branching and Version Control]]

• **File Structure & Attributes:**
Maintain a clean directory structure with appropriate **.gitignore** and **.gitattributes** configurations.

• **Permissions:**
Choose between public or private repositories based on project needs.
Manage collaborator access carefully.

• **CI/CD Integration:**
Use **Webhooks** to trigger automated testing, building, and deployment processes.
**Hugging Face CLI:**
The CLI is a powerful tool for repository management tasks such as logging in, uploading, and downloading.
**See also:** [[Hugging Face CLI Tool Usage Guide]]

| **Task**           | **Command/Link**                                                     |
| ------------------ | -------------------------------------------------------------------- |
| Clone Model Repo   | git clone https://huggingface.co/FreddieTree/<model-name>            |
| Clone Dataset Repo | git clone https://huggingface.co/datasets/FreddieTree/<dataset-name> |
| Install Git LFS    | git lfs install                                                      |
| Enable Large Files | huggingface-cli lfs-enable-largefiles .                              |
| Open as PR         | Use the **Open as a pull request** option in the web interface       |
