## Router

`Router` describes what `Components` are rendered depending on current URL.

```ruby
class Router
  include Inesita::Router

  def routes
    route '/', to: Home, props: {}
    route '/description', to: Description
  end
end
```

As we see, when browser points to `/`, `Home` component is rendered, and when we go to `/description`, application will render `Description` component.
You can pass props to components with a props hash.
All routes are automatically named. First route is named `:home`, second one `:description`.
You can use these names when creating links in components. Router instance is available in every component.
For example, lets create a simple navigation bar with [bootstrap](http://getbootstrap.com):

```ruby
class NavBar
  include Inesita::Component

  def render
    nav class: 'navbar navbar-default' do
      div class: 'container' do
        div class: 'navbar-header' do
          span class: 'navbar-brand' do
            text 'Inesita'
          end
          ul class: 'nav navbar-nav' do
            li class: "#{"active" if router.current_url?(:home)}" do
              a href: router.url_for(:home) do
                text 'Home'
              end
            end
            li class: "#{"active" if router.current_url?(:description)}" do
              a href: router.url_for(:description) do
                text 'Description'
              end
            end
          end
        end
      end
    end
  end
end
```

`url_for(:name)` method return a URL for a given route.

`current_url?(:name)` returns `true` if a given route is currently set.

When we're using an `a` tag in components that are belong to `Inesita::Application`, `onclick` events are handled by the router.
