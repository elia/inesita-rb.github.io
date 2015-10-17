## Layout

`Layout` is a component that is used as a common part on every page.

```ruby
class Layout
  include Inesita::Layout

  def render
    div class: 'container' do
      component NavBar
      component outlet
    end
  end
end
```

`outlet` is an component that will render all sub components.
With this layout all pages will include a `Navbar` component.
