## Store

`Store` is a simply a wrapper for your data. You decides how you store it, and how to fetch it.

```ruby
class Store
  include Inesita::Store

  def initialize
    @store = {}
  end

  def set_value(value)
    @store[:value] = value
  end

  def get_value
    @store[:value]
  end
end
```

This is the simplest store, that stores data within Hash. You can use it with your components like this:

```ruby
class Input
  include Inesita::Component

  def change(e)
    store.set_value(e.target.value)
    update_dom
  end

  def render
    input type: "text", class: "form-control", value: store.get_value, onchange: ->(e) { change(e) }
  end
end
```

