---
layout: lesson
title: "Using CSS variables"
desc: "Learn how to use CSS variables to make your CSS more easily understood and more maintainable."

markbot_notes: |
  *Ignore the “the first heading is an `<h2>`…” error message—but fix everything else.*

  I feel like this is part of a larger website so the `<h1>` would probably be somewhere else on the page.

extra_tutorials:
  - title: "CSS variables"
    url: css-variables

goal:
  image: goal.png
  before: |
      CSS variables are a powerful solution to create reusable information in your CSS that can be changed and manipulated more easily than doing a search and replace.

      Another great benefit is that we can give the variables names that make our CSS more obvious instead of having random numbers & colours scattered around.

      **Browser support is decent, but probably not ready for use in a live, client-facing website yet. We’re still waiting for support from Microsoft Edge (though last time I checked it was in development).**
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"
    - label: "Browser support"
      text: "Probably not quite ready to be used in a live, client-facing website yet. Still waiting on Microsoft Edge for support."

steps:
  - title: "Set up project"
    before: |
      To get started we need some HTML & CSS files and we’ll include a copy of Modulifier & Typografier.
    folders:
      - label: "using-css-variables"
        type: folder
      - label: "index.html"
        indent: 1
      - label: "css"
        type: folder
        indent: 1
      - label: "main.css"
        indent: 2
      - label: "modules.css"
        indent: 2
      - label: "type.css"
        indent: 2
    after: |
      1. Create a folder named `using-css-variables`
      2. Make an `index.html` & add the boilerplate code.
      3. Make a `main.css` in your `css` folder—it can remain empty.
      4. Make a `modules.css` in your `css` folder—[get a new version from Modulifier](https://modulifier.web-dev.tools/). **Make sure to press “Select All”.**
      5. Make a `type.css` in your `css` folder—[get a new version from Typografier](https://typografier.web-dev.tools/).
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`, `css`"

  - title: "Write a little HTML"
    before: |
      Let’s write a little HTML to get started, a simple card that we can style with a few CSS variables.
    code_lang: html
    code_file: "index.html"
    code: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Using CSS variables</title>
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <link href="css/modules.css" rel="stylesheet">
        <link href="css/type.css" rel="stylesheet">
        <link href="css/main.css" rel="stylesheet">
      </head>
      <body>

        <div class="card chop">
          <img class="img-flex" src="https://placehold.it/320x240" alt="">
          <div class="island">
            <h2 class="card-title push-0">Giant robots</h2>
            <p>Smashing, crashing, bashing all,<br>Giant robots have real gall.</p>
            <a class="btn" href="#">Destroy!</a>
          </div>
        </div>

      </body>
      </html>
    lines:
      - num: 17
        text: |
          Using the `<br>` tag here is okay because the text is a poem, and in poetry the line breaks are part of the content.

  - title: "Write a little CSS"
    before: |
      Let’s add a little CSS to our card to get it looking kinda actually like a card.

      *Some of these properties are temporary and I’ll probably replace them later.*
    code_lang: css
    code_file: "css/main.css"
    code: |
      html {
        font-family: sans-serif;
      }

      .card {
        max-width: 24em;

        border: 3px solid red;
        border-radius: 4px;
      }
    lines:
      - num: 8
        text: |
          Let’s make the border `red` for now, but we’ll likely change it later.
      - num: 9
        text: |
          I’m not sure if I like the `4px` border radius, I think I’ll change it later to have more personality.
    after: |
      With the CSS in place, we should now be seeing this in our browser:

      ![](after-css.png)

  - title: "Change colours & border-radii to variables"
    before: |
      CSS variables allow us to put information in a common location. We can then use that information in multiple places in our CSS.

      It works really well for things like colours and fonts. We define them once, at the top, then use them in multiple places. It’s especially helpful for colours because we don’t have to remember the hex value, just the name of the variable—which our code editor should autocomplete for us.

      *We can define our variables anywhere in the CSS, but it’s often best to define them at the very top, in the `:root` selector.*
    code_lang: css
    code_file: "css/main.css"
    code: |
      :root {
        --color-primary: red;
        --border-radius: 4px;
      }

      html {
        font-family: sans-serif;
      }

      .card {
        max-width: 24em;

        border: 3px solid var(--color-primary);
        border-radius: var(--border-radius);
      }
    lines:
      - num: 1
        text: |
          We can create a new block in our CSS called `:root`—within this we can create variables that are shared on the whole website.

          The `:root` block should always be at the top of the CSS file.
      - num: "2-3"
        text: |
          Variable names always start with two dashes (`--`), then you make up whatever you want afterwards.

          I always start the variable name with `--color` if it’s a colour or `--font` if it’s a font.
      - num: "6-11"
        fade: true
      - num: "13-14"
        text: |
          When we want to use the variable we start with the `var()` function and write the name of the variable inside it.

          Whatever value is defined for the variable at the top of the page, inside `:root`, will be output into the location you use `var()`
      - num: 15
        fade: true
    after: |
      If everything was spelled properly, it should still look exactly the same in the browser:

      ![](after-css.png)

  - title: "Style more things with variables"
    before: |
      Let’s now style a few more things on the page with our variables.
    code_lang: css
    code_file: "css/main.css"
    code: |
      ⋮
        border: 3px solid var(--color-primary);
        border-radius: var(--border-radius);
      }

      .card-title {
        color: var(--color-primary);
      }

      .btn {
        background-color: var(--color-primary);
        border-color: var(--color-primary);
        border-radius: var(--border-radius);
      }
    lines:
      - num: "2-4"
        fade: true
      - num: "6-8"
        text: |
          If we target `.card-title` we can use the `--color-primary` variable to change its colour to match the border of our card.
      - num: "10-14"
        text: |
          We can do the same on our button, using the colour and border radius variables to adjust the button to match our card a little more.
    after: |
      Our card should now have matching colours and border radii for the whole thing:

      ![](after-vars.png)

  - title: "Variables for fonts"
    before: |
      I’d like to make the fonts into variables. But first, let’s add another font to our website.
    multi_code:
      - code_before: |
          Go to Google Fonts and select “Roboto Slab”—make sure to choose “Normal” and “Bold”.
        code_lang: html
        code_file: "index.html"
        code: |
          ⋮
            <link href="css/modules.css" rel="stylesheet">
            <link href="css/type.css" rel="stylesheet">
            <link href="css/main.css" rel="stylesheet">
            <link href="https://fonts.googleapis.com/css?family=Roboto+Slab:400,700" rel="stylesheet">
          </head>
          <body>
          ⋮
        lines:
          - num: "2-4"
            fade: true
          - num: "6-7"
            fade: true
      - code_before: |
          In our CSS let’s add two variables:

          1. One for the primary font, `sans-serif`
          2. And one for the secondary font, `"Roboto Slab"`

          Then we’ll use those fonts in a few places in our CSS.
        code_lang: css
        code_file: "css/main.css"
        code: |
          :root {
            --color-primary: red;
            --border-radius: 4px;
            --font-primary: sans-serif;
            --font-secondary: "Roboto Slab", sans-serif;
          }

          html {
            font-family: var(--font-primary);
          }

          .card {
            max-width: 24em;

            border: 3px solid var(--color-primary);
            border-radius: var(--border-radius);
          }

          .card-title {
            color: var(--color-primary);
            font-family: var(--font-secondary);
          }

          .btn {
            background-color: var(--color-primary);
            border-color: var(--color-primary);
            border-radius: var(--border-radius);
            font-family: var(--font-secondary);
          }
        lines:
          - num: "1-3"
            fade: true
          - num: "7-8"
            fade: true
          - num: 9
            text: |
              Here we’ll set the font of all the main body copy to our primary font.
          - num: "10-20"
            fade: true
          - num: "21"
            text: |
              We’ll set the font family of the main card heading to our secondary font, to make it stand out from the rest of the text.
          - num: "22-27"
            fade: true
          - num: 28
            text: |
              We’ll also set the button to use our secondary font.
          - num: 29
            fade: true
    after: |
      Now with the the font variables in place we should see this:

      ![](after-fonts.png)

  - title: "Edit once, change everywhere"
    before: |
      I’m not happy with the colours or the border radii of the design. So I want to change them all—this is where CSS variables really show their flexibility.

      If I just change just the variables at the top of my file then everything that uses them will automatically change too.
    code_lang: css
    code_file: "css/main.css"
    code: |
      :root {
        --color-primary: #f39;
        --border-radius: 14px 0 14px 0;
        --font-primary: sans-serif;
        --font-secondary: "Roboto Slab", sans-serif;
      }
      ⋮
    lines:
      - num: 1
        fade: true
      - num: "4-6"
        fade: true
    after: |
      Check it out in your browser! You should see that all the colours are a much nicer magenta and the border radii are more unique and engaging—and we only had to change two lines of code.

---
