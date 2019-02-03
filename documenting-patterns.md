---
layout: lesson
title: "Documenting patterns"
desc: "A look at how to document & rationalize your patterns, describing when & how to use each."

hide_markbot: true

extra_tutorials:
  - title: "Pattern library cheat sheet"
    url: "pattern-library-cheat-sheet"

goal:
  before: |
    Since one of the important aspects of our pattern library is documentation, we also need to look at how to document each single pattern.
  no_image: true
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

important:
  title: "Start Jekyll in Terminal"
  text: |
    Before you continue—make sure to get Jekyll running in your Terminal for your `ecommerce-pattern-library`

steps:
  - title: "Documenting pattern groups"
    before: |
      Each pattern grouping should have a title & description to help rationalize the purpose and use of the patterns.

      We can do this within the `config.yml` file for each pattern folder.
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
      - label: "js"
        type: folder
        indent: 1
        fade: true
      - label: "_patterns"
        indent: 1
        type: folder
      - label: "buttons"
        type: folder
        indent: 2
      - label: "config.yml"
        indent: 3
        notes: "Make a new YAML file"
    code_before: |
      1. Inside the `buttons` folder make the following empty file: `config.yml`

      Now we’ll type a little bit of code for the pattern grouping.
    code_lang: yml
    code_file: "_patterns/buttons/config.yml"
    code: |
      title: "Buttons"
      description: |
        Buttons should be used in situations where a dramatic, obvious action is required. Try not to over use buttons because they should be the primary call-to-action for a screen.
    lines:
      - num: 1
        text: "If you leave `title` out of this file, Patternbot will generate a title based on the folders name."
    after: |
      ![](buttons-desc.jpg)

      **Refresh your pattern library and see the description within the buttons pattern.**

  - title: "Documenting single patterns"
    before: |
      We should even document each single pattern within the grouping. *To describe when & how each pattern should be integrated into the design.*
    code_lang: yml
    code_file: "_patterns/buttons/config.yml"
    code: |
      title: "Buttons"
      description: |
        Buttons should be used in situations where a dramatic, obvious action is required. Try not to over use buttons because they should be the primary call-to-action for a screen.

      patterns:
        basic:
          title: "Basic"
          description: |
            Default to using the basic button. It should always be used in front of light backgrounds.
        ghost:
          title: "Ghost"
          description: |
            The ghost button is specifically for banners, where it will be placed in front of busy images.
    lines:
      - num: "1-3"
        fade: true
      - num: 5
        text: |
          All the descriptions for each pattern is found under the `patterns` key.
      - num: 6
        text: |
          The key is spelled exactly the same as the HTML file: so `basic.html` becomes `basic:` within the `config.yml` file.
      - num: 7
        text: |
          If you leave off the title it will be inferred from the HTML file’s name.
      - num: 8
        text: |
          Be descriptive, explain when and how the specific pattern should be used & included.
    after: |
      ![](pattern-descs.jpg)

      *Refresh your pattern library to see the changes.*

  - title: "Configure Patternbot’s display"
    before: |
      With some patterns, the way they’re displayed in Patternbot isn’t always ideal. For example, cards can be displayed way too wide.

      **That flexibility is extremely important, we want our cards to flex to lots of sizes.** But sometimes we don’t want them displayed that big inside Patternbot.

      Or maybe you need to change the background colour of a specific pattern.
    code_lang: yml
    code_file: "_patterns/buttons/config.yml"
    code: |
      title: "Buttons"
      description: |
        Buttons should be used in situations where a dramatic, obvious action is required. Try not to over use buttons because they should be the primary call-to-action for a screen.

      patterns:
        basic:
          title: "Basic"
          description: |
            Default to using the basic button. It should always be used in front of light backgrounds.
          width: "12em"
        ghost:
          title: "Ghost"
          description: |
            The ghost button is specifically for banners, where it will be placed in front of busy images.
          background: "--color-primary-light"
    lines:
      - num: "1-9,11-14"
        fade: true
      - num: 10
        text: |
          Use the `width` option to affect how wide the pattern displays in Patternbot.
      - num: 15
        text: |
          Use the `background` option to affect the background of the whole pattern within Patternbot.
    after: |
      ![](config.jpg)

      [*Check out the Pattern library cheat sheet to see more options.*](/topics/pattern-library-cheat-sheet/)

      **Continue to document *all* the patterns in your library—and all future patterns.**
---
