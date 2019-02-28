---
layout: lesson
topic: "Building pages with patterns"
desc: "Look at how to reuse your pattern code when building-out the example pages in your pattern libraries."

hide_markbot: true

extra_tutorials:
  - title: "Jekyll"
    url: jekyll
    highlight: true
  - title: "Jekyll cheat sheet"
    url: jekyll-cheat-sheet
  - title: "Pattern libraries"
    url: pattern-libraries
    highlight: true
  - title: "Pattern library cheat sheet"
    url: pattern-library-cheat-sheet
  - title: "Markdown & YAML cheat sheet"
    url: markdown-yaml-cheat-sheet

goal:
  no_image: true
  before: |
    We’re going to make a couple example pages in our `ecommerce-pattern-library` to see how the syntax works, and what it’s capable of doing.

    We’ll explores the ideas of Jekyll’s include system, passing information into them and displaying multiple copies of the same pattern—but with different text & content.
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
  - title: "Insert banners into pages"
    before: |
      **Continue on with your `ecommerce-pattern-library` repository.**

      We’ve already got our layouts working, so now, to see how this works, let’s add banners to the top of both our `index.html` & our `products.html`

      **In the final version of these two pages, in your website, you may not want banners at the top—and that’s completely okay—but follow along for now to see how the system works.**
    multi_code:
      - code_before: |
          ![](copy-banner.jpg)

          From your pattern library, copy one of your banner’s includes and paste it onto your homepage.
        code_lang: liquid
        code_file: "index.html"
        code: |
          ---
          layout: default
          ---

          {% pattern banner/banner %}
      - code_before: |
          *Now paste that same code into your products page too!*
        code_lang: liquid
        code_file: "products.html"
        code: |
          ---
          layout: default
          ---

          {% pattern banner/banner %}
    after: |
      Open your website up in the browser and click between the two pages—they should look exactly the same—and have a banner!

      ![](home-banner.jpg)

  - title: "Add variables for banner text"
    before: |
      The first thing I want to adjust is text on the banner—I don’t want the text to be exactly the same for every page.

      - On the homepage the banner text should say one thing
      - On the products page the banner text should say something different

      In the banner pattern’s code, we’re going to provide placeholder variables—similar to our layout—that will allow us to configure parts of the banner.

      **Remember that this code will look radically different from your banner. We’re learning a technique right now, not directly copying and pasting.**
    code_lang: "html"
    code_file: "_patterns/banner/banner.html"
    code: |
      <div class="banner embed embed-24by10 push-1-2">
        <div class="banner-content pin-lc gutter">
          <h1 class="banner-title yotta push-1-2">{{include.heading}}</h1>
          <p class="banner-info exa italic max-length-no-center">{{include.text}}</p>
          {% pattern buttons/light %}
        </div>
        <i class="banner-icon icon i-256 pin-rb"><svg><use xlink:href="/images/icons.svg#ruby"></use></svg></i>
      </div>
    lines:
      - num: "1-2,5-8"
        fade: true
      - num: 3
        text: |
          Notice, that instead of actually placing text in the `<h1>` tag I’ve replaced it with a placeholder variable.

          - They’re always surrounded by two pairs of `{`—that’s part of Jekyll’s template engine
          - They always start with `include.`—that’s part of Jekyll’s include system
          - What comes after the dot is completely made up—you decide what you want to call it
      - num: 4
        text: |
          I’ve added a second placeholder variable into the paragraph too.
    after: |
      ![](banner-text-missing.jpg)

      *If you refresh in the browser now you should see both of those pieces of text disappear. That’s because we haven’t actually inserted anything into the placeholder variables yet.*

  - title: "Document all the include fields"
    before: |
      Oh documentation, how do we love thee. By documenting the two placeholder variables we just created, Patternbot will help us copy and paste the include code by adding the variables.

      Open up your banner’s `_config.yml` file so we can document the fields.
    code_lang: yml
    code_file: "_patterns/banner/config.yml"
    code: |
      patterns:
        banner:
          fields:
            - name: heading
              type: string
              example: "Brilliant, stunning, bright"
            - name: text
              type: string
              example: "Geological marvels: gems, crystals, diamonds, geodes and much more!"
    lines:
      - num: 2
        text: |
          We’ve targeted the `banner.html` file that we want to modify.
      - num: 3
        text: |
          Add a new key underneath `banner` called `fields`—you likely already have `title` & `description` there.
      - num: 4
        text: |
          The `fields` entry is an array—a list—so each item within it must start with a `-`

          We can then specify the name of the field, spelled exactly the same way you wrote it in `{{include.heading}}` except without the brackets or the `include.` parts.
      - num: 5
        text: |
          Next up we should specify the “type” of information the field expects, refer to the list of types we look at during our [“Fried data”](/courses/web-dev-4/fried-data/#slide-3) exercise.
      - num: 6
        text: |
          Finally we should specify an example of what to write in that field. Patternbot will also use this example to display within the pattern library.
    after: |
      Now if you view the code in your pattern library you can see that it shows the fields that the pattern requires, with nice documentation.

      ![](pattern-fields.jpg)

      The include code snippet is now updated too, which we’ll use in the next step.

  - title: "Re-copy & re-paste the banner includes"
    before: |
      Now that the pattern’s include code snippet has been updated, we can re–copy-n-paste it into the two pages.

      **We can then use the fields, within the include code, to adjust the text so our homepage’s banner is different than our product list’s banner.**
    multi_code:
      - code_lang: liquid
        code_file: "index.html"
        code: |
          ---
          layout: default
          ---

          {% pattern banner/banner heading="Brilliant, stunning, bright" text="Geological marvels: gems, crystals, diamonds, geodes and much more!" %}
      - code_lang: liquid
        code_file: "products.html"
        code: |
          ---
          layout: default
          ---

          {% pattern banner/banner heading="Crystals" text="See all the sparkly, wonderful crystals from the depths of the Earth." %}
        lines:
          - num: 5
            text: |
              Adjust the text in the banner to match the page more appropriately.
    after: |
      ![](crystals-banner.jpg)

      Check it out in your browser and see the banner text change between the two pages!

  - title: "Tweak the image"
    before: |
      Now I’d like to adjust the image on the banner. In this situation it’s an icon—but the technique can be used for absolutely anything. So it would work just as well for an image `src` itself.

      **You can put a placeholder variable anywhere! And pass it anything you want! Numbers, text, URLs, image paths—anything!**
    multi_code:
      - code_lang: html
        code_file: "_patterns/banner/banner.html"
        code: |
          <div class="banner embed embed-24by10 push-1-2">
            <div class="banner-content pin-lc gutter">
              <h1 class="banner-title yotta push-1-2">{{include.heading}}</h1>
              <p class="banner-info exa italic max-length-no-center">{{include.text}}</p>
              {% pattern buttons/light %}
            </div>
            <i class="banner-icon icon i-256 pin-rb"><svg><use xlink:href="/images/icons.svg#{{include.icon}}"></use></svg></i>
          </div>
        lines:
          - num: "1-6,8"
            fade: true
          - num: 7
            text: |
              Notice how I’ve replaced the ID of the icon with a variable: `{{include.icon}}`. The variables can go absolutely anywhere we want in the HTML.

              This allows me to pick the name of one of the icons and insert it into this placeholder.
      - code_before: |
          Don’t forget the documentation!
        code_lang: yaml
        code_file: "_patterns/banner/config.yml"
        code: |
          patterns:
            banner:
              fields:
                - name: heading
                  type: string
                  example: "Brilliant, stunning, bright"
                - name: text
                  type: string
                  example: "Geological marvels: gems, crystals, diamonds, geodes and much more!"
                - name: icon
                  type: string
                  example: "ruby"
        lines:
          - num: "1-9"
            fade: true
      - code_before: |
          Now let’s insert the icon into our homepage:
      - code_lang: html
        code_file: "index.html"
        code: |
          ---
          layout: default
          ---

          {% pattern banner/banner icon="ruby" heading="Brilliant, stunning, bright" text="Geological marvels: gems, crystals, diamonds, geodes and much more!" %}
        lines:
          - num: "1-3"
            fade: true
          - num: 5
            text: |
              Notice how there’s now an `icon=""` field entry within the include.
    after: |
      ![](crystals-banner-icon.jpg)

      **If you aren’t using icons within your banners—no problem! See if you can figure out how to apply a similar technique to the image’s `src=""` attribute.**

  - title: "Tweak & hide the button"
    before: |
      For the button, I’d like it to be visible, with different text, on the homepage and invisible on the banner page.

      *We can make use of Jekyll’s if-statements to hide & show content inside patterns.*
    multi_code:
      - code_before: |
          ### i. Modify your buttons

          Step one is to modify your buttons so they can support text & URLs. *Here’s an example:*
        code_lang: html
        code_file: "_patterns/buttons/light.html"
        code: |
          <a class="btn btn-light" href="{{include.url}}">{{include.text}}</a>
      - code_before: |
          Don’t forget to document the button fields within `config.yml`
        code_lang: yml
        code_file: "_patterns/buttons/config.yml"
        code: |
          patterns:
            light:
              fields:
                - name: text
                  type: string
                  example: "See collection"
                - name: url
                  type: url
                  example: "/crystals/"
      - code_before: |
          ### ii. Modify the banner

          Next up we’ll modify the banner a few different ways:

          1. We’ll add fields for the button’s URL & the button’s text
          2. Then we’ll pass the information from the banner into the button’s include
          3. Then we’ll add an if-statement to hide the button if the URL is missing

          *First we’ll update the banner’s documentation.*
        code_lang: yml
        code_file: "_patterns/banner/config.yml"
        code: |
          patterns:
            banner:
              fields:
                ⋮
                - name: button_text
                  type: string
                  example: "See collection"
                  required: false
                - name: button_url
                  type: url
                  example: "/crystals/"
                  required: false
        lines:
          - num: "1-3"
            fade: true
          - num: 8
            text: |
              We can specify that fields are not required—this really just just for documentation purposes and shows in the pattern library.
      - code_before: |
          Now update the banner’s HTML file.
        code_lang: html
        code_file: "_patterns/banner/banner.html"
        code: |
          <div class="banner embed embed-24by10 push-1-2">
            <div class="banner-content pin-lc gutter">
              <h1 class="banner-title yotta push-1-2">{{include.heading}}</h1>
              <p class="banner-info exa italic max-length-no-center">{{include.text}}</p>
              {% if include.button_url %}
                {% pattern buttons/light url=include.button_url text=include.button_text %}
              {% endif %}
            </div>
            <i class="banner-icon icon i-256 pin-rb"><svg><use xlink:href="/images/icons.svg#{{include.icon}}"></use></svg></i>
          </div>
        lines:
          - num: "1-4,8-10"
            fade: true
          - num: 5
            text: |
              The if-statement is part of Jekyll/Liquid (Jekyll’s templating language). If we were to convert that to English, it would say this:

              “When there is something inside the variable `include.button_url` proceed to the next line.”

              By having this if-statement, if we were to not specify the `button_url` in the banner’s include code, then the button just wouldn’t show on the page.
          - num: 6
            text: |
              Now we pass the fields we defined for our banner, to adjust the button, into the button include itself.

              Notice how we’re saying: `url=include.button_url`:

              - `url` is the name of the field our buttons support
              - `include.button_url` is the placeholder from our banner itself
          - num: 7
            text: |
              Don’t forget to close the if-statement or Jekyll won’t render your page.
      - code_before: |
          ### iii. Modify the page

          Now if we edit the code within each page we can change the button’s text or hide it.
        code_lang: html
        code_file: "index.html"
        code: |
          ---
          layout: default
          ---

          {% pattern banner/banner button_text="See collection" button_url="/crystals/" heading="Brilliant, stunning, bright" text="Geological marvels: gems, crystals, diamonds, geodes and much more!" icon="ruby" %}
        lines:
          - num: 5
            text: |
              See how I’ve added the `button_text` & `button_url` fields to the banner include.
    after: |
      ![](home-button.jpg)

      **I’ve only done this on the homepage—and so my homepage has a button.**

      ![](crystals-no-button.jpg)

      *But the product page doesn’t have a button because those fields weren’t set in the include code.*

  - title: "Highlight the navigation"
    before: |
      The final thing I want to show you is passing information from the page itself into an include without changing the include code snippet.

      In Jekyll each HTML file is a “page” which means that we always have access to a `page` variable.

      We can store information at the top of each page, like we’re doing with the `layout` and retrieve it later to do something with.

      So, let’s open up our products page, and add a new page variable to the top, like this:
    multi_code:
      - code_lang: yaml
        code_file: "products.html"
        code: |
          ---
          layout: default
          highlight_nav: crystals
          ---

          {% pattern banner/banner heading="Crystals" text="See all the sparkly, wonderful crystals from the depths of the Earth." icon="crystal" %}
        lines:
          - num: "1-2,4-6"
            fade: true
          - num: 3
            text: |
              I made up a new variable here called `highlight_nav`, then I set it to the word `crystals`—all this stuff is made-up, those things don’t exist as part of Jekyll.
      - code_before: |
          Now if I pop into my header pattern I can use more Jekyll if-statements to highlight the correct navigation item.
        code_lang: liquid
        code_file: "_patterns/header/header.html"
        code: |
          ⋮
            <nav class="nav pad-t-1-2 pad-b-1-2 giga" role="navigation" id="nav">
              <ul class="list-group-inline push-0">
                <li class="gutter-1-2 {% if page.highlight_nav == 'crystals' %}current{% endif %}"><a href="/crystals/">Crystals</a></li>
                <li class="gutter-1-2 {% if page.highlight_nav == 'diamonds' %}current{% endif %}"><a href="#">Diamonds</a></li>
                <li class="gutter-1-2 {% if page.highlight_nav == 'gems' %}current{% endif %}"><a href="#">Gems</a></li>
              </ul>
            </nav>
          ⋮
        lines:
          - num: "2,3,7,8"
            fade: true
          - num: "4-6"
            text: |
              It’s difficult to clearly see, but there are if-statements within each `class=""` attribute.

              The if-statement is checking to see what the value of the `highlight_nav` variable is and when it matches one of the strings, the if-statement will execute and Jekyll will output a new class: `.current`
    after: |
      Now if I refresh in the browser I see this:

      ![](nav-home.jpg)

      *My homepage doesn’t have any navigation highlighted.*

      ![](nav-crystals.jpg)

      *But the crystals page is highlighted!*

---
