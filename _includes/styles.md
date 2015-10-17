## Styles

Default style sheet is `app/stylesheet.css.sass`. It use sass. You can create you own stylesheets structure and include it in this files.
For example if we want to include bootstrap:

```sass
@import "bootstrap"
```

External styles are included within a Gemfile using a `rails-assets.org` service.

```
source 'https://rails-assets.org' do
  gem 'rails-assets-bootstrap'
end
```
