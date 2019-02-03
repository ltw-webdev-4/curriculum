---
layout: lesson
title: "Integrating JavaScript into your pattern library"
desc: "Walk through the process of integrating JavaScript into your pattern library: both JavaScript you’ve written & 3rd-party JavaScript."

hide_markbot: true

goal:
  before: |
    We’re going to explore how to include JavaScript in our pattern library, specifically how to integrate the form validation helper.

    But some of you may want to include more JavaScript in the future—so this will help you set it up.
  no_image: true
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

steps:
  - title: "Download the form validation helper"
    before: |
      Let’s start some JavaScript integration in our pattern library by including the form validation helper that we previously explored. It will be very helpful when completing our form patterns.

      ### [Download `form-validation-helper` »](https://github.com/thomasjbradley/form-validation-helper/)

      ![](download-js.jpg)

      *Make sure to press “Download ZIP” instead of what we normally press.*

  - title: "Move & rename the code file"
    before: |
      Inside the download package there is a file named `index.js`—that’s the file that we need.

      But keeping it called `index.js` isn’t helpful for us—it’s not descriptive enough.

      So, let’s move it and rename it:
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "css"
        type: folder
        indent: 1
        fade: true
      - label: "images"
        type: folder
        indent: 1
        fade: true
      - label: "_patterns"
        indent: 1
        type: folder
        fade: true
      - label: "js"
        indent: 1
        type: folder
        notes: "Make a new js folder in your repo"
      - label: "form-validation-helper.js"
        indent: 2
        notes: "Move index.js here & rename it"
    after: |
      1. Make a new `js` folder within your `ecommerce-pattern-library` folder.
      2. Then move the form validation helper’s `index.js` into your new `js` folder.
      3. Rename `index.js` to `form-validation-helper.js`

  - title: "Make a main JavaScript file"
    before: |
      Integrating JavaScript into our pattern library follows the identical format to CSS: a `main.js` file with a bunch of includes inside it.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "css"
        type: folder
        indent: 1
        fade: true
      - label: "images"
        type: folder
        indent: 1
        fade: true
      - label: "_patterns"
        indent: 1
        type: folder
        fade: true
      - label: "js"
        indent: 1
        type: folder
      - label: "form-validation-helper.js"
        indent: 2
        fade: true
      - label: "main.js"
        indent: 2
        notes: "A brand new file"
    code_before: |
      Inside your code editor, make a new file and immediately save it to your `js` folder named exactly `main.js`—this will be the shared JavaScript code file, just like our `main.css`

      Now add this code into your `main.js` file:
    code_lang: js
    code_file: "js/main.js"
    code: |
      ---
      ---

      {% include_relative form-validation-helper.js %}
      {% pattern_js %}
    lines:
      - num: 5
        text: |
          This will look inside every pattern you have for `.js` files and include them into this location.
    after: |
          **We can add JavaScript files in our patterns the same way we add CSS files: just right inside the pattern’s folder.**
---
