---
layout: lesson
title: "Preparing product data"
desc: "Look at how to use Jekyll’s collections to create a bunch of projects, then have each of those files automatically generate pages."

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
    We’re going to explore Jekyll’s collection system. Collections allow us to write out content, and not have to write code. Each of the content files will be inserted into a layout where the layout will be in charge of rendering the content in the HTML.
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
  - title: "Set up product collection"
    before: |
      **Continue on with your `ecommerce-pattern-library` repository.**

      We’re going to make some adjustments to our `_config.yml` file where we can add a collection.

      **Add this to the bottom of your `_config.yml` file—after everything else in the file.**
    code_lang: yaml
    code_file: "_config.yml"
    code: |
      ⋮
      collections:
        products:
          output: true
    lines:
      - num: 2
        text: |
          Tell Jekyll we want to add collections to our website.
      - num: 3
        text: |
          The name of the collection—will also be the name of our folder.
      - num: 4
        text: |
          We want each product in the collection to have it’s own page, we’ll tell Jekyll to output the files as HTML files.
    after: |
      **Start & stop Jekyll to make this change.** *Remember that the `_config.yml` file is the only file that Jekyll doesn’t automatically reload.*

  - title: "Create the first product"
    before: |
      Now that we’ve got our collection made we can start by creating our first product.

      But before we do that, we need to make a folder for our collection of products.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "_products"
        type: folder
        indent: 1
        notes: "Matches the name of our collection + underscore"
      - label: "24-carat-diamond.md"
        indent: 2
      - continue: true
    code_before: |
      Inside Atom, go ahead and make a new file. It’s representing one single product on your ecommerce website, so name it appropriately.

      **It should have the `.md` file extension, to denote that it’s only Markdown content.**
    code_lang: yml
    code_file: "/_products/24-carat-diamond.md"
    code: |
      ---
      name: "24 carat diamond"
      description: |
        A wonderfully cut, exquisite and sparkling non-conflict diamond—made out of crushed & aged dinosaurs.
      image: "/images/diamonds/24-carat.jpg"
      price: 576
      colors:
        - "Green"
        - "Olive"
      shape: "Round"
      clarity: "VVS1"
      ---
    after: |
      Similar to how we did with the [“Fried data”](/courses/web-dev-4/fried-data/) exercise, determine every attribute you’ll need to describe each product.

      **Add all the product attributes—for a single product—to this Markdown file.**

  - title: "Set up the product details layout"
    before: |
      At this point, if we were to view the product in the browser it would be a blank page. The Markdown file only has metadata: stuff in the `---` which doesn’t render naturally.

      To make something render for our product, we need to create and define a layout.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "_layouts"
        type: folder
        indent: 1
      - label: "default.html"
        indent: 2
        fade: true
      - label: "product.html"
        indent: 2
      - label: "_products"
        type: folder
        indent: 1
        fade: true
      - label: "24-carat-diamond.md"
        indent: 2
        fade: true
      - continue: true
    code_before: |
      Make a brand new layout, called `product.html`.

      We are going to explore the idea of nested layouts. Layouts, that use other layouts.

      - We created a new layout specifically for products because we want those pages to all look the same—but different from other pages on the website.
      - But, we still want to share the header & footer from within default.
    code_lang: html
    code_file: "_layouts/product.html"
    code: |
      ---
      layout: default
      ---

      <h1>{{page.name}}</h1>
      <p>{{page.description}}</p>
      <img src="{{page.image}}" alt="">
    lines:
      - num: 2
        text: |
          Tell Jekyll that our `product` layout should still inherit the `default` layout, getting our header & footer.
      - num: 5
        text: |
          I’m putting just a simple `<h1>` on this page for now, it’s outputting the name from our Markdown file.
      - num: 6
        text: |
          We’ll do the same thing again to output the description for our product.
      - num: 7
        text: |
          The image isn’t too terribly different, just the placeholder variable is being inserted into the images’ `src` attribute.
    after: |
      **We’re not going to finalize the product details page yet—that will happen later in the term.**

      Still can’t quite see anything in the browser…

  - title: "Define layout for all products"
    before: |
      We need to tell the product itself which layout to use—we’ve seen how to do this previously on our home & products list pages. We can go into the Markdown file and add the layout there—*but that’s not an optimal solution.*

      We’re eventually going to have lots of products—and I don’t like repeating myself—so let’s set the layout in one place: `_config.yml`

      Pop open your `_config.yml` and add this hunk of code to the bottom:
    code_lang: yml
    code_file: "_config.yml"
    code: |
      ⋮
      collections:
        products:
          output: true

      defaults:
        - scope:
            path: _products
          values:
            layout: product
    lines:
      - num: "2-4"
        fade: true
      - num: 6
        text: |
          Configure Jekyll’s default front matter.
      - num: "7-8"
        text: |
          Define that we’re configuring every single file within the `_products` folder.
      - num: "9-10"
        text: |
          Define the front-matter we’re interested in changing: specifically setting `layout: product`
    after: |
      Stop & start Jekyll and go to your browser to view the page.

      ![](page-in-layout.jpg)

      **Since you haven’t linked the product anywhere yet, you’ll have to type the URL into the URL bar.**

      Everything should be merged together now. Here’s a little illustration to help you understand what Jekyll is doing to generate this page.

      ![](jekyll-layout-process.svg)

      1. Start to render the Markdown file
      2. Notices it requires the `product` layout
      3. Grabs the appropriate fields from the Markdown file & inserts them into placeholder variables
      3. Notices the `product` layout uses the `default` layout
      4. Grabs all the product information it just rendered & inserts it into the `default` layout between the header & footer

  - title: "Create second product"
    before: |
      Let’s continue adding to the products on our website by making another Markdown file.
    folders:
      - label: "ecommerce-pattern-library"
        type: folder
      - label: "_layouts"
        type: folder
        indent: 1
        fade: true
      - label: "default.html"
        indent: 2
        fade: true
      - label: "product.html"
        indent: 2
        fade: true
      - label: "_products"
        type: folder
        indent: 1
        fade: true
      - label: "24-carat-diamond.md"
        indent: 2
        fade: true
      - label: "fancy-bright-ruby.md"
        indent: 2
      - continue: true
    code_before: |
      Make a new Markdown file within your `_products` collection and fill in the details for second product on your website.
    code_lang: yml
    code_file: "_products/fancy-bright-ruby.md"
    code: |
      ---
      name: "Fancy bright ruby"
      description: |
        Fancy coloured, bright red ruby make solely from deceased carnivorous tyrannosauruses.
      image: "/images/ruby/fancy-bright.jpg"
      price: 257
      colors:
        - "Red"
      shape: "Diamond"
      clarity: "VVS1"
      ---
    after: |
      ![](second-product.jpg)

      **Navigate to this product in your browser and see that you’ve made a full second page on your website without writing any code!**

  - title: "Finish off all products…"
    before: |
      **Now it’s completely up to you: add many more Markdown files for your website.** Ideally 1 Markdown file for each product listed on your products page.
---
