---
layout: lesson
title: "Pattern library integration"
desc: "Integrate the new changes your teammate completed on your pattern library into your version."

hide_markbot: true

extra_tutorials:
  - title: "Branching & GitHub Flow"
    url: branching-github-flow
  - title: "Using GitHub for project management"

goal:
  no_image: true
  before: |
    We’re going to send the changes you completed on your teammate’s pattern library to them using a pull request.

    You will then review your teammate’s code and eventually integrate it into the original pattern library.

    **I suggest doing this together, on one pattern library at a time.** After you complete one person’s move to the next person’s.
  person_legend:
    - icon: "person-1"
      label: "Dev"
      desc: "The person who developed/wrote the code/created the new product details page."
    - icon: "person-2"
      label: "Owner"
      desc: "The person who owns this pattern library, the person who created all the patterns."

steps:
  - title: "Do any final commits"
    person:
      icon: "person-1"
      label: "Dev"
    before: |
      Do any final commits that are outstanding. **This is not the time to write more code—it should already be done.** But if there are changes that you forgot to commit do them now.

  - title: "Publish the branch"
    person:
      icon: "person-1"
      label: "Dev"
    before: |
      To be able to integrate the two chunks of code we need to put the new chunk up on GitHub.

      Go into the GitHub Desktop application.

      ![](publish.jpg)

      Press the “Publish branch” button if you haven’t already. If you have done it when working previously make sure to push.

  - title: "Create a pull request"
    person:
      icon: "person-1"
      label: "Dev"
    before: |
      Your code cannot be integrated directly, it requires approval from your teammate. We go through this approval process with a pull request.

      ![](pr-create.jpg)

      In the menu, go to `Branch > Create Pull Request`. This will send you to GitHub’s website.

      ## Set the base fork

      *This may not be necessary.* (Because the eCommerce website is originally forked from the Learn the Web repository you can create pull request against that even earlier version.)

      ![](base-fork.jpg)

      Make sure the “base” is set to your teammate’s repository not the original Learn the Web repo (`acgd-webdev-4`).

      **If if just says “base: gh-pages” (and there’s no “base fork” option) then move along.**

      ## Describe, assign & go

      To get your code into the default branch you need to get it approved.

      ![](pr-assign.jpg)

      Write an appropriate description in the box and assign your teammate as the reviewer.

      ![](pr-button.jpg)

      Make sure to press “Create pull request”

  - title: "Review the code"
    person:
      icon: "person-2"
      label: "Owner"
    before: |
      *Now it’s the repository owner’s turn to review the code.* After reviewing the code we can move on to integrating it back into the original codebase.

      ![](pr.jpg)

      Go to the “Pull requests” tab and press on the link to the newly created pull request.

      ![](add-review.jpg)

      You should see a yellow banner with an “Add your review” button in it—press the button.

      ![](review.jpg)

      On the review screen you can see all the code they wrote and confirm it looks okay. If you want to see what it looks like, it’s most easiest to look at it on their screen. *If you want to look at the final product on your own computer call the teacher over for assistance.*

      **Approve or reject the code.** Make sure to write your reasons in the text box; be polite and helpful.

      ### Rejection is expected

      I expect the code to be rejected on the first pass. Nothing is perfect the first time.

      #### Create more commits

      If your code (the Dev’s code) gets rejected you need to make adjustments—on your own computer. Commit them to your `product-details` branch and push them to GitHub.

      The new commits will show up automatically on the pull request page and the repo owner can do another code review.

      *Once the code is approved move onto the next step…*

  - title: "Merge the pull request"
    person:
      icon: "person-2"
      label: "Owner"
    before: |
      Merging is the process of moving the code changes from one branch into another.

      ![](merge.jpg)

      Press the big green “Merge pull request” button.

      ![](merge-confirm.jpg)

      Then the “Confirm merge” button.

      ![](delete-branch.jpg)

      And finally the “Delete branch” button.

  - title: "Delete your teammate’s repo"
    person:
      icon: "person-1"
      label: "Dev"
    before: |
      You can now safely delete your teammate’s repository folder from your computer and remove it from the GitHub Desktop application.

  - title: "Pull the code into your repo"
    person:
      icon: "person-2"
      label: "Owner"
    before: |
      Now that the pull request has been approved & merged that code actually exists inside your `gh-pages`.

      Go to your own eCommerce repository in your GitHub Desktop application. Make sure you are on the `gh-pages` branch. Then pull the code.

      ![](pull.jpg)

      Press “Fetch origin” then “Pull” or just go to the menu: `Repository > Pull`

      *Now check out your pattern library code—or use Patternbot—and you should see the page your teammate created.*

      **And do it all over again for your teammate’s pattern library.**
---
