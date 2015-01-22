# Simple Jekyll based styleguide

This is a simple styleguide generator in Jekyll. It is not particularily original but I tried to make it as flexible as possible to correspond to various use cases.

- simple list-based styleguide ([Code for America styleguide](http://codeforamerica.clearleft.com/) by [Clearleft](http://clearleft.com/))
- more complex styleguide using posts or pages ([Lonely Planet "Rizzo" styleguide](http://rizzo.lonelyplanet.com/styleguide/design-elements/colours) by [Lonely Planet](http://www.lonelyplanet.com/))

I used a custom collection rather than posts or pages so I can use those to create more complex styleguides if needed.

## How it works

Define components in the `_components` folder. Each component is output twice (code and preview) using a single include file `_includes/component.html`.

Display components in your templates using simple `{% for %}` tags.

- The `type` variable in components is used to be able to group them (using the `group_by` parameter) or only display a certain type of components (using the `where` parameter) in more complex style guides.
- The `sass` variable is used to reference the sass file for all the CSS rules applied to each component.
- Easy to expand the list of component variables: maybe you need notes or js files. Just update your components YAML front matter and your component template and you're good to go.