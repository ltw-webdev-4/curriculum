---
layout: slide-deck

title: "Form error messages"

slides:
  - type: super-big-text
    content: |
      **Form error messages**

  - content: |
      ## Designing forms is hard, <br>Designing validation states is harder

  - content: |
      ## Error messages are friends

      We’ve all run into error messages when filling out forms.

      They need to be designed & designed well.

      Because: we’ve all run into poor error messages.

  - content: |
      ## Form usability

      Here are some major concerns when designing form error messages:

      - Obviousness & clarity
      - Colours (color blindness)
      - Accessibility (screen readers)

  - type: figure
    image: errors.png
    caption: |
      **Why are these error messages pretty good?**

  - content: |
      ## CSS selectors

      ```css
      input:invalid {
        border-color: red;
      }

      input:valid {
        border-color: green;
      }
      ```

  - content: |
      ## Adjacent selector

      ```css
      input:invalid + .error-message {
        display: block;
      }
      ```

  - content: |
      ## Needs Javascript

      Form validation really needs Javascript to be super awesome

      We’re going to include a little big of Javascript to help simplify and & design some items

  - content: |
      ## Videos & tutorials

      - [Forms](/topics/forms/)
      - [Forms cheat sheet](/topics/forms-cheat-sheet/)

---
