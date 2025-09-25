# docs-template

This repository provides a template for the any documentation on the microservices that make up the SciCat project.

It includes:

   *  Preconfigured GitHub Actions workflow for automated documentation deployment
   *  Custom CSS styling for consistent branding across the SciCat project.
   *  MkDocs Material theme setup for professional-looking documentation
   *  Flexibility to accommodate different documentation structures from embedded README.md files to `docs` directories.

# Adding to an existing repository

## Default
The default way of using this repository is to use it as an action in the repository of interest. This will apply the configuration from [./.github/actions/mkdocs-pages/](./.github/actions/mkdocs-pages/), which contains defautls from `navigations`, `assets` and `styles` 

To use this in your repository copy `./.github/workflows/publish-docs.yml` into a folder into the `.github/workflows/` folder in your repository. [./.github/workflows/publish-docs.yml](./.github/workflows/publish-docs.yml) is an example of the use of the action.

To extend the documentation you can use a `docs` directory or a `README.md` file.
### Use a docs directory

Make a `docs` directory in the root directory of your repository and add markdown files to it. To use add your new files to the docs you will need to copy the file [./.github/actions/mkdocs-pages/mkdocs.yml](./.github/actions/mkdocs-pages/mkdocs.yml) to your repository in a `.github/actions/mkdocs` directory. From here add to the `nav` panel to add your new docs.

**Example**

 Given a folder structure like this add markdown files to the `docs`
```
 ├── .github/
 │   ├── mkdocs/
 │   │         └── mkdocs.yml
 │   └── workflows/publish-docs.yml
 ├── docs/
         └──Example.md
```
 Once you have added your documentation you need to add it to the navigation on the `.github/mkdocs/mkdocs.yml`. Open the file and add your page in the nav section:
 ```yaml
 INHERIT: mkdocs-default.yml
 nav:
   - index.md
   - Example.md
   - About: about/index.md
 ```

### Using nested README.md

If you want to use a nested `README.md` structure for your documentation create the following `mkdocs.yml` in `.github/mkdocs/mkdocs.yml`.
```yaml
INHERIT: mkdocs-nested.yml
```
The nested implementation uses the package `awesome-pages` which collapses down folders with single files to a single web page.

## Using dedicated mkdocs settings

You can override any of the settings from your repo, by placing configurations in the `./github/mkdocs` folder in your repo and documentation in your `docs` folder. For example, if your repository has a `./github/mkocs/mkdocs.yml` this will take precedence over [./.github/actions/mkdocs-pages/mkdocs.yml](./.github/actions/mkdocs-pages/mkdocs.yml). 

Please note that adding new files in `docs` requires changing the `nav` in `./github/mkocs/mkdocs.yml`. When you add to `docs` you will require `./github/mkocs/mkdocs.yml` to add these pages to the navigation see [here](#use-a-docs-directory).

## Merging defaults and dedicated settings

To ease the use of defautls and override the required portions only, the local `./github/mkocs/mkdocs.yml` can use the INHERIT mechanism defined by mkdocs and inherit defaults from the [./.github/actions/mkdocs-pages/mkdocs-default.yml](./.github/actions/mkdocs-pages/mkdocs-default.yml), like this one [./.github/actions/mkdocs-pages/mkdocs.yml](./.github/actions/mkdocs-pages/mkdocs.yml).

For example, to change the site name, the repo using the action should have a file `./.github/mkdocs/mkdocs.yml` with content:

```yaml
INHERIT: mkdocs-default.yml

site_name: my-site-name
```

# Local Testing

To use this repository locally, just clone the repo and run

```bash
docker compose up -d
```
Then navigate to `localhost:8000` in your web browser to see the docs.

All following changes in the `docs` repo and/or in the `.github/mkdocs` config files (e.g. mkdocs.yaml), will be mirrored on localhost:8000.
