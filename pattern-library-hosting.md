---
layout: lesson
title: "Pattern library hosting"
desc: "Set up hosting for our pattern library on Netlify because GitHub only supports a few Jekyll plugins."

hide_markbot: true

extra_tutorials:
  - title: "Pattern libraries"
    url: pattern-libraries
  - title: "Pattern libraries slide deck"
    url: "/courses/web-dev-4/pattern-libraries/"

goal:
  no_image: true
  before: |
    We’re going to set up hosting for our eCommerce pattern library on a new service: [Netlify](https://www.netlify.com/).

    **GitHub supports hosting Jekyll websites but only with a limited number of plugins.** Since we’re using the Patternbot plugin, which isn’t approved by GitHub, we need to host our website’s elsewhere.

steps:
  - title: "Make a Netlify account"
    before: |
      Netlify has a free plan that we can use for hosting static websites like Jekyll-based websites. So the first step is to sign-up for Netlify—it actually used GitHub as your login credentials.

      ### [Head over to Netlify »](https://app.netlify.com/signup)

      ![](sign-up.jpg)

      *Choose the GitHub option.*

      ![](authorize.jpg)

      *Authorize Netlify access to your GitHub credentials.*

      Now we’re ready to connect our new website.

  - title: "Make a new site"
    before: |
      We can host any repository we have setup on GitHub, similar to how GitHub Pages works—which is what we’ve been doing with all our previous websites. But Netlify gives us much more control over everything.

      ![](new-site.jpg)

      *Press the “New site from Git” button.*

      ![](github.jpg)

      *Choose a site from GitHub.*

      ![](auth-site.jpg)

      *Authorize Netlify again.*

      ![](choose-username.jpg)

      *Choose your username if it asks, “where you want to install Netlify”.*

      ![](repo.jpg)

      *Pick “Only select repositories”. Then, in the dropdown, choose your eCommerce repo.*

      **Press the big green button to move on.**

  - title: "Define build settings"
    before: |
      Now that we’ve given all our authorizations on GitHub we’re moved back to Netlify, where we can configure how our website will be created and built.

      ![](repo-add.jpg)

      *Press on the repo link to move to the build settings.*

      ![](build.jpg)

      *These should already be set, but double check:*

      - “Build command” set to `jekyll build`
      - “Publish directory” set to `_site`

      **Then press “Deploy site”.**

  - title: "Wait for deployment"
    before: |
      Just like on GitHub, building our website takes a little bit of time. Netlify shows us in the dashboard when the site is being built so we can know when it’s done and we can check the live URL.

      ![](deploying.jpg)

      *Just wait out the deployment…*

      ![](deployed.jpg)

      **Now we’re live!** Click that link to view your page.

      ![](404.jpg)

      **You’ll receive a 404 page initially because we don’t have an `index.html` file.** We got a file listing on our local computer when we went to `localhost`—but file listings are suppressed on live web servers for security.

      ![](pattern-library.jpg)

      So, type `/pattern-library` into the URL to see yours!

  - title: "Submit Netlify URL into GitHub"
    before: |
      Because the hosting URL isn’t just your GitHub account any more, I need to know URL. Let’s submit the URL back to GitHub so I can find the pattern library for grading.

      ![](edit-repo.jpg)

      *Press the “Edit” button on your repo’s page.*

      ![](paste-url.jpg)

      *Paste in your Netlify URL.*

      ![](save-details.jpg)

      *Save the edits and our URL should now be clickable at the top of our repo’s page.*

---
