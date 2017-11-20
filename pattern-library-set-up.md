---
layout: lesson
title: "Pattern library set up"
desc: "Create the first few basic files for your ecommerce pattern library and use Patternbot to generate the component website."

extra_tutorials:
  - title: "Pattern libraries"
    url: pattern-libraries
  - title: "Pattern libraries slide deck"
    url: "/courses/web-dev-4/pattern-libraries/"

steps:
  - title: "Set up project"
    before: |
      We’re going to start the pattern library that you’ll be working for the rest of the term in this lesson.

      We’ll get the first bits set up and ready to use so you can move onto styling the typography.

      ### [Fork & clone this repo.](https://github.com/acgd-webdev-4/ecommerce-pattern-library/fork)
    notes:
      - label: "Type it, type it real good"
        text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

  - title: "Get the Web Dev Tools CSS files"
    before: |
      The first step is to get copies of all the [Web Dev Tools](http://web-dev.tools/).
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
        notes: "This is the folder you forked"
      - label: "common"
        type: folder
        indent: 1
      - label: "modules.css"
        indent: 2
      - label: "grid.css"
        indent: 2
      - label: "type.css"
        indent: 2
    after: |
      1. Make a `modules.css` in your `common` folder—[get a new version from Modulifier](https://modulifier.web-dev.tools/).
        <br>*Include all the modules you’ll need for your website. (You can always add more later.)*
      2. Make a `grid.css` in your `common` folder—[get a new version from Gridifier](https://gridifier.web-dev.tools/).
        <br>*Set up the columns and breakpoints you’ll need based on your wireframes.*
      3. Make a `type.css` in your `common` folder—[get a new version from Typografier](https://typografier.web-dev.tools/).
        <br>*Set up the font-sizes and type scales based on your visual design choices.*
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."

  - title: "Make the shared CSS file"
    before: |
      Next up we’ll create a shared CSS file, named `theme.css`. In here we’ll be putting a bunch of CSS variables and styling the general typographic tags for your website.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "common"
        type: folder
        indent: 1
      - label: "modules.css"
        indent: 2
        fade: true
      - label: "grid.css"
        indent: 2
        fade: true
      - label: "type.css"
        indent: 2
        fade: true
      - label: "theme.css"
        indent: 2
    code_before: |
      At the top of your `theme.css` file, add a few variables that match the visual design of your eCommerce website.
    code_lang: css
    code_file: "common/theme.css"
    code: |
      :root {
        --color-primary: goldenrod;
        --color-primary-light: gold;
        --color-secondary: lightcoral;
        --color-accent: greenyellow;
        --color-neutral-beige: #e2e2e2;
        --color-whatever: peachpuff;

        --font-primary: "Alegreya Sans", "Trebuchet MS", Arial, sans-serif;
        --font-secondary: "Source Code Pro", Menlo, Consolas, monospace;
      }

      html {
        font-family: var(--font-primary);
      }
    lines:
      - num: 2
        text: |
          Add a `primary` colour at least—Patternbot will use this in different situations.
      - num: 3
        text: |
          If you have any variations of the primary colour (lighter, darker, tints, shades, etc.) name those similarly with descriptive words.
      - num: 4
        text: |
          You can do the same for your secondary colour too.
      - num: "5-7"
        text: |
          If you have more colours you can name them as `accent` or `neutral` colours, or just give them any ol’ name.
      - num: "9-10"
        text: |
          Add in the different fonts you want to use. You’ll likely only need a `primary` & `secondary` font for your website. You can do `accent` font families too.
      - num: "13-15"
        text: |
          Go ahead and set the body copy of your website to use your primary font.
    after: |
      All the colours & fonts above should match your visual design—**don’t just copy these values, they’re wrong.**

  - title: "Add your logo SVGs"
    before: |
      Patternbot will detect your logo images and display them on the screen, so let’s add those into your pattern library folder.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "common"
        type: folder
        indent: 1
        fade: true
      - label: "images"
        type: folder
        indent: 1
      - label: "logo-256.svg"
        indent: 2
      - label: "logo-64.svg"
        indent: 2
      - label: "logo-32.svg"
        indent: 2
      - label: "logo-16.svg"
        indent: 2
    after: |
      Put as many of the four sizes in as you can. Patternbot will figure out which are available and display those.

      *If you only made one logo and it works well at all four sizes just name it `logo.svg`*

  - title: "Put details into the README"
    before: |
      We’ll spend more time on this file next week when we learn about [Markdown](/topics/markdown/). But for this week we’re going to put one line of code in it, just so our typography works properly.

      *First create a new file named exactly `README.md`* (Yes those are capital letters—gasp!)
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "common"
        type: folder
        indent: 1
        fade: true
      - label: "images"
        type: folder
        indent: 1
        fade: true
      - label: "README.md"
        indent: 1
    code_before: |
      Now open up the README and type the following code. Be sure to substitute this Google Font URL with your own.
    code_lang: markdown
    code_file: "common/theme.css"
    code: |
      ---
      fontUrl: "https://fonts.googleapis.com/css?family=Alegreya+Sans:400,400i,700|Source+Code+Pro:400,700"
      ---
    lines:
      - num: 2
        text: |
          Patternbot will use the `fontUrl` to make sure all the type in the builtin patterns is rendered in the correct font family. It will also use the weights and styles provided by Google Fonts to display in the pattern library.
    after: |
      **Make sure the first set of triple dashes (`---`) touches the top of your file—it should be the very first thing.**

      *This URL is the stuff inside the `href="…"` attribute of the `<link>` tag that Google Fonts gives you.*

  - title: "Drop it into Patternbot"
    before: |
      We’re finally ready to run [Patternbot](https://github.com/thomasjbradley/patternbot). Drag and drop your `ecommerce-pattern-library` folder into Patternbot’s window.

      ![](patternbot.jpg)

      Patternbot will generate a bunch of new things for you:

      - a new folder named `patterns`—with more folders inside
        <br>*Don’t touch the folders Patternbot generated inside `patterns`—they’ll just get replaced*

      - a new file named `pattern-library.html`
        <br>*This is your pattern library website!*

      *We’ll spend more time on the `patterns` folder next week.*

  - title: "View the pattern library"
    before: |
      Many of the features that Patternbot generates and uses are advanced features of browsers and require a web server to function properly.

      If we pop our `pattern-library.html` page open in a browser we’ll see a bunch of error messages—and it won’t work quite right.

      ![](chrome-errors.jpg)

      So we need to use Patternbot’s internal web server to load the website.

      ![](browse-menu.jpg)

      In the `File` menu go to `Browse Pattern Library` (`⌘B`)—this will pop open your default browser with the URL to your pattern library running over with a web server.

      The URL will most likely be: [**https://localhost:8000/**](https://localhost:8000/).

      ![](chrome-security.jpg)

      Next up we’ll see a security error about the connection not being private. The browser doesn’t believe the HTTPS certificate Patternbot uses is secure because it wasn’t signed by an authority.

      **You should never bypass this error message on websites.** In this situation it’s okay because we’re loading our “localhost” testing server.

      So, click “ADVANCED”.

      ![](chrome-security-proceed.jpg)

      Then click “Proceed to localhost (unsafe)”.

      ![](pattern-lib.jpg)

      Now we should see our pattern library!

---
