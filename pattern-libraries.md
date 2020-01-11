---
layout: slide-deck
title: "Pattern libraries"
desc: "An introduction to pattern libraries, how to use them, what they’re for, and a tool, Patternbot, that we can use to generate a pattern library."

slides:
  - type: super-big-text
    content: |
      **Pattern libraries**

  - content: |
      ## Pattern libraries

      A common approach to designing websites

      - Break everything down into the smallest components
      - Write all the CSS individually
      - Combine the smaller components together into larger chunks, then into pages

      *Create a library to showcase all the pieces together*

  - content: |
      ## Pattern library examples

      - [MailChimp Pattern Library](http://ux.mailchimp.com/patterns)
      - [HMCTS Design System](http://hmcts-design-system.herokuapp.com/)
      - [U.S. Web Design System](https://designsystem.digital.gov/)
      - [Walmart Styleguide](https://walmartlabs.github.io/web-style-guide/)

  - type: three-col
    heading: Previous year pattern libraries
    col1: |
      #### For content sites
      - [Matt Peixoto](https://student-work.algonquindesign.ca/pattern-libraries/matt-peixoto/)
      - [Kayla Obritsch](https://student-work.algonquindesign.ca/pattern-libraries/kayla-obritsch/)
      - [Katrin Emery](https://student-work.algonquindesign.ca/pattern-libraries/katrin-emery/)
    col2: |
      #### For ecommerce websites
      - [Janelle Zhao](https://student-work.algonquindesign.ca/pattern-libraries/janelle-zhao/)
      - [Ksenia Zhelovatykh](https://student-work.algonquindesign.ca/pattern-libraries/ksenia-zhelovatykh/)
      - [Melany Pelletier-Vaillant](https://student-work.algonquindesign.ca/pattern-libraries/melany-pelletier-vaillant/)
      - [Adam Robillard](https://student-work.algonquindesign.ca/pattern-libraries/adam-robillard/)
    col3: |
      #### For ecommerce websites<br>(with sample pages)
      - [Sebastian Turner](https://student-work.algonquindesign.ca/pattern-libraries/sebastian-turner/pattern-library/) • [Sample pages](https://student-work.algonquindesign.ca/pattern-libraries/sebastian-turner/)
      - [Patricia Danochristos](https://student-work.algonquindesign.ca/pattern-libraries/patricia-danochristos/pattern-library/) • [Sample pages](https://student-work.algonquindesign.ca/pattern-libraries/patricia-danochristos/)
      - [Maddy Pierce](https://student-work.algonquindesign.ca/pattern-libraries/maddy-pierce/pattern-library/) • [Sample pages](https://student-work.algonquindesign.ca/pattern-libraries/maddy-pierce/)

  - content: |
      ## Many individual files

      We’ll have **lots** of different HTML & CSS files

      - *Buttons:* `buttons.html`, `buttons.css`

      - *Cards:* `link-card.html`, `image-card.html`, `cards.css`

      - *etc.*

  - content: |
      ## Shared CSS

      Some CSS will be shared, but only the most basic stuff:

      - `modules.css`
      - `grid.css`
      - `type.css`
      - `theme.css`

      The `theme.css` will contain the common fonts, colours & basic typography & CSS variables

  - content: |
      ## Class everything!

      Unless you’re working in the `theme.css`—**do not target HTML elements**

      Absolutely everything will have a class on it—to avoid conflicts

      The `theme.css` is the only place you’ll target `<h1>` or `<dl>`, etc.

  - content: |
      ## Pattern library generator

      We don’t want to—and shouldn’t have to—write all the CSS to make the library display website

      It’s much better to use a tool to generate the page

      *We can then concentrate on making the patterns—not on making the layout*

  - content: |
      ## Pattern library generators

      - [Fabricator](https://fbrctr.github.io/)
      - [Pattern Lab](http://patternlab.io/)
      - [Styleguide](https://hugeinc.github.io/styleguide/)

  - type: figure
    image: patternbot.svg
    caption: |
      **Jekyll Patternbot**—Your pompous and persnickety patterning robot.
      *A system for making pattern libraries, integrated with Jekyll for amazing static site generation.*
      [Jekyll Patternbot »](https://github.com/thomasjbradley/jekyll_patternbot/)

  - type: folders
    folders:
      - label: "my-pattern-lib"
        type: folder
      - label: "index.html"
        indent: 1
        notes: "Your standard homepage—but Jekyll-ified"
      - label: "_config.yml"
        indent: 1
        notes: "Customization & details about the brand"
      - label: "css"
        type: folder
        indent: 1
      - label: "modules.css"
        indent: 2
      - label: "grid.css"
        indent: 2
      - label: "type.css"
        indent: 2
      - label: "theme.css"
        indent: 2
        notes: "For shared CSS, common tags, colours & fonts"
      - label: "main.css"
        indent: 2
        notes: "Automatically combines all the CSS into one big file"
      - label: "images"
        type: folder
        indent: 1
      - label: "_patterns"
        type: folder
        indent: 1
        notes: "For each different pattern—Patternbot will add some defaults"
      - label: "buttons"
        type: folder
        indent: 2
        notes: "Each pattern gets its own folder…"
      - label: "buttons.html"
        indent: 3
        notes: "& HTML file (or many HTML files)"
      - label: "buttons.css"
        indent: 3
        notes: "& CSS file"
      - label: "config.yml"
        indent: 3
        notes: "Used to document the pattern"

  - content: |
      ## Videos & tutorials

      - [CSS variables ➔](/topics/css-variables/)
      - [Pattern libraries ➔](/topics/pattern-libraries/)
---
