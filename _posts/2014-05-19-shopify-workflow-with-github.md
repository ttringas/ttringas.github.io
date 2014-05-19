---
published: false
---

## Shopify Development Workflow with Github

Recently had to write up my Shopify development workflow. I'm using Github and Shopify Theme Gem and it seems to work pretty well. Love to hear any feedback of course.

* Pull latest code base from github

* Create a new development branch with the pattern [version]-[name]. As best as possible use [semantic versioning](http://semver.org/)

```
git checkout -b 3.2.0-new-feature
```

* Head to the Shopify Admin > Themes. Duplicate a theme. If you created your branch from the master branch, then duplicate the live theme, if your development branch works of an existing unpublished development theme, then duplicate that theme.

* Rename the duplicated theme the same as your branch name (i.e. 3.2.0-new-feature)

* Install the [Shopify Theme Gem](https://github.com/Shopify/shopify_theme) and follow the installation process. Example:

```
gem install shopify_theme
theme configure [api_key] [password] [shop_url]
```
Note: this only needs to be done once

* Once this is installed, head the config.yml file in your development branch. You need to change the theme_id to your new development theme's ID. Get the ID from the URL in the theme editor. Set theme_id to this new ID and commit changes.

* Now you can use the Shopify Theme Gem's functions to sync your local version of the theme with the unpublished development theme you created (from the duplicate). Open console, cd to the directory and type:

```
theme watch
```

The gem will now watch for saved files and automatically sync those files with your Shopify account. 

Note: I recommend doing a test like adding a comment to confirm you are syncing changes with the development theme and NOT the live published theme.

* To see the effects of your changes just go to the theme manager and Preview the theme in the browser.

* When you're finished either push a new branch to Github, or merge your changes into master and publish your development theme. The master branch should always match the published theme and development branches should always have an unpublished theme with the same name.


