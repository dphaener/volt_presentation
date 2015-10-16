class: center, middle, inverse

# Volt

## Darin Haener

---

class: center, middle, inverse

# What is Volt?

[Volt](https://github.com/voltrb/volt) is a Ruby web framework where your Ruby 
code runs on both the server and the client. It accomplishes this by 
leveraging a Ruby to JavaScript compiler called [Opal](https://github.com/opal/opal).

---

class: center, middle, inverse

# Ever used Angular?

Volt is very, very similar to Angular. It uses two way data bindings to 
acheive lightning fast UI updates.

Because it's so very much like Angular, you have to get yourself out of the
Rails mindset (if you're there), and think of the application architecture
in more of an Angular way.

---

class: middle, inverse

# Controllers are client side

That's right. In Volt all of the controllers run client side code:

```ruby
module Main
  class MainController < Volt::ModelController
    model :store

    def index
      # Add code for when the index view is loaded
    end

    def select_conversation(user)
      params._user_id = user._id
    end

    def is_current_user?(user)
      user.id == Volt.current_user_id 
    end
  end
end
```

---

class: middle, inverse

# Views

Views even look remarkably similar to Angular. It's also very similar to
using the Liquid templating engine.

```erb
<:Title>
  Home

<:Body>
  <h1>Home</h1>

  {{ if Volt.current_user }}
    <div class="row">
      <div class="col-md-4">
      {{ users.each do |user| }}
        {{ unless is_current_user?(user) }}
          <div class="contact {{ if params._user_id == user.id }} active {{ end }}" e-click="select_conversation(user)">
            {{user.name}}
          </div>
        {{ end }}
      {{ end }}
      </div>
    </div>
  {{ end }}
```

---

class: center, middle, inverse

# Persistence

Currently, Volt only supports MongoDB (although it is rumored that both
Postgres and RethinkDB will be supported soon).

This makes for incredibly easy persistence to the database, but at the cost
of possibly not having strong data integrity.

---

# Websockets are free

You heard me right. Probably one of the coolest features that Volt has, is
that Websockets come baked right in, so there's no setup at all.

Let's take a look at the chat demo that I made.....

---

# Thank you
