# Simple Jekyll based styleguide

This is a simple styleguide generator in Jekyll. It is not particularily original but I tried to make it as flexible as possible to correspond to various use cases.

- simple list-based styleguides ([Code for America styleguide](http://codeforamerica.clearleft.com/) by [Clearleft](http://clearleft.com/))
- more complex styleguides using posts or pages ([Lonely Planet "Rizzo" styleguide](http://rizzo.lonelyplanet.com/styleguide/design-elements/colours) by [Lonely Planet](http://www.lonelyplanet.com/))

I used a custom collection (with output set to false) rather than posts or pages so I can use those to create more complex styleguides if needed.

## Demo

Here is what the [default output looks like](http://www.webstoemp.com/jekyllstyleguide).

## How it works

Define components in the `_components` folder. Each component is output twice (code and preview) using a single include file `_includes/component.html`.

- The `type` variable in components is used to be able to group them (using the `group_by` parameter) or only display a certain type of components (using the `where` parameter) in more complex style guides.
- The `sass` variable is used to reference the sass file for all the CSS rules applied to each component.
- Easy to expand the list of component variables: maybe you need notes or js files. Just update your components YAML front matter and your component include and you're good to go.

Display components in your templates using simple `{% for %}` loops.

Simple `{% for %}` loop to display all components (ordered using file names)

```liquid
{% assign entries = site.components %}
{% for entry in entries %}
  {% include component.html %}
{% endfor %}
```

`{% for %}` loop using `group_by` to display components grouped by type

```liquid
{% assign componentsByType = site.components | group_by:"type" %}
{% for type in componentsByType %}
  <h3 class="sg-h2">{{ type.name | capitalize }}</h3>
  {% for entry in type.items %}
    {% include component.html %}
  {% endfor %}
{% endfor %}
```

When creating a more detailed style guides using pages, it is useful to be able to display only a certain type of components in your pages using a `where` parameter in your `{% for %}` loop

```liquid
{% assign entries = site.components | where:"type","buttons" %}
{% for entry in entries %}
  {% include component.html %}
{% endfor %}
```
