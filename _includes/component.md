<h2>Component</h2>
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum
</p>

{% highlight ruby %}
class Welcome
  include Inesita::Component

  def render
    dom do
      div class: 'jumbotron text-center' do
        h1 do
          text "Hi, I'm Inesita"
        end
        h4 do
          text 'This is a sample component'
        end
      end
    end
  end
end
{% endhighlight %}