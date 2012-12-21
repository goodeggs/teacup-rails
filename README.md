# Teacup::Rails

Teacup::Rails makes [Teacup](http://goodeggs.github.com/teacup) native CoffeeScript templates
available to the Rails asset pipeline.

## Installation

Add this line to your application's Gemfile:

    gem 'teacup-rails'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install teacup-rails

Make Teacup available to your JavaScript application by requiring it in `app/assets/javascripts/application.js`
before your application files.

``` javascript
// This is a manifest file that'll be compiled into application.js, which will include all the files
// listed below.

//= require jquery
//= require jquery_ujs
//= require teacup
//= require_tree .
```

## Usage

Teacup exports one reference to the global scope as `window.teacup`. Import the tags you need to render your view.

```coffeescript
{renderable, h1, table, tr, th, td, a} = teacup
template = renderable ({posts})->
  h1 'Listing posts'
  table "#posts-table", ->
    tr ->
      th 'Title'
      th 'Content'
    for post in posts
      tr '.post-row', ->
        td post.title
        td post.content
  a href: '#/new', 'New Post'

class IndexView extends Backbone.View
  template: template

  constructor: ({@posts}) ->
    super()

  render: =>
    @$el.html @template(posts: @posts.toJSON())
    @
```

See [Teacup](http://goodeggs.github.com/teacup) for more usage examples.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
