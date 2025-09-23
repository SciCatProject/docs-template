# docs-template

This repository provides a template for the any documentation on the microservices that make up the SciCat project.

It includes:

   *  Preconfigured GitHub Actions workflow for automated documentation deployment
   *  Custom CSS styling for consistent branding across the SciCat project.
   *  MkDocs Material theme setup for professional-looking documentation
   *  Flexibility to accommodate different documentation structures from embedded README.md files to `docs` directories.

# Using the Docs-Template Repository

## Default
The default way of using this repository is to use it in a new project as a template repository. It will set up the docs structure and workflows for you.

To edit the documentation of your new repository, write `.md` files inside its `docs` directory.

### Editing the mkdocs.yml
**Structuring the docs**
You can add structure the documentation by adding the names of the files to the `nav` section inside `mkdocs.yml`. See the example of adding a "Getting Started" page to your docs:
```yaml
nav:
  - Home: index.md
  - Getting Started: getting-started.md
  - About:
      - about/index.md
```
**Updating the site-name**
Your site name will have a default of "SciCat Documentation"

To update this open the `mkdocs.yml` and update the variable `site_name:` to the preferred name of your site.

## Adding to an existing repository
### Repositories with no existing documentation
To add to an existing repository you can copy the `.github/mkdocs` and `docs` locally to your repository. Follow the structure

```
.
├── .github/
│   ├── mkdocs/
│   │   └── mkdocs.yml
│   └── workflows/
├── docs/
    ├── index.md
    ├── about.md


```
You can now write your documentation in markdown and store it in the docs folder. You can structure it using the `nav` [section](#editing-the-mkdocsyml)

You will also need to copy the `publish-docs.yml` to your `.github/workflows` folder.

### Repositories with existing documentation

For repositories with existing documentation copy the folder `.github/mkdocs` into your repository under the top directory. Open the file `.github/mkdocs/mdocs.yml` and change the `do
`docs_dir` path to the path to your current documentation:
```yaml
site_name: SciCat Documentation
docs_dir: `..\..\my_docs`
```
You can also update the `nav` to include the structure of your directories see [here](#editing-the-mkdocsyml) for an example.

You will then need to add the following `publish-mkdocs.yml` workflow to your `.github/workflows` folder.

## Advanced


# Local Testing

To use this repository locally, just clone the repo and run

To build the conda environment use the following:
```bash
docker compose up -d

Then navigate to `localhost:8000`in your web browser to see the docs.

All following changes in the `docs` repo and/or in the `.github/mkdocs` config files (e.g. mkdocs.yaml), will be mirrored on localhost:8000.
