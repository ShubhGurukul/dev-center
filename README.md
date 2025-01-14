# Algorithmia Developer Center

Welcome to the repository for Algorithmia's Developer Center. Here you will find guides, tutorials, sample apps, as well as some documentation on getting started with the API and basic set up.

These docs are built on Jekyll. Learn more over at [the official Jekyll page](http://jekyllrb.com/).

## Running locally

### Initial setup

1. Install [Docker](https://www.docker.com/products/docker-desktop)
2. Log in to Docker using the `algojenkins` account. (Email `devops+jenkins@algorithmia.com`, password in LastPass; note that the `Username` will be `algojenkins`, not the email address that's in LastPass)
3. Clone this repo and run `yarn setup` from within the top-level directory
  - If you're on MacOS and don't have `yarn` yet, [you can install it globally](https://classic.yarnpkg.com/en/docs/install#mac-stable)
  - Then, if `yarn setup` returns "The engine "node" is incompatible with this module..." error, you can first `brew install nvm` and then `nvm install 14.17.1`
  - Once that’s installed you may need to run one final `nvm use <version_number>` command to ensure node uses the latest version


### Normal dev workflow

1. Make sure the Docker daemon is running
2. `yarn dev`*
3. Visit `http://localhost:4000/developers/` or `http://localhost:4000/developers/api/`
4. While the local server is running, the local repo is being watched and changes will be reflected in the locally served version within ~10 seconds upon page refresh. Some changes, however, for example changes to navigation bar structure, are not automatically reflected. To clear the cache and completely rebuild the site to see these changes reflected, stop the server (CMD/CTRL + C) and then restart as in step 2.

*If this doesn't work (results in exit code != 0) and you've recently pulled down new code, try updating the dependencies by rerunning `yarn` and then `yarn setup` from the top-level directory. Once the dependencies update, rerun `yarn dev`.

### Running a prod build locally

The dev build builds to `_site`, while the prod build will build to `sites/public/`. To run a prod build locally, for example for debugging purposes, run:

`docker run -v $PWD:/jekyll algorithmiahq/dev-center:local-dev-jekyll-server bundle exec jekyll build -d sites/public/developers -c _config.yml`

### Building images for docker-compose

If changes are made to `package.json`, `Gemfile`, or any server-related code (`server/*`, `_config-*.yml`), you'll probably want to update the docker image that docker-compose uses for local dev.

```bash
docker build --no-cache -t algorithmiahq/dev-center:local-dev-node-server -f local.node.Dockerfile .
docker push algorithmiahq/dev-center:local-dev-node-server
```

```bash
docker build --no-cache -t algorithmiahq/dev-center:local-dev-jekyll-server -f local.jekyll.Dockerfile .
docker push algorithmiahq/dev-center:local-dev-jekyll-server
```

## Making changes

### Project organization

All posts, layouts, includes, stylesheets, assets, and whatever else is grouped nicely under the root folder.

Find all pages under the `_pages` directory, organized by URL route structure.

The compiled Jekyll site outputs to `_site/`. Do not edit anything in this directory (or your changes will be lost).

### Writing pages

The first thing that goes in each new post is the [YAML front-matter](http://jekyllrb.com/docs/frontmatter/). Below is an example of front-matter:

```ruby
---
layout: article
title:  "Example post!"
excerpt: "This is an example post."
date:   2016-01-05 11:39:38
categories: guides example
tags: [stuff, things]

# optional fields:
exclude_from_search: true #false by default
share: false #true by default
sitemap: false #true by default
---
```

For our purposes, the minimum you will need is `layout`, `title`, `date`, & `categories`. The other fields only need to be present if you are overriding the default.

Use `excerpt` to set the text that appears in under the article title in the collection view of all articles. The template will automatically grab the first sentence if you do not set an excerpt, so you'll want to make sure that is appropriate or set one by hand. _Note:_ If the first line of your post is a templating tag, it will not automatically pick up an excerpt.

In the case of `author`, the default author can be found in `_config.yml`. The default author is Algorithmia. If you need to add yourself as an author, please fill out your author data in `_data/authors.yml`. Then, set the author field in your front-matter in the post.

### Changing styles

#### Synapse changes

[Synapse](https://github.com/algorithmiaio/synapse) is added to this project through a pre-built CSS file that lives in `css`. If any new Synapse changes are required, build a new Synapse file (see the Synapse repository for steps on how to do this), and then increment the query parameter in `_layouts/default.html` so that browsers fetch the latest version.

#### Dev Center changes

Update the appropriate file within the `css` directory.

### When mentioning statistics and numbers

When you're mentioning the number of algorithms in the marketplace, or the maximum number of algorithms you can call, to be consistent across the whole developer center, please use variables instead.

For example, if you want to mention the number of algorithms we have in an article, use the following:

```text
And if you need a pre-trained model or utility function for your project, check out the over {{site.data.stats.marketplace.total_num_algorithms}} algorithms and microservices that have been deployed on Algorithmia's <a href="https://algorithmia.com/algorithms">AI Marketplace</a>.
```

You can find more variables in the `_data/stats.yml` file.

### CDN

Image and video assets can be prefixed with `{{site.cdnurl}}` to automatically serve them via CDN. Note that it can take over 24h for the CDN's cache to clear, so if replacing an asset which is already in the CDN, consider renaming the asset to force its immediate reloading.

### API Docs

The API docs are built using [Redoc](https://redoc.ly/docs). During local development, the API docs are generated using `/assets/openapispec.yml`. In test and prod environments, the docs are generated using `https://SITE_URL/v1/openapispec`.

### Plugins

This Jekyll site uses several plugins to help generate content and make the site extra-awesome. All plugins live in the `plugins` directory. In order to speed up development, we've opted to use some plugins only in a production environment. You can see which plugins are used for development versus production by opening the `_plugins-dev` or `_plugins-prod` folders, which use symlinks to refer to files in the `plugins` folder.  Included in the `plugins` directory:

- `Emoji.rb`: Emojify your posts. Simply use the text version (like you would on GitHub) and this plugin will replace it with the emoji image. See the [emoji cheat sheet](http://www.emoji-cheat-sheet.com) for a full listing of emoji codes. :nail_care:
- `author_page_generator.rb`: This plugin will generate a page that lists all posts by a given author.
- `jekyll-lunr-search.rb`: __(Production Only)__ Generates the index of all posts for the search function.
- `navmenu.rb`: A tag plugin to generate the side navigation menu.
- `strip.rb`: Removes some excess whitespace and new lines generated by the Liquid templating process.

### Third-Party Component Vulnerability Detection

Per the [Third-Party Component Maintenance Policy](https://algorithmia.atlassian.net/wiki/spaces/PLATFORM/pages/1851129905/Third-Party+Component+Maintenance+Policy), the Developer Center uses [an automated, weekly scan](https://gitlab.com/algorithmia-eng/dev-center/-/pipeline_schedules/160002/edit) to detect security vulnerabilities with a CVE score of 7.0 or higher. Components with vulnerabilities with scores of 7.0 or greater are reported as Jira tickets into [the UXENG Jira board](https://algorithmia.atlassian.net/secure/RapidBoard.jspa?projectKey=UXENG&useStoredSettings=true&rapidView=21). All [failed scans are reported into Slack](https://gitlab.com/algorithmia-eng/dev-center/-/services/slack/edit) with a [Slack Incoming Webhook](https://algorithmia.slack.com/services/B02BP6QDDD2).

Scanning and Jira ticket creation is performed by a script:
-   `report-os-package-security-vulnerabilities algorithmiahq/dev-center:<version> UXENG "Developer Center"` - scans OS packages
-   `report-node-security-vulnerabilities algorithmiahq/dev-center:<version> UXENG "Developer Center"` - scans Node code libraries

These scripts are part of the [CI-tools repository](https://github.com/algorithmiaio/ci-tools/blob/traack-add-single-image-vulnerability-scanner/vulnerabilities/tools/report-os-package-security-vulnerabilities) and are packaged for use in the `algorithmiahq/vulnerability-scanner:latest` Docker image.

Running a script with `--no-jira` appended will run scanning and CLI reporting of vulnerabilities without Jira ticket creation; for example: `report-os-package-security-vulnerabilities algorithmiahq/dev-center:<version> UXENG "Developer Center" --no-jira`.

## Environment variables

### `ENFORCE_CSP` | Boolean

**Default**: `false`

**Description**: If set to `true`, enforces a content security policy for the application.

### `DISABLE_HSTS` | Boolean

**Default**: `false`

**Description**: If set to `true`, disables the `Strict-Transport-Security` header on server responses.

### `DISABLE_X_CONTENT_TYPE_OPTIONS` | Boolean

**Default**: `false`

**Description**: If set to `true`, disables the `X-Content-Type-Options` header on server responses.

### `DISABLE_X_FRAME_OPTIONS` | Boolean

**Default**: `false`

**Description**: If set to `true`, disables the `X-Frame-Options` header on server responses.

### `DISABLE_X_XSS_PROTECTION` | Boolean

**Default**: `false`

**Description**: If set to `true`, disables the `X-XSS-Protection` header on server responses.

### `PROMETHEUS_TOKEN` | Boolean

**Default**: `undefined`

**Description**: The authorization bearer token necessary for the application to expose Prometheus metrics at the /metrics endpoint.

## Contributing

First, fork the repository and follow the instructions above to get set up. Make sure all your changes work locally. When you are ready, make a pull request to this repo and we will review the changes. Be sure to describe the changes, attach screenshots of any cosmetic changes, and if applicable, link to the open issue. Please follow the [screenshot guidelines](https://algorithmia.atlassian.net/wiki/spaces/CUSTOMERS/pages/1634861478/CFD+Style+Guide#Screenshots) when including screenshots.

When contributing please refer to the [Algorithmia manual of style](https://docs.google.com/document/d/1PPVfgMkX7-EVGLPMhN1E485CAXu9QfhSLKM0lZhnZdU/edit?usp=sharing) for grammar, punctuation, voice, and tone.

## Need help? Found a bug?

If you find a bug, can't follow the documentation, or have a question -- please [submit an issue!](https://github.com/algorithmiaio/dev-center/issues)

We will respond to you or reach out for more information as soon as possible. And, of course, feel free to submit pull requests with bug fixes or changes.
