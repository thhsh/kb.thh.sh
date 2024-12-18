# Material for MkDocs

This site is  built and hosted using Cloudflare Pages. These are a couple notes on tweaks that seem to be needed to get everything working nicely.

## Finalized Build Command
This command is what's currently working to properly build this site:  

!!! warning "Updated build command"
    The build command below has been updated to reflect that the `mkdocs-material-insiders` repo is now being mirrored to a private Github repo within the 41N org. The deprecated build command is still stored below, for posterity.

**Build command:**  
```
git fetch --unshallow && pip install git+https://oauth2:${GH_TOKEN}@github.com/41-north/mkdocs-material-insiders_mirror.git && pip install mkdocs-awesome-pages-plugin && pip3 install mkdocs-git-revision-date-localized-plugin && mkdocs build --site-dir public
```
See the important note below about the `GH_TOKEN` environment variable.  
**Build output directory:** `/public`

(I'm sure there's a way to clean up this command some, but it's what is working for me for now!)

??? note "Deprecated build command"
    This is the previous build command used, which is now deprecated as noted above.

    ```
    git fetch --unshallow && pip install git+https://${GH_TOKEN}@github.com/squidfunk/mkdocs-material-insiders.git && pip install mkdocs-awesome-pages-plugin && pip3 install mkdocs-git-revision-date-localized-plugin && mkdocs build --site-dir public
    ```

## Cloudflare Pages Environment Variables
Since we're using [:simple-materialformkdocs: Material for MkDocs Insiders](https://squidfunk.github.io/mkdocs-material/insiders/), the build command needs access to the private GitHub repo where Insiders is hosted. We give Cloudflare Pages an API key to allow it to access this repo.

To set the API key in Cloudflare Pages, go to **Workers & Pages** > ***your_site*** > **Settings** > **Environment variables**. 

For **each** Production and Preview environment, do the following:

1. Click **Edit Variables**
2. Click **Add Variable**
3. Set the **Variable Name** to `GH_TOKEN`
4. Copy the API key from [:simple-1password: 1Password](https://start.1password.com/open/i?a=B5NVCNGFJBCCLCDCN5FKFPGVBI&v=jsiictzq3qvzmkew4xt5mjqi6u&i=lefcltdoiybedpaadhyoaqmsem&h=41-north.1password.com) (:octicons-lock-24: Internal) and paste it in the **Value** box
5. Click the grey **Encrypt** button
6. Click **Save**

## Awesome-Pages
Using the [:octicons-mark-github-16: mkdocs-awesome-pages-plugin plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin) for navigation.

[:octicons-link-external-16: Info on how to use this plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin?tab=readme-ov-file#features)

## TimeAgo/Revision Date
Because these docs are hosted in a Git repo, we can use the [:octicons-mark-github-16: mkdocs-git-revision-date-localized-plugin plugin](https://github.com/timvink/mkdocs-git-revision-date-localized-plugin) to note for each page when it was last edited/revised.

Because Cloudflare Page's build pipeline by default fetches only the latest revision, we have to add `git fetch --unshallow &&` to the CF build command, to have it fetch the full repo.
