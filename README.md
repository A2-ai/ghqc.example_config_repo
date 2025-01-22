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

Simple:
```
"Checklist name":
- item 1
- item 2
- item 3
```
The simple structure:
- begins with the name of the checklist to be displayed in `ghqc_assign_app()`
- each item is prepended with a tick mark.
- Note: to include a colon in a checklist item, wrap the item in quotes.
- Note: to span a checklist item across multiple lines, begin the first line with the pipe operator.

## Logo

## Options


