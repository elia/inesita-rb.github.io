## Application

We're know how component works, so lets build an application!

`app/application.rb` This is where all magic starts.
Here you can include all project files, external gems etc.
Most important part is `Inesita::Application`.

```ruby
Inesita::Application.new(
  router: Router,
  store: Store,
  layout: Layout
).mount_to($document.body)
```

This is where we configure all parts of our application, and where we mount it.
This application will use `Router` object as a router, `Store` object as a store and `Layout` as a layout.
In this case application will mount in `<body></body>`.
