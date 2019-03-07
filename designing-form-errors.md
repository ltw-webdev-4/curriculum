---
layout: lesson
title: "Designing form errors"
desc: "Write up code for accessible, well designed form error messages with a little JavaScript to help."

markbot_submit: true
hide_show_for_marks: true

extra_tutorials:
  - title: "Forms"
    url: forms
  - title: "Forms cheat sheet"
    url: forms-cheat-sheet
    highlight: true
  - title: "Form error messages slide deck"
    url: "/courses/web-dev-4/form-error-messages/"

goal:
  image: goal.png
  before: |
    We’re going to create a fairly basic, but decently accessible form with error messages.

    Most forms really require JavaScript to become fully functional & accessible. We are going to include a little bit of JavaScript to help out but it’s only going to help hide/show the error messages.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

fork:
  url: "https://github.com/acgd-webdev-4/designing-form-errors/fork"

steps:
  - title: "Set up project"
    before: |
      After forking & cloning the repository we have a few starter files, but not everything we need…
    folders:
      - label: "designing-form-errors"
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
      - label: "images"
        type: folder
        fade: true
        indent: 1
    after: |
      1. Make an `index.html` & add the boilerplate code.
      2. Make a `modules.css` in your `css` folder—[get a new version from Modulifier](https://modulifier.web-dev.tools/). **Make sure to press “Select All”.**
      3. Make a `type.css` in your `css` folder—[get a new version from Typografier](https://typografier.web-dev.tools/).
      4. Make a `main.css` in your `css` folder—it can remain empty.
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`, `css`"

  - title: "Add HTML for the form & an input"
    before: |
      We’re going to start by adding the `<form>` tag and a single `<input>` tag to make sure things work. Afterwards we’ll add the remainder of the HTML.

      *And don’t forget to add the submit button.*
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
      </head>
      <body>

        <form class="max-length island" method="post" action="#">
          <div class="push-1-2">
            <label for="name">Name</label>
            <input id="name" required>
          </div>

          <div class="pad-t-1-2">
            <button class="btn" type="submit">Send</button>
          </div>
        </form>

      </body>
      </html>
    lines:
      - num: "2-3"
        fade: true
      - num: 8
        text: |
          Notice the `required` attribute on the `<input>` tag. The user will not be able to submit the form without putting correct information into this field.
      - num: "16-17"
        fade: true
    after: |
      This is what we should see in the browser right now:

      ![](html-start.png)

  - title: "Add some starter CSS"
    before: |
      Next up we’ll add a little bit of CSS. Nothing too fancy: just a font change and the styling to highlight optional fields.
    code_lang: css
    code_file: "css/main.css"
    code: |
      html {
        font-family: sans-serif;
      }

      .flag-optional {
        color: #999;
      }
    lines:
      - num: "5-7"
        text: |
          We’ll use this class to highlight the fields that are optional in our form.

  - title: "Add the remaining form fields"
    before: |
      To complete our form fields we want to add an “email” field, a “website” field and an “agree” checkbox.

      Putting them in separate `<div>` tags keeps things organized and easily style-able.
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
      <form class="max-length island" method="post" action="#">
        <div class="push-1-2">
          <label for="name">Name</label>
          <input id="name" required>
        </div>

        <div class="push-1-2">
          <label for="email">Email</label>
          <input type="email" id="email" required>
        </div>

        <div class="push-1-2">
          <label for="url">Website <em class="flag-optional milli normal">(optional)</em></label>
          <input type="url" id="url">
        </div>

        <div class="push-1-2 pad-t-1-2">
          <input type="checkbox" id="agree" required>
          <label for="agree">I’m totally awesome!</label>
        </div>

        <div class="pad-t-1-2">
          <button class="btn" type="submit">Send</button>
        </div>
      </form>
      ⋮
    lines:
      - num: "2-6"
        fade: true
      - num: "23-26"
        fade: true
      - num: 14
        text: |
          Notice how the optional form field is highlighted. It’s best practice to highlight the optional fields, and not the required fields. All fields should be required; if they aren’t required why are they on the form?
    after: |
      Our form should now have all the fields we want:

      ![](all-fields.png)

  - title: "Add the error messages"
    before: |
      Since this lesson is all about designing error messages that’s what we’re going to add next.

      The error messages always exist on the page in the HTML but are hidden—later we’ll add some CSS to show them.
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
      <form class="max-length island" method="post" action="#">
        <div class="error-message error-message-highlighted push island-1-2" role="alert" aria-live="assertive">
          <h3 class="push-0">
            <i class="icon i-32"><svg><use xlink:href="images/icons.svg#error" /></svg></i>
            <span class="icon-label">There are items that require your attention</span>
          </h3>
        </div>

        <div class="push-1-2">
          <label for="name">Name</label>
          <input id="name" required aria-describedby="name-error">
          <p class="error-message milli island-1-4 push-0" id="name-error">
            <i class="icon i-16"><svg><use xlink:href="images/icons.svg#error" /></svg></i>
            <span class="icon-label">Please provide a name</span>
          </p>
        </div>

        <div class="push-1-2">
          <label for="email">Email</label>
          <input type="email" id="email" required aria-describedby="email-error">
          <p class="error-message milli island-1-4 push-0" id="email-error">
            <i class="icon i-16"><svg><use xlink:href="images/icons.svg#error" /></svg></i>
            <span class="icon-label">Please provide a properly formatted email address</span>
          </p>
        </div>

        <div class="push-1-2">
          <label for="url">Website <em class="flag-optional milli normal">(optional)</em></label>
          <input type="url" id="url">
        </div>

        <div class="push-1-2 pad-t-1-2">
          <input type="checkbox" id="agree" required aria-describedby="agree-error">
          <label for="agree">I’m totally awesome!</label>
          <p class="error-message milli island-1-4 push-0" id="agree-error">
            <i class="icon i-16"><svg><use xlink:href="images/icons.svg#error" /></svg></i>
            <span class="icon-label">Please agree that you’re totally awesome</span>
          </p>
        </div>

        <div class="pad-t-1-2">
          <button class="btn" type="submit">Send</button>
        </div>
      </form>
      ⋮
    lines:
      - num: 2
        fade: true
      - num: "3-8"
        text: |
          This is the main error message—it shows at the top to indicate that fields further down have errors.

          Notice we included an icon in the error message, this is to help with clarity & accessibility. We aren’t relying on just the colour for denoting an error message because not everybody can see the colour.

          - `role="alert"` will force screen readers to recognize when this item becomes visible.
          - `aria-live="assertive"` will force the screen reader to immediately read this message before anything else.
      - num: "10-11"
        fade: true
      - num: 12
        text: |
          The `aria-describedby=""` attribute helps screen readers associate the error message with this form field—the information can be then found and read out by the screen reader.

          It points to one or more IDs of other elements on the page.
      - num: "13-16"
        text: |
          This is the actual error message. Notice how the `id=""` matches the `aria-describedby` attribute on the `<input>` tag.
      - num: "17-20"
        fade: true
      - num: "26-33"
        fade: true
      - num: 35
        fade: true
      - num: "40-45"
        fade: true

  - title: "Style the error messages"
    before: |
      Now let’s style those error messages. We want to make them big and obvious and clearly associate them with the fields.

      Also, adding a red border around the invalid inputs helps them stand out a little.
    code_lang: css
    code_file: "css/main.css"
    code: |
      ⋮
      .flag-optional {
        color: #999;
      }

      input:invalid,
      input[type="checkbox"]:invalid + label::before {
        border-color: #f33;
      }

      .error-message {
        display: none;
        background-color: #fee;
        color: #c33;
      }

      .error-message-highlighted {
        background-color: #c33;
        color: #fff;
      }

      .error-message:first-child,
      input:invalid + .error-message,
      input:invalid + label + .error-message {
        display: block;
      }
    lines:
      - num: "2-4"
        fade: true
      - num: "6-9"
        text: |
          Yep—those are some complex selectors.

          The new part is `:invalid`. It’s a pseudo-selector (like `:hover`) that only targets an `<input>` when the information a user entered is wrong in some way.

          Essentially these selectors target invalid fields and change their border colour to red.
      - num: 12
        text: |
          Here we’re going to hide the error messages by default, then further down make them visible again when the fields are invalid.
      - num: "22-26"
        text: |
          This chunk of code will show the appropriate error messages when the field is invalid.
    after: |
      We can now see our messages all the time. Because all the fields are technically invalid (they don’t have the correct information) all the messages show.

      ![](all-errors.png)

      If you fill information into each of the fields you’ll see that their individual error messages disappear, but we can’t get rid of the one at the top.

      ![](some-errors.png)

      **Remember that since we’re using icon sprite sheets you’ll need to use a web server in Chrome to see them: drop the folder into Markbot and press `⌘B`**

  - title: "Add the helper JavaScript"
    before: |
      When we refresh the page or first come to the page, the error messages are already visible. Showing the error messages right away isn’t good for usability.

      So: JavaScript to the rescue. With a little JS we can hide the error messages by default, then when the user submits the form we can display the error messages at that point.

      *Don’t worry though, the JS is pre-written and ready to run.*
    multi_code:
      - code_before: |
          First we need to add a new attribute to the `<form>` tag: the `novalidate` attribute. It tells the browser not to run it’s default validation and allows our JavaScript to control the validation instead.
        code_lang: html
        code_file: "index.html"
        code: |
          ⋮
          </head>
          <body>

            <form class="max-length island" method="post" action="#" novalidate>
          ⋮
        lines:
          - num: "2-3"
            fade: true
          - num: 5
            text: |
              Notice the new `novalidate` attribute on the form. This will tell the browser to not automatically validate the form on submission and allow our Javacript to do it instead.
      - code_before: |
          Then down at the bottom of the code we add the actual `<script>` tag to the JS file.
        code_lang: html
        code_file: "index.html"
        code: |
          ⋮
                <button class="btn" type="submit">Send</button>
              </div>
            </form>

            <script src="https://thomasjbradley.github.io/form-validation-helper/index.js"></script>
          </body>
          </html>
        lines:
          - num: "2-4"
            fade: true
          - num: 6
            text: |
              Add the script tags immediately above the closing `</body>` tag—always.

              This script is a simple piece of JavaScript that will help with the usability of our forms. Combined with a few CSS tweaks it’ll hide the error messages until after the user tries to submit the form.
          - num: "7-8"
            fade: true
    after: |
      Here’s the JavaScript URL for quick copying-and-pasting:

      ```
      https://thomasjbradley.github.io/form-validation-helper/index.js
      ```

  - title: "Fix the error messages"
    before: |
      With the JavaScript in place we now need to tweak our CSS a little to better support what the JS is doing.

      The JavaScript code will add the class `.is-validated` to our `<form>` tag when the user submits the form—but only if there are errors that should be shown.

      It’s up to our CSS to show the right errors to the user with the right selectors.
    code_lang: css
    code_file: "css/main.css"
    code: |
      ⋮
      .flag-optional {
        color: #999;
      }

      .is-validated input:invalid,
      .is-validated input[type="checkbox"]:invalid + label::before,
      .is-validated:invalid,
      .is-validated[type="checkbox"]:invalid + label::before {
        border-color: #f33;
      }

      .error-message {
        display: none;
        background-color: #fee;
        color: #c33;
      }

      .error-message-highlighted {
        background-color: #c33;
        color: #fff;
      }

      .is-validated > .error-message:first-child,
      .is-validated input:invalid + .error-message,
      .is-validated input:invalid + label + .error-message,
      .is-validated:invalid + .error-message,
      .is-validated:invalid + label + .error-message {
        display: block;
      }
    lines:
      - num: "2-4"
        fade: true
      - num: "6-7"
        text: |
          Prepend each of the selectors with `.is-validated`. This is what the JavaScript does: it adds the class to our `<form>` tag after the user tries to submit the form information.
      - num: "8-9"
        text: |
          Add a few more selectors to handle different form field situations, and different ways of writing forms.
      - num: "10-23"
        fade: true
      - num: "24-26"
        text: |
          Also prepend each of these selectors with the `.is-validated` class.
      - num: "27-28"
        text: |
          And some more different scenarios—gotta cover all possible situations!
      - num: "29-30"
        fade: true
    after: |
      When we load the page we should see the form like this:

      ![](all-fields.png)

      And after we send the information we should see the error messages pop up:

      ![](goal.png)
---
