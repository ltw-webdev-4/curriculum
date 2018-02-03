---
layout: lesson
title: "Pattern Library README"
desc: "Pattern libraries need to provide more information that just the pattern code—they need to explain why."

extra_tutorials:
  - title: "Pattern libraries"
    url: pattern-libraries
  - title: "Pattern libraries slide deck"
    url: "/courses/web-dev-4/pattern-libraries/"
  - title: "Markdown"
    url: markdown
  - title: "YAML"
    url: yaml
  - title: "Markdown & YAML cheat sheet"
    url: markdown-yaml-cheat-sheet
    highlight: true
  - title: "Markdown & YAML slide deck"
    url: "/courses/web-dev-4/markdown-yaml/"

goal:
  no_image: true
  before: |
    In order to make our pattern library effective for other people we need to describe lots of the different pieces—saying when and why to use the patterns.

    The `README.md` files are used specifically for describing all the settings, patterns, etc. within our pattern library.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

steps:
  - title: "Company name & description"
    before: |
      We’re going to update and add some information to the `README.md` file within our pattern library.

      We’ll start by adding the company’s name and a quick description at the top.
    code_lang: markdown
    code_file: "README.md"
    code: |
      ---
      name: "Super Company"
      fontUrl: "https://fonts.googleapis.com/css?family=Overpass:400,400i,700|Source+Code+Pro:400,700"
      ---

      This is the company introduction—we’re so amazing and our brand signifies awesomeness!
    lines:
      - num: 1
        fade: true
      - num: "3-4"
        fade: true
      - num: 2
        text: |
          This is the name of the company the pattern library is for, a.k.a. your eCommerce website.
      - num: 6
        text: |
          After the chunk of YAML we’ll write a little description of the company. This is all Markdown and will be displayed after the company in the pattern library.
    after: |
      If you re-generate your pattern library and give it a look you should see your information now.

      ![](readme-company.jpg)

      *If you can’t see what you wrote, drop the folder into Markbot and make sure there are no error messages.*

    notes:
      - label: "Naming conventions"
        text: |
          Yes, the README files completely break our naming convention. But it’s a community convention, all on its own, to name readmes with capital letters.

  - title: "Type choice descriptions"
    before: |
      One of the major goals of the pattern library is to explain why the patterns exist and when to use the patterns. That equally applies to the type choices.

      So next up, we’ll describe why we chose the fonts we did and when they should be used.

      **Remember you’re describing your eCommerce website—don’t just copy this information below.**
    code_lang: markdown
    code_file: "README.md"
    code: |
      ---
      name: "Super Company"
      fontUrl: "https://fonts.googleapis.com/css?family=Overpass:400,400i,700|Source+Code+Pro:400,700"
      fonts:
        primary: |
          The primary typeface represents a strong and bold face with lines that show stability and arrogance to fully express the power and dominance of our company.

          Use the primary typeface for body copy, captions and should really anything by default.
        secondary: |
          The secondary typeface is a compressed serif that really shows strength and dominance over our domain.

          The secondary typeface should be used for headings, buttons and to highlight important things.
      ---

      This is the company introduction—we’re so amazing and our brand signifies awesomeness!
    lines:
      - num: "1-3"
        fade: true
      - num: "13-15"
        fade: true
      - num: 4
        text: |
          Make a new entry named `fonts`, this will describe all the typography related information.
      - num: 5
        text: |
          Using the `primary` entry we can describe the primary typeface—especially describe why you chose it and when to use it.

          Notice the vertical pipe (`|`) this signifies a block of text—you can use Markdown in here.
      - num: 9
        text: |
          Also describe the `secondary` typeface choice’s whys & whens.
    after: |
      **Be really careful with your indentation—YAML treats indentation with extreme importance.**

  - title: "Colour descriptions"
    before: |
      Next up is the color choices; describe primary, secondary, accent, etc. colours using a format similar to the type.
    code_lang: markdown
    code_file: "README.md"
    code: |
      ⋮
        secondary: |
          The secondary typeface is a compressed serif that really shows strength and dominance over our domain.

          The secondary typeface should be used for headings, buttons and to highlight important things.
      colors:
        primary: |
          The primary colours are amazing and represent amazingness. Use them for headers, footers and emphasis.
        secondary: |
          The secondary colours represent things and stuff. Use them for links or when you want an extra pop.
        neutral: |
          The neutral colours are bland. Their real purpose is for body copy, captions, tables, etc.
      ---

      This is the company introduction—we’re so amazing and our brand signifies awesomeness!
    lines:
      - num: "2-5"
        fade: true
      - num: 6
        text: |
          Add a `colors` entry to start describing the colours. Patternbot is cool and will accept the correct spelling with a “u” too.
      - num: "7-12"
        text: |
          The entries can be `primary`, `secondary`, `neutral` and `accent`
      - num: "13-15"
        fade: true
    after: |
      *Re-generate your pattern library with Patternbot and make sure the text is all visible and looks the way you want.*
---
