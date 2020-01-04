---
layout: lesson
title: "Pattern Library customization"
desc: "Pattern libraries need to provide more information than just the pattern code—they need to explain why."

hide_markbot: true

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

    The `config.yml` files are used specifically for describing all the settings, patterns, etc. within our pattern library.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

important:
  title: "Start Jekyll in Terminal"
  text: |
    Before you continue—make sure to get Jekyll running in your Terminal for your `ecommerce-pattern-library`

    1. Press `Open in Terminal` from GitHub Desktop
    2. Press `Up`—you should see `bundle exec jekyll serve`
      <br>*You can press `Up` multiple times to search through your Terminal history.*
    3. Press `Return` to start Jekyll

steps:
  - title: "Company name & description"
    before: |
      **Continue on with your `ecommerce-pattern-library` repository.**

      We’re going to update and add some information to the `_config.yml` file within our pattern library.

      We’ll start by adding the company’s name and a quick description at the top.
    code_lang: yml
    code_file: "_config.yml"
    code: |
      permalink: pretty
      theme: jekyll_patternbot
      patternbot:
        title: "Dino Rescue"
        description: |
          A small local dinosaur rescue organization specializing in herbivores. Dinos are in danger and we need to save them all!
        font_url: "https://fonts.googleapis.com/css?family=Overpass:400,400i,700|Source+Code+Pro:400,700"
    lines:
      - num: "1-2,7"
        fade: true
      - num: 4
        text: |
          The `title` key is the name of the company the pattern library is for, a.k.a. your eCommerce website.
      - num: 5
        text: |
          Use the `description` key to write a little description of the company. This is all Markdown and will be displayed after the company in the pattern library.
    after: |
      ![](title-desc.jpg)

      *Now go refresh your browser to see the changes.*
    notes:
      - label: "Indentation!"
        text: |
          **YAML is very strict about indentation!** If you mess up the indentation within this file, things won’t work.

  - title: "Type choice descriptions"
    before: |
      One of the major goals of the pattern library is to explain why the patterns exist and when to use the patterns. That equally applies to the type choices.

      So next up, we’ll describe why we chose the fonts we did and when they should be used.

      **Remember you’re describing your eCommerce website—don’t just copy this information below.**
    code_lang: yml
    code_file: "_config.yml"
    code: |
      ⋮
      font_url: "https://fonts.googleapis.com/css?family=PT+Sans+Narrow:400,700"
      rationales:
        typefaces.primary: |
          Georgia was selected because it’s a classic font—for classic creatures. Georgia is to be used for all body copy and most situations.
        typefaces.secondary: |
          PT Sans Narrow is only to be used for highlighting text: headings, buttons, banners, etc.
    lines:
      - num: 2
        fade: true
      - num: 3
        text: |
          Make a new entry named `rationales`, this will describe all the typography (and eventually colour) related information.
      - num: 4
        text: |
          Using the `typefaces.primary` entry we can describe the primary typeface—especially describe why you chose it and when to use it.

          Notice the vertical pipe (`|`) this signifies a block of text—you can use Markdown in here.
      - num: 6
        text: |
          Also describe the `typefaces.secondary` typeface choice’s whys & whens.
    after: |
      ![](typefaces.jpg)

      *Then look in your browser at your typeface descriptions.*

  - title: "Colour descriptions"
    before: |
      Next up is the color choices; describe primary, secondary, accent, etc. colours using a format similar to the type.
    code_lang: markdown
    code_file: "_config.yml"
    code: |
      ⋮
        typefaces.secondary: |
          PT Sans Narrow is only to be used for highlighting text: headings, buttons, banners, etc.
        colors.primary: |
          The primary colours represent herbivores & plants & greenery. They should be used for text and in foregrounds.
        colors.secondary: |
          The secondary colours are more neutral, continuing with the earth tones, and should be used for backgrounds.
    lines:
      - num: 2
        fade: true
      - num: "4-7"
        text: |
          The entries can be `colors.primary`, `colors.secondary`, `colors.neutral` and `colors.accent`
    after: |
      ![](colors.jpg)

      *Have a look in your browser at your colour descriptions.*

  - title: "Customize the pattern library"
    before: |
      Using a few more configuration options we can even customize the look of the pattern library itself. It’s often a good idea to make the pattern library more closely match the website’s brand.

      There’s a `colors` configuration entry that has a few options:
    code_lang: yml
    code_file: "_config.yml"
    code: |
      ⋮
      patternbot:
        title: "Dino Rescue"
        description: |
          A small local dinosaur rescue organization specializing in herbivores. Dinos are in danger and we need to save them all!
        font_url: "https://fonts.googleapis.com/css?family=PT+Sans+Narrow:400,700"
        colors:
          background: "--color-secondary-light"
          accent: "--color-primary-dark"
          patterns:
            brand.logos: "--color-primary-light"
        rationales:
          typefaces.primary: |
            Georgia was selected because it’s a classic font—for classic creatures. Georgia is to be used for all body copy and most situations.
      ⋮
    lines:
      - num: "2-6,12-14"
        fade: true
      - num: 7
        text: |
          Add the `colors` configuration option under the `patternbot` entry.
      - num: 8
        text: |
          If you add a `background` key the whole page background of the pattern library will change.

          You don’t have to use your variables here—you can use hex colours—but it does make the most sense.
      - num: 9
        text: |
          The `accent` key will add foreground colours in a few places. Right now Patternbot is using your primary colour for this.
      - num: 10
        text: |
          If you add a `patterns` entry within `colors` you can change the background color behind certain built-in patterns, like the brand logos section.
      - num: 11
        text: |
          The key format is “pattern_group.pattern_name”.
    after: |
      **Only include the colours you want—leave anything off that you don’t want to change.**

      ![](color-customization.jpg)

      *Check it out in your browser to see the colour customizations.*

---
