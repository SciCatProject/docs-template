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

[./.github/workflows/publish-docs.yml](./.github/workflows/publish-docs.yml) is an example of the use of the action.

## Using dedicated mkdocs settings

You can override any of the settings from your repo, by placing configurations in the `./github/mkdocs` folder in your repo and documentation in your `docs` folder. For example, if your repository has a `./github/mkocs/mkdocs.yml` this will take precedence over [./.github/actions/mkdocs-pages/mkdocs.yml](./.github/actions/mkdocs-pages/mkdocs.yml). 

Please note that adding new files in `docs` requires changing the `nav` in `./github/mkocs/mkdocs.yml`, so it's likely that whenever changing `docs` also having `./github/mkocs/mkdocs.yml` will be required.

# Local Testing

To use this repository locally, just clone the repo and run

To build the conda environment use the following:
```bash
docker compose up -d

Then navigate to `localhost:8000`in your web browser to see the docs.

All following changes in the `docs` repo and/or in the `.github/mkdocs` config files (e.g. mkdocs.yaml), will be mirrored on localhost:8000.
