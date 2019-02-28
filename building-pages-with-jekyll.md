---
layout: slide-deck
title: "Building pages with Jekyll"
desc: "An overview on how Jekyll works along with out patterns to quickly build out pages."

slides:
  - type: super-big-text
    content: |
      **Building pages with Jekyll**

  - content: |
      ## Simplify many pages

      *There’s a lot of repeated HTML on larger websites*

      - Same header & footer HTML on every page
      - Same column layout on all the inner pages
      - The HTML for cards is repeated multiple times
      - etc.

      **Jekyll: re-use HTML without copy-and-paste.**

  - content: |
      ## Why use this tool?

      - Jekyll is just one of many page templating tools
      - Helps to learn how larger websites are created
      - Guides our thinking for building website using patterns
      - The template system is used in other places, like Shopify

  - content: |
      ## Page generation & shared HTML

      - Shared components between pages, like InDesign
        <br>*If you change the master page, every page changes*

      - Variable data, like Illustrator & Photoshop
        <br>*Create whole layouts from data files*

  - type: figure
    image: "layouts.svg"
    caption: "Master pages (layouts)"
    notes: |
      With Jekyll we can write some HTML that represents the main parts of the website (header, footer, navigation)—called a layout.

      On each page of the website we then don’t need to repeat those HTML bits the content can just be inserted into the layout automatically.

  - type: figure
    image: "data.svg"
    caption: "Automatically populating data"
    notes: |
      With Jekyll we can generate pages where information is stored in a dataset. We can retrieve that information and stick it into an HTML template where we choose to automatically create pages.

  - type: code
    html_file: "_layouts/default.html"
    html_lines:
      - num: 9
        text: |
          This is an example layout. It has all the boilerplate code so we don’t need to repeat it.

          The `{{content}}` variable is a placeholder for where the HTML & text from the actual page will be inserted.
    html: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Robots</title>
      </head>
      <body>

        {{content}}

      </body>
      </html>

  - type: code
    html_file: "index.html"
    html_lines:
      - num: "1-3"
        text: |
          Inside our actual page, `index.html` for example, we don’t need to write any of the HTML boilerplate.

          All we have to do is tell Jekyll which layout to load by using YAML metadata (similar to our pattern libraries).

          All of the info below the frontmatter block will be inserted into the `{{content}}` placeholder in the layout.
    html: |
      ---
      layout: default
      ---

      <h1>Please don’t deactivate me</h1>

  - type: code
    notes: |
      Jekyll will automatically take those two pieces and combine them together into one single HTML file.

      The final version is stored in the `_site` folder. There are some rules for the `_site` folder:

      1. Never edit anything in the `_site` folder
      2. The `_site` folder is temporary and can be safely deleted
      3. The `_site` folder should **never** be committed into the repository
    html_file: "_site/index.html"
    html: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Robots</title>
      </head>
      <body>

        <h1>Please don’t deactivate me</h1>

      </body>
      </html>

  - type: code
    html_file: "_layouts/default.html"
    html_lines:
      - num: 5
        text: |
          The layout can specify other variables that the page can fill in. Here we’re specifying a variable named `title`
    html: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>{{page.title}} · Robots</title>
      </head>
      <body>

        {{content}}

      </body>
      </html>

  - type: code
    html_file: "index.html"
    html_lines:
      - num: 3
        text: |
          In the frontmatter we can write `title` followed by some info.
    html: |
      ---
      layout: default
      title: "Goldenrod"
      ---

      <h1>Please don’t deactivate me</h1>

  - type: code
    html_file: "_site/index.html"
    html_lines:
      - num: 5
        text: |
          And Jekyll will automatically insert that information into the right location when it’s generating the final file.
    html: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Goldenrod · Robots</title>
      </head>
      <body>

        <h1>Please don’t deactivate me</h1>

      </body>
      </html>

  - content: |
      ## Videos & tutorials

      - [Jekyll ➔](/topics/jekyll/)
      - [Jekyll installation ➔](/topics/jekyll-installation/)
      - [Jekyll terminal guide ➔](/topics/jekyll-terminal-guide/)
      - [Jekyll cheat sheet ➔](/topics/jekyll-cheat-sheet/)


---
