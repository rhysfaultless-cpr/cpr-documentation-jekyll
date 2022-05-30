# cpr-documentation-jekyll

## Tools used:

1. [Ruby](https://www.ruby-lang.org/en/)
2. [GitHub](https://github.com/about)
3. [GitHub Pages](https://pages.github.com/)
4. [GitHub Actions](https://github.com/features/actions)
5. [Jekyll](https://jekyllrb.com/)

## Steps to create this repository

I was following the installation instructions described in [Jekyll's documentation](https://jekyllrb.com/docs/installation/)
These were my steps for Windows in May 2022:

1.  Install [Ruby 2.5.0](https://www.ruby-lang.org/en/downloads/) or higher. 
    (Note that I installed  [Ruby+Devkit 3.1.2-1 (x64)](https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-3.1.2-1/rubyinstaller-devkit-3.1.2-1-x64.exe) for my Windows 10 machine)
    - I selected option 1, for Base Install of Ruby
2.  Install [RubyGems](https://rubygems.org/pages/download). 
    I downloaded the ZIP, extracted the contents, and then ran the *setup.rb* file from the extracted folder.
3.  Click the Windows Start menu, and select the application *Start Command Prompt with Ruby*.
4.  In the terminal window, run the command `gem install jekyll bundler`
5.  After the installation is complete; confirm that Jekyll was installed by running `jekyll -v` in the terminal.
    - I received a response of `jekyll 4.2.2`
6.  Create a new GitHub repository.
7.  Clone the repository to my laptop.
8.  In a command-prompt-with-ruby, navigate to the root directory of the cloned repository, and enter the command `jekyll new cpr-documentation-jekyll`
9.  It will generate a new folder named *cpr-documentation-jekyll* inside the root directory. 
    I copied all the contents to the root directory, and then deleted the generated folder. 
    (not the correct way to run this operation)
10. Then run `bundle add webrick`
11. Then run `bundle exec jekyll serve --config _config_local.yml --livereload`
    - I received the response `... Server address: http://127.0.0.1:4000/ ...`

Note: I am testing a new theme: just-the-docs

- [GitHub](https://github.com/just-the-docs/just-the-docs)
- [Live](https://just-the-docs.github.io/just-the-docs/)
- [Example Website Repository](https://github.com/pmarsceill/jtd-remote)
