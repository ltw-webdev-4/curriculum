---
layout: slide-deck
title: "Piecing pages with patterns"
desc: "A super short exercise to get you thinking about what patterns are necessary for the homepage & product list page, and how each pattern will need to be configured."

slides:
  - type: super-big-text
    content: |
      **Piecing pages with patterns**

  - content: |
      ## A little pre-planning

      1. Write out a list of every pattern needed for the homepage
      2. Write out a sublist for each pattern describing how they need to be configured with placeholder variables
      3. Repeat the whole process again for the product list page

      *You should probably get the teacher to look over this.*

  - type: code
    markdown: |
      ## Homepage

      - banner
        - heading
        - description
        - image
        - button_text
        - button_url
      - cards
        - image
        - title
        - description
        - button_text
        - button_url
      - section
        - heading
        - image
---
