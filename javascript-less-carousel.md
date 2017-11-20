---
layout: lesson
topic: "JavaScript-less carousel"
desc: "Learn to implement a functional and reusable carousel without JavaScript."

extra_tutorials:
  - title: "Advanced CSS interactions"
    url: advanced-css-interactions
  - title: "Forms cheat sheet"
    url: forms-cheat-sheet

goal:
  before: |
    We’re going to create a fairly basic carousel using only CSS.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

important:
  title: "Simple but not accessible"
  text: |
    The example that we’re completing here is simple to set up and requires no JavaScript.

    But it is not the most accessible, feature-rich, or even reusable piece of code. To make a truly good & accessible carousel we should add JavaScript and a bunch more ARIA attributes & roles to fully realize the functionality.

fork:
  url: "https://github.com/acgd-webdev-4/javascript-less-carousel/fork"

steps:
  - title: "Set up project"
    before: |
      After forking & cloning the repository we have a few starter files, but not everything we need…
    folders:
      - label: "javascript-less-carousel"
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

  - title: "Create the HTML images"
    before: |
      Let’s start the HTML by adding a bunch of wrapper `<div>` tags and the HTML necessary to display the four images.

      Here’s the names of the images for quick copying-and-pasting:

      ```
      arsinoitherium
      elasmotherium
      glyptodon
      megatherium
      ```

      *All the different wrapper tags are needed for grouping the controls and making sure the correct `relative` containers are used.*
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
      </head>
      <body>

        <section class="max-length">

          <div class="carousel">

            <div class="carousel-inner relative">
              <div class="carousel-items">
                <div class="carousel-item embed embed-golden" id="arsinoitherium">
                  <img class="embed-item" src="images/arsinoitherium.jpg" alt="">
                </div>

                <div class="carousel-item embed embed-golden" id="elasmotherium">
                  <img class="embed-item" src="images/elasmotherium.jpg" alt="">
                </div>

                <div class="carousel-item embed embed-golden" id="glyptodon">
                  <img class="embed-item" src="images/glyptodon.jpg" alt="">
                </div>

                <div class="carousel-item embed embed-golden" id="megatherium">
                  <img class="embed-item" src="images/megatherium.jpg" alt="">
                </div>
              </div>

            </div>

          </div>

        </section>
      ⋮
    lines:
      - num: "2-3"
        fade: true
    after: |
      Have a quick refresh in the browser and you should see this (though the images will be much bigger):

      ![](image-html.jpg)

  - title: "Add the controls"
    before: |
      Next up we’re going to add all the controls. We’re going to use radio buttons in a hacky way: instead of representing collected information they’ll represent the state of our application, aka which slide is currently visible.

      *This is definitely not the most accessible approach to using radio buttons, but it’s a fairly common pattern and is good for getting a quick demo going.*
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
      </head>
      <body>

        <section class="max-length">

          <div class="carousel">
            <input class="carousel-input" type="radio" name="mammals" id="arsinoitherium-control">
            <input class="carousel-input" type="radio" name="mammals" id="elasmotherium-control">
            <input class="carousel-input" type="radio" name="mammals" id="glyptodon-control">
            <input class="carousel-input" type="radio" name="mammals" id="megatherium-control">

            <div class="carousel-inner relative">
              <div class="carousel-items">
                <div class="carousel-item embed embed-golden" id="arsinoitherium">
                  <img class="embed-item" src="images/arsinoitherium.jpg" alt="">
                </div>

                <div class="carousel-item embed embed-golden" id="elasmotherium">
                  <img class="embed-item" src="images/elasmotherium.jpg" alt="">
                </div>

                <div class="carousel-item embed embed-golden" id="glyptodon">
                  <img class="embed-item" src="images/glyptodon.jpg" alt="">
                </div>

                <div class="carousel-item embed embed-golden" id="megatherium">
                  <img class="embed-item" src="images/megatherium.jpg" alt="">
                </div>
              </div>

              <ul class="carousel-controls">
                <li>
                  <label class="carousel-btn" for="arsinoitherium-control">Arsinoitherium</label>
                </li>
                <li>
                  <label class="carousel-btn" for="elasmotherium-control">Elasmotherium</label>
                </li>
                <li>
                  <label class="carousel-btn" for="glyptodon-control">Glyptodon</label>
                </li>
                <li>
                  <label class="carousel-btn" for="megatherium-control">Megatherium</label>
                </li>
              </ul>
            </div>

          </div>

        </section>
      ⋮
    lines:
      - num: "2-7"
        fade: true
      - num: "8-11"
        text: |
          These are the radio buttons here. They’ll actually be hidden but whichever one is currently checked will denote which slide is currently visible.
      - num: "13-30"
        fade: true
      - num: "32-45"
        text: |
          This list and `<label>` tags will represent the little buttons at the bottom of the carousel for us to hide/show.
      - num: "46-50"
        fade: true

  - title: "Style the images"
    before: |
      To get the images styled we need only a little bit of CSS!
    code_lang: css
    code_file: "css/main.css"
    code: |
      .carousel-items > div {
        display: none;
      }
    after: |
      If you now refresh in your browser you’ll see nothing… just the names of the four mammals from the `<label>` tags.

  - title: "Make it functional"
    before: |
      The next thing I think we should do is add the CSS necessary to make the carousel functional.

      This requires some complex CSS selectors. We need to select each radio button that’s checked, then go into the `<div>` beside and select the correct slide.
    multi_code:
      - code_lang: css
        code_file: "css/main.css"
        code: |
          ⋮
          #arsinoitherium-control:checked ~ .carousel-inner #arsinoitherium,
          #elasmotherium-control:checked ~ .carousel-inner #elasmotherium,
          #glyptodon-control:checked ~ .carousel-inner #glyptodon,
          #megatherium-control:checked ~ .carousel-inner #megatherium {
            display: block;
          }
      - code_before: |
          If you ever want to add another slide to your carousel you have to come into the CSS and add the appropriate new selectors.

          *Another benefit of using JavaScript is that the JS code would help maintain all this complex CSS.*

          Now, we’d like to make the first slide visible on the page. That requires a simple tweak to our HTML.
        code_lang: html
        code_file: "index.html"
        code: |
          ⋮
          <section class="max-length">

            <div class="carousel">
              <input class="carousel-input" type="radio" name="mammals" id="arsinoitherium-control" checked>
              <input class="carousel-input" type="radio" name="mammals" id="elasmotherium-control">
              <input class="carousel-input" type="radio" name="mammals" id="glyptodon-control">
              <input class="carousel-input" type="radio" name="mammals" id="megatherium-control">

              <div class="carousel-inner relative">
                <div class="carousel-items">
          ⋮
        lines:
          - num: "2-4"
            fade: true
          - num: 5
            text: |
              By adding the `checked` attribute to this radio button the associated image should now be visible because of those complex CSS selectors we wrote.
          - num: "6-11"
            fade: true
    after: |
      Refresh this in the browser and we should see a single slide:

      ![](single-slide.jpg)

      **But not only that—it should fully work!** Click on the different slide names at the bottom and see that the carousel changes.

  - title: "Style the controls"
    before: |
      The last thing we have to do is make the controls look nice. That’ll require a little HTML & CSS.
    multi_code:
      - code_lang: html
        code_file: "index.html"
        code: |
          ⋮
          <ul class="carousel-controls list-group-inline pin-cb w-1 text-center push-0 island-1-2">
            <li>
              <label class="carousel-btn icon i-18 ir" for="arsinoitherium-control">Arsinoitherium</label>
            </li>
            <li>
              <label class="carousel-btn icon i-18 ir" for="elasmotherium-control">Elasmotherium</label>
            </li>
            <li>
              <label class="carousel-btn icon i-18 ir" for="glyptodon-control">Glyptodon</label>
            </li>
            <li>
              <label class="carousel-btn icon i-18 ir" for="megatherium-control">Megatherium</label>
            </li>
          </ul>
          ⋮
        lines:
          - num: "3,5-6,8-9,11-12,14-15"
            fade: true
          - num: 2
            text: |
              Add the following new classes:

              - `.list-group-inline`
              - `.pin-cb`
              - `.w-1`
              - `.text-center`
              - `.push-0`
              - `.island-1-2`
          - num: 4
            text: |
              Add the following new classes:

              - `.icon`
              - `.i-18`
              - `.ir`
      - code_before: |
          Now for a little bit of CSS to make them look like circles.

          We’re also going to add some CSS that will highlight the current button. Using complex CSS selectors, like we used for showing the right slide, we’ll color the correct button.
        code_lang: css
        code_file: "css/main.css"
        code: |
          ⋮
          .carousel-btn {
            border: 4px solid #fff;
            border-radius: 50%;
          }

          #arsinoitherium-control:checked ~ .carousel-inner [for="arsinoitherium-control"],
          #elasmotherium-control:checked ~ .carousel-inner [for="elasmotherium-control"],
          #glyptodon-control:checked ~ .carousel-inner [for="glyptodon-control"],
          #megatherium-control:checked ~ .carousel-inner [for="megatherium-control"] {
            background-color: #fff;
          }
        lines:
          - num: "2-5"
            text: |
              This CSS will make the buttons be circles that aren’t filled.
          - num: "7-12"
            text: |
              This CSS will make the currently visible slide shown in it’s associated button by making the background-color white.

    after: |
      And that’s it! A fully functional carousel using only CSS.

---
