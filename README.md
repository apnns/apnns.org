# Asia Pacific Neural Network Society's Website

apnns.org website code based on [Hugo](https://gohugo.io) extended version 0.54+

<!-- TOC -->

- [1. Usage](#1-usage)
  - [1.1. Running the Site](#11-running-the-site)
  - [1.2. Structure](#12-structure)
  - [1.3. Creating a New Content](#13-creating-a-new-content)
  - [1.4. Checks Before Building the Pages](#14-checks-before-building-the-pages)
- [2. Building the HTML Pages](#2-building-the-html-pages)

<!-- /TOC -->

## 1. Usage

This is a static site generator based on Go language template.

### 1.1. Running the Site

1. Download the Hugo extended version from [https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases). Add it to your path.
2. Clone this repository
3. Open CMD/Terminal and `cd` to the cloned repository.
4. Type in `hugo serve` or `hugo server`, then open your web browser and type in `http://localhost:1313/`

### 1.2. Structure

Ignore the folders that say `# Ignore`

```
root
|   config.toml
|
+---archetypes # Ignore
|       default.md
|
+---content  # Every markdown file is a webpage
|       awards.md
|       bog.md
|       bylaws.md
|       competition.md
|       conference.md
|       education.md
|       industry-relations.md
|       membership.md
|       publications.md
|       _index.md
|
+---data  # Ignore
+---layouts  # Ignore
+---public  # All these files should be uploaded to the FTP (DO NOT ADD THIS TO VERSION CONTROL)
|   |   index.html
|   |   index.xml
|   |   sitemap.xml
|   |
|   +---awards
|   |       index.html
|   |
|   +---bog
|   |       ...
|
+---resources  # Ignore
|   \---_gen
|       +---assets
|       \---images
+---static  # File that can be used within *.md files (root/content/)
|   +---img
|   |       ahirose.jpg
|   |       andrew.jpg
|   |       arik.jpg
|   |       blu.jpg
|   |       ...
|   |
|   \---pdf
|           APNNS-Newsletter2018-10-12.pdf
|           ...
|
\---themes  # Theme for this particular website
    \---apnns
        |   LICENSE  # DO NOT CHANGE THIS
        |   theme.toml  # DO NOT CHANGE THIS
        |
        +---archetypes
        |       default.md
        |
        +---layouts
        |   |   404.html
        |   |   index.html  # Main index file
        |   |
        |   +---awards
        |   |       single.html # This means a single page for awards only
        |   |
        |   +---bog
        |   |       single.html
        |   |
        |   +---bylaws
        |   |       single.html
        |   |
        |   +---competition
        |   |       single.html
        |   |
        |   +---conference
        |   |       single.html
        |   |
        |   +---education
        |   |       single.html
        |   |
        |   +---industry-relations
        |   |       single.html
        |   |
        |   +---membership
        |   |       single.html
        |   |
        |   +---partials # Minimal codes cane be imported any where in the themes (part of Hugo)
        |   |       footer.html
        |   |       head.html
        |   |       nav.html
        |   |       scripts.html
        |   |
        |   +---publications
        |   |       single.html
        |   |
        |   +---shortcodes # Shortcut codes (part of Hugo)
        |   |       bog-image.html
        |   |
        |   \---_default # If single.html is not provided this default page will be used (part of Hugo)
        |           baseof.html
        |           list.html
        |           single.html
        |
        \---static
            +---css
            |       uikit.min.css
            |
            +---img
            |       a.png
            |       apnns_logo.png
            |       icon.jpg
            |       n.png
            |       p.png
            |       s.png
            |
            \---js
                    uikit-icons.min.js
                    uikit.min.js
```

### 1.3. Creating a New Content

Open your Terminal/CMD and type in `hugo new education.md`, this will generate a new file under `contents/education.md` with the following contents:

```yaml
---
title: "Education" # Title of the page
date: 2019-03-24T13:32:44+13:00 # Date and time when it was created
draft: false # Render the page even though in development
menu:
    main: # Menu name is "main"
        weight: 6 # The order of this page in navbar is 6, always increment this
type: education # Type of page is education, an independent page
--- # Write only after this line
```

you can use GitHub type markdown format after the `---`.

Once this is done, you need to create a page under `themes/education/single.html` and Add

```go
{{ define "main" }}

    {{ .Content }}

{{ end }}
```

### 1.4. Checks Before Building the Pages

1. Make sure the `baseURL` pointing to the correct URL in `config.toml`.
2. Run and check if all the URLs/pages are working as expected by doing `hugo serve` in CMD/Terminal.

## 2. Building the HTML Pages

Open your Terminal/CMD and type in `hugo`, this will generate a folder `public` with all the files. Upload the contents of the folder to `www` in FTP.
