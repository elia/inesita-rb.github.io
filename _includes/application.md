## Application

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

This is where we configure all parts of our application, and where we mount it. In this case all application lives in `<body>`.
