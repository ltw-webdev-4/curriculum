---
layout: lesson
title: "Jekyll generators"
desc: "Dig into Jekyll to learn how to generate a bunch of similar patterns onto a page from a collection."

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
    Now that we’ve written all the details for the products in our ecommerce pattern library, in the previous lesson, we’re going to look at how to generate the product list page using the Jekyll and our patterns.
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
  - title: "Set up the product card"
    before: |
      Before we start, let’s add all the include placeholders within our product card: the card that we’ll use on the product listing page.

      Open up your product card and add placeholders similar to what I’ve done below.

      **Remember: your code will be very different, this is just an example of what you should apply to your own pattern.**
    multi_code:
      - code_lang: html
        code_file: "_patterns/cards/product-card.html"
        code: |
          <div class="card text-center chop">
            <img class="img-flex" src="{{include.data.image}}" alt="">
            <div class="island-1-2">
              <strong class="push-1-4 peta color-primary">${{include.data.price}}</strong>
              <h2 class="push-1-4">{{include.data.title}}</h2>
              <p class="push-1-2">{{include.data.description}}</p>
              {% pattern buttons/primary text="Buy now" %}
            </div>
          </div>
        lines:
          - num: 2
            text: |
              Here I’ve replaced the image’s `src` attribute with an include placeholder. Notice that it’s `include.data`—this will become more clear later on.
      - code_before: |
          Make sure that the names of the include placeholder variables match the Markdown files.

          For example, in your `.md` file if you have field names like below:
        code_lang: yml
        code_file: "_products/super-product.md"
        code: |
          ---
          title: "Super product"
          desc: "Big, long description."
          cost: 56
          ---
      - code_before: |
          The field names must match inside the include placeholders:
        code_lang: "liquid"
        code_file: "_patterns/cards/product-card.html"
        code: |
          {{include.data.title}}
          {{include.data.desc}}
          {{include.data.cost}}

  - title: "Document the fields"
    before: |
      Before we move on, let’s not forget to document the include fields.

      This one is a little different for documentation purposes because we technically only have one field: `data`. All of the information after `data` is not a field we can manipulate directly, those fields come from our Markdown files.

      **So, the only field we have to document is the `data` field:**
    code_lang: yml
    code_file: "_patterns/cards/config.yml"
    code: |
      ⋮
      patterns:
        product-card:
          width: 400
          description: |
            The product card is used on the product listing page to display each available product.
          fields:
            - name: data
              type: object
              data:
                source: "site.products[0]"
                type: Product
    lines:
      - num: "2-6"
        fade: true
      - num: 8
        text: |
          We are stating that we have one editable field, named `data`
      - num: 9
        text: |
          It’s information data type is an object: meaning it holds many things inside.
      - num: "10-11"
        text: |
          The example of where the data can be found is in our `site.products` collection. We’re grabbing just the first product to display in the pattern library.
      - num: 12
        text: |
          The `type` field is a little freeform: describe what kind of object should be passed to the field: in this case it’s a “Product” meaning from the `_products` collection.

  - title: "Create a for loop"
    before: |
      Now that our product card is ready to accept information into it, we can generate the product listing page from our collection of products.

      Open up your products page, and add the following code:
    code_lang: liquid
    code_file: "products.html"
    code: |
      ⋮
      {% for product in site.products %}
        {% pattern cards/product-card data=product %}
      {% endfor %}
    lines:
      - num: 2
        text: |
          As Jekyll loops through all the products it finds in our product’s collection folder, each single product it finds gets inserted into a container called `product` (that name’s completely made up, `dust-bunny-fluff` and it would work the same).
      - num: 3
        text: |
          Notice here, how we’ve only sent a single field into the pattern include. We called is specifically `data`; it maps to our placeholders that start with `include.data`. We could have inserted many fields like we’ve looked a previously, but it seems like extra, unnecessary code.

          We are sending whatever information is stored in `product` into our include, and inside the include we want to refer to that information as `data`.
    after: |
      **Refresh your browser!** You should see every single one of the products listed out on the page. Though kinda messy-like.

  - title: "Add a grid to lay out the page"
    before: |
      Our products page is a little messy now, we kinda need a grid. **So let’s add a grid!**
    code_lang: html
    code_file: "products.html"
    code: |
      ⋮
      <div class="grid gutter-1-4">
        {% for crystal in site.crystals %}
          <div class="unit [ xs-1 s-1 m-1-3 ] island-1-4">
            {% pattern cards/product-card data=crystal %}
          </div>
        {% endfor %}
      </div>
    lines:
      - num: "4-6"
        text: |
          Notice how the `.unit` `<div>` is within the for loop? That’s so we’ll get a brand new unit for each single product on the website.
    after: |
      **Check it out!** Your product listing page should be almost done! (That was easy!)

  - title: "Make each card clickable"
    before: |
      I think the only thing we’re missing is the ability to click on each of the products to see their full details.

      Let’s pop back to the pattern to make a small adjustment:
    code_lang: html
    code_file: "_patterns/cards/product-card.html"
    code: |
      <div class="card text-center chop">
        <img class="img-flex" src="{{include.data.image}}" alt="">
        <div class="island-1-2">
          <strong class="push-1-4 peta color-primary">${{include.data.price}}</strong>
          <h2 class="push-1-4">{{include.data.title}}</h2>
          <p class="push-1-2">{{include.data.description}}</p>
          {% pattern buttons/primary text="Buy now" url=include.data.url %}
        </div>
      </div>
    lines:
      - num: "1-6,8-9"
        fade: true
      - num: 7
        text: |
          The only change is that we’re passing the `url` into our button pattern now. Notice we’re passing: `include.data.url`, but we never specified a URL at the top of our collection’s `.md` files.

          This is where Jekyll is magic: each of those files in the collection have a URL, as we explored in a previous lesson—and Jekyll knows what that is.
    after: |
      Refresh your product list page and you should be able to click on every single product on your website.

      *It’s showing you the product details inside the `_layouts/product.html` we created previously.*

      **With just a little bit of code we generated the whole product list page & all the product pages too!**

---
