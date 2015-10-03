## Application

This is where all magic starts!

```ruby
Inesita::Application.new(
  router: Router,
  store: Store,
  layout: Layout
).mount!($document.body)
```
