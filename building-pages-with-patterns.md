---
layout: lesson
topic: "Building pages with patterns"
desc: "Look at how to reuse your pattern code when building-out the example pages in your pattern libraries."

markbot_notes: |
  Drop just the `pages` folder into Markbot—it’s the only thing that changed and the only thing that we need to check right now.

goal:
  image: goal.jpg
  before: |
    We’re going to make an example page in a sample pattern library to see how the syntax works, and what it’s capable of doing.

    Patternbot contains a very simple “include” system that allows us to pull the HTML & CSS from our patterns into example pages. In real websites we write as little HTML as possible; we make patterns and then *include* them on pages.

    *We’re going to explore the idea of includes & code separation much more thoroughly when we learn about [Jekyll](/topics/jekyll).*
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

fork:
  url: "https://github.com/acgd-webdev-4/geohub/fork"
  repo: "geohub"

steps:
  - title: "Browse the pattern library"
    before: |
      What you’ve cloned is a simple pattern library with a bunch of components that we’re going to use on our example homepage.

      Drop the cloned `geohub` folder into Patternbot and browse the available patterns. Notice that we have the following patterns available for the homepage:

      1. “Header”
      2. “Footer”
      3. “Banner”
      4. ”Cards”

      And some icons for use in the cards.

      *Since the patterns are done & complete it’s not best practice to copy and paste the code.* **If you find yourself copying-and-pasting code you’re doing something wrong.**

      What we’re going to do is use a simple templating engine to pull (“include”) the patterns into our homepage without writing their code over again.

  - title: "Create a pages folder"
    before: |
      Before we can do anything we need to make a new folder in our pattern library: `pages`
    folders:
      - label: "geohub"
        type: folder
      - label: "common"
        type: folder
        indent: 1
        fade: true
      - label: "images"
        type: folder
        indent: 1
        fade: true
      - label: "pages"
        type: folder
        indent: 1
        notes: "Make the folder in the root of the website"
      - label: "patterns"
        type: folder
        indent: 1
        fade: true
      - label: "index.html"
        indent: 1
        fade: true
      - label: "README.md"
        indent: 1
        fade: true
    after: |
      The `pages` directory is were all the example pages of our pattern library are going to reside.

      Patternbot treats this folder specially by linking every HTML file within into the pattern library’s navigation.
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."

  - title: "Create a new HTML file"
    before: |
      Inside our `pages` folder we’re going to make a new example website page: `home.html`
    folders:
      - label: "geohub"
        type: folder
      - label: "common"
        type: folder
        indent: 1
        fade: true
      - label: "images"
        type: folder
        indent: 1
        fade: true
      - label: "pages"
        type: folder
        indent: 1
      - label: "home.html"
        indent: 2
      - label: "patterns"
        type: folder
        indent: 1
        fade: true
      - label: "index.html"
        indent: 1
        fade: true
      - label: "README.md"
        indent: 1
        fade: true
    after: |
      Go ahead and populate the `home.html` with all our standard boilerplate code.

      **Don’t add any CSS files. Don’t add `grid.css`, `theme.css`, etc.** We’ll deal with the CSS files later.

      **Pages themselves do not get their own CSS files.** If the styling doesn’t exist within a pattern, it doesn’t exist at all.

      *Check your pattern library in the browser: we should see a new navigation section named “Pages” with one entry, “Home”.*
    notes:
      - label: "Naming conventions"
        text: |
          Homepages on websites are always named `index.html`

          We’re only calling this one `home.html` because it’s isn’t a true homepage, it’s an example of a page within the confines of our pattern library. The pattern library itself is the true “homepage” and you’ll notice it is named `index.html`
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5` & `viewport`"

  - title: "Connect the JavaScript"
    before: |
      You may have noticed that Patternbot has added a JavaScript file to your `common` folder. `patternbot.js` contains lots of information about your pattern library but most importantly it is the include/template system we’ll use for our pages.

      We need to connect `patterbot.js` into our `home.html` so the include system can start working on our example pages.
    code_lang: "html"
    code_file: "pages/home.html"
    code: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Home · GeoHub</title>
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <script src="../common/patternbot.js"></script>
      </head>
      <body>
      ⋮
    lines:
      - num: "1-6"
        fade: true
      - num: "8-9"
        fade: true
      - num: 7
        text: |
          Here were adding the new `<script>` tag, this is how we include JavaScript files in our websites.

          It’s bad practice to put the `<script>` tag inside the HTML `<head>` tag—it **should** be at the very bottom of the HTML, below all the content, right above the closing `</body>` tag. But, in this instance, we need it at the top so it blocks all page rendering until it executes.
    notes:
      - label: "HTML snippets"
        text: "Create the JavaScript `<script>` tag with `jss`"
    after: |
      Notice the path has `../` in it: we need to go out of the `pages` folder so we can find the `common` folder.

  - title: "Add the header"
    before: |
      We’re going to start with the header. We’re going to get a little snippet of code from Patternbot that will include the header HTML onto our page. All magic-like.

      Browse to the “Header” pattern in the pattern library. There’s a small button in the pattern toolbar named “Copy include” that will generate the snippet we need. Press it.

      ![](header-copy-include.jpg)

      Now jump into the code for the `home.html` file and paste, right inside the body.
    code_lang: "html"
    code_file: "pages/home.html"
    code: |
      ⋮
        <script src="../common/patternbot.js"></script>
      </head>
      <body>

        <script type="application/json" data-pattern="header/header"></script>

      </body>
      </html>
    lines:
      - num: "2-4,8-9"
        fade: true
    after: |
      Browse the pattern library and click the “Home” link in the navigation. It will pop open the homepage in a new tab.

      Patternbot will go about it’s business to build the homepage by finding the correct pattern, denoted by the `<script>` tag we just pasted, and including it onto the page **in the exact same location as the include tag**.

      ![](home-header.jpg)

      **We didn’t even have to touch the header pattern!**

      ### A note on CSS files

      *We don’t need to connect any CSS files!* Patternbot will find & connect all the CSS files inside the `patterns` folder as well as connect the standard CSS files from within the `common` folder automatically.

      **Pages themselves do not get their own CSS files.** If the styling doesn’t exist within a pattern, it doesn’t exist at all.

  - title: "Add the footer & banner"
    person:
      icon: "person-1"
      label: "You"
    before: |
      *This is all up to you.* Add the footer & banner patterns into the HTML file by copying their include code from the pattern library and pasting it into the `home.html` file.

      When you’re done, it should look like this:

      ![](home-wrapper.jpg)

  - title: "Set up a grid for cards"
    before: |
      Now we’re going to get a little more complicated. We’re going to set up a grid and add 3 copies of the same pattern into the units.

      Let’s start with just the grid.
    code_lang: "html"
    code_file: "pages/home.html"
    code: |
      ⋮
      <script type="application/json" data-pattern="banner/banner"></script>

      <main class="push-1-2 pad-t-1-2 pad-b-1-2" role="main" id="main">
        <div class="grid wrapper">
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">

          </div>
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">

          </div>
          <div class="unit xs-1 s-1 m-hidden l-1-3 island-1-2">

          </div>
        </div>
      </main>

      <script type="application/json" data-pattern="footer/footer"></script>
      ⋮
    lines:
      - num: "2,18"
        fade: true
    after: |
      *Notice how we added the `<main>` tag below the banner but above the footer.*
  - title: "Include the cards"
    before: |
      Now we can include the card into each of the units that we just recently created.

      *Use the “Copy include” button for the card pattern and paste one into each `.unit` tag.*
    code_lang: "html"
    code_file: "pages/home.html"
    code: |
      ⋮
      <script type="application/json" data-pattern="banner/banner"></script>

      <main class="push-1-2 pad-t-1-2 pad-b-1-2" role="main" id="main">
        <div class="grid wrapper">
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index"></script>
          </div>
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index"></script>
          </div>
          <div class="unit xs-1 s-1 m-hidden l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index"></script>
          </div>
        </div>
      </main>

      <script type="application/json" data-pattern="footer/footer"></script>
      ⋮
    lines:
      - num: "2-6,8-9,11-12,14-18"
        fade: true
    after: |
      Check the page out in your browser and see that the card is displayed 3 times: once in each unit. And it should be completely responsive.

      ![](cards.jpg)

  - title: "Modify the card headings"
    before: |
      But, we have a small problem: each card is completely identical. Ideally we want to have a different icon, text & button for each card. *Adjusting the pattern information requires just a little configuration.*

      We’re only going to adjust two of the cards because one card is already perfect set up for “Diamonds”. So we’ll make the other two cards “Gems” and “Crystals”.

      We’ll start with something simple: just changing the text in the headings.
    code_lang: "html"
    code_file: "pages/home.html"
    code: |
      ⋮
      <main class="push-1-2 pad-t-1-2 pad-b-1-2" role="main" id="main">
        <div class="grid wrapper">
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index">
              {
                "h2": "Gems"
              }
            </script>
          </div>
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index">
              {
                "h2": "Crystals"
              }
            </script>
          </div>
          <div class="unit xs-1 s-1 m-hidden l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index"></script>
          </div>
        </div>
      </main>
      ⋮
    lines:
      - num: "2-4,10-11,17-22"
        fade: true
      - num: "6-8"
        text: |
          In between the open and close `<script>` tag for the pattern include we can define configuration. The configuration is in another markup language called [JSON](https://json.org/), which is based on JavaScript.

          We surround it all with curly braces `{ }`, kinda like CSS.

          Inside there are 2 pieces of information separated by a colon (`:`) and surrounded by double quotes (`"`). **The double quotes are fatally important.**

          ![Zoomed code snippet of the include JSON](include-json.svg)

          1. The information on the left side (before the colon) is a CSS selector. Use any CSS selector you want: class, ID, etc. It will be scoped to within the pattern itself.
          2. The information on the right side (after the colon) is the replacement text. Patternbot will replace all the text inside the selected element you chose with the new text you supply.

          ---

          This isn’t how all JSON is used; JSON is a generic data storage & representation system. The selector/replacement system is just how Patternbot uses the language to describe the include configuration.

    after: |
      View the page in the browser and you should see the new text headings for each card!

      ![](card-headings.jpg)

      **If it isn’t working, check in the web developer tools under the “Console” tab. There will be helpful, detailed error messages.**

  - title: "Modify more card details"
    before: |
      Okay, let’s take this a step further: we’ll adjust the paragraphs & buttons.
    code_lang: "html"
    code_file: "pages/home.html"
    code: |
      ⋮
      <main class="push-1-2 pad-t-1-2 pad-b-1-2" role="main" id="main">
        <div class="grid wrapper">
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index">
              {
                "h2": "Gems",
                "p": "Lots of bright, wonderful colours—and shapes.",
                ".btn": "See more gems"
              }
            </script>
          </div>
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index">
              {
                "h2": "Crystals",
                "p": "Shiny, glowly and they make great sounds.",
                ".btn": "See more crystals"
              }
            </script>
          </div>
          <div class="unit xs-1 s-1 m-hidden l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index"></script>
          </div>
        </div>
      </main>
      ⋮
    lines:
      - num: "2-4,12-13,21-26"
        fade: true
      - num: 7
        text: |
          Notice the comma (`,`) added at the end of this line. Each line should have a comma after it.
      - num: 9
        text: |
          Except the last line before the closing curly brace (`}`) **must never have a comma**.
    after: |
      Check it out in the browser and make sure the paragraphs & headings have unique content inside each card.

  - title: "Modify the icons"
    before: |
      Finally we want to make sure that each icon is unique, so we can replace the `xlink:href=""` attribute inside each card’s `<svg>` to point to a new icon.
    code_lang: "html"
    code_file: "pages/home.html"
    code: |
      ⋮
      <main class="push-1-2 pad-t-1-2 pad-b-1-2" role="main" id="main">
        <div class="grid wrapper">
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index">
              {
                "use[xlink:href]": "../images/icons.svg#gem",
                "h2": "Gems",
                "p": "Lots of bright, wonderful colours—and shapes.",
                ".btn": "See more gems"
              }
            </script>
          </div>
          <div class="unit xs-1 s-1 m-1-2 l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index">
              {
                "use[xlink:href]": "../images/icons.svg#crystal",
                "h2": "Crystals",
                "p": "Shiny, glowly and they make great sounds.",
                ".btn": "See more crystals"
              }
            </script>
          </div>
          <div class="unit xs-1 s-1 m-hidden l-1-3 island-1-2">
            <script type="application/json" data-pattern="cards/index"></script>
          </div>
        </div>
      </main>
      ⋮
    lines:
      - num: "2-6,8-16,18-28"
        fade: true
      - num: 7
        text: |
          This selector is a little different because we want to replace an attribute. To replace an attribute we must select using an attribute selector.

          ![Zoomed code snippet of the include JSON attribute selector](include-json-attr.svg)

          1. Start the selector with a tag or class to get the correct element.
          2. Finish the selector with the attribute selector for the attribute that should be changed.
          3. The info after the comma is the text replacement to replace all the text inside the attribute.

          **In this situation we’re replacing the whole path for the `xlink:href=""` attribute with a different icon’s path so we can have unique icons on each displayed card.**
    after: |
      Check it out in the browser and you should see three completely unique cards!

      ![](cards-unique.jpg)

  - title: "Modify the navigation"
    before: |
      There’s one final change I’d like to make—because of my perfectionist nature.

      You may have noticed that the “Crystals” page is highlighted in the navigation as the current page. That’s completely untrue, this is supposed to be the homepage.

      I’d like to get rid of that highlight. There’s a `.current` class, already in the header pattern’s HTML, so we can use the include configuration JSON to replace the class with something else.
    code_lang: "html"
    code_file: "pages/home.html"
    code: |
      ⋮
      <body>

        <script type="application/json" data-pattern="header/header">
          {
            ".current[class]": "gutter-1-2"
          }
        </script>

        <script type="application/json" data-pattern="banner/banner"></script>
      ⋮
    lines:
      - num: "2,10"
        fade: true
      - num: 6
        text: |
          Here we’re selecting the element inside the pattern that has the class `.current`, then using the attribute selector for `[class]` because that’s the attribute we want to change.

          We’re changing the `class` to `gutter-1-2` because, if you look in the pattern its class attribute is currently `class="gutter-1-2 current"`. Since the config JSON only does **replacements** we have to remember that everything inside that attribute will be changed and keep the stuff we want.

          This line of JSON does not have a comma because it’s the last line before the closing curly brace.
    after: |
      **That’s it! We generated a whole page using our patterns without copying-and-pasting any of the HTML code.**

      We’re getting much closer to how professional websites are built and we’ll expand on these ideas when we learn [Jekyll](/topics/jekyll/). (Learn the Web is built using Jekyll!)

---
