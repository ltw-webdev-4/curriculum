---
layout: lesson
title: "Install more developer tools"
desc: "Walk through the process of installing an up-to-date version of Ruby & Bundler on your computer in preparation for doing our pattern libraries."

hide_markbot: true

extra_tutorials:
  - title: "Terminal cheat sheet"
    url: terminal-cheat-sheet
    disabled: true

steps:
  - title: "Open Terminal"
    before: |
      MacOS comes with the Ruby scripting language—but it’s usually out-of-date and quite restricted. So we need to install our own version, which isn’t too difficult to install, but it does require everything to be completed from within Terminal.

      **So first: open “Terminal” on your computer.** It’s in `Applications > Utilities` or you can search with “Spotlight”.

      ![](terminal.jpg)

      *Yours will look different: I have mine super customized.*

      **You will not be able to get to the next line in the Terminal like mine shows—mine is extremely customized because I use it so often.**

  - title: "Install Homebrew"
    before: |
      Homebrew is a package manager for Mac & Terminal—it’s like an app store, but specifically in the Terminal and mostly for developer tools.

      ### First go to the [Homebrew website](http://brew.sh/).

      ![](brew.jpg)

      On the page, you’ll see a chunk of code—copy it.

      ![](brew-copy.jpg)

      Paste it into your Terminal and hit return, your computer will go off an install Homebrew.

      ![](brew-paste.jpg)

      **It will prompt you for your computer’s password. As you type it in you won’t see anything—but it is being entered. When you’ve finished typing your password, hit `Return`.**
    notes:
    - label: "Be patient…"
      text: |
        The installation of Homebrew will likely take a long time—wait it out before continuing.

  - title: "Install Ruby with Homebrew"
    before: |
      Later in the term we’ll be using an application framework called Jekyll. Jekyll is written in the Ruby programming language, so we need to get that installed on our systems.

      Using `brew` we can install the most recent version of Ruby.

      ![](ruby.jpg)
    code_file: "Terminal"
    code_can_copy: true
    code: |
      brew install ruby
    notes:
    - label: "Be patient…"
      text: |
        The installation of Ruby will likely take a long time—wait it out before continuing.

  - title: "Check Ruby is installed"
    before: |
      Just to confirm that Ruby is installed, we’re actually going to look for another app that was installed alongside Ruby: RubyGems. We’re going to look to see which RubyGems app your computer tries to load.

      ![](which-gem.jpg)
    code_file: "Terminal"
    code_can_copy: true
    code: |
      which gem
    after: |
      **You should see exactly this output: `/usr/local/opt/ruby/bin/gem` otherwise it didn’t install properly.** *It’s likely that your `$PATH` variable wasn’t set properly when Homebrew was installed—your teacher can help you fix that.*

  - title: "Install Bundler"
    before: |
      Bundler is another tool we’ll need later in the term: its purpose is to allow us to define what plugins & packages our application will rely on: specifically we’ll use it to define that our app uses Jekyll & Patternbot.

      ![](bundler.jpg)
    code_file: "Terminal"
    code_can_copy: true
    code: |
      gem install bundler
    notes:
    - label: "Be patient…"
      text: |
        The installation of Bundler will likely take a long time—wait it out before continuing.

---
