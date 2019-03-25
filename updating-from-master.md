---
layout: lesson
title: "Updating from master"
desc: "One common problem you’ll run into is the need to get updated code from the “designer” this will quickly show you how to solve the problem."

hide_markbot: true

extra_tutorials:
  - title: "Branching & GitHub Flow"
    url: branching-github-flow
  - title: "Using GitHub for project management"

goal:
  no_image: true
  before: |
    We’re going look at how you can make adjustments to your pattern library—your repository—and get those adjustments copied down to your teammate’s already cloned repositories.

    **I expect you’ll have to update your pattern library to fix problems your teammate will run into. This lesson will show you how to push code changes to your teammate’s cloned repository.**
  person_legend:
    - icon: "person-1"
      label: "Owner"
      desc: "The person who owns this pattern library, the person who created all the patterns."
    - icon: "person-2"
      label: "Dev"
      desc: "The person who will be developing/writing the code/creating the new product details page."

steps:
  - title: "Add collaborator names to README"
    person:
      icon: "person-1"
      label: "Owner"
    before: |
      To get started, let’s make a small change to your `README.md` file—we’ll add all your names to it.

      Open up your `README.md` file and add something like this (probably above the copyright notice):
    code_lang: md
    code_file: "README.md"
    code: |
      ⋮
      ---

      ## Collaborators

      - [@thomasjbradley](https://github.com/thomasjbradley)
      - [@dinodemos](https://github.com/dinodemos)

  - title: "Commit & push"
    person:
      icon: "person-1"
      label: "Owner"
    before: |
      Like normal, head into your GitHub Desktop application and make a commit & push.

      **Make sure you’re committing to *your own* repository—and that you’re committing to the `master` branch!**

  - title: "Update from master"
    person:
      icon: "person-2"
      label: "Dev"
    before: |
      Now we pop over to the “developer” teammate. We want to pull this new change into their cloned repository so they can have the most up-to-date code to work from.

      ![](github.jpg)

      1. Open the `README.md` in Atom and notice the “Collaborators” section is missing.
      2. Got into the GitHub desktop application—**make sure you’re viewing your teammate’s repository & that you’re on the `product-details` branch.**
      3. Switch to the `master` branch.
      4. In the menu go to `Repository > Pull`
      5. Switch back to the `product-details` branch.
      6. In the `Branch` menu, press `Update from master` (or `⌘⇧U`) and GitHub will pull the code your teammate just wrote into your `product-details` branch.
      7. Check out the `README.md` in Atom and notice the “Collaborators” section is now visible.

      *That’s it. If you ever need to make changes to your pattern library & share them with your teammate follow the above steps.*
---
