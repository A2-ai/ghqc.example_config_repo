# ghqc.example_config_repo
An example information repository for ghqc that stores an organization's QC checklists, logo, and options.

## Repo
The Information Repository created by an organization to load organization-specific attributes to ghqc apps can be named anything. The convention is to name in ghqc.org, where org is the organization name.

The https web URL is set as the GHQC_CONFIG_REPO environment variable for ghqc.
To configure ghqc to use this info repo, add the line to your .Renviron:
```
GHQC_CONFIG_REPO=https://github.com/A2-ai/ghqc.example_info_repo.git
```
Alternatively, input the https web URL when running `ghqc::setup_ghqc()`:

```
> ghqc::setup_ghqc()

── GHQC RENVIRON SETUP ───────────────────────────────────────────────────────────────────────────────────────────────

GHQC_CONFIG_REPO is not set in your ~/.Renviron
Provide the URL to the configuring information repository: https://github.com/A2-ai/ghqc.example_info_repo.git
✔ GHQC_CONFIG_REPO was successfully updated to https://github.com/A2-ai/ghqc.example_info_repo.git in ~/.Renviron

── CONFIGURING INFORMATION REPOSITORY ────────────────────────────────────────────────────────────────────────────────

Path to download the configuration information repository (~/.local/share/ghqc/ghqc.example_info_repo) 

→ Attempting to clone https://github.com/A2-ai/ghqc.example_info_repo.git to ~/.local/share/ghqc/ghqc.example_info_repo...
✔ Successfully cloned ghqc.example_info_repo to ~/.local/share/ghqc/ghqc.example_info_repo

── ghqc.example_info_repo Local Content ──

✔ logo.png successfully found

✔ 'note' successfully found

    “Checklist items should be editted by the author on GitHub after checklist generation by the app to
    include specific details about each selected qc file.The author should also add or subtract generated
    checklist items on a case-per-case basis.”
    — 

✔ Checklists directory successfully found

── Checklist directory content 
✔ advanced_checklist.yaml
✔ simple_checklist.yaml
```

### Repo Structure

The the config repo must have a folder named "checklists" in the root.
The logo.png and options.yaml are optional.

If the logo.png or options.yaml are included, they must have those names exactly to be recognized by ghqc.

## Checklists

Checklists should be located in the checklists folder.
All checklists are yaml files with one of the following structures:

### Simple structure

yaml contents:
```
General Script:
  - good documentation
  - only relative paths to sourced files
  - consistent style and naming conventions
```
Output rendered in GitHub Issue:

<img width="324" alt="Screenshot 2025-01-23 at 3 25 33 PM" src="https://github.com/user-attachments/assets/246b1040-df10-491d-ad34-48fa420e1004" />

The simple structure:
- begins with the name of the checklist to be displayed in `ghqc_assign_app()` as the key
- the value is a list of checklist items, each of which is prepended with a tick mark on a new line

### Header structure
yaml contents:
```
Report:
  Table of Contents:
    - depth of 2

  Body:
    - Page numbers exist on each page
    - Page numbers indicate total page length (e.g. Page 1 of 3)

  Tables and Figures:
    - Titles are correct
    - Captions are descriptive
    - Footnotes are accurate

  Appendix:
    - |
      Sources are given in one of the following formats:
        1) APA
        2) MLA
        3) Chicago
```
Output rendered in GitHub Issue:

<img width="432" alt="Screenshot 2025-01-23 at 3 26 29 PM" src="https://github.com/user-attachments/assets/4fd7c6a8-7489-4555-91cf-17ba532efee3" />

The header structure:
- begins with the name of the checklist to be displayed in `ghqc_assign_app()` as the key
- the value is a set of headers are given as keys themselves
- the value of each header key is a list of checklist items to appear under the header
- each checklist item is prepended with a tick mark on a new line

Extra considerations:
- Note: to include a colon in a checklist item, wrap it in quotation marks.\
  Example:
    ```
    - "the code is: readable, scalable, and documented"
    ```
- Note: to span a checklist item across multiple lines, begin the first line with the pipe operator, then start the checklist item contents on the next line.\
  Example:
  ```
  - |
      Sources are given in one of the following formats:
        1) APA
        2) MLA
        3) Chicago
  ```

## Logo

## Options


