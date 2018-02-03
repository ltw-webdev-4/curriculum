---
layout: lesson
title: "Making a new pattern"
desc: "Create the first pattern in our pattern library—the button styles for our website."

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

    But a pattern library isn’t much use if it is empty of patterns—so we’re going to look at how to add new patterns to our library in this lesson.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

steps:
  - title: "Set up project"
    before: |

      We’ll set up our button styles then you can continue to finish them in this week’s homework assignment.

      Let’s create a few new folders & code files:
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "README.md"
        indent: 1
        fade: true
      - label: "common"
        type: folder
        indent: 1
        fade: true
      - label: "images"
        type: folder
        indent: 1
        fade: true
      - label: "patterns"
        indent: 1
        type: folder
      - label: "buttons"
        type: folder
        indent: 2
      - label: "buttons.html"
        indent: 3
      - label: "buttons.css"
        indent: 3
      - label: "README.md"
        indent: 3
    after: |
      1. Inside the `patterns` folder make a new folder named `buttons`
      2. Inside the `buttons` folder make the following empty files:
        - `buttons.html`
        - `buttons.css`
        - `README.md`
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."

  - title: "Set up the HTML file"
    before: |
      In our `buttons.html` file we’re going to put the generic HTML boilerplate and add a few buttons.

      We’ll also point the buttons CSS file to all the common CSS files we have, and to whatever fonts we plan on using.
    code_lang: html
    code_file: "patterns/buttons/buttons.html"
    code: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Buttons</title>
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <link href="../../common/modules.css" rel="stylesheet">
        <link href="../../common/grid.css" rel="stylesheet">
        <link href="../../common/type.css" rel="stylesheet">
        <link href="../../common/theme.css" rel="stylesheet">
        <link href="https://fonts.googleapis.com/css?family=Overpass:400,400i,700" rel="stylesheet">
        <link href="buttons.css" rel="stylesheet">
      </head>
      <body>

        <a class="btn" href="#">Standard button</a>
        <a class="btn btn-light" href="#">Light button</a>
        <a class="btn btn-ghost" href="#">Ghost button</a>

      </body>
      </html>
    lines:
      - num: "7-10"
        text: |
          Here we’re hooking up all 4 common CSS files. Notice how the paths are different than normal, they include two `../` chunks in them. The `../` means go out of this folder.

          So the paths say:

          - “go out of this folder (`buttons`),”
          - “then go out of the next folder (`patterns`),”
          - “then go into the `common` folder,”
          - “and find `theme.css`”
      - num: 11
        text: |
          Hook up your Google/Typkit font, if you’re using one.
      - num: 12
        text: |
          Finally point to the buttons CSS file. Notice how there is no `css/` in this URL. That’s because the `buttons.css` file is in the same location as the HTML file.
      - num: "16-18"
        text: |
          Add as many button styles as you need for your eCommerce website.

          If the default classes (like `.btn-ghost`) don’t make sense for your website make up some new ones, e.g. `.btn-banner`, `.btn-pill`, etc.
    after: |
      *When writing the HTML for a pattern we want to be as minimal as possible. Notice there are no grids or `<main>` tags or `<header>` tags or anything like that above—just the buttons.*
    notes:
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`, `css`"

  - title: "Start some CSS"
    before: |
      Now, let’s write a little CSS, just style the buttons ever so slightly.

      *You’ll be finishing all the button stuff as your assignment this week.*
    code_lang: css
    code_file: "patterns/buttons/buttons.css"
    code: |
      .btn {
        background-color: var(--color-primary);
        border-color: var(--color-primary);

        color: #fff;
      }

      .btn-light {
        background-color: var(--color-primary-light);
        border-color: var(--color-primary-light);

        color: #fff;
      }

      .btn-ghost {
        background-color: transparent;
        border-color: var(--color-primary);

        color: var(--color-primary);
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
      We’re now ready to see what we have. *Because we’re working on an individual pattern, it’s completely self-contained and we don’t need to use Patternbot yet.*

      **Just open up the `buttons.html` in your browser by itself.**

      You should see something like this:

      ![](buttons.jpg)

      *After the buttons pattern is within Patternbot, you can use Patternbot’s “pop-out” button to view the buttons on their own and get the automatic refreshing too.*

  - title: "Write the README"
    before: |
      Now we’re ready to describe the buttons and when to use them.

      In the `README.md` file we can use plain Markdown—no YAML necessary—to describe the buttons:
    code_lang: markdown
    code_file: "patterns/buttons/README.md"
    code: |
      The buttons use our primary colour to draw attention and stand out. Each button has a specific purpose:

      - The regular buttons are for cards, forms and where the background is a light colour
      - The light buttons are for dark background areas
      - The ghost buttons should be used exclusively on banners where the background is an image

      Feel free to mix them with the `font-size` classes to make different sizes of buttons.
    after: |
      **Make sure the description isn’t directly copied from above—use your own descriptions to describe your own buttons.**

      Once we’re happy with the description we can build the buttons pattern into our library…

  - title: "Generate in Patternbot"
    before: |
      When we want to render new patterns into the library or when we want to update the content from the `README.md` we need Patternbot.

      So drop your `ecommerce-pattern-library` folder into Patternbot. Then press `⌘B` to view it.

      ![](patternbot.jpg)

      If you click the “Buttons” link in the navigation you should see everything you’ve done.

      ![](pattern-lib-buttons.jpg)

      ### When & when-not to use Patternbot

      You don’t have to refresh your whole library in Patternbot every time you make a small change—that’s too much waiting, so here are some scenarios:

      - **“I changed a colour in the `buttons.css` file”**
        <br>Open your `buttons.html` file directly in the browser (like you’re used to) to see the changes.

      - **“I added another button to the `buttons.html`”**
        <br>Open your `buttons.html` file directly in the browser (like you’re used to) to see the changes.

      - **“I fixed some grammar in the buttons `README.md`**
        <br>Let Patternbot regenerate your library and view with `localhost` (`⌘B`).

      - **“I added a new pattern to my library”**
        <br>Let Patternbot regenerate your library and view with `localhost` (`⌘B`).

      *When working specifically on a single pattern open the HTML file directly in the browser—or use the Patternbot “pop-out” button.*
      *When adjusting the display of the pattern library itself page use Patternbot.*

---
