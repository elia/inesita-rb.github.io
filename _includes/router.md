## Router

`Router` describes what `Components` are rendered depending on current url.

```ruby
class Router
  include Inesita::Router

  def routes
    route '/', to: Home, props: {}
    route '/description', to: Description
  end
end
```

As we see. When browser points to `/` `Home` component is rendered, when we go to `/description` application will render `Description` component.
You can pass a props to components with props hash.
All routes a automaticaly named. First route is named `:home` socound one `:description`
You can use this names while creating link in components. Router instance is available in every component.
For example lets create a simple navigation bar with `bootstrap`:

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

`url_for(:name)` method return an url for given route.

`current_url?(:name)` return `true` if a giver route is currently set.

When we're use an `a` tag in components that are belongs to `Inesita::Application`, `onclick` are handled by router.
