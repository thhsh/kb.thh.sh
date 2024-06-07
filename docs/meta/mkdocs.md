# Material for MkDocs

This site is  built and hosted using Cloudflare Pages. These are a couple notes on tweaks that seem to be needed to get everything working nicely.

## Finalized Build Command
This command is what's currently working to properly build this site:  
**Build command:**  
```
git fetch --unshallow && pip install git+https://${GH_TOKEN}@github.com/squidfunk/mkdocs-material-insiders.git mkdocs-git-revision-date-localized-plugin pip install mkdocs-awesome-pages-plugin; mkdocs build --site-dir public
```
See the important note below about the `GH_TOKEN` environment variable.  
**Build output directory:** `/public`

## Cloudflare Pages Environment Variables
Since we're using [:simple-materialformkdocs: Material for MkDocs Insiders](https://squidfunk.github.io/mkdocs-material/insiders/), the build command needs access to the private GitHub repo where Insiders is hosted. We give Cloudflare Pages an API key to allow it to access this repo.

To set the API key in Cloudflare Pages, go to **Workers & Pages** > ***your_site*** > **Settings** > **Environment variables**. 

For **each** Production and Preview environment, do the following:

1. Click **Edit Variables**
2. Click **Add Variable**
3. Set the **Variable Name** to `GH_TOKEN`
4. Copy the API key from [:simple-1password: 1Password](https://start.1password.com/open/i?a=B5NVCNGFJBCCLCDCN5FKFPGVBI&v=jsiictzq3qvzmkew4xt5mjqi6u&i=w5l45q5wofbqe4s2qhtyn4dk3a&h=blackcat-labs.1password.com) (:octicons-lock-24: Internal) and paste it in the **Value** box
5. Click the grey **Encrypt** button
6. Click **Save**

## Awesome-Pages
Using the [:octicons-mark-github-16: mkdocs-awesome-pages-plugin plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin) for navigation.

[:octicons-link-external-16: Info on how to use this plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin?tab=readme-ov-file#features)

## TimeAgo/Revision Date
Because these docs are hosted in a Git repo, we can use the [:octicons-mark-github-16: mkdocs-git-revision-date-localized-plugin plugin](https://github.com/timvink/mkdocs-git-revision-date-localized-plugin) to note for each page when it was last edited/revised.

Because Cloudflare Page's build pipeline by default fetches only the latest revision, we have to add `git fetch --unshallow &&` to the CF build command, to have it fetch the full repo.