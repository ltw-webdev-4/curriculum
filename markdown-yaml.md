---
layout: slide-deck

title: "Markdown & YAML"

slides:
  - type: super-big-text
    content: |
      **Markdown & YAML**

  - content: |
      ## Content & data

      Markup languages like HTML for representing content & data

      - *Markdown* — simplified HTML
      - *YAML* — simplified Javascript data

      *Can be combined together: Markdown in YAML & YAML in Markdown*

  - content: |
      ## Why use Markdown or YAML?

      - They’re easier to write
      - They’re ubiquitous & standardized (mostly)
      - They can be written without special tools

  - content: |
      ## Where are they used?

      - *READMEs for open source projects*
        <br>All your assignment descriptions

      - *Configuration for applications*
        <br>All your assignment requirements

      - *Making auto-generated websites*
        <br>Pretty much the whole of Learn the Web

  - content: |
      ## Extensions & editors

      Use Atom or Sublime or anything for editing

      - **`.md` — Markdown** (can have YAML inside)
      - **`.yml` — YAML** (can have Markdown inside)

      *Atom provides built-in Markdown preview:*

      `Packages > Markdown Preview`

  - type: code
    markdown: |
      # For heading level 1                         <!-- Denote headings with # -->
      ## For heading level 2
      ### For heading level 3

      - List item 1                                 <!-- Unordered list -->
      - List item

      1. Numbered list item 1                       <!-- Ordered list -->
      2. Numbered list item 2

      Just a *plain* old **paragraph**!             <!-- Paragraphs are just lines by themselves -->
                                                    <!-- Single * is italic. Double ** is bold -->

      Link to [Wikipedia](https://wikipedia.org/).

      ![](images/dino.jpg)

  - type: code
    yaml: |
      ---                                       # Start the file
      name: Tyrannosaurus                       # A list, like a <dl>
      period: Late Cretaceous
      dimensions:                               # List inside a list!
        width: 3 metres
        height: 8 metres

      likes_to_eat:                             # Another list, like a <ul>
        - Other dinosaurs
        - Meat

      desc: |                                   # Markdown in my YAML!
        ## The T.Rex

        ![](images/trex.jpg)

        The **most fearsome** of all *dinosaurs*.

  - type: code
    markdown: |
      ---
      name: Tyrannosaurus
      period: Late Cretaceous
      ---

      The **most fearsome** of all *dinosaurs*.

  - content: |
      ## Markdown editors

      - [Mou](http://25.io/mou/)
      - [IA Writer](https://ia.net/writer/)
      - [Ulysses](https://ulyssesapp.com/)

  - content: |
      ## Videos & tutorials

      - [Markdown](/topics/markdown/)
      - [YAML](/topics/yaml/)
      - [Markdown & YAML cheat sheet](/topics/markdown-yaml-cheat-sheet/)
---
