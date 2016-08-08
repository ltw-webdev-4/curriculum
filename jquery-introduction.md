---
layout: slide-deck

title: "jQuery introduction"

slides:
  - type: super-big-text
    content: |
      **jQuery introduction**

  - content: |
      ## jQuery is Javascript

      - Simplifies the interface to HTML
      - Provides a bunch of already made functionality
      - *Not required to do HTML manipulation*

  - content: |
      ## Use from a CDN

      Include jQuery from a content delivery network
      —like we do with Google Fonts

      [**cdnjs ➔**](https://cdnjs.com/)

  - content: |
      ## It’s all money from here

      Everything that is jQuery is inside the `$()` function

      Use the `$()` function to select HTML then manipulate it

  - content: |
      ## Based around CSS selectors

      jQuery (and Javascript) use CSS selectors to grab things in HTML

      - `ul`, `h1`, `div`
      - `.dino-list`, `.bones`
      - `#stego`
      - `main > p:first-child`
      - etc.

  - type: code
    html: |
      <h1>Dinosaurs!</h1>
      <ul>
        <li>Stegosaurus</li>
        <li>Triceratops</li>
        <li>Ankylosaurus</li>
      </ul>
    js: |
      $('h1')
      $('ul')
      $('ul li:last-child')

  - type: code
    js: |
      var $h1 = $('h1');                          // Store a reference to the HTML element
      $h1.html('Dinosaurs rock!');                // Change the HTML inside the <h1>

      $('ul li:last-child').remove()              // Delete and HTML element
      $('ul').append('<li>Apatosaurus</li>');     // Add HTML to the end of the element

      var $newLi = $('<li>');                     // Make a new HTML tag, notice the `<>`
      $newLi.html('Diplodocus');
      $('ul').prepend($newLi);                    // Add HTML to the start of an element

      $h1.addClass('mega');                       // Add a class to the HTML element
      $newLi.hasClass('dino');                    // Checks if a class exists

      $('ul li').each(function () {               // Loop over a bunch of HTML elements
        $(this).addClass('kilo');                 // $(this) is the current HTML element
      });

  - content: |
      ## Videos & tutorials

      [Document object model ➔](/topics/dom/)
      [Javascript cheat sheet ➔](/topics/javascript-cheat-sheet/)

---
