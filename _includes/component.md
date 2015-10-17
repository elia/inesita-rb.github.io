## Component

Component is a crutial part.
Lets create simple component named `Clock`

```ruby
class Clock
  include Inesita::Component

  def initialize
    @time = Time.now
  end

  def render
    div class: 'clock' do
      text @time.strftime('%r')
    end
  end
end
```

Now we should mount it to dom element to `<div id="clock"></div>`:

```ruby
$document.ready do
  Clock.new.mount_to($document['clock'])
end
```

It works, but what's the clock that won't refresh ? Let's fix it:

```ruby
class Clock
  include Inesita::Component

  def initialize
    @time = Time.now
    every 1 do
      @time = Time.now
      update_dom
    end
  end

  def render
    div class: 'clock' do
      text @time.strftime('%r')
    end
  end
end
```

Beautiful, clock works like a charm.
We're add a simple block that executes every 1 secound. In this case we re refresh a `@time` variable and update component with `update_dom`
Simple, isn't it ?

Components can be nested. For example add another component, that wraps `Clock` into `code` tag:

```ruby
class CodeClock
  include Inesita::Component

  def render
    code do
      component Clock
    end
  end
end
```

Mount it.

```ruby
$document.ready do
  CodeClock.new.mount_to($document['clock'])
end
```

When components are nested we can pass props to child components like this:

```ruby
class CodeClock
  include Inesita::Component

  def render
    code do
      component Clock, props: { label: 'This is clock' }
    end
  end
end
```

And use it like this:

```ruby
class Clock
  include Inesita::Component

  def initialize
    @time = Time.now
    every 1 do
      @time = Time.now
      update_dom
    end
  end

  def render
    div class: 'clock' do
      span do
        text props[:label]
      end
      text @time.strftime('%r')
    end
  end
end
```


Nice. Now we're move forward, and describe other parts.
