---
layout: slide-deck
title: "Wet code is bad code"
desc: "A discussion of best practices related to writing and maintaining code bases."

slides:
  - type: super-big-text
    content: |
      **Wet code is bad code**

  - content: |
      ## Don’t Repeat Yourself

      **If you find yourself copying-and-pasting code you’re doing something wrong.**

      - Whenever possible we should not write the same code more than once

      *Don’t Repeat Yourself (DRY) — the opposite of wet.*

  - content: |
      ## Write less damn code

      **The more code you write the more bugs you’ll introduce.**

      - Whenever possible err on the side of writing less code
      - Delete unused code & refactor to simplify
      - Don’t solve problems by adding—remove first

  - content: |
      ## Prefer readability over cleverness

      **When trying to name things, readability is paramount.**

      - Name your CSS classes with full words that make sense
      - Don’t use acronyms whenever possible
      - Use standard naming conventions
      - Use consistent words, patterns & names

  - content: |
      ## Write for your future self

      **Code should be written with the understanding that you’ll forget.**

      - Your future self will not have the same memorized head space of the code base
      - Make everything clear & understandable
      - If you did something weird: write a comment

  - content: |
      ## Systemize all the things

      **Automation is the best.**

      - Automate as many things in your code base as possible
      - Use generators and includes to reduce duplication
      - Use systems that can generated coded templates for you
---
