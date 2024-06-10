# Material MkDocs on Windows
For at least one of the Windows computers that I use, there's a bit of finesse required to get Material for MkDocs Insiders installed and behaving properly.

## Install Python
1.  Download Python for Windows from [python.org - Python Releases for Windows](https://www.python.org/downloads/windows/).
2.  Run the installer, making sure to include in PATH.

## Install Material for MkDocs Insiders
1.  Grab the GitHub API key for the Insiders repo from 1Password, see [Cloudflare Pages Environment Variables](mkdocs.md/#cloudflare-pages-environment-variables). Hang onto that for the next step.
2.  Run this command in Windows Terminal: 
```
py -m pip install git+https://API_KEY_YOU_JUST_COPIED@github.com/squidfunk/mkdocs-material-insiders.git mkdocs-git-revision-date-localized-plugin pip install mkdocs-awesome-pages-plugin
```
3.  Wait while everything installs.

!!! example "To Do"
    Figure out env. variables on Windows, and save the GH_TOKEN_INSIDERS token as a variable, use that variable in the install command.

## Serving in dev mode
While working on docs, before committing and having Cloudflare Pages build and push everything, use `mkdocs serve` to build and serve the docs locally.

1.  From Terminal in the docs location (you should see `mkdocs.yml` and `docs`), run:
```
py -m mkdocs serve
```
2.  Open `http://127.0.0.1:8000` to see the built site in all its glory!