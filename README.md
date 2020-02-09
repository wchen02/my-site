# My Site

[![Netlify Status](https://api.netlify.com/api/v1/badges/c4f88e48-9fe8-4380-8281-e8bb25578c4d/deploy-status)](https://app.netlify.com/sites/wensheng/deploys)
[![Build Status](https://travis-ci.org/sylhare/Type-on-Strap.svg?branch=master)](https://travis-ci.org/sylhare/Type-on-Strap)
[![Gem Version](https://badge.fury.io/rb/type-on-strap.svg)](https://badge.fury.io/rb/type-on-strap)
[![Docker Pulls](https://img.shields.io/docker/pulls/sylhare/type-on-strap)](https://hub.docker.com/repository/docker/sylhare/type-on-strap)

A free and open-source [Jekyll](https://jekyllrb.com) theme. Based on Rohan Chandra [type-theme](https://github.com/rohanchandra/type-theme) with a few new features:

* Responsive design
* Portfolio page for your projects
* Tags compatibility
* Bootstrap : [Get Bootstrap](http://getbootstrap.com/)
* Search feature : [Simple-Jekyll-Search](https://github.com/christian-fei/Simple-Jekyll-Search)
* Math Rendering : [KateX](https://github.com/Khan/KaTeX)
* Nice fonts : [Font Awesome](https://fontawesome.com/), [Source Sans Pro](https://fonts.google.com/specimen/Source+Sans+Pro), [Pacifico](https://fonts.google.com/specimen/Pacifico?selection.family=Pacifico)
* Seo Tags : [Jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag)
* Syntax Highlighting: Easily customisable [Base16](https://github.com/chriskempson/base16)
* Free of rights images from [pexels](https://www.pexels.com/)

### Use as Ruby Gem

You can use Type-on-strap as a [gem](https://rubygems.org/gems/type-on-strap).

Ruby Gem Method
Add this line to your Jekyll site's Gemfile (or create one):

```ruby
gem "type-on-strap"
```

Add this line to your Jekyll site's `_config.yml` file:

```yml
theme: type-on-strap
```

Then run Bundler to install the theme gem and dependencies:

```bash
bundle install
```

Then you can start adding content like:

- Add a `index.html` file
- Add the feature page you want. (ex: as it is already in `pages`)
- Add posts in `_posts` and `_portfolio` to be displayed

### Remote Theme

Now you can use any theme gem with github pages with [29/11/2017 Github Pages Broadcast](https://github.com/blog/2464-use-any-theme-with-github-pages).
For that remove all `theme:` attributes from `_config.yml` and add instead:

```yml
remote_theme: sylhare/Type-on-Strap
```

## License

There are some fonts and component on this theme going under the MIT licence as well in this theme.
[The MIT License (MIT)](https://raw.githubusercontent.com/Sylhare/Type-on-Strap/master/LICENSE)
