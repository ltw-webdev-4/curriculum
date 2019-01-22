---
layout: slide-deck
title: "Piecing Jekyll together"
desc: "Using paper-made Jekyll replicas, piece together multiple pages by using Jekyll-like functionality."

slides:
  - type: super-big-text
    content: |
      **Piecing Jekyll together**

  - content: |
      ## What & why

      Jekyll provides us with lots of features to simplify making website and reducing duplication.

      It can be difficult to see how everything connects together and see now to use all the available pieces.

      **We’re going to visualize some of Jekyll’s features without writing any code.**

  - content: |
      ## Set up

      1. Form into pairs
      2. [Download & print the files](https://github.com/acgd-webdev-4/piecing-jekyll-together/archive/master.zip)
      3. Get a pencil to write with
      4. **Create the following pages using snippets of Jekyll code**
          1. Look at the patterns & see if they’re missing things
          2. Look at the layouts and determine what to insert
          3. Look at the pages and determine what to insert

  - content: |
      ## Definitions

      - **Pattern:** a reusable piece of a website

      - **Layout:** like an InDesign master page: contains all the site’s common elements

      - **Page:** a combination of layouts & patterns to make something a user would see

  - type: code
    before: |
      ### Snippets of Jekyll & Patternbot code
    html: |
      <!-- Finds a pattern, by filename, and inserts it into this location -->
      {% pattern __________ %}


      <!-- Repeats a pattern multiple times into this location
           You need to specify how many times the loop happens -->
      {% for (1..____) %}
        {% pattern __________ %}
      {% endfor %}

  - type: figure
    image: index.png
    caption: "`index.html`"

  - type: figure
    image: products.png
    caption: "`products.html`"

---
