---
layout: slide-deck

title: "Javascript events"

slides:
  - type: super-big-text
    content: |
      **Javascript events**

  - content: |
      ## Event listening

      1. When a user interacts with your website an event is triggered
      2. Your JS can listen to when that event happens
      3. A function you write can be called when an event happens

  - content: |
      ## Events

      - `click`, `dblclick`, `contextmenu`
      - `mousedown`, `mouseup`, `mouseover`, `mouseout`, `mousemove`
      - `keypress`, `keydown`, `keyup`
      - `focus`, `blur`, `change`, `submit`
      - animation, transition, touch, drag, browser
      - [and many, many more…](https://developer.mozilla.org/en-US/docs/Web/Events)

  - content: |
      ## Responding to events

      jQuery’s `on()` function can be used to listen and respond

      There’s also `off()` if you want to stop listening

  - type: interactive
    html: |
      <button id="click-me">Click me!</button>
    js: |
      $('#click-me').on('click', function () {
        alert('Hello, World!');
      });
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0-beta1/jquery.min.js"></script>

  - type: interactive
    html: |
      <ul>
        <li>Titanosaurus</li>
        <li>Apatosaurus</li>
        <li>Brontosaurus</li>
        <li>Brachiosaurus</li>
      </ul>
    css: |
      .is-clicked {
        background-color: limegreen;
      }
    js_lines: "1,2"
    js: |
      $('ul').on('click', 'li', function (e) {
        $(this).toggleClass('is-clicked');
      });
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0-beta1/jquery.min.js"></script>

  - type: interactive
    html: |
      <a class="stego-link" href="https://en.wikipedia.org/wiki/Stegosaurus">Go!</a>
    js_lines: "3,4"
    js: |
      var $link = $('.stego-link');

      $link.on('click', function (e) {
        e.preventDefault();
        alert($(this).attr('href'));
      });
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0-beta1/jquery.min.js"></script>

  - type: interactive
    html: |
      <form>
        <label for="grocery-input">Shopping list</label>
        <input id="grocery-input">
        <button type="submit">Add</button>
      </form>
      <ul class="list"></ul>
    js_lines: "4,7"
    js: |
      var $input = $('#grocery-input');
      var $list = $(".list");

      $('form').on('submit', function (e) {
        var $li = $('<li>');
        e.preventDefault();
        $li.html($input.val());
        $list.append($li);
      });
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0-beta1/jquery.min.js"></script>

  - content: |
      ## Videos & tutorials

      [Document object model ➔](/topics/dom/)
      [Javascript cheat sheet ➔](/topics/javascript-cheat-sheet/)

---
