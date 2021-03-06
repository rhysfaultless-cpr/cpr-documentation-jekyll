# cpr-documentation-jekyll

## Tools used:

1.  [Ruby](https://www.ruby-lang.org/en/)
2.  [GitHub](https://github.com/about)
3.  [GitHub Pages](https://pages.github.com/)
4.  [GitHub Actions](https://github.com/features/actions)
5.  [Jekyll](https://jekyllrb.com/)
6.  Jekyll theme, [Just-The-Docs](https://github.com/just-the-docs/just-the-docs)
    - [Example Website Repository](https://github.com/pmarsceill/jtd-remote)


## How the documentation-website builds, on GitHub Pages

GitHub Pages supports Jekyll by default.
GitHub has gone so far as to make this process _easy_ by allowing you to deploy sites without a _Gemfile_ to list dependencies.
For me, this was a difficult process, where my local _Gem_ dependencies were different than the Pages server.
This difference in dependencies makes testing and quality-assurance difficult, especially since GitHub Pages only gives you website instance, deployed from your main branch (this repository's main branch is _production_ and was configured in the Settings panel of GitHub).

Some frequent issues during testing:

- differences between the Jekyll themes (Local versus Remote)
- links, tags, and includes working well locally, but do not complete on GitHub pages (Liquid/Jekyll path issues)
- HTML and CSS customizations building as intended locally, but causeing issues on GitHub Pages

GitHub runs a GitHub-Action whenever it sees new commits on the main branch. 
This Action will review *_config.yml*, and will deploy all your _.md_ and _.html_ files.
GitHub Pages lets you choose to host your files from the project's root directory `/` or from a docs folder `/docs`.
I chose the root directory, since I wanted to also test the site locally on my computer.

## How the documentation-website builds, Locally

Ruby uses your project's Gemfile as a package manager.
When you run `bundle install` from the root of the project directory, Ruby will read your _Gemfile_ and install all the Gems (dependencies) listed in it.
Running `bundle update` is similar, but comparing the current state of you project's _Gemfile.lock_ to the _Gemfile_ and installing or removing files based on the differences.
Note that the _.gitignore_ for this project prevents the _Gemfile.lock_ from being added to GitHub, so it is a new installation every time a User clones the repository.
This is okay for our use case with GitHub Pages as our deployment server, 
  since Pages does not reference the repository's _Gemfile.lock_ for CI/CD _(Continuous-Integration/Continuous-Deployment)_.
After running `bundle install`, you can start the server by running the command:

    bundle exec jekyll serve --config _config_local.yml --livereload

This command has 3 main aspects:

1.  `bundle exec jekyll serve` will deploy the website using Jekyll, which was an installed dependency in the _Gemfile_
2.  `--config _config_local.yml` is telling Jekyll to use the configuration file *_config_local.yml* in the root of the project directory.
    Omitting this aspect of the command would have Jekyll use the default file, *_config.yml*. 
    The default file has been configured for GitHub Pages, and causes issues for local deployments.
3.  `--livereload` tells Jekyll to redeploy the website every time the project is updated. 
    This includes any new file, updating an existing file, or changing the directory folder structure. 
    Note that this automatic redeployment does not capture changes to *_config_local.yml*, so you will need to manually restart the server if you make changes to the configuration.

After running the command, you can access the website in a web-browser like Google Chrome at the address <http://127.0.0.1:4000>

## Steps to update documentation on Windows (assuming fresh installation)

1.  Set up your GitHub account.  
2.  Install Git on your computer.
    1.  Go to the Git website <https://git-scm.com/download/win> and select the _Click here to download_ button for the latest version.
    2.  Run through the installer.
3.  Set up the Ruby programming lanuguage on your computer
    1.  Open a terminal, and enter `ruby -v`.
        You will receive an error messge if you do not have the Ruby interpretter installed on this Windows machine.
    2.  To install Ruby on Windows, got to <https://rubyinstaller.org/downloads/> and download [Ruby+Devkit 3.1.2-1 (x64)](https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-3.1.2-1/rubyinstaller-devkit-3.1.2-1-x64.exe) or a newer version.
4.  Set up VS Code as your text editor
    1.  Go to <https://code.visualstudio.com/download> and select the Windows download.
    2.  Open the _.exe_ installer, and go through the installation instructions
    3.  Launch VS Code after it has been installed.
        The welcome screen will likely ask you what programming extensions you want to use.
        You can skip this for now.
    4.  From the homescreen, click _extensions_.

        <img src="/assets/images/windows_installation_vscode_1.png" width="400"/>

    5.  Search for _Ruby_, and click the _Install_ icon beside the extension.

        <img src="/assets/images/windows_installation_vscode_2.png" width="400"/>

    6.  Search for _Prettier_, and click the _Install_ icon beside the extension.

        <img src="/assets/images/windows_installation_vscode_3.png" width="400"/>

    7.  Search for _Live Server_, and click the _Install_ icon beside the extension.

        <img src="/assets/images/windows_installation_vscode_4.png" width="400"/>

    8.  Search for _Git Lens_, and click the _Install_ icon beside the extension.

        <img src="/assets/images/windows_installation_vscode_5.png" width="400"/>

    9.  Open a new terminal in VS Code, and enter `ruby -v`.

        <img src="/assets/images/windows_installation_vscode_6.png" width="400"/>

        Close and re-open VS Code if you get an error message.

        <img src="/assets/images/windows_installation_vscode_7.png" width="400"/>

        You should get a confirmation message indicating the version of Ruby.

        <img src="/assets/images/windows_installation_vscode_8.png" width="400"/>

    10. In the same terminal, enter `gem -v`

        You should get a confirmation message indicating the version of Ruby Gems.

        <img src="/assets/images/windows_installation_vscode_9.png" width="400"/>

    11. Now configure your Git settings in the same terminal.
 
        - Enter `git config --global user.name <"Your name goes here in quotes">`
        - And enter `git config --global user.email <Your email goes here>`
 
        For example, my Git settings look like this:
        
            git config --global user.name "Rhys Faultless"
            git config --global user.email rfaultless@clearpathrobotics.com

5.  Clone this repository to your computer.
    1.  Open a terminal in VS Code.
    2.  Use _cd_ and _cd .._ to navigate to the directory you want to store GitHub repositories locally on your computer.
        I save mine to the directory `C:\Users\rfaultless\Documents\Github`.
    3.  Now clone this repository to your computer by entering:

            git clone https://github.com/rhysfaultless-cpr/cpr-documentation-jekyll.git

    4.  Once the command is finished running, enter _ls_ in the terminal.
        You should see a new folder named _cpr-documentation-jekyll_
    5.  In VS Code, click _File_ and select _Open Folder ..._

        <img src="/assets/images/windows_installation_vscode_10.png" width="400"/>

    6.  In the window, navigate to the cloned directory _cpr-documentation-jekyll_ and then click _Select Folder_

        <img src="/assets/images/windows_installation_vscode_11.png" width="400"/>

        
6.  Testing the Documentation server on your computer.
    1.  Open a terminal in VS Code.
    2.  Make sure your terminal session is directed to the root directory of the project, such as:

            C:\Users\rfaultless\Documents\Github\cpr-documentation-jekyll>

    3.  In the termainal session, enter:

            bundle install

        This will install all the project dependencies listed in the Ruby file _Gemfile_.
        You will see new files and folders appearing in the project directory, like:

        - Gemfile.lock
        - _site

    4.  After the files are installed, enter this in the terminal session:

            bundle exec jekyll serve --config _config_local.yml --livereload

        This will start a server on your local computer for hosting the Documentation website.
        Windows Defender may show a pop-up asking if it should allow this application port permissions for Public, Home, or Work networks.
        After ~5 seconds, the terminal will show:

                    Jekyll Feed : Generating feed for posts
                GitHub Metadata : No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
                                  done in 10.315 seconds.
              Auto-regeneration : enabled for 'C:/Users/rfaultless/Documents/Github/cpr-documentation-jekyll'
            LiveReload address  : http://127.0.0.1:35729
                Server address  : http://127.0.0.1:4000/
                Server running... press ctrl-c to stop.

    5.  You can now access the Documentation website by opening a web-browser like Google Chrome, and entering the URL: <http://127.0.0.1:4000>
