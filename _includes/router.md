## Router

```ruby
class Router
  include Inesita::Router

  def routes
    route '/', to: Home
    route '/welcome', to: Welcome
    route '/goodbye', to: Goodbye
  end
end
```
