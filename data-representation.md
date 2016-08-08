---
layout: slide-deck

title: "Data representation"

slides:
  - type: super-big-text
    content: |
      **Data representation**

  - content: |
      ## Set up

      1. Form into pairs
      2. Get a piece of paper & pencil, or open a code file
      3. We’ll step through each together—don’t look ahead
      4. Write out the data structure you think is appropriate

  - type: normal-text
    raw: |
      <table>
        <tr><th scope="col">Answers</th></tr>
        <tr><td>A</td></tr>
        <tr><td>C</td></tr>
        <tr><td>B</td></tr>
        <tr><td>A</td></tr>
        <tr><td>C</td></tr>
        <tr><td>D</td></tr>
        <tr><td>B</td></tr>
        <tr><td>C</td></tr>
        <tr><td>A</td></tr>
        <tr><td>D</td></tr>
      </table>

  - type: code
    js: |
      // An array

      var answers = ['A', 'C', 'B', 'A', 'C', 'D', 'B', 'C', 'A', 'D'];

  - raw: |
      <dl>
        <dt><b>Name</b></dt>
        <dd>Elasmosaurus</dd>
        <dt><b>Period</b></dt>
        <dd>Late Cretaceous</dd>
        <dt><b>Length</b></dt>
        <dd>14 m</dd>
      </dl>

  - type: code
    js: |
      // An object

      var dino = {
        name: 'Elasmosaurus',
        period: 'Late Cretaceous',
        length: 14
      }

  - type: normal-text
    raw: |
      <table>
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Period</th>
            <th scope="col">Length</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Elasmosaurus</td>
            <td>Late Cretaceous</td>
            <td>14 m</td>
          </tr>
          <tr>
            <td>Stegosaurus</td>
            <td>Late Jurassic</td>
            <td>9 m</td>
          </tr>
          <tr>
            <td>Tyrannosaurus</td>
            <td>Cretaceous</td>
            <td>12.3 m</td>
          </tr>
        </tbody>
      </table>

  - type: code
    js: |
      // Objects inside an array

      var dinos = [{
          name: 'Elasmosaurus',
          period: 'Late Cretaceous',
          length: 14
        }, {
          name: 'Stegosaurus',
          period: 'Late Jurassic',
          length: 9
        }, {
          name: 'Tyrannosaurus',
          period: 'Cretaceous',
          length: 12.3
      }];

---
