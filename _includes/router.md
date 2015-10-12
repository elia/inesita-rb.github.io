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
