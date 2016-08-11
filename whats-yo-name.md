---
layout: lesson
title: "What’s yo name?"
desc: "Watch some videos showing basic Javascript syntax and build a small name comparing program."

extra_tutorials:
  - title: "Javascript syntax"
    url: javascript-syntax
  - title: "Javascript validator"
    url: /topics/validators/#validating-javascript
  - title: "Javascript cheat sheet"
    url: javascript-cheat-sheet
    highlight: true
  - title: "Javascript intro slide deck"
    url: /courses/web-dev-4/javascript-intro/
    highlight: true

steps:
  - title: "Javascript introduction"
    before: |
      Watch this video on creating a Javascript file and connecting it to your HTML file.
    video: "j2ppuBwAATg"

  - title: "Program flow"
    before: |
      Watch this video on controlling the flow of your program in Javascript.
    video: "WxRwf5KvNVI"

  - title: "Variables & strings"
    before: |
      Watch this video on creating variables to hold information in your Javascript program as well as looking at text and strings.
    video: "czTWbdwbt7E"

  - title: "Numbers"
    before: |
      Watch this video on using numbers in Javascript and applying arithmetic and mathematical operations.
    video: "LLAd7PybpdQ"

  - title: "Boolean datatypes"
    before: |
      A quick look at the boolean data type in Javascript.
    video: "tScxERK1fMY"

  - title: "If-statements & logic "
    before: |
      Watch this video covering if-statements in Javascript and all different possible boolean logic operators: comparisons, greater/less than, and/or, etc.
    video: "4lATbwt87Cs"

  - title: "What’s yo name? program set up"
    before: |
      *This code tutorial is recreating the last section—the name comparison if-statement—in the final video above.*
    folders:
      - label: "whats-yo-name"
        type: folder
      - label: "index.html"
        indent: 1
      - label: "js"
        type: folder
        indent: 1
      - label: "main.js"
        indent: 2
    after: |
      Before we get started, create some files and get ready.

      1. Create a folder named `whats-yo-name`
      2. Make an `index.html` & add the boilerplate code.
      3. Make a `main.js` in your `js` folder.
    notes:
      - label: "Type it, type it real good"
        text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`"

  - title: "Link the Javascript to the HTML"
    before: |
      At the bottom of the `index.html` file we need to connect the Javascript file.
    code_lang: "html"
    code_file: "index.html"
    code: |
      ⋮
      </head>
      <body>

        <script src="js/main.js"></script>
      </body>
      </html>
    lines:
      - num: "2-3"
        fade: true
      - num: 5
        text: |
          The `<script>` tag is used to connect a Javascript file to HTML.

          It should always go at the bottom for two reasons:

          1. **Performance** — Javascript will stop rendering the page until the JS loads. Putting it at the bottom makes the load time appear faster because the page can be displayed first.
          2. **HTML manipulation** — we want to manipulate HTML with our JS, but the HTML must be rendered to the screen before JS can do anything.
      - num: "6-7"
        fade: true

  - title: "Write some Javascript!"
    before: |
      *This is taken right from the last bit of the video.*

      These few lines of code will ask a user for their name and display a message based on what they type.
    code_lang: "js"
    code_file: "main.js"
    code: |
      var newName = prompt('What is your name?');

      if (newName == 'Thomas') {
        alert('Names are the same!');
      } else {
        alert('Names are different.');
      }
    lines:
      - num: 1
        text: |
          The variable `newName` will hold whatever someone types into the dialogue box.

          The `prompt()` is a function built into Javascript that will display a dialogue people can type into.
      - num: 3
        text: |
          The if-statement is going to compare the contents of `newName` against the string `'Thomas'`.

          - If they are the same the first path is taken.
          - If they are different the second path is taken.

          The double equals `==` means compare.
          A single equals `=` means set.
      - num: 4
        text: |
          The `alert()` function is built into Javascript and will display a dialogue with some text.

  - title: "Bonus challenge"
    before: |
      Change the program above so that the `alert` messages say what the user typed in. Make the messages read:

      - **“Hey Thomas, our names are the same!”**
      - **“Too bad our names are different, Thomas.”**
    notes:
      - label: "Hint"
        text: "You’ll have to combine strings and variables together with a special character."

---
