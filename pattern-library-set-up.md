---
layout: lesson
title: "Pattern library set up"
desc: "Create the first few basic files for your ecommerce pattern library and use Patternbot to generate the component website."

hide_markbot: true

extra_tutorials:
  - title: "Pattern libraries"
    url: pattern-libraries
  - title: "Pattern libraries slide deck"
    url: "/courses/web-dev-4/pattern-libraries/"

goal:
  no_image: true
  before: |
    We’re going to start the pattern library that you’ll be working for the rest of the term in this lesson.

    We’ll get the first bits set up and ready to use so you can move onto styling the typography.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

fork:
  url: "https://github.com/acgd-webdev-4/ecommerce-pattern-library"
  repo: "ecommerce-pattern-library"

steps:
  - title: "Set the Ruby version"
    before: |
      After we’ve forked our repository we’re going to immediately add a new file into the folder.

      We’re going to set which version of the Ruby programming language we’d like to use; it’s very critical for when we start hosting our website, but not too important on our local computers.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
        notes: "This is the folder you forked"
      - label: ".ruby-version"
        indent: 1
        notes: "This won’t show in Finder, only your code editor"
    code_file: ".ruby-version"
    code: |
      2.5.3
    lines:
      - num: 1
        text: |
          Version 2.5.3 is a fairly recent version of Ruby that you can use—but you can always [go to Ruby’s website to find a newer version](https://www.ruby-lang.org/en/).
    after: |
      *You’re literally just typing those numbers into this code file—absolutely nothing else.*

      **Because we started the filename with a `.` we won’t be able to see it in Finder; the starting `.` instructs Finder that it’s a hidden file.**

  - title: "Initialize Ruby & Bundler"
    before: |
      We’re almost ready to install & setup Jekyll & Patternbot—but first we need to initialize Ruby & Bundler. We need to—again—use your computer’s Terminal application. *In fact we’re going to be using Terminal quite regularly now.*

      Inside GitHub Desktop, go to the `Repository` menu and press `Open in Terminal`—this will open the Terminal app and point it to the correct folder.

      ![](open-in-terminal.jpg)

      Once inside Terminal type exactly: `bundle init`—then hit `Return`

      ![](bundle-init.jpg)

      *Your Terminal will look different—mine is highly customized.* **You won’t even be able to get down to the next line like the screenshot shows.**

  - title: "Modify the Gemfile"
    before: |
      If you pop back to your code editor now you’ll see that Bundler has created a new file: `Gemfile` (*Capital letters—gasp!*)

      Inside the `Gemfile` we’re going to make some adjustments to the code to install Jekyll & Patternbot.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: ".ruby-version"
        indent: 1
        fade: true
      - label: "Gemfile"
        indent: 1
    code_before: |
      Some of the code is already written for use—that’s why we used the `bundle init` command: so we don’t have to type it all ourselves.
    code_lang: "ruby"
    code_file: "Gemfile"
    code: |
      # frozen_string_literal: true

      source "https://rubygems.org"

      git_source(:github) {|repo_name| "https://github.com/#{repo_name}" }

      gem "jekyll"

      group :jekyll_plugins do
        gem "jekyll_patternbot"
      end
    lines:
      - num: "1-5"
        fade: true
      - num: 7
        text: |
          Remove the `#` from the start of the line to un-comment the code. Then change it so it says `jekyll` instead of `rails`
      - num: "9-11"
        text: |
          Add these 3 new lines of code: they instruct Bundler to install the following Jekyll plugins along with Jekyll—specifically we want to install the Jekyll Patternbot plugin.
    after: |
      Save that and we’re ready to install everything!

  - title: "Install Jekyll & Patternbot"
    before: |
      Pop back over to your Terminal and type the following command: `bundle install`—this will go off and download Jekyll & Jekyll Patternbot (and all their dependencies) and install them on your computer.

      ![](bundle-install.jpg)

      **It’ll take quite a while.** Wait until it’s done before moving to the next step.

  - title: "Configure Jekyll & Patternbot"
    before: |
      The final step, before getting on to actually make our pattern library is to configure Jekyll so that it uses Patternbot. We do that by adding a `_config.yml` file to our folder. (*Underscores—ugh!*)
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: ".ruby-version"
        indent: 1
        fade: true
      - label: "Gemfile"
        indent: 1
        fade: true
      - label: "_config.yml"
        indent: 1
    code_lang: "yml"
    code_file: "_config.yml"
    code: |
      permalink: pretty
      theme: jekyll_patternbot
    lines:
      - num: 1
        text: |
          This tells Jekyll to strip the `.html` from our files when it generates our website to make the URLs nice ’n’ clean & search engine friendly.
      - num: 2
        text: |
          This tells Jekyll that we’re using Patternbot in this website and that it should include all Patternbot’s includes, layouts, assets, etc. within our own site.
    after: |
      Now we’re ready to go—let’s run all the things!

  - title: "Run Jekyll"
    before: |
      We’re ready! Let’s get Jekyll running in our Terminal so we can see our pattern library as we develop it.

      Pop back to Terminal and type this command: `bundle exec jekyll serve`—then hit `Return`.

      This is the *all important* command that you need to remember—though Terminal will remember it for you, next time you come into Terminal to turn your site on just press the `Up Arrow` and it will scroll through the command history.

      ![](jekyll-serve.jpg)

      Running this command will start Jekyll. **You must keep the Terminal window active for your website to function.** You can minimize the window if you’d like. If you close the Terminal window Jekyll will stop running and your website will be inaccessible.

      I’ve highlighted in the Terminal window an important bit: that’s the URL where you must view your website. So, let’s pop it open:

      ### [http://localhost:4000](http://localhost:4000)

      *The IP address `127.0.0.1` and `localhost` are interchangeable—I just find `localhost` much easier to type.*

      ![](localhost.jpg)

      When you pop it open in your browser you’ll see a pretty blank screen. **It’s because we don’t have an `index.html` file.**

      But we’re most interested in the `pattern-library` folder—so click that to access our pattern library.

      ![](pattern-library.jpg)

      **That’s it—our pattern library!** Though, it is quite empty.

  - title: "Get the Web Dev Tools CSS files"
    before: |
      The first step to actually setting up our pattern library is to get copies of all the [Web Dev Tools](http://web-dev.tools/).
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: ".ruby-version"
        indent: 1
        fade: true
      - label: "Gemfile"
        indent: 1
        fade: true
      - label: "_config.yml"
        indent: 1
        fade: true
      - label: "css"
        type: folder
        indent: 1
      - label: "modules.css"
        indent: 2
      - label: "grid.css"
        indent: 2
      - label: "type.css"
        indent: 2
    after: |
      1. Make a `modules.css` in a `css` folder—[get a new version from Modulifier](https://modulifier.web-dev.tools/).
        <br>*Include only the modules you’ll need for your website. (You can always add more later.)*
      2. Make a `grid.css` in a `css` folder—[get a new version from Gridifier](https://gridifier.web-dev.tools/).
        <br>*Set up the columns and breakpoints you’ll need based on your wireframes.*
      3. Make a `type.css` in a `css` folder—[get a new version from Typografier](https://typografier.web-dev.tools/).
        <br>*Set up the font-sizes and type scales based on your visual design choices.*
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."

  - title: "Make the shared CSS file"
    before: |
      Next up we’ll create a shared CSS file, named `theme.css`. In here we’ll be putting a bunch of CSS variables and styling foro the general typographic tags for your website.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: ".ruby-version"
        indent: 1
        fade: true
      - label: "Gemfile"
        indent: 1
        fade: true
      - label: "_config.yml"
        indent: 1
        fade: true
      - label: "css"
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
      At the top of your `theme.css` file, add a few variables that **match the visual design of your eCommerce website.**
    code_lang: css
    code_file: "css/theme.css"
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

      *The **primary font is your body copy**—I consider “primary” to mean the font that’s used the most.*

      ![](theme.jpg)

      **Check it out by refreshing in your browser!**

  - title: "Add the mega CSS file"
    before: |
      The final CSS file we’re going to create is going to mash all the other CSS files together into one large file. *The technical term for this is concatenation.*

      *CSS concatenation is great for website performance because we only download a single CSS file for the website instead of 4 or 5 different files.*

      Name this new CSS file `main.css`—which is a pretty standard name we’re used to using at this point.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: ".ruby-version"
        indent: 1
        fade: true
      - label: "Gemfile"
        indent: 1
        fade: true
      - label: "_config.yml"
        indent: 1
        fade: true
      - label: "css"
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
        fade: true
      - label: "main.css"
        indent: 2
    code_before: |
      **Inside your `main.css` file we’re going to add a little bit of Jekyll code.** This code instructs Jekyll to load all the other CSS files into this file—therefore combining them together into a single file.
    code_lang: css
    code_file: "css/main.css"
    code: |
      ---
      ---

      {% include_relative modules.css %}
      {% include_relative grid.css %}
      {% include_relative type.css %}
      {% include_relative theme.css %}
      {% pattern_css %}
    lines:
      - num: "1-2"
        text: |
          The two lines of 3 hyphens instruct Jekyll that this file should be parsed. If you don’t have these triple dashes in a file Jekyll will simply *copy* the file not *compile* it.
      - num: "4-7"
        text: |
          Tell Jekyll to go find these other 4 files, in this same folder and include all of their contents into this location. Essentially it copies everything from the other CSS files into `main.css` automatically for us.
      - num: 8
        text: |
          This is a Patternbot thing, it tells Jekyll & Patternbot to find all the CSS files we’ve created for our pattern and load them into here also.
    after: |
      You won’t see any changes in the browser right now.

  - title: "Add your logo SVGs"
    before: |
      Patternbot will detect your logo images and display them on the screen, so let’s add those into your pattern library folder.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: ".ruby-version"
        indent: 1
        fade: true
      - label: "Gemfile"
        indent: 1
        fade: true
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
      - label: "logo.svg"
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

  - title: "Put details into the config file"
    before: |
      We’ll spend more time on this file next week when we learn about customization. But for this week we’re going to put one line of code in it, just so our typography works properly.

      Now open up the `config.yml` and type the following code. Be sure to substitute this Google Font URL with your own. *Typekit works too (ask the teacher for help).*
    code_lang: yml
    code_file: "_config.yml"
    code: |
      permalink: pretty
      theme: jekyll_patternbot

      patternbot:
        font_url: "https://fonts.googleapis.com/css?family=Alegreya+Sans:400,400i,700|Source+Code+Pro:400,700"
    lines:
      - num: 4
        text: |
          All of Patternbot’s configuration & documentation will be found under the `patternboty` entry.
      - num: 5
        text: |
          Patternbot will use the `font_url` to make sure all the type in the built-in patterns is rendered in the correct font family. It will also use the weights and styles provided by the font service to display in the pattern library.
    after: |
      **YAML is very strict about indentation!** If you mess up the indentation within this file, things won’t work.

      *This URL is the stuff inside the `href="…"` attribute of the `<link>` tag that Google/Typekit gives you.*

      ![](font-url.jpg)

      **Go refresh your browser and you should see the whole pattern library is now rendered in your font choices.**

      *If your fonts don’t show up you can try stopping & starting Jekyll.* In Terminal press `Control C`, then press `Up`, and `Return`—this will restart Jekyll and hopefully it will work.
---
