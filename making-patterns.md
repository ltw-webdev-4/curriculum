---
layout: lesson
title: "Making patterns"
desc: "Create the first pattern in our pattern library—the button styles for our website."

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
    We already have our pattern library set up so now we’re ready to create our first pattern.

    Pattern libraries aren’t much use empty of patterns—so we’re going to look at how to add new patterns to our library in this lesson.
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
  - title: "Set up project"
    before: |
      **Continue on with your `ecommerce-pattern-library` repository.**

      We’ll set up our button styles then you can continue to finish them in this week’s homework assignment.

      Let’s create a few new folders & code files:
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "_config.yml"
        indent: 1
        fade: true
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
      - label: "buttons"
        type: folder
        indent: 2
      - label: "basic.html"
        indent: 3
      - label: "buttons.css"
        indent: 3
    after: |
      1. Inside the `_patterns` folder make a new folder named `buttons`
      2. Inside the `buttons` folder make the following empty files:
        - `basic.html`
        - `buttons.css`
    notes:
      - label: "Naming conventions"
        text: |
          Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions).

          Though, since we’re using Jekyll underscores are okay and are going to show up lots.

  - title: "Set up the HTML file"
    before: |
      In our `basic.html` file we’re going to put a single, boring button.

      **In fact that’s all we need! No boilerplate. No CSS. Nothing.**
    code_lang: html
    code_file: "_patterns/buttons/basic.html"
    code: |
        <a class="btn" href="#">Rescue a Dino</a>
    after: |
      *When writing the HTML for a pattern we want to be as minimal as possible. Notice there are no grids or `<main>` tags or `<header>` tags or anything like that above—just the button.*

  - title: "Start some CSS"
    before: |
      Now, let’s write a little CSS, just style the button ever so slightly.

      *You’ll be finishing all the button stuff as your assignment this week.*
    code_lang: css
    code_file: "_patterns/buttons/buttons.css"
    code: |
      .btn {
        background-color: var(--color-primary-dark);
        border-color: var(--color-primary-dark);
        color: var(--color-secondary-light);
      }

      .btn:hover {
        background-color: var(--color-primary);
        border-color: var(--color-primary);
      }
    after: |
      Notice how the above code extensively uses our variables that we created in the `theme.css` file.
    notes:
      - label: "Don’t just copy"
        text: |
          Customize the CSS for your own buttons, using your own colours & fonts. Also add hover effects, transitions, etc.

          This is actually this week’s assignment.

  - title: "Preview in the browser"
    before: |
      As soon as you saved the HTML & CSS Jekyll went off and compiled your website. We need to now open it up in our browser to see how our button looks.

      ### [http://localhost:4000/](http://localhost:4000/)

      ![](patlib-button.jpg)

      *Check out your button pattern in the pattern library!*

      ![](patlib-button-pop-out.jpg)

      *You can use Patternbot’s “pop-out” button to view the button by itself so you don’t have to refresh the whole pattern library to see small changes.*

      ![](button-dev-tools.jpg)

      *It also makes using the browser’s developer tools much more straight forward.*

  - title: "Moar buttons!"
    before: |
      Let’s add a couple more button patterns: “ghost” & “light”.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "_config.yml"
        indent: 1
        fade: true
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
      - label: "buttons"
        type: folder
        indent: 2
      - label: "basic.html"
        indent: 3
        fade: true
      - label: "ghost.html"
        indent: 3
      - label: "light.html"
        indent: 3
      - label: "buttons.css"
        indent: 3
        fade: true
    multi_code:
      - code_before: |
          The HTML is going to be almost completely identical, with just a few `class` changes.
        code_lang: html
        code_file: "_patterns/buttons/ghost.html"
        code: |
            <a class="btn btn-ghost" href="#">Adopt a Dino</a>
      - code_lang: html
        code_file: "_patterns/buttons/light.html"
        code: |
            <a class="btn btn-light" href="#">Save a Herbivore</a>
      - code_before: |
          Let’s pop into the CSS & do just a touch of styling.
        code_lang: css
        code_file: "_patterns/buttons/buttons.css"
        code: |
          ⋮
          .btn:hover {
            background-color: var(--color-primary);
            border-color: var(--color-primary);
          }

          .btn-ghost {
            background-color: transparent;
            color: var(--color-primary-dark);
          }

          .btn-ghost:hover {
            color: var(--color-secondary-light);
          }

          .btn-light {
            background-color: var(--color-secondary);
            border-color: var(--color-secondary);
            color: var(--color-primary-dark)
          }
        lines:
          - num: "2-5"
            fade: true
    after: |
      ![](buttons.jpg)

      *Check ’em all out in your pattern library!*
    notes:
      - label: "Don’t just copy"
        text: |
          Customize the CSS for your own buttons, using your own colours & fonts. Also add hover effects, transitions, etc.

          This is actually this week’s assignment.

  - title: "Making a second pattern group"
    before: |
      We’re going to look at how to integrate patterns into other patterns—but first we need a second pattern to work with. A pattern that needs a button.

      To see how this works, let’s make a new pattern: “cards”.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "_config.yml"
        indent: 1
        fade: true
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
      - label: "buttons"
        type: folder
        indent: 2
        fade: true
      - label: "cards"
        type: folder
        indent: 2
      - label: "dino.html"
        indent: 3
    code_before: |
      Inside our “dino card” we’re going to put some basic HTML:
    code_lang: html
    code_file: "_patterns/cards/dino.html"
    code: |
      <div class="card">
        <img class="img-flex" src="/images/dinos/stegosaurus.jpg" alt="">
        <h2>Stegosaurus</h2>
        <p>The might—and spiky—Stegosaurus roams the Late Jurassic land.</p>
      </div>
    lines:
      - num: 2
        text: |
          Notice the `/` at the start of the images’s `src=""` attribute. That means the path is absolute—and is very critical for when working with Jekyll & Patternbot.

          It helps us forget about what folder our pattern is in and just start at the root of our website directory all the time.

          We haven’t used absolute paths until now because they don’t work without a web server—but Jekyll is running a web server for us.

          [☛ Read more about paths](/topics/paths-folders/)
    after: |
      ![](card.jpg)

      *Check out your new—un-styled—pattern in your pattern library.*

  - title: "Integrate patterns into other patterns"
    before: |
      Using patterns in lots of different places is exactly what a pattern library is about. We break everything down into small chunks and reuse those pieces many times.

      So, let’s insert a button into our card.

      First, go to your pattern library and choose the button you want.

      ![](show-code.jpg)

      *1. Press the “Show code” button beside it’s title.*

      ![](copy-code.jpg)

      *2. Copy the code that will output a button—you can press the “Copy code” button.*

      **3. Paste it into the card where you want it to display:**
    code_lang: html
    code_file: "_patterns/cards/dino.html"
    code: |
      <div class="card">
        <img class="img-flex" src="/images/dinos/stegosaurus.jpg" alt="">
        <h2>Stegosaurus</h2>
        <p>The might—and spiky—Stegosaurus roams the Late Jurassic land.</p>
        {% pattern buttons/light %}
      </div>
    lines:
      - num: "1-4,6"
        fade: true
      - num: 5
        text: |
          In Jekyll terminology this is called an “include”. It tells Jekyll, “Go find this file, read it’s code, and put it right here—so I don’t have to.”

          This is a slightly customized include syntax that will look in your `_patterns` folder. Jekyll only looks in the `_includes` folder by default.
    after: |
      ![](card-with-btn.jpg)

      *Finally! Check out your new card + button in the pattern library!*
---
